# Odoo API Ecosystem: Technical Deep Dive for Spider

**Research date**: February 2026
**Purpose**: Map the full technical landscape of Odoo's API, schema, ecosystem, and upcoming changes to inform Spider's ontology layer architecture.

---

## 1. Odoo API Capabilities & Limits

### 1.1 Rate Limits by Deployment Type

| Deployment | Rate Limit | Parallel Calls | Notes |
|---|---|---|---|
| **Odoo Online (SaaS)** | ~1 call/sec sustained; ~60 req/min burst | No parallel calls allowed | Acceptable Use Policy enforced; violation can trigger suspension without notice |
| **Odoo.sh** | Higher limits (dedicated hosting mode) | Configurable | "Dedicated hosting mode can be considered as an alternative to lift [SaaS] restriction" |
| **Self-hosted** | No platform-imposed limits | Unlimited | Constrained only by server hardware and PostgreSQL capacity |

**Critical detail**: External API access is **only available on the Custom plan** ($37.40+/user/month). One App Free and Standard plans have no API access at all.

Sources:
- [Odoo Acceptable Use Policy](https://www.odoo.com/acceptable-use)
- [Odoo External API Limitations Forum Thread](https://www.odoo.com/forum/help-1/odoo-external-api-limitations-219797)
- [Odoo SaaS Custom Plan API Access](https://www.odoo.com/forum/help-1/can-we-use-the-external-api-with-odoo-online-in-the-custom-plan-282627)

### 1.2 Bulk Data Export & Pagination Model

**Pagination**: Odoo uses a classic **limit/offset** model.

- **Default limit**: 100 records per `search_read` call (can be overridden)
- **No hard maximum**: You can set `limit` to higher values (500, 1000+), but performance degrades
- **Practical recommendation**: 100-500 records per call, iterating with incrementing `offset`

**Example (XML-RPC/JSON-RPC)**:
```python
models.execute_kw(db, uid, password, 'res.partner', 'search_read',
    [[['is_company', '=', True]]],
    {'fields': ['name', 'email'], 'limit': 500, 'offset': 0}
)
```

**Bulk export strategy**:
- Use `search_count` first to know total records
- Paginate with `search_read` in batches of 200-500
- On SaaS: respect 1 call/sec throttle = ~500 records/sec max throughput
- Use `read_group` for aggregation instead of looping searches (major performance gain)
- Related/nested exports possible: `search_read` can traverse Many2one/Many2many relationships in a single call

**Batch import API**: Odoo also provides dedicated batch APIs for imports, so high-volume ingest does not need to rely on per-record RPC calls.

Sources:
- [Odoo API Pagination Forum](https://www.odoo.com/forum/help-1/how-to-make-pagination-in-json-rpc-api-call-189583)
- [XML-RPC search_read 100 Record Limitation](https://www.odoo.com/forum/help-1/xml-rpc-api-search-read-method-100-records-limitation-216563)
- [Odoo External API 18.0 Documentation](https://www.odoo.com/documentation/18.0/developer/reference/external_api.html)

### 1.3 Webhook / Event System for Real-Time Sync

Odoo has a **native webhook system** (available since Odoo 17, refined in 18/19), built into Studio's Automated Actions:

**Outgoing webhooks** (Odoo sends data out):
- Trigger on: **create, update, delete** events on any model
- Sends HTTP POST with JSON payload to configured URL
- Can specify which **fields** trigger the webhook (granular control)
- Payload includes the changed record's data
- Built-in logging for debugging

**Incoming webhooks** (External system sends data to Odoo):
- Odoo generates a unique webhook URL
- External system POSTs payload to this URL
- Automated action processes and maps the payload to Odoo records

**Limitations**:
- Requires **Odoo Studio** (paid module) for the visual UI
- Alternatively, can use `base_automation` module programmatically
- No guaranteed delivery / retry mechanism in core (need custom or third-party module)
- No native event streaming (no WebSocket/SSE)

**Spider implication**: For real-time sync, Spider can register outgoing webhooks on key models (res.partner, sale.order, account.move, etc.) to receive change notifications. For initial sync, use bulk `search_read` pagination. Hybrid approach recommended.

Sources:
- [Odoo 18.0 Webhooks Documentation](https://www.odoo.com/documentation/18.0/applications/studio/automated_actions/webhooks.html)
- [Odoo 19.0 Webhooks Documentation](https://www.odoo.com/documentation/19.0/applications/studio/automated_actions/webhooks.html)
- [Synchronize Data Using Webhooks - Odoo Experience 2024](https://www.odoo.com/event/odoo-experience-2024-4662/track/synchronize-data-using-webhooks-6359)

### 1.4 Odoo 18 API-Relevant Features

Odoo 18 (released October 2024) did not introduce a new external API protocol but brought:

- **API-first approach**: Clearer, more developer-friendly APIs across modules
- **Enhanced security**: OAuth and JWT support improvements for authentication
- **AI-powered features**: Lead scoring, demand prediction, inventory optimization (relevant for Spider as additional data dimensions)
- **OWL frontend framework**: New JavaScript framework (less relevant for backend API)
- **LinkedIn API integration**: New social media data connectors
- **Improved POS, barcode, payroll** modules with refined data models

The major API shift happens in **Odoo 19** (released October 2025) with the JSON-2 API.

Sources:
- [Odoo 18 Release Notes](https://www.odoo.com/odoo-18-release-notes)
- [Odoo 18 vs 19 Comparison](https://boyangcs.com/odoo-18-vs-odoo-19/)

---

## 2. Odoo 20 Migration: The XML-RPC Deprecation

### 2.1 Confirmed Timeline

| Milestone | Date | Impact |
|---|---|---|
| **Odoo 19 release** | October 2025 | XML-RPC, JSON-RPC **deprecated** (still functional). JSON-2 API introduced. |
| **Odoo 19.1 (SaaS)** | ~Early-Mid 2026 | `/xmlrpc`, `/xmlrpc/2`, `/jsonrpc` endpoints **removed** on Odoo Online |
| **Odoo 20 release** | ~October 2026 | `/xmlrpc`, `/xmlrpc/2`, `/jsonrpc` endpoints **removed** on Odoo.sh and self-hosted |

**This timeline is aggressive.** SaaS customers lose XML-RPC/JSON-RPC access within months. Self-hosted and Odoo.sh customers have until Odoo 20 (fall 2026).

### 2.2 What Replaces It: The JSON-2 API

The replacement is called the **External JSON-2 API** -- not REST, not GraphQL, but a streamlined HTTP+JSON interface.

**Endpoint structure**:
```
POST /json/2/<model>/<method>
```

**Key characteristics**:
- **Authentication**: API key via `Authorization: bearer <key>` header (replaces login/password)
- **Database selection**: Custom HTTP header to select database
- **Request body**: JSON object with method arguments (named parameters required, e.g., `vals_list`)
- **HTTP semantics**: Proper status codes (4xx/5xx for errors -- no more "HTTP 200 even on error")
- **Standard JSON error payloads**
- **API key lifetime**: 90-day max for regular users; admins can create permanent keys
- **Scope**: Covers only the former "object" service (model CRUD + methods). Legacy "db" and "common" services are excluded.

**Example call**:
```bash
curl -X POST https://myodoo.com/json/2/res.partner/search_read \
  -H "Authorization: bearer my-api-key" \
  -H "Content-Type: application/json" \
  -H "X-Odoo-Db: mydb" \
  -d '{"domain": [["is_company", "=", true]], "fields": ["name"], "limit": 100}'
```

**Self-documenting `/doc` endpoint** (new in Odoo 19):
- Available at `https://<instance>/doc`
- Navigable interface showing all models, fields, and public methods
- Generates ready-to-run code snippets in 4 languages (Python, JSON, etc.)
- Can test API calls directly in the browser
- Restricted to "Technical Documentation Users" group
- **Updates in real-time** as modules are installed/modified

### 2.3 Impact on Existing Integrations

- **Every XML-RPC integration must be rewritten** to use JSON-2 by fall 2026
- The migration is relatively straightforward (same model/method semantics, different transport)
- **n8n has already flagged this**: [GitHub issue #21545](https://github.com/n8n-io/n8n/issues/21545) tracks Odoo node using deprecated RPC endpoints
- Self-managed instances can technically "archive and re-install the RPC module" to keep legacy endpoints, but this is **not recommended** beyond Odoo 20

### 2.4 Partners/Integrators Affected

- **7,500 partners worldwide** in the Odoo ecosystem (as of January 2025)
- **86% are smaller operations** -- many with XML-RPC-based tools and scripts
- Every partner with custom integrations, middleware, or reporting tools connecting via XML-RPC/JSON-RPC is affected
- Major platforms (n8n, Make, Zapier, custom ERPNext bridges) must all update their connectors

**Spider opportunity**: Many integrations will break during this transition. Spider can position itself as a "migration-proof" abstraction layer that handles the API transition transparently.

Sources:
- [XMLRPC is Dead. All Hail JSON-2 - Odoo Experience 2025](https://oduist.com/blog/odoo-experience-2025-ai-summaries-2/286-xmlrpc-is-dead-all-hail-json-2-288)
- [Odoo Experience 2025 - API 101](https://oduist.com/blog/odoo-experience-2025-ai-summaries-2/177-odoo-api-101-how-does-it-work-and-what-s-new-in-odoo-19-179)
- [Odoo 19.0 External JSON-2 API Documentation](https://www.odoo.com/documentation/19.0/developer/reference/external_api.html)
- [Odoo 19.0 External RPC API (Deprecated)](https://www.odoo.com/documentation/19.0/developer/reference/external_rpc_api.html)
- [n8n GitHub Issue - Deprecated RPC Endpoints](https://github.com/n8n-io/n8n/issues/21545)
- [Odoo Partner Ecosystem](https://alten.capital/blog/odoo-services-partner-ecosystem)

---

## 3. Odoo Schema Structure for Ontology Mapping

### 3.1 Schema Standardization Across Versions (14-18)

**Core models are highly stable** across versions. The fundamental data model (res.partner, sale.order, account.move, product.product, stock.move) has been consistent since at least Odoo 10. What changes between versions:

| Change Type | Frequency | Examples |
|---|---|---|
| New fields added to existing models | Every version | New computed fields, tracking fields |
| Field type changes | Rare but impactful | Odoo 17+: some Text fields became JSONB |
| New models added | Common (new features) | New AI/analytics models in v18 |
| Models removed/merged | Rare | account.invoice merged into account.move in v13 |
| Module restructuring | Occasional | UoM packaging unified in v19 |

**Key migration fact**: Odoo only supports **3 latest versions** (currently 16, 17, 18). Customers on 14/15 are on unsupported versions. Official migration requires stepping through each version (14->15->16->17->18), though some providers offer direct jumps.

**Spider implication**: The ontology layer should version-tag its model mappings and handle field presence/absence gracefully. The core ~20 models are safe anchors; peripheral models need per-version discovery.

Sources:
- [Odoo 18.0 Upgrade Documentation](https://www.odoo.com/documentation/18.0/administration/upgrade.html)
- [Odoo 16 to 18 Migration Guide](https://www.webbycrown.com/odoo-16-to-18-migration-guide/)

### 3.2 Core Models Present in Every Odoo Instance

These models exist in every Odoo installation (base module):

| Model | Description | Typical Relationships |
|---|---|---|
| `res.partner` | Contacts (companies + individuals) | 68+ related tables |
| `res.users` | System users | Extends res.partner |
| `res.company` | Multi-company management | Root of hierarchy |
| `res.currency` | Currencies | Used across all financial models |
| `ir.model` | Model metadata (meta-model) | Lists all installed models |
| `ir.model.fields` | Field metadata | Lists all fields of all models |
| `ir.attachment` | File attachments | Linked to any record |
| `ir.sequence` | Sequence generators | For invoice numbers, etc. |
| `ir.config_parameter` | System parameters | Key-value config store |

These models are added with common modules (Sales, Accounting, Inventory, Purchase):

| Model | Module | Description |
|---|---|---|
| `sale.order` / `sale.order.line` | Sales | Sales orders (22+ relationships) |
| `account.move` / `account.move.line` | Accounting | Invoices, bills, journal entries |
| `account.account` | Accounting | Chart of accounts |
| `account.journal` | Accounting | Journals (bank, sales, purchase) |
| `account.tax` | Accounting | Tax definitions |
| `product.product` / `product.template` | Product | Product catalog |
| `stock.move` / `stock.picking` | Inventory | Inventory movements |
| `purchase.order` / `purchase.order.line` | Purchase | Purchase orders |
| `hr.employee` | HR | Employee records |
| `crm.lead` | CRM | Leads and opportunities |
| `project.project` / `project.task` | Project | Project management |

Sources:
- [Odoo 14 Database Model: Sale Order (MCD)](https://codingdodo.com/sale-order-database-model/)
- [Odoo res.partner GitHub Source](https://github.com/odoo/odoo/blob/14.0/odoo/addons/base/models/res_partner.py)
- [Odoo account.move GitHub Source](https://github.com/odoo/odoo/blob/14.0/addons/account/models/account_move.py)

### 3.3 Custom Fields: ir.model.fields

Odoo handles custom fields through the `ir.model.fields` meta-model:

- **Studio-created fields** are stored with `state="manual"` in `ir.model.fields`
- Custom fields follow naming convention: `x_` prefix (e.g., `x_custom_rating`)
- **Python-defined fields** (from modules) have `state="base"`
- **Computed fields** cannot be added via `ir.model.fields` (require Python code)
- Defaults and onchange logic cannot be set via `ir.model.fields` alone

**Field metadata available via API**:
- `name`: Technical field name
- `field_description` (string): Human-readable label
- `ttype`: Field type (char, integer, float, many2one, one2many, many2many, selection, boolean, date, datetime, text, html, binary, monetary)
- `relation`: Target model for relational fields
- `required`: Mandatory flag
- `readonly`: Read-only flag
- `store`: Whether persisted in database
- `depends`: Dependencies for computed fields

### 3.4 Programmatic Schema Auto-Discovery

**Method 1: Using `fields_get()` per model**
```python
# Get all field definitions for a model
fields = models.execute_kw(db, uid, password,
    'res.partner', 'fields_get',
    [], {'attributes': ['string', 'help', 'type', 'relation', 'required']})
```

**Method 2: Full schema enumeration via ir.model + ir.model.fields**
```python
# Step 1: Get all models
all_models = models.execute_kw(db, uid, password,
    'ir.model', 'search_read',
    [[]], {'fields': ['model', 'name']})

# Step 2: For each model, get all fields
for model in all_models:
    fields = models.execute_kw(db, uid, password,
        'ir.model.fields', 'search_read',
        [[['model_id', '=', model['id']]]],
        {'fields': ['name', 'field_description', 'ttype', 'relation', 'required', 'readonly']})
```

**Method 3: Odoo 19+ `/doc` endpoint**
- Browse `https://<instance>/doc` for interactive schema exploration
- Auto-generates documentation for all installed models
- Shows fields, methods, parameters, and return types
- Updates in real-time as modules change

**Method 4: Schema diff tool** (community)
A [community script by sebalix](https://gist.github.com/sebalix/8cb0acc2cff419f4529e) uses `oerplib` to:
1. Connect to an Odoo instance
2. Query `ir.model` for all registered models
3. Call `fields_get()` for each model
4. Serialize to JSON
5. Compare two snapshots to detect added/removed/modified models and fields

**Spider architecture recommendation**: On initial connection to a customer's Odoo instance, Spider should:
1. Enumerate all models via `ir.model`
2. Fetch all field definitions via `ir.model.fields` or `fields_get()`
3. Store the schema snapshot as a versioned artifact
4. Detect custom fields (prefix `x_`) and `state="manual"` fields
5. Map discovered schema to Spider's ontology layer
6. Set up webhooks for schema change detection (new fields/models installed)

Sources:
- [Odoo REST API: Inspection and Introspection](https://odoo-restapi.readthedocs.io/en/latest/inspection_and_introspection/inspection_and_introspection.html)
- [Odoo Forum: Retrieve Complete Model Schema via XML-RPC](https://www.odoo.com/fr_FR/forum/aide-1/how-to-retrieve-complete-model-schema-via-xml-rpc-for-documentation-288086)
- [Schema Diff Script - GitHub Gist](https://gist.github.com/sebalix/8cb0acc2cff419f4529e)
- [Odoo 19 API Documentation Module](https://numla.com/blog/erp-15/odoo-19-api-documentation-module-explained-308)

---

## 4. Odoo Ecosystem in France

### 4.1 Market Size and Presence

| Metric | Value |
|---|---|
| Odoo customers in France | ~1,368 (12.8% of global) |
| Official Odoo partners in France | **123** (10 Gold, 21 Silver, 92 Ready) |
| France rank in Odoo ecosystem | **Largest national market** |
| Odoo global users | 13M+ |
| Odoo global revenue (2025) | ~$552M (billings ~EUR650M) |
| Odoo valuation | EUR5B (November 2024 round) |
| Global partner count | 7,500 |

### 4.2 Major French Odoo Integrators

| Partner | Tier | Location | Team Size | Revenue | References |
|---|---|---|---|---|---|
| **Apik** | Gold | Baden (Brittany) | 40+ employees | EUR4M | 278 references |
| **Captivea** | Gold | Paris + Angers | ~30 employees | N/A | 124 references, 17+ years |
| **Camptocamp** | Gold (OCA) | Paris, Chambery (+ CH, DE) | 130 employees (group) | N/A | Historical partner since 2006 |
| **IROKOO** | Gold | Ludon-Medoc | N/A | N/A | 177 references |
| **ArkeUp eDoo** | Gold | Paris | N/A | N/A | 96 references |
| **Sudokeys** | Gold | Montauban | N/A | N/A | 98 references |
| **Nalios France** | Gold | Paris | N/A | N/A | 83 references, 100% rating |
| **Scalizer** | Gold | Nantes | N/A | N/A | Retail, utilities focus |
| **Port Cities France** | Gold | Marseille | N/A | N/A | International network |
| **Smile** | Silver/OCA | Paris | Large (200+ group) | N/A | Open source leader in France |
| **OKTEO** | Silver | France | N/A | N/A | Manufacturing focus |

### 4.3 Typical Odoo Implementation Cost for French PME

| Company Size | Typical Budget | Approach |
|---|---|---|
| Micro (<10 employees) | EUR5,000-15,000 | Direct with Odoo, Success Packs |
| PME (10-50 employees) | EUR15,000-50,000 | Partner-led, 2-4 modules |
| ETI (50-250 employees) | EUR50,000-150,000+ | Partner-led, full suite, customization |
| Large (250+ employees) | EUR150,000-500,000+ | Multi-site, multi-company, heavy custom |

**Licensing costs**:
- Standard plan: ~EUR29/user/month (annual)
- Custom plan (required for API): ~EUR35/user/month (annual), increasing to ~EUR44 after year 1
- Odoo.sh hosting: additional EUR72-720/month depending on workers

### 4.4 Odoo vs Sage vs Cegid/EBP in France

| Dimension | Odoo | Sage 100 | Cegid XRP Flex | EBP (now Cegid) |
|---|---|---|---|---|
| **Target** | SMB to mid-market, tech-forward | Established SMBs, accounting-heavy | French mid-market, finance-focused | Micro to small businesses |
| **Price/user/mo** | From EUR25 | EUR80-100 | EUR varies (higher) | Budget-friendly |
| **Open source** | Yes (Community) | No | No | No |
| **API access** | Full (Custom plan) | Limited | Limited | Minimal |
| **Growth trend** | Fastest growing in # of users | Stable/mature | Stable, Cegid acquiring | Acquired by Cegid (2024) |
| **Market position** | Challenger, gaining fast | Incumbent reference | Strong in accounting/compliance | Legacy, budget segment |
| **France specifics** | Strong community, many partners | Dominant in accounting | Deep French compliance | Wide TPE adoption |

**Key insight**: SAP dominates large enterprises in value, Microsoft Dynamics 365 and Sage are widespread in French SMBs, but **Odoo has the strongest growth rate** in number of users. Cegid's acquisition of EBP in 2024 consolidates the traditional French ERP market, creating a clearer two-horse race: Cegid (legacy) vs Odoo (modern).

Sources:
- [Odoo Partners France Directory](https://www.odoo.com/partners/country/france-74)
- [Odoo Users by Country](https://www.spreadthoughts.com/odoo-users-by-country/)
- [Odoo Partner Ecosystem Analysis](https://alten.capital/blog/odoo-services-partner-ecosystem)
- [Best Odoo Development Company in France 2026](https://www.allodoojobs.com/blog/best-odoo-development-company-in-france-provider-selection-guide/)
- [Apik Partner Page](https://www.odoo.com/partners/apik-732280)
- [Odoo vs EBP Comparatif PME](https://www.drakkar.io/blog/odoo-vs-ebp-comparatif-pme)
- [ERP SaaS PME France 2025](https://deeops.fr/blog/erp-saas/)
- [Comparatif ERP PME 2025](https://www.apogea.fr/votre-besoin/erp-pme/)
- [Odoo Revenue and Valuation](https://getlatka.com/companies/odoo-sa)

---

## 5. Integration Platforms & Connection Strategy

### 5.1 Nango + Odoo

**Nango does not currently list Odoo as a supported integration.** Out of 600+ supported APIs across 400+ platforms, Odoo is absent from Nango's catalog. The only ERP listed is Apaleo.

This means Spider cannot rely on Nango for Odoo connectivity and would need to build a custom connector.

Source: [Nango API Integrations Catalog](https://nango.dev/api-integrations)

### 5.2 iPaaS/Integration Platforms Supporting Odoo

| Platform | Odoo Support | Connector Quality | Best For |
|---|---|---|---|
| **n8n** | Native node, good | Deep, 1000+ integrations | Technical teams, self-hosted, open-source |
| **Make (Integromat)** | Native module | Good, visual builder | No-code teams, mid complexity |
| **Zapier** | Listed but basic | Surface-level triggers/actions | Simple automations |
| **Prismatic** | Available | Embedded iPaaS for B2B SaaS | Building customer-facing integrations |
| **Paragon** | Available | Embedded iPaaS | B2B SaaS product integrations |
| **Nango** | **Not available** | N/A | N/A for Odoo |

**n8n caveat**: Already flagged that their Odoo node uses deprecated RPC endpoints and needs migration to JSON-2.

### 5.3 Best Approach for Spider to Connect to Customer Odoo Instances

**Recommended architecture** (in priority order):

**Option A: API Key Authentication (Recommended)**
- Customer generates an API key in their Odoo instance (Settings > Users > API Keys)
- Spider stores the key securely (encrypted at rest)
- Spider uses JSON-2 API (for Odoo 19+) or JSON-RPC (for 18 and below)
- Works on: SaaS (Custom plan), Odoo.sh, self-hosted
- **Pros**: Simple, no OAuth dance, works everywhere
- **Cons**: Key management burden on customer; must be on Custom plan for SaaS

**Option B: OAuth 2.0 (Aspirational)**
- Requires customer to configure Odoo as OAuth provider
- More complex setup but better UX for SaaS
- OAuth endpoints: `/restapi/1.0/common/oauth2/authorize` and `/restapi/1.0/common/oauth2/access_token`
- **Pros**: Standard flow, auto-refresh tokens
- **Cons**: Requires REST API module (community/third-party); not native in all deployments

**Option C: Direct Database Access (Anti-pattern for SaaS, viable for on-prem)**
- Direct PostgreSQL read replica connection
- **Pros**: Fastest bulk reads, no rate limits, real-time CDC possible
- **Cons**: Only works for self-hosted; bypasses Odoo security layer; fragile to schema changes; breaks Odoo TOS for SaaS/Odoo.sh

**Spider recommendation**: Build for **Option A (API Key + JSON-2)** as the primary path. Design the connector to auto-detect the Odoo version and use JSON-2 or JSON-RPC accordingly. For Odoo 19+, use the `/doc` endpoint for automatic schema discovery.

Sources:
- [Odoo API Key Authentication](https://www.odoo.com/forum/help-1/how-i-can-auth-my-user-to-access-odoo-with-api-key-or-access-token-181562)
- [Odoo OAuth2 REST API Documentation](https://odoo-restapi.readthedocs.io/en/latest/connection/logging_in/oauth2_authentication.html)
- [n8n Odoo Integration](https://n8n.io/integrations/odoo/)
- [n8n Deprecated RPC Issue](https://github.com/n8n-io/n8n/issues/21545)

---

## 6. E-Invoicing 2026 (Factur-X / Peppol)

### 6.1 September 2026 Obligation: What Exactly Is Required

The French government mandates electronic invoicing for all B2B transactions between VAT-registered companies in France, with a phased rollout:

| Date | Obligation | Who |
|---|---|---|
| **1 September 2026** | **Receive** electronic invoices | **All companies** (including TPE/PME) |
| **1 September 2026** | **Emit** electronic invoices | **Grandes entreprises** (large) and **ETI** (mid-sized) |
| **1 September 2027** | **Emit** electronic invoices | **PME** (small) and **micro-enterprises** |

**Key requirements**:
- Invoices must be transmitted via a **PDP** (Plateforme de Dematérialisation Partenaire) certified by the State, or via the public portal **Chorus Pro**
- Accepted formats: **Factur-X** (hybrid PDF+XML), **UBL**, **CII**
- PeppolBIS and EDIFACT also supported for interoperability
- **E-reporting obligation**: Tax-relevant transaction data must also be reported to the DGFiP (Direction Generale des Finances Publiques)
- DGFiP became the **Peppol France authority** in July 2025
- All French PDPs must integrate into the **Peppol network** for inter-PDP communication

### 6.2 Odoo 18/19 E-Invoicing Support

| Capability | Status |
|---|---|
| **Factur-X format** | Supported natively (PDF + embedded XML) |
| **UBL XML** | Supported for Peppol transactions |
| **Peppol integration** | Native -- send/receive via Peppol access point |
| **Chorus Pro** | Supported via Peppol network (module: France - Factur-X integration with Chorus Pro) |
| **PDP certification** | **Odoo is in the process of becoming a certified PDP** |
| **PDP pricing** | Odoo plans to offer PDP services **for free** (vs competitors using credit/per-doc pricing) |

**Odoo's competitive move**: By offering free PDP services, Odoo is using the e-invoicing mandate as a **customer acquisition funnel** -- companies that adopt Odoo for compliance may expand into other modules.

### 6.3 Market Opportunity for Spider

The e-invoicing 2026 mandate creates a **massive window of opportunity** for Spider:

**1. Forced Upgrades**
- Companies on Odoo 14/15/16 must upgrade to 17/18/19 for e-invoicing compliance
- Every upgrade is a moment of disruption where additional services can be sold
- Partners will be overwhelmed with migration projects through 2026-2027

**2. Data Quality Imperative**
- E-invoicing requires clean, structured data (correct VAT numbers, addresses, product codes)
- Companies will need to audit and clean their Odoo data before September 2026
- Spider's ontology layer can help identify data quality issues across connected systems

**3. Multi-System Reconciliation**
- Many French PMEs use Odoo alongside other tools (Sage for accounting, custom tools for industry-specific needs)
- E-invoicing requires consistent data across all systems
- Spider as the ontology layer can ensure invoicing data is consistent across the stack

**4. Timeline Pressure**
- September 2026 for reception = **~7 months from now**
- September 2027 for PME emission = **~19 months from now**
- Partners and integrators are scrambling -- Spider can ride this wave as an add-on service

**5. Peppol as Cross-Border Bridge**
- Once companies are on Peppol for French compliance, they can transact electronically across 40+ countries
- Spider's ontology layer becomes more valuable as the data network expands internationally

Sources:
- [Odoo Electronic Invoicing France](https://www.odoo.com/electronic-invoicing/france)
- [Odoo 18 E-Invoicing Documentation](https://www.odoo.com/documentation/18.0/fr/applications/finance/accounting/customer_invoices/electronic_invoicing/france.html)
- [FNFE-MPE: Reforme de la Facture Electronique 2026](https://fnfe-mpe.org/reforme-de-la-facture-electronique-cap-2026/)
- [Service Public: Facturation Electronique](https://entreprendre.service-public.gouv.fr/actualites/A15683)
- [Facturation Electronique: PDP, Peppol et Perspectives 2026](https://www.nexelans.fr/blog/ta-odoo-3/facturation-electronique-en-france-pdp-peppol-et-perspectives-2026-51)
- [Cegid: Calendrier Facture Electronique 2026-2027](https://www.cegid.com/fr/facture-electronique-obligatoire/calendrier-facture-electronique/)
- [Pennylane: Dates Cles Facturation Electronique](https://www.pennylane.com/fr/fiches-pratiques/facture-electronique/facturation-electronique-dates-cles-et-calendrier)

---

## Summary: Key Takeaways for Spider Architecture

### Technical Decisions

1. **Build on JSON-2 API first**, with fallback to JSON-RPC for Odoo 18 and below. Do not invest in XML-RPC at all.
2. **Schema discovery via `ir.model` + `ir.model.fields`** is the foundation of Spider's ontology auto-mapping. On Odoo 19+, supplement with the `/doc` endpoint.
3. **Pagination at 200-500 records/batch** with 1 req/sec pacing for SaaS customers. Self-hosted customers can go faster.
4. **Webhooks for real-time sync** on key models (res.partner, sale.order, account.move). Requires Odoo Studio or base_automation.
5. **API Key authentication** is the pragmatic path. OAuth is nice-to-have but not universally available.

### Market Timing

1. **XML-RPC death (2026)** forces every Odoo integration to migrate -- Spider can be the new-generation connector.
2. **E-invoicing mandate (Sept 2026)** forces SMB upgrades and data cleanup -- perfect entry point for Spider's value proposition.
3. **France has 123 official partners + 1,368 customers** as the primary beachhead market.
4. **Nango does not support Odoo** -- Spider must build its own connector, but this is also a competitive moat.

### Risk Factors

1. **SaaS rate limits (1 call/sec)** constrain initial sync speed for large datasets. A 100K-record initial sync takes ~200 seconds minimum.
2. **Custom plan requirement** for API access means some small customers on Standard plans cannot use Spider without upgrading.
3. **Schema drift between versions** requires Spider to handle field presence/absence gracefully.
4. **Odoo becoming a free PDP** positions it as increasingly sticky -- customers who adopt Odoo for e-invoicing are less likely to switch, but more likely to need integration with other systems (Spider's sweet spot).
