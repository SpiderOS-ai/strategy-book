# Cas Jordan -- Spider's First Beta Test (ComPrivee)

> **Author:** Nathan Menard + Jordan (CEO ComPrivee)
> **Date:** February 2026
> **Nature:** The FIRST concrete beta test of Spider's "Service as a Software" model. Jordan is Nathan's close friend.
> **Reliability:** HIGH on the operational data (726 campaigns, real financials, real workflow). The strategy doc is Nathan's plan for how Spider addresses this.
> **Key insight:** This is THE proof-of-concept. Nathan says "2h30 of work" to build a prototype that eliminates triple data entry. Jordan will be paying -- amount TBD.
> **Person:** Jordan = CEO ComPrivee, outdoor advertising media agency, Normandy. About to launch Verian Advisory (international consulting).

---

## 1. ComPrivee Profile

### The Business

ComPrivee is an outdoor advertising media agency based in Normandy (Herouville-Saint-Clair, near Caen). They plan and execute advertising campaigns for clients -- primarily outdoor billboards, but also radio, digital, and LED. Their work spans from media recommendation through to campaign reporting. Legal entity: SARL, capital 10,000 EUR, SIREN 852.110.592.

Jordan (full name Jordan Lefranc) is about to launch a second structure called **Verian Advisory** -- an international consulting firm built on top of ComPrivee. Any system built for ComPrivee must be duplicable to Verian.

### Key Figures (2025 actuals, from Notion export)

| Metric | Value |
|---|---|
| CA Total (revenue) | 1,145,304.61 EUR |
| Marge (margin) | 311,325.71 EUR |
| Average margin rate | 27.2% |
| Campaign lines tracked | 726 |
| Unique clients | 73 |
| Unique media/advertising networks | 32 |
| Sole printer | Publitex (173 print jobs) |

### The Team

| Person | Role | Primary Tools | Key Tasks |
|---|---|---|---|
| Jordan | CEO / Commercial Director | UaG, Sheets, Notion | Strategy, client relations, media plan construction, network negotiations |
| Eline | Marketing / Digital / CM | Notion, Sheets | Paid media management, community management, ComPrivee's own marketing |
| Audrey | Admin Coordination | Sheets, Notion, Pennylane | Notion data entry, Pennylane invoicing, payment follow-up, purchase order tracking, general admin |
| Freelance 1 | Operational support (new) | -- | Content creation, paid media, photos, videos |
| Freelance 2 | Occasional | -- | Motion design, creative work |

### Constraints and Realities

- **Zero internal code capability.** Solution must be maintainable without a developer on staff.
- **Loi Sapin compliance.** French law mandating transparency on advertising costs and mandates -- non-negotiable.
- **800+ campaigns in flight.** Transition must be progressive, no operational disruption.
- **Sensitive data.** Negotiated margins, client-specific rates, confidential commercial terms.

---

## 2. The Problem: Triple Data Entry and the 9-Step Workflow

### The Core Pain

Every campaign's data is entered **three times** in three disconnected tools, with zero automatic bridges between them:

| Entry | Tool | Content | Who |
|---|---|---|---|
| 1st entry | Google Sheets | Full media plan: dates, networks, quantities, rates, fees, totals | Jordan / Audrey / Eline |
| 2nd entry | Notion | Same data + statuses, deliveries, addresses, operational tracking (33+ fields per campaign) | Jordan / Eline / Audrey |
| 3rd entry | Pennylane | Invoicing data manually extracted from Notion | Audrey |

**Impact:** With 726+ campaign lines per year, each containing multiple media entries, this represents hundreds of hours of avoidable data entry -- plus transcription errors and inconsistencies between tools.

### The 9-Step Campaign Workflow

| Step | Description | Tool(s) | Irritant |
|---|---|---|---|
| 1. Brief client | Receive brief: catchment area, dates, budget, objectives | Email / Phone | No standard form, info scattered |
| 2. Analysis & recommendation | Research suitable media: types, formats, availability, zones. Consult UaG software + call networks | L'Usine a Gaz (UaG), phone, email | Dependent on network response times (variable delays). Exception: some media with fixed negotiated rates |
| 3. Media plan construction | Manual creation: dates, periods, networks (logos inserted), quantities, formats. Calculate: purchase + commission (13-15%) + monitoring (85/150 EUR) + fees. Insert network maps (UaG links, Mixture) | Google Sheets | 100% manual. Hand calculations. Logos dragged one by one. High error risk -- and errors are observed |
| 4. Client validation | Send plan via Drive link, back-and-forth, modifications | Email + Sheets | No versioning. Modifications by email = no clean audit trail. Fictional checkbox |
| 5. Network ordering | Re-contact networks, verify availability still holds. Sign purchase orders | Email / Phone | Manual process, no centralized PO tracking |
| 6. Notion entry | Once validated, re-enter line by line into Notion: network, dates, client, rates, delivery addresses, quantities, statuses | Notion | DOUBLE ENTRY. 33+ fields per campaign. Time-consuming and error-prone. Source of bugs |
| 7. Creative production (D-28) | Remind client for artwork/creatives. Or prepare visuals per brief, validation rounds. Order posters (Publitex), radio recordings (studio). Client validation then transfer to networks | Email / Notion | Manual reminders, no automatic alerts |
| 8. Launch & tracking | Launch campaign. Track deliveries and transport. Collect photos and reports | Notion / Email / Canva | Delivery tracking scattered, manual reporting |
| 9. Invoicing | Transfer Notion data to Pennylane to generate invoices (start of month or start of campaign) | Notion to Pennylane | TRIPLE ENTRY. Everything re-entered manually into Pennylane |

### The 5 Tool Stack (None Connected)

| Tool | Current Role | Strengths | Limits |
|---|---|---|---|
| Google Sheets | Media plan construction (production tool) | Flexible, collaborative, known by team | Manual calculations, no rate database, no Notion connection |
| Notion | Operational dashboard (internal CRM) | Kanban view, campaign tracking, relational database | Chokes on volume (800+ campaigns x 33+ fields across years), not connected to other tools |
| Pennylane | Invoicing and accounting | Compliant, used by accountant | Zero inbound connection, 100% manual entry |
| L'Usine a Gaz (UaG) | Market data for outdoor advertising (availability, networks) | Exclusive outdoor advertising market data | No known API, manual consultation only |
| Email | Client and network communication | Universal | No centralization, no structured tracking |

**Key statement from the presentation:** "Aucune connexion automatique entre ces outils. Chaque transfert de donnees est fait a la main." (No automatic connection between these tools. Every data transfer is done by hand.)

### Identified Problems (ranked by severity)

1. **CRITICAL -- Triple data entry.** The #1 problem. Each campaign entered 3x in 3 tools with no automatic bridge. Source #1 of time loss and errors.
2. **HIGH -- Notion saturated.** 800+ campaigns x 33+ fields, accumulated over years. Macs struggle to load databases. Daily friction for Eline and Audrey.
3. **HIGH -- Manual calculations on media plans.** Rates calculated manually each time: network price + commission (typically 15%) + monitoring (often 150 EUR) + miscellaneous fees (posters, creatives, motion design). No centralized rate database. No automated formulas. Each quote built from scratch.
4. **MEDIUM -- No automatic alerts.** Creative reminders at D-28 before launch are done manually. No system alerts on key deadlines. Risk of missing critical dates relies entirely on human vigilance.
5. **MEDIUM -- Manual reporting.** Campaign reports (photos, results, KPIs) assembled by hand. No standardized template, no automatic generation.

---

## 3. Spider Phase 0 Plan -- What Nathan Proposes

### From the spider-strategy.docx

Spider's Phase 0 is explicitly built around Jordan as the single first client:

**Phase 0: Jordan (Weeks 1-4) -- Single client. Single process. Single price. Minimum viable everything.**

| Parameter | Value |
|---|---|
| Client | Jordan (ComPrivee, outdoor advertising, 1.16M EUR revenue, 800 campaigns/year) |
| Service | Managed campaign operations. Jordan sends the brief, Drakkar/Spider handles everything |
| Price | 990 EUR/month, standard Drakkar invoice. First 30 days free |
| Team | 1 Drakkar consultant + AI tools. No Spider branding. No separate entity |
| Internal tracking | Time per campaign (human vs AI), error rate, client satisfaction, unprompted expansion requests |

### What Jordan Wants to Achieve (Target Workflow)

The objective is NOT to change all tools, but to eliminate the triple entry and automate repetitive tasks:

1. **Single source of truth.** Each piece of data entered once, then auto-propagated to other tools. Media plan, once built, directly feeds operational tracking and invoicing with no additional human intervention.
2. **Automated calculations.** A centralized rate database with network rates, commission rules, monitoring costs, and standard fees. Media plan auto-calculates as soon as a network and format are selected.
3. **Smart alerts.** Automatic notifications at D-28 for creatives, alerts on unreceived purchase orders, invoicing reminders. The team reacts instead of manually anticipating.
4. **Fluid invoicing.** When a campaign is validated and launched, invoicing data flows automatically to Pennylane (or the chosen invoicing tool). No more re-entry.
5. **Lightweight and performant Notion.** Notion stores only macro piloting data (statuses, key dates, alerts). Granular data stays in the production tool. Result: Notion becomes fluid and useful again.

### Expected Impact (from presentation)

| Zone | Today | Tomorrow | Estimated Gain |
|---|---|---|---|
| Media plan creation | Manual calculations | Auto calculations | 30-40% |
| Notion data entry | Complete re-entry | Auto-populated | 80-90% |
| Invoicing | Re-entry into Pennylane | Auto-generated | 90% |
| Creative reminders | Manual (memory) | Auto alerts at D-28 | 100% |
| Error risk | High (3 entries) | Minimal (1 entry) | Massive reduction |

### Jordan's Questions for Nathan

**Architecture:**
- What tool should become the central source of truth? Sheets, Notion, Airtable, Odoo, other?
- Should Notion be kept or replaced by a tool better suited to the volumes?
- What automation layer do you recommend?

**Technical feasibility:**
- Does Pennylane have a sufficiently open API to automate invoicing?
- L'Usine a Gaz (UaG): No API, nothing accessible, database too large. Jordan will manually load network map links.
- Automated PDF generation for media plans: what approach?

**Vision:**
- How to structure the system so it is duplicable to Verian Advisory?

---

## 4. Financial Model (Spider strategy document)

### Unit Economics Target

| Metric | Phase 1 (Human-Heavy) | Phase 3 (AI-Heavy) |
|---|---|---|
| Avg Revenue / Client / Month | 990 EUR | 1,500-2,500 EUR |
| Human Time / Client / Month | 15-20 hours | 3-5 hours |
| AI Compute Cost | 50-100 EUR | 150-300 EUR |
| Gross Margin | 30-40% | 65-80% |
| AI / Human Ratio | 20% AI / 80% Human | 80% AI / 20% Human |

### Revenue Trajectory

| Period | Clients | Avg MRR/Client | Monthly Rev | Annual Rate |
|---|---|---|---|---|
| Month 3 | 3-5 | 990 EUR | 3-5K EUR | 36-60K EUR |
| Month 6 | 8-12 | 1,200 EUR | 10-14K EUR | 120-170K EUR |
| Month 12 | 20-30 | 1,500 EUR | 30-45K EUR | 360-540K EUR |
| Month 24 | 80-150 | 1,800 EUR | 144-270K EUR | 1.7-3.2M EUR |

### Jordan Cost Comparison (Why Spider at 990 EUR/month)

| Option | Monthly Cost | Hours Saved | Availability | Scaling |
|---|---|---|---|---|
| Part-time assistant | 1,500 EUR | ~80h | 35h/week | Hire another |
| BPO service | 2-4K EUR | ~100h | Business hours | Linear cost |
| DIY (Zapier + ChatGPT) | 50-200 EUR | Variable | If it works | Owner maintains |
| Spider | 990 EUR | ~120h equivalent | 24/7, supervised | Add agents |

### Phased Execution Plan

| Phase | Timeline | Description |
|---|---|---|
| Phase 0 | Weeks 1-4 | Jordan only. Single process, single price. Billed as Drakkar. No product dev beyond internal tools |
| Phase 1 | Months 2-4 | 5 Drakkar clients across different functions. 500-2,000 EUR/month each. Track AI/human ratio, expansion requests, edge cases. Build shared knowledge base |
| Phase 2 | Months 5-8 | Productization. Standardized onboarding. Supervision dashboard. 14-day free trials. Spider branding begins. 3-5 agent catalog |
| Phase 3 | Months 9-12 | Free assistant connected to Odoo. Proactive recommendations. Assistant becomes primary sales channel |
| Phase 4 | Year 2 | Platform + partners. Certify external partners. Drakkar retains premium status. Separate entity if traction warrants |

---

## 5. Hypotheses to Validate (H1-H6)

| # | Hypothesis | How We Test | Kill Criteria |
|---|---|---|---|
| H1 | SMB owners will pay 500-2,000 EUR/mo for managed back-office operations | Sell to 5 Drakkar clients within 90 days | < 3 clients convert, or > 50% churn in 3 months |
| H2 | AI handles 50%+ of tasks with human supervision within 6 months | Track AI/human ratio per process monthly | Ratio stays < 40% AI after 6 months |
| H3 | Clients expand from 1 to 2-3 processes within 6 months | Track unprompted expansion requests | < 30% of clients request expansion |
| H4 | Operational ontology transfers across clients in same vertical | Measure onboarding time: Client 1 vs Client 5 | Client 5 takes > 60% of Client 1's time |
| H5 | The "hire an agent" metaphor converts better than "buy a subscription" | A/B test messaging in sales conversations | No measurable conversion difference |
| H6 | Free diagnostic converts at 40%+ to paid engagement | Run diagnostic on 20 Odoo prospects | Conversion < 20% |

### Decision Gates

| Gate | Timing | Question | Proceed If |
|---|---|---|---|
| G1 | Week 4 | Does Jordan renew after free month? | Yes + measurable value delivered |
| G2 | Month 3 | Do we have 3+ paying clients? | 3+ clients at 500+ EUR with < 20% churn |
| G3 | Month 6 | Is AI/human ratio improving? | 50%+ AI on at least 2 processes |
| G4 | Month 9 | Should we build the assistant? | 5+ agents operational, ontology covers 2+ verticals |
| G5 | Month 12 | Should Spider become a separate entity? | 20+ clients, 30K+ EUR MRR, path to 65%+ margins |
| G6 | Month 18 | Should we raise capital? | PMF confirmed, unit economics validated, partner demand exists |

---

## 6. Raw Data Summary -- The 726 Campaign Lines

### Overview

The Notion export (Pilotage 2025 database) contains 726 individual campaign line items for 2025. This is the actual operational data that would flow through Spider's system.

### Campaign Status Distribution

| Status | Count | % |
|---|---|---|
| Termine (completed) | 655 | 90.2% |
| Reporte (postponed) | 32 | 4.4% |
| Annule (cancelled) | 14 | 1.9% |
| Pas commence (not started) | 13 | 1.8% |
| En cours (in progress) | 12 | 1.7% |

### Invoicing and Payment Status

| Metric | Yes | No |
|---|---|---|
| Facture (invoiced) | 686 (94.5%) | 40 (5.5%) |
| Paye (paid) | 441 (60.7%) | 285 (39.3%) |

Note: 39.3% unpaid is a significant receivables management opportunity -- a future Spider agent target.

### Formats (Media Types)

| Format | Count | Description |
|---|---|---|
| 2m2 | 167 | Standard small outdoor poster |
| Led | 109 | LED digital screens |
| 8m2 colle | 47 | Large pasted billboards |
| 4m2 | 34 | Medium outdoor poster |
| 12m2 | 28 | Extra-large billboards |
| 30s | 26 | 30-second radio spots |
| CM | 24 | Community management |
| 8m2 der (deroulant) | 23 | Large scrolling billboards |
| BUS ARR (bus arriere) | 23 | Rear-of-bus advertising |
| SMS | 18 | SMS campaigns |
| 12m2 + 8m2 colle | 16 | Combined large format |
| Site / SEO | 14 | Website / SEO work |
| SMO | 13 | Social media optimization |
| 1/4 page | 13 | Quarter-page press ads |
| 20s | 13 | 20-second radio spots |
| SEA | 11 | Search engine advertising |
| Bandeaux | 10 | Address banner advertising |
| Other formats | 22 | 1/2 page, prospectus, podcast, flyers, sacs a pain, fonds de rames, etc. |

### Top Advertising Networks (by media spend volume)

| Network | Campaign Lines | Total Espace (space cost) EUR |
|---|---|---|
| Cadres Blancs | 101 | 151,699.36 |
| JCDecaux | 43 | 119,297.51 |
| Cityz | 63 | 107,742.25 |
| Oxialive | 89 | 60,974.20 |
| Giraudy | 43 | 59,111.00 |
| Medialine | 53 | 42,348.80 |
| Affiouest | 31 | 40,200.15 |
| ANPSAM | 26 | 29,945.90 |
| Vediaud | 11 | 29,306.60 |
| Mediatransports | 4 | 26,811.60 |
| CompPrivee (own digital) | 67 | 26,723.52 |
| Europe 2 | 7 | 9,408.85 |
| Tendance Ouest | 16 | 8,881.40 |
| NRJ | 8 | 6,112.12 |
| Sweet FM | 9 | 5,110.80 |
| Nostalgie | 3 | 4,052.46 |
| Meta | 69 | 0.00 (managed fee, not space) |
| Google Ads | 17 | 0.00 (managed fee, not space) |

### Commission Rates

| Commission Rate | Campaign Lines |
|---|---|
| 13% | 365 (50.3%) |
| 15% | 304 (41.9%) |
| 20% | 24 (3.3%) |

The dominant commission structure is 13% (likely negotiated rate for largest networks) and 15% (standard rate).

### Monitoring / Management Fees (Gestion)

| Fee Amount | Count |
|---|---|
| 85.00 EUR | 250 |
| 150.00 EUR | 140 |
| 59.50 EUR | 25 |
| 25.50 EUR | 14 |
| 125.00 EUR | 12 |
| 62.50 EUR | 10 |
| 22.50 EUR | 10 |
| 250.00 EUR | 8 |
| 50.00 EUR | 7 |
| 365.98 EUR | 6 |

Two dominant fee tiers: 85 EUR (simpler campaigns) and 150 EUR (more complex campaigns).

### Seasonality (Campaign Start Month)

| Month | Campaigns |
|---|---|
| September | 125 |
| March | 111 |
| January | 86 |
| July | 71 |
| June | 68 |
| November | 59 |
| October | 57 |
| April | 50 |
| May | 32 |
| February | 29 |
| August | 27 |
| December | 11 |

Strong seasonal peaks in September (Foire de Caen, rentrée campaigns) and March (Salon de l'Habitat). December near-zero.

### Top 20 Clients by Revenue

| Client | Campaigns | CA HT (EUR) | Marge (EUR) | Margin % |
|---|---|---|---|---|
| CAO Paris | 13 | 79,173.08 | 17,901.44 | 22.6% |
| Grin | 24 | 61,122.03 | 17,128.66 | 28.0% |
| Caen evenements | 27 | 58,365.87 | 8,575.12 | 14.7% |
| Schmidt Mondeville | 36 | 50,155.87 | 12,594.39 | 25.1% |
| Game Fest | 9 | 44,937.43 | 14,179.84 | 31.6% |
| Art et Fenetres | 18 | 44,190.38 | 8,565.96 | 19.4% |
| Cuisinella Mondeville | 26 | 44,089.82 | 11,971.82 | 27.2% |
| Aasgard Mondeville | 14 | 35,134.73 | 6,902.93 | 19.6% |
| Aasgard Saint Lo | 17 | 33,471.61 | 6,656.74 | 19.9% |
| Schmidt Bayeux | 34 | 33,126.33 | 7,859.20 | 23.7% |
| Aasgard Lisieux | 18 | 30,421.19 | 6,891.39 | 22.7% |
| Schmidt Cherbourg | 23 | 27,220.20 | 8,576.80 | 31.5% |
| Logikinov Fleury sur Orne | 13 | 27,004.89 | 6,718.09 | 24.9% |
| McDonald | 9 | 24,018.72 | 6,404.33 | 26.7% |
| MCC | 28 | 22,805.70 | 14,438.20 | 63.3% |
| Cuisinella Falaise | 32 | 22,594.33 | 9,468.77 | 41.9% |
| Schmidt Carpiquet | 35 | 22,020.28 | 6,174.04 | 28.0% |
| Schmidt Yvetot | 17 | 19,443.51 | 3,821.65 | 19.7% |
| Schmidt Tourville | 11 | 16,379.96 | 2,904.76 | 17.7% |
| Brisach Guerande | 4 | 16,350.40 | 3,316.65 | 20.3% |

### Full Client List (all 73 clients)

| Client | Campaigns | CA HT (EUR) | Marge (EUR) | Margin % |
|---|---|---|---|---|
| CAO Paris | 13 | 79,173.08 | 17,901.44 | 22.6% |
| Grin | 24 | 61,122.03 | 17,128.66 | 28.0% |
| Caen evenements | 27 | 58,365.87 | 8,575.12 | 14.7% |
| Schmidt Mondeville | 36 | 50,155.87 | 12,594.39 | 25.1% |
| Game Fest | 9 | 44,937.43 | 14,179.84 | 31.6% |
| Art et Fenetres | 18 | 44,190.38 | 8,565.96 | 19.4% |
| Cuisinella Mondeville | 26 | 44,089.82 | 11,971.82 | 27.2% |
| Aasgard Mondeville | 14 | 35,134.73 | 6,902.93 | 19.6% |
| Aasgard Saint Lo | 17 | 33,471.61 | 6,656.74 | 19.9% |
| Schmidt Bayeux | 34 | 33,126.33 | 7,859.20 | 23.7% |
| Aasgard Lisieux | 18 | 30,421.19 | 6,891.39 | 22.7% |
| Schmidt Cherbourg | 23 | 27,220.20 | 8,576.80 | 31.5% |
| Logikinov Fleury sur Orne | 13 | 27,004.89 | 6,718.09 | 24.9% |
| McDonald | 9 | 24,018.72 | 6,404.33 | 26.7% |
| MCC | 28 | 22,805.70 | 14,438.20 | 63.3% |
| Cuisinella Falaise | 32 | 22,594.33 | 9,468.77 | 41.9% |
| Schmidt Carpiquet | 35 | 22,020.28 | 6,174.04 | 28.0% |
| Schmidt Yvetot | 17 | 19,443.51 | 3,821.65 | 19.7% |
| Schmidt Tourville | 11 | 16,379.96 | 2,904.76 | 17.7% |
| Brisach Guerande | 4 | 16,350.40 | 3,316.65 | 20.3% |
| Schmidt Mayenne | 11 | 16,270.95 | 3,540.45 | 21.8% |
| Schmidt Saint-Pair-sur-Mer | 13 | 16,114.83 | 3,631.83 | 22.5% |
| Cogeli | 8 | 15,671.98 | 4,979.42 | 31.8% |
| Cuisinella Pont L'eveque | 18 | 15,589.16 | 5,464.48 | 35.1% |
| Euroceane | 7 | 15,274.20 | 4,493.10 | 29.4% |
| Schmidt Saint Lo | 15 | 15,130.25 | 3,098.01 | 20.5% |
| Brisach Pontivy | 6 | 14,818.62 | 3,617.11 | 24.4% |
| Aquamalo | 6 | 14,722.30 | 3,041.49 | 20.7% |
| Brisach Quimper | 4 | 14,709.30 | 3,112.69 | 21.2% |
| Sirena | 14 | 14,519.45 | 5,106.25 | 35.2% |
| Cuisinella Barentin | 11 | 13,952.81 | 4,370.64 | 31.3% |
| C au Carre | 6 | 13,525.16 | 2,947.06 | 21.8% |
| O CAPE | 5 | 12,791.53 | 2,958.02 | 23.1% |
| 1er Rang | 7 | 12,477.96 | 3,524.90 | 28.2% |
| Schmidt Barentin | 11 | 12,090.51 | 3,535.51 | 29.2% |
| Lotiseine | 16 | 11,040.92 | 5,627.00 | 51.0% |
| L'Oasis | 9 | 10,927.60 | 3,795.90 | 34.7% |
| Leicht | 21 | 10,923.44 | 9,454.00 | 86.5% |
| Aquapole | 5 | 10,104.35 | 2,836.05 | 28.1% |
| Aquabella | 8 | 10,074.50 | 2,548.81 | 25.3% |
| Aquanacre | 12 | 10,072.85 | 3,243.53 | 32.2% |
| Cuisinella Yvetot | 10 | 9,941.17 | 2,078.07 | 20.9% |
| Ze Carrosserie | 3 | 9,503.36 | 1,947.34 | 20.5% |
| Scan Line | 2 | 9,489.53 | 1,974.68 | 20.8% |
| Cuisinella Rouen Centre | 9 | 8,923.65 | 3,086.02 | 34.6% |
| Schmidt Deauville | 4 | 7,020.85 | 1,281.44 | 18.3% |
| Aquadiva | 6 | 6,848.60 | 2,083.60 | 30.4% |
| Tradibat | 2 | 6,586.16 | 1,023.76 | 15.5% |
| Logikinov Equemauville | 5 | 6,576.71 | 1,724.41 | 26.2% |
| Festival des extraverties | 6 | 6,344.41 | 1,370.53 | 21.6% |
| Le Tablier | 12 | 6,050.00 | 6,050.00 | 100.0% |
| Aquarena | 3 | 6,030.95 | 1,787.95 | 29.6% |
| La Bulle | 3 | 5,685.62 | 1,493.12 | 26.3% |
| Omega recrea | 2 | 5,511.25 | 1,302.05 | 23.6% |
| Aquaplaine | 2 | 5,493.54 | 1,021.06 | 18.6% |
| Logikinov Saint Lo | 3 | 5,382.65 | 1,331.15 | 24.7% |
| Aquaspot | 2 | 5,154.32 | 1,166.30 | 22.6% |
| Carrefour Falaise | 1 | 5,052.00 | 813.60 | 16.1% |
| AQUAOUEST | 3 | 4,754.76 | 1,424.45 | 30.0% |
| Carrefour Etampes | 1 | 3,174.44 | 564.34 | 17.8% |
| Frivole | 7 | 3,109.00 | 2,750.00 | 88.5% |
| Aquapolis | 1 | 2,986.20 | 583.60 | 19.5% |
| Nature Energies | 2 | 2,906.38 | 732.98 | 25.2% |
| BMW | 1 | 2,822.50 | 647.30 | 22.9% |
| Medialine | 4 | 2,800.00 | 2,800.00 | 100.0% |
| Brisach Redon | 1 | 2,675.56 | 687.66 | 25.7% |
| SOS Depannage | 1 | 2,514.00 | 674.04 | 26.8% |
| Aquathelle | 1 | 2,167.83 | 825.84 | 38.1% |
| O2 Falaise | 1 | 1,880.86 | 455.96 | 24.2% |
| Puces Caennaises | 2 | 1,773.00 | 553.00 | 31.2% |
| Balneor | 1 | 1,209.69 | 524.46 | 43.4% |
| L'O-Vive | 1 | 1,190.91 | 453.68 | 38.1% |
| Untitled | 1 | 915.82 | 136.40 | 14.9% |

### Notion Database Fields (35 columns)

The Pilotage 2025 database tracks 35 fields per campaign line. This is the data structure Spider must ingest:

| Field | Description |
|---|---|
| Ref pages | Unique campaign line reference (e.g., Schmidt_Bayeux_janvier_Cadres_Blancs_2m2) |
| % Com Espace | Commission rate on media space (0.13, 0.15, or 0.20) |
| Achat digital | Digital purchase amount |
| Adresses Livraison Affiches | Poster delivery addresses |
| CM / Monitoring | Community management / monitoring details |
| Chiffres 2025 | Link to financial summary |
| Code campagne | Campaign code |
| Commentaires | Comments |
| Creations (Visuels/Radio/LED) | Creative assets status |
| Date de livraison (affiches) | Poster delivery date |
| Dates | Campaign date range (e.g., "January 9, 2025 -> January 16, 2025") |
| Entreprises | Client company (linked to company database) |
| Facture | Invoiced? (Yes/No) |
| Formats | Media format (2m2, Led, 8m2 colle, BUS ARR, etc.) |
| Gestion | Monitoring/management fee (EUR) |
| Imprimeur | Printer (always Publitex when applicable) |
| Instructions de livraison envoyees | Delivery instructions sent? |
| Jours restants | Days remaining until campaign |
| Lien vers visuels | Link to visual assets |
| Medias | Advertising network (linked to network database) |
| Paye | Paid? (Yes/No) |
| Photos | Campaign photos received? |
| Qtt a commander | Quantity to order |
| Quantites | Quantities |
| References Campagnes | Campaign reference code |
| Statut | Status (Termine, En cours, Pas commence, Reporte, Annule) |
| Total Campagne HT | Total campaign amount excl. VAT |
| Total Marge Agence | Total agency margin |
| EUR Com Espace | Commission on space in EUR |
| EUR Espace | Space cost in EUR |
| EUR Impressions | Printing cost in EUR |
| EUR Marge impressions | Margin on printing in EUR |
| EUR Radio Enregistrement | Radio recording cost in EUR |
| EUR Total Espace HT | Total space cost excl. VAT |
| EUR Total impressions | Total printing cost |

### Sample Campaign Line (what one record looks like)

```
Ref: Schmidt_Bayeux_janvier_Cadres_Blancs_2m2
Client: Schmidt Bayeux
Dates: January 9, 2025 -> January 16, 2025
Media/Network: Cadres Blancs
Format: 2m2
Quantities: 40 faces
Qty to order (posters): 42
Printer: Publitex
Commission rate: 13%
Space cost (EUR Espace): 1,375.40 EUR
Commission (EUR Com Espace): 178.80 EUR
Total space HT: 1,554.20 EUR
Printing cost: 202.00 EUR (unit cost derived: ~4.81 EUR/poster)
Printing margin: 84.70 EUR
Management fee (Gestion): 150.00 EUR
Total campaign HT: 1,906.20 EUR
Total agency margin: 413.50 EUR (margin rate: 21.7%)
Status: Termine
Invoiced: Yes
Paid: Yes
```

### Example Media Plans (from xlsx)

The xlsx file contains 4 real media plans as separate sheets:

**1. Foire de Caen 2026** (largest event)
- Total campaign HT (Caen only): 31,809.20 EUR
- Total with satellite towns: 37,598.19 EUR
- Multiple phases: Foire s-2, Foire s-1, Events
- Networks used: Medialine (LED), Cityz (bus, 2m2), Cadres Blancs (2m2), Oxialive (LED), Affiouest (8m2)
- 476 posters ordered for print at 2,915 EUR
- Columns: Periodes, Departs (start dates), Date de fin, Durees, Medias, Formats, Quantites, Tarifs espaces HT, Frais, Diff (calculated total), Affiches, Crea, Total HT, Valide, Notes, Liens, Cartes reseaux, Bons de commandes

**2. Villes satellites FIC (Foire Internationale de Caen)**
- Total: 5,788.99 EUR
- 4 lines covering Falaise, JCDecaux, Vire, Saint-Lo

**3. Salon de l'Habitat**
- Total: 16,521.62 EUR
- March 2026, mixed media (LED, 2m2, bus, print)

**4. Salon de l'Auto**
- Total: 19,357.42 EUR (with option)
- November 2026, Caen area

### Example Invoices (Pennylane output)

**Invoice F-2024-011371 (C au Carre -- Salon Home Days, Nov 2025)**
- Total HT: 13,524.34 EUR / TTC: 16,229.21 EUR
- Line items show how the media plan translates to invoice:
  - Cityz: 2,413.75 EUR
  - Affiches Arrieres de Bus: 50 x 5.26 EUR = 263.00 EUR
  - Medialine: 1,531.13 EUR + 1,197.63 EUR + 1,370.70 EUR (3 separate lines)
  - Oxialive: 1,561.60 EUR
  - Cadres Blancs Affichage: 3,683.35 EUR
  - Affiches 120 x 176 cm: 101 x 7.36 EUR = 743.36 EUR
  - Creation Motion Design: 200.00 EUR

**Invoice F-2026-01-1412 (Cuisines Schmidt Mondeville -- January 2026)**
- Total HT: 6,851.22 EUR / TTC: 8,221.46 EUR
- Shows the full range of billing line types:
  - Commission sur Achats d'espaces publicitaires: 457.62 EUR
  - Monitoring des campagnes: 5 x 97.50 EUR = 487.50 EUR
  - Community Management Mensuel: 300.00 EUR
  - FB/Insta ADS: 750.00 EUR
  - Tendance Ouest (radio): 174.09 EUR
  - RFM (radio): 601.25 EUR
  - Oxialive (LED): 1,112.80 EUR
  - Cadres Blancs Affichage: 1,268.71 EUR
  - Medialine: 363.35 EUR
  - Creation Motion Design: 290.00 EUR
  - Enregistrement spot radio: 100.00 EUR
  - Bandeaux Adresses annuelle: 741.00 EUR
  - Affiches 120 x 176 cm: 25 x 8.20 EUR = 204.90 EUR

### Example Supplier Order (Regie Ouest / Tendance Ouest -- for Aasgard Mondeville)

The Aasgard PDF shows the supplier-side documents (bons de commande from radio networks):
- **Devis D014T01956** -- Radio Tendance Ouest, Aasgard Caen January 2026
  - 28 spots x 25 seconds, 12-19 Jan, floating schedule, 9.35 EUR/spot = 261.80 EUR
  - Minus 25% budget commitment discount = -65.45 EUR
  - Net: 196.35 EUR
- **Second order same ref** -- 24 spots x 25 seconds, 15-17 Jan, THI schedule, 13.20 EUR/spot = 316.80 EUR
  - Minus 25% budget discount = -79.20 EUR, minus 14.99% exceptional discount = -65.09 EUR
  - Net: 172.51 EUR
  - Total net HT both: 368.86 EUR, TVA: 73.77 EUR, TTC: 442.63 EUR
- Signed by Audrey LE MAIGAT (Pour ordre) on 24/11/2025

This demonstrates the multi-layer pricing: gross rate -> budget discount -> exceptional discount -> net. All currently calculated manually.

---

## 7. Spider Strategy Document -- Competitive Landscape and Architecture

### The Full Strategic Thesis (from spider-strategy.docx)

Nathan's Spider strategy document positions ComPrivee/Jordan as Phase 0 within a much larger vision. Key elements:

**Core principle:** Do not sell software to help clients do work. Use software internally and sell the finished result at 10-100x the margin of manual delivery.

**The Palantir Blueprint:** Phase 1 = Drakkar consultants (FDEs) embed with clients and operate AI agents under supervision. Phase 2 = Operational knowledge crystallizes into a platform. Phase 3 = External partners deploy Spider, Drakkar retains premium insider access.

### Competitive Landscape Summary

**The structural gap:** At the top are expensive enterprise platforms (45K+ EUR/year). At the bottom are DIY workflow builders (9-37 EUR/month). In the middle -- where a non-technical SMB owner wants AI to just work -- almost nothing exists.

**AI Business Assistants benchmarked:**
- Dust.tt: 29 EUR/user/month, no SMB focus, 21.5M USD raised
- Lindy AI: 29-199 USD/month, DIY builder, ~50M USD raised
- MS 365 Copilot: 21 USD/user/month, Microsoft-only ecosystem

**Workflow Automation benchmarked:**
- Zapier: 19.99 USD/month, 8,000+ integrations -- but user must define what to automate
- Make: 9 USD/month, 3,000+ integrations -- steep learning curve
- n8n: 20 EUR/month, 500+ integrations -- developer-focused

**"AI Employees" benchmarked:**
- 11x.ai: ~45K USD/year, enterprise-only, ~2,500 USD per positive reply
- Artisan AI: ~2K USD/month, high churn, hallucination issues admitted by CEO
- Sintra AI: 12 AI helpers, no ERP integration, no business ontology

**French ecosystem:** 1,114 AI startups, 16B EUR total raised, but only ~10% of French SMBs actively use AI. Key players remain vertical (Pennylane, Axonaut, Mistral, H Company). None operates managed AI agents for PME back-offices.

**Five gaps nobody fills:**
1. No truly free, full-featured business assistant
2. No platform proactively recommends agents
3. No per-agent pricing with free trials
4. The "hire" metaphor is incomplete
5. Non-technical SMB owners remain underserved (89% want AI, almost nothing serves them)

**Real competitors are not tech** -- they are: the executive assistant (2,500-3,500 EUR/month), the accounting firm (150-250 EUR/hour), BPO/outsourced office managers (35-50 EUR/hour), and doing nothing (80% of PMEs).

### Spider Architecture: Two Layers

**Layer 1 -- The Assistant (Reactive):** A free AI chatbot connected to business data (ERP, accounting, CRM). The owner asks questions. The assistant responds, analyzes, diagnoses. Crucially, it reveals problems the owner did not know they had, then recommends specific agents.

**Layer 2 -- The Agents (Proactive):** Autonomous workers in the background. Agent Relance chases unpaid invoices. Agent Campagnes manages advertising campaigns. Agent Achats optimizes procurement. Each has a "salary" (190-990 EUR/month) and a 14-day free trial. The owner does not interact with them. They receive results.

**The Flywheel:** Each deployed agent generates more data for the assistant -> better diagnostics -> more agent recommendations -> more agents -> more data. Compounds with each client, each mission, each interaction.

### Structural Advantages

1. **Operational Ontology (the real moat).** 5 years of Drakkar installing ERPs in French PMEs. Knows that payment reminder #2 should go at J+15 in construction, that outdoor advertising media plans require different validation steps than purchase orders in food distribution, that Sage exports have different quirks than Odoo exports.
2. **Deep ERP Integration.** Connects to real ERP systems (Odoo, Sage, Pennylane) because Drakkar deploys them professionally. Reads actual invoices, purchase orders, account balances -- not Gmail threads.
3. **Human-in-the-Loop Supervision.** Edge cases trigger human intervention from Drakkar professionals. Cites the Bench collapse (600 employees fired overnight, 12,000 customers stranded) as proof pure automation destroys trust.
4. **Self-Funded R&D.** Drakkar generates 1.5M EUR/year in revenue. No VC pressure to scale before understanding.
5. **The Palantir Parallel.** Drakkar consultants = Spider's Forward Deployed Engineers. Every client project = revenue + R&D simultaneously.

### Risk Analysis

**Execution risks:**
- Premature platformization (temptation to build dashboards before validating delivery)
- Human cost stagnation (if AI/human ratio stays at 40/60, unit economics remain consulting-level)
- Key person dependency (if operational knowledge lives in one head, it does not scale)

**Market risks:**
- Incumbents move down-market (Dust could launch SMB tier, Zapier could add proactive recommendations)
- AI capability plateau (model assumes human supervision -- AI handles 80% volume, humans 20% complexity)
- SMB willingness to pay (French PMEs are price-sensitive and slow to adopt)

**Strategic risks:**
- Drakkar distraction (mitigation: Phase 0-1 generates Drakkar revenue; Spider work IS consulting work)
- Partner misalignment (mitigation: Spider remains Drakkar project through Phase 2; separate entity only when traction justifies)

---

## 8. Supplementary Document -- Decotec Email (Context for Drakkar)

A forwarded email (Feb 12, 2026) from Isabelle de Bray (Decotec) to Thierry Menard shows a Drakkar client (industrial/manufacturing) deciding to switch to another Odoo integrator with deeper industrial-production expertise. This is included in the cas_jordan folder as context -- it illustrates both:

1. The limits of Drakkar's current consulting model (losing clients who need deeper vertical specialization)
2. The opportunity Spider represents (productized domain knowledge that scales beyond individual consultant capability)

Key quote: "Nous sommes convaincus que, a ce stade et pour les prochains lots, celui-ci requiert une expertise plus specifique et un chef de projet experimente en production. C'est la raison pour laquelle nous souhaiterions nous orienter vers un integrateur possedant un pool d'experts indus-prod."

---

## 9. Pricing Structure Analysis (derived from raw data)

### How ComPrivee Makes Money -- The Revenue Formula

For each campaign line, revenue is built from these components:

```
Total Campagne HT =
    EUR Espace (media space cost, paid to network)
  + EUR Com Espace (commission on space = EUR Espace x % Com Espace)
  + Gestion (monitoring/management fee: 85 or 150 EUR typically)
  + EUR Total impressions (printing: quantity x unit cost)
  + EUR Radio Enregistrement (radio recording, when applicable)
  + Achat digital (digital ad spend, when applicable)
  + CM / Monitoring (community management, when applicable)
```

### Where ComPrivee's Margin Comes From

```
Total Marge Agence =
    EUR Com Espace (commission on space: 13-15-20% of space cost)
  + Gestion fee (85-150 EUR monitoring fee, 100% margin)
  + EUR Marge impressions (markup on printing)
  + Any fully-managed services at 100% margin (CM, content creation)
```

Average overall margin is 27.2%, but varies hugely by client type:
- Pure media buying clients: 15-25% margin (commission + monitoring)
- Managed service clients (CM, content, digital): 35-100% margin
- The highest-margin clients (Leicht 86.5%, Le Tablier 100%, Frivole 88.5%) are those buying managed services, not media space

**This validates Spider's thesis:** the shift from media buying (low margin, high manual work) to managed services (high margin, automatable) is exactly where AI-native delivery creates the most value.

---

## SOURCE FILES

All source files are located in `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/07-spider-inputs/raw/cas_jordan/`:

| File | Type | Content |
|---|---|---|
| spider-strategy.docx | Nathan's strategy doc | Full Spider strategic plan: thesis, competitive landscape, architecture, hypotheses, execution plan, financials, risks |
| Rdv avec Nathan .docx | Jordan's work dossier | ComPrivee profile, team, 9-step workflow, pain points, tool map, target workflow, questions for Nathan |
| Presentation-Nathan-ComPrivee.pdf | Meeting slides (12 pages) | Visual presentation covering same ground as the dossier: company brief, workflow, problems, goals, constraints, questions |
| exemple_plan_media.xlsx | Real media plans (4 sheets) | Foire de Caen 2026 (37.6K EUR), Villes satellites (5.8K EUR), Salon de l'Habitat (16.5K EUR), Salon de l'Auto (19.4K EUR) |
| export_notion/data/Pilotage 2025...csv | Notion database export | 726 campaign lines, 35 fields each. Full 2025 operational data |
| export_notion/data/Chiffres 2025...csv | Financial summary | Single row: CA 1,145,304.61 EUR, Marge 311,325.71 EUR, links to all 726 campaigns |
| export_notion/vue_principale.html | Notion HTML export | 1.7MB HTML rendering of the Pilotage database (visual reference) |
| exemples_factures/Facture-C AU CARRE...pdf | Pennylane invoice | Example client invoice: C au Carre, Salon Home Days, 13,524.34 EUR HT |
| exemples_factures/Facture-CUISINES SCHMIDT...pdf | Pennylane invoice | Example client invoice: Schmidt Mondeville, January 2026, 6,851.22 EUR HT |
| exemples_factures/COM PRIVEE ASGARD...pdf | Supplier order (bon de commande) | Radio Tendance Ouest orders for Aasgard Mondeville, showing multi-layer discount structure |
| Messagerie Drakkar...pdf | Forwarded email | Decotec client departing Drakkar for specialist industrial integrator -- context for Spider thesis |
| _explications.md | Empty file | No content |
