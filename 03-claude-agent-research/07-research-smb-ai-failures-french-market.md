# SMB AI Failures & French Market Data

**Date:** February 17, 2026

**Source:** Research compilation covering AI agent benchmark failures, enterprise AI pilot failure rates, agentic AI skepticism, cost of AI agent deployment, consulting firms response to AI, and FDE/consulting economics.

---

# AI Agents, Enterprise AI FailureS, CONSULTING ECONOMICS

## 1. AI AGENT BENCHMARK FAILURES

### APEX-Agents Benchmark (January 2026)
- **Paper:** arXiv:2601.14242
- **Created by:** Mercor (published on Hugging Face under CC-BY)
- **Covered by:** [TechCrunch, January 22, 2026](https://techcrunch.com/2026/01/22/are-ai-agents-ready-for-the-workplace-a-new-benchmark-raises-doubts/)
- **Dataset:** 200 test cases across 4 domains: investment banking, management consulting, law, and primary medical care
- **Task complexity:** Each task takes an expert 1-8 hours (mean 3.5 hours), requiring sophisticated reasoning
- **Expert sources for task creation:** Goldman Sachs, McKinsey, Cravath
- **Environment:** Google Workspace with complex datarooms
- **Each task has 1-10 pass/fail criteria** defining "client-ready" standards

**One-shot accuracy results:**
| Model | Score |
|---|---|
| Gemini 3 Flash (Thinking=High) | 24.0% |
| GPT-5.2 (Thinking=High) | 23% |
| Claude Opus 4.5 (Thinking=High) | ~18% |
| Gemini 3 Pro (Thinking=High) | ~18% |
| GPT-5 | ~18% |

- **With 8 attempts:** Best agents only reach ~40% completion
- **Key finding:** "No model is ready to replace a professional end-to-end."
- **Failure modes:** Not lack of capability per se, but inability to manage ambiguity, find the right file, or hold context across entire workflows
- Source: [Mercor blog](https://www.mercor.com/blog/introducing-apex-agents/), [arXiv](https://arxiv.org/abs/2601.14242), [BankInfoSecurity](https://www.bankinfosecurity.com/blogs/24-success-rate-for-ai-agents-that-acceptable-p-4038)

### SWE-Bench Pro (Scale AI, November 2025)
- **Paper:** arXiv:2509.16941
- **Focus:** Long-horizon software engineering tasks requiring hours to days for professionals
- **Average reference solution:** 107.4 lines of code across 4.1 files, every problem involves at least 10 lines of change, 100+ tasks require >100 lines

**Results:**
| Model | SWE-Bench Pro Score | SWE-Bench Verified Score |
|---|---|---|
| GPT-5 | 23.3% | >70% |
| Claude Opus 4.1 | 23.1% | >70% |

- **Key gap:** Models score 70%+ on simple SWE-Bench Verified but only ~23% on Pro (long-horizon tasks)
- **Pattern:** Performance degrades significantly as solutions require more lines and more files
- Some repos below 10% resolve rate across all models
- Source: [Scale AI leaderboard](https://scale.com/leaderboard/swe_bench_pro_public), [arXiv](https://arxiv.org/abs/2509.16941)

### SWE-Bench Verified (Current Leaderboard, 500 samples)
| Model | Score |
|---|---|
| Claude Opus 4.6 (Thinking) | 79.2% |
| Gemini 3 Flash | 76.2% |
| GPT 5.2 | 75.4% |

- Source: [SWE-Bench Verified Leaderboard](https://llm-stats.com/benchmarks/swe-bench-verified)

### Compound Error Problem
- If each step has 95% reliability, 20-step task yields only 36% success
- 1% error per action becomes near-certain collapse over long task chains
- A 63% failure rate emerges on 100-step tasks even with "tiny" per-step hallucination rates
- **Multi-agent systems:** "17x error trap" in bag-of-agents architectures
- **Vishal Sikka (former SAP CTO)** co-authored paper "Hallucination Stations" claiming to mathematically prove LLMs fundamentally incapable of reliable agentic tasks beyond certain complexity
- **OpenAI's own research (September 2025):** Their scientists demonstrated models fabricate dissertation titles and misreport dates, concluding "accuracy will never reach 100 percent"
- Source: [Towards Data Science](https://towardsdatascience.com/why-your-multi-agent-system-is-failing-escaping-the-17x-error-trap-of-the-bag-of-agents/), [TechBuzz](https://www.techbuzz.ai/articles/new-research-claims-ai-agents-are-mathematically-doomed-to-fail)

### CMU AgentCompany Benchmark
- **Failure rates of 70%** on some tasks
- Source: Gary Marcus citing CMU research

---

## 2. ENTERPRISE AI PILOT FAILURE RATES

### MIT "State of AI in Business 2025" Report
- **The statistic:** 95% of generative AI pilots fail to deliver measurable P&L impact
- **Investment at stake:** $30-40B in enterprise AI investment, with 95% showing zero financial return
- **Only 5% achieve rapid revenue acceleration**
- **Methodology:** 150 interviews with leaders, survey of 350 employees, analysis of 300 public AI deployments
- **Lead researcher:** Aditya Challapally, MIT NANDA initiative
- **Vendor vs. internal:** Purchasing from specialized vendors succeeds 67% of the time; internal builds succeed only ~22%
- **Budget misallocation:** Over half of GenAI budgets target sales & marketing (low ROI); largest ROI is in back-office automation
- Source: [Fortune, August 18, 2025](https://fortune.com/2025/08/18/mit-report-95-percent-generative-ai-pilots-at-companies-failing-cfo/), [MIT report PDF](https://mlq.ai/media/quarterly_decks/v0.1_State_of_AI_in_Business_2025_Report.pdf)

### Gartner Predictions
- **"At least 30% of generative AI projects will be abandoned after proof of concept by the end of 2025"** due to poor data quality, inadequate risk controls, escalating costs, or unclear business value
- **Rita Sallam, Distinguished VP Analyst at Gartner:** "After last year's hype, executives are impatient to see returns on GenAI investments, yet organizations are struggling to prove and realize value."
- **"There is no one size fits all with GenAI, and costs aren't as predictable as other technologies."**
- **Only 48% of AI projects make it past pilot**
- **Gartner predicts >40% of agentic AI projects will be canceled by end of 2027** due to escalating costs, security risks, or failure to demonstrate business value
- Announced July 2024 at Gartner Data & Analytics Summit
- Source: [Gartner press release](https://www.gartner.com/en/newsroom/press-releases/2024-07-29-gartner-predicts-30-percent-of-generative-ai-projects-will-be-abandoned-after-proof-of-concept-by-end-of-2025)

### S&P Global Market Intelligence (2025)
- **42% of companies abandoned most AI initiatives** in 2025, up from just 17% in 2024
- **46% of POCs scrapped before scale**
- Source: [ServicePath](https://servicepath.co/2025/09/ai-integration-crisis-enterprise-hybrid-ai/)

### BCG "The Widening AI Value Gap" (September 2025)
- **60% of companies generate no material value** from AI despite investments
- **Only 5% create substantial value at scale**
- **Median reported ROI is just 10%** -- well below the 20% many target
- Source: [BCG publication](https://www.bcg.com/publications/2025/are-you-generating-value-from-ai-the-widening-gap), [BCG PDF](https://media-publications.bcg.com/The-Widening-AI-Value-Gap-Sept-2025.pdf)

### McKinsey Data
- **88% of companies use AI in at least one function**
- **Only 39% see an impact on EBIT, most often less than 5%**
- Source: [duperrin.com analysis](https://www.duperrin.com/english/2025/12/08/impacy-ai-transformation-bcg-mckinsey/)

### IDC Data
- **For every 33 AI prototypes built, only 4 reach production** (88% scaling failure rate)
- Source: [Quest blog](https://blog.quest.com/the-hidden-ai-tax-why-theres-an-80-ai-project-failure-rate/)

### Deloitte Tech Trends 2026 Survey (500 US tech leaders, June-July 2025)
- **11% actively using agentic AI in production**
- **38% piloting**
- **14% have solutions ready to deploy**
- **30% exploring**
- **35% have no agentic strategy at all**
- Source: [Deloitte Insights](https://www.deloitte.com/us/en/insights/topics/technology-management/tech-trends/2026/agentic-ai-strategy.html)

### Enterprise Budget Misallocation
- **93% of AI budgets go toward technology; only 7% fund training and cultural readiness**
- **Only 12% of organizations report data quality sufficient for AI**
- Source: [Directual blog](https://www.directual.com/blog/ai-agents-in-2025-why-95-of-corporate-projects-fail)

---

## 3. AGENTIC AI SKEPTICISM

### Gary Marcus (NYU Professor Emeritus, Cognitive Psychology)
- **Prediction (January 2025):** AI agents would be "endlessly hyped throughout 2025 but far from reliable, except possibly in very narrow use cases" -- **proven correct**
- **16 of 17 "high confidence" predictions for 2025 proved correct** by his own count
- **Essay title:** "AI Agents have, so far, mostly been a dud" (Substack)
- **On LLMs as agent foundation:** "They're building clumsy tools on top of clumsy tools"
- **On investment:** The tech industry made "a massive mistake, intellectually and economically" by investing almost exclusively in LLMs
- **On neurosymbolic AI:** Receives "maybe 1%" of total AI investment; without it "I don't see how agents can work out"
- **On reliability:** Reliable agents require "robust, trustworthy AI" -- which LLMs aren't providing
- **Security finding he cites:** Even the most secure AI agent tested was undermined 1.45% of the time
- **AI bubble prediction:** Wrote for WIRED predicting AI bubble collapse in 2025
- Source: [Gary Marcus Substack](https://garymarcus.substack.com/p/ai-agents-have-so-far-mostly-been), [Substack predictions](https://garymarcus.substack.com/p/25-ai-predictions-for-2025-from-marcus), [Project Syndicate](https://www.project-syndicate.org/magazine/generative-ai-fundamentally-unreliable-and-with-no-apparent-solution-by-gary-marcus-2025-06)

### Cal Newport (Georgetown CS Professor, Author)
- **Core argument:** AI agents failed to live up to hype; Sam Altman's prediction that agents would "join the workforce" and "materially change the output of companies" did not happen
- **Specific failure example:** ChatGPT Agent spent **14 minutes trying to select a value from a dropdown menu** on a real estate website
- **On generalization failure:** Claude Code and Codex succeeded in programming but this did not generalize to other knowledge work domains
- **Quote on scaling laws:** "Scaling laws have begun to falter" -- companies investing massively in bigger models but performance stopped leaping forward as much
- Source: [Cal Newport blog](https://calnewport.com/why-didnt-ai-join-the-workforce-in-2025/)

### Failed Predictions by Industry Leaders
- **Sam Altman (OpenAI CEO):** "In 2025, we may see the first AI agents 'join the workforce' and materially change the output of companies" -- **did not happen**
- **Kevin Weil (OpenAI CPO):** 2025 would see AI "doing things in the real world for you" like filling out paperwork and booking hotels -- **did not happen**
- **Mark Benioff (Salesforce CEO):** AI agents would trigger "a digital labor revolution" worth trillions -- **not materialized**
- Source: [Cal Newport](https://calnewport.com/why-didnt-ai-join-the-workforce-in-2025/), [Reworked](https://www.reworked.co/digital-workplace/2025-was-supposed-to-be-the-year-of-the-agent-it-never-arrived/)

### Broader Skepticism Trends
- AI adoption among researchers rose to 62% in 2025, but **trust in AI outputs plummeted** -- "Greater exposure to AI breeds more skepticism, not less"
- AI tools deployed rapidly but "few organizations are using them well," reporting **new inefficiencies: duplicated work, increased oversight burdens, time correcting AI errors**
- Source: [NH Journal](https://nhjournal.com/counterpoint-meet-the-ai-agents-of-2026-ambitious-overhyped-and-still-in-training/), [WebProNews](https://www.webpronews.com/rising-ai-denialism-in-2025-critics-call-generative-tech-overhyped-slop/)

### Vishal Sikka (Former SAP CTO)
- Co-authored paper claiming to **mathematically prove LLMs can't reliably handle complex computational and agentic tasks** beyond a certain complexity
- **Quote:** "There is no way they can be reliable"
- Agents might handle routine paperwork but will inevitably make consequential errors
- Source: [TechBuzz](https://www.techbuzz.ai/articles/new-research-claims-ai-agents-are-mathematically-doomed-to-fail)

---

## 4. COST OF AI AGENT DEPLOYMENT

### Hidden Evaluation Costs
- **"LLM as a judge"** (using a second LLM to vet agent outputs) can be **more expensive than running the agent itself**
- Nearly 80% of enterprises have deployed AI agents but most don't understand the cost of evaluating outputs
- Source: [CIO](https://www.cio.com/article/4123029/ai-agent-evaluations-the-hidden-cost-of-deployment.html)

### Scaling Cost Explosion
- One client started at **$8K/month** but hit **$50K/month** when volumes scaled
- Typical sales AI agents rely on 3-5 integrations adding **$800-$900/month** just for integration tools
- **Average monthly AI spending reached $85,521 in 2025** -- a 36% jump from 2024
- Source: [Symphonize](https://www.symphonize.com/tech-blogs/costs-of-building-ai-agents-what-decision-makers-need-to-know), [Altamira](https://www.altamira.ai/blog/ai-agent-development-cost/)

### Enterprise Cost Reality
- **96% of enterprises going with GenAI and agentic automation agree costs are higher than expected** (IDC research)
- Source: [Accelirate](https://www.accelirate.com/ai-agent-costs-hidden-scaling-enterprise/)

### Hallucination Financial Impact
- **Financial losses exceeding $250M annually** from hallucination-related incidents across industry
- 72-80% of enterprise RAG implementations **significantly underperform or fail within first year**
- 51% of all enterprise AI failures in 2025 are RAG-related
- Legal RAG implementations hallucinate citations **17-33% of the time**
- Source: [GetMaxim](https://www.getmaxim.ai/articles/the-state-of-ai-hallucinations-in-2025-challenges-solutions-and-the-maxim-ai-advantage/)

### Human-in-the-Loop (HITL) Costs
- Traditional HITL model means **labor costs rise linearly with usage**, offsetting automation savings
- Proving unsustainable in high-volume environments
- Effective HITL systems target **10-15% escalation rates** (85-90% autonomous)
- But AI systems making millions of decisions/second make meaningful human supervision per-decision "no longer realistic"
- HITL cost is emerging as **major economic driver** -- traditional AI oversight labor costs scale linearly while AI usage scales exponentially
- Source: [Deloitte](https://www.deloitte.com/us/en/services/consulting/articles/ai-agent-observability-human-in-the-loop.html), [SiliconANGLE](https://siliconangle.com/2026/01/18/human-loop-hit-wall-time-ai-oversee-ai/)

### AI Agent Production Failure Rates
- Agents succeed **less than 65% of the time** at executing function calls for key CRM use cases
- **89% of organizations have observability** for agents; quality issues are primary barrier at 32%
- Source: [Cleanlab](https://cleanlab.ai/ai-agents-in-production-2025/)

---

## 5. CONSULTING FIRMS' RESPONSE TO AI

### McKinsey & Company
- **2024 revenue:** ~$16-18.8B (varying estimates; grew only 2% in 2024)
- **Workforce:** 40,000 human employees + **25,000 AI agents** (as of early 2026)
- **CEO Bob Sternfels (at CES, January 2026 on "All-In" podcast):** Expects roughly the same number of AI agents as human employees by end of year
- **"25 squared" strategy:** Growing client-facing roles by 25%, shrinking non-client-facing roles by 25%, while output from non-client side grew 10%
- **Internal AI tool "Lilli":** Draws on 40+ knowledge sources with 100,000+ documents; cuts time spent searching/synthesizing information by up to 30%
- **Productivity gains:** Saved **1.5 million hours** in search and synthesis work in one year
- **Layoffs:** Plans to cut ~10% of workforce (potentially thousands) across non-client-facing roles over 18-24 months; already cut 200 global tech jobs
- **AI replacing junior consultants:** AI agents automate summarizing documents, building slide decks, analyzing data, checking logic, generating first drafts -- "AI is not helping the junior consultant; it is replacing them in their core function of synthesis"
- **40% of revenue** expected to be AI-related
- Source: [Yahoo Finance](https://finance.yahoo.com/news/mckinseys-ceo-breaks-down-ai-100301404.html), [Yahoo Finance](https://finance.yahoo.com/news/ceo-bob-sternfels-says-mckinsey-104101601.html), [Fast Company](https://www.fastcompany.com/91463039/why-the-mckinsey-layoffs-are-a-warning-signal-for-consulting-in-the-ai-age-ai-layoffs-management-consulting)

### BCG (Boston Consulting Group)
- **2024 revenue:** $13.5B (10% growth, 21st consecutive year of growth)
- **AI revenue:** 20% of revenue (~$2.7B) from AI-related advisory -- a revenue stream that didn't exist two years ago
- **Growth rate comparison:** BCG grew 10% vs McKinsey's 2%; at this rate BCG expected to overtake McKinsey by 2027
- **BCG research ("Widening AI Value Gap"):** 60% of companies generate no material value from AI; only 5% create value at scale
- Source: [BCG press release](https://www.bcg.com/press/bcg-announces-re-election-of-chief-executive-officer-christoph-schweizer), [BCG publication](https://www.bcg.com/publications/2025/are-you-generating-value-from-ai-the-widening-gap)

### Accenture
- **FY2024 revenue:** $64.9B (1% growth USD, 2% local currency)
- **FY2025 revenue growth:** 7%
- **GenAI/Agentic AI revenue:** **$2.7B** (tripled year-over-year)
- **GenAI bookings:** $5.9B (nearly doubled YoY)
- **AI talent:** Nearly doubled AI/data staff to **77,000** in two years; 550,000+ employees trained in GenAI fundamentals
- **AI market share:** ~7% of AI services market (leading), ahead of Deloitte (3%) and IBM (2%)
- **Strategic investment:** $3B committed to AI
- Source: [Accenture Q4 FY25 results](https://newsroom.accenture.com/content/4q-full-fy25-earnings/accenture-reports-fourth-quarter-and-full-year-fiscal-2025-results.pdf), [CIO Dive](https://www.ciodive.com/news/accenture-generative-ai-revenue-skills-training-data-modernization/761161/)

### Deloitte
- **FY2024 revenue:** $67.2B
- **AI strategy:** Declaring multibillion-dollar spending on AI assistants in auditing, tax, and management consulting
- **AI services market share:** ~3%
- **Research output:** Tech Trends 2026, State of AI in Enterprise 2026 reports
- Source: [Statista](https://www.statista.com/statistics/269013/deloitte-revenue-worldwide/), [Deloitte Insights](https://www.deloitte.com/us/en/insights/topics/technology-management/tech-trends/2026/agentic-ai-strategy.html)

### AI Consulting Market
- **2024 market size:** $14B (AI consulting and support services)
- **Projected 2030:** $72.8B (CAGR 31.6%)
- **AI consulting market grew** from $8.75B in 2024 to $11.07B in 2025
- Source: [BusinessWire](https://www.businesswire.com/news/home/20251124215144/en/AI-Consulting-and-Support-Services-Analysis-Report-2025-2032)

### Are They Being Disrupted?
- Consulting firms are **simultaneously profiting from and being disrupted by AI**
- Firms like **Palantir and OpenAI are reshaping consulting** -- Palantir deploys engineers directly with clients; OpenAI embeds into workflows
- Salaries at MBB firms **remain flat for third consecutive year** in 2025 -- AI and remote work allow firms to "achieve more with smaller teams"
- Source: [BrainForge](https://www.brainforge.ai/blog/how-big-consulting-firms-profit-massively-from-ai-consulting), [BusinessBecause](https://www.businessbecause.com/news/in-the-news/9655/management-consultant-salaries-2025)

---

## 6. FDE / CONSULTING ECONOMICS

### MBB Consultant Compensation (2025-2026)
| Level | Base Salary | Bonus | Total Comp |
|---|---|---|---|
| Business Analyst (undergrad) | $90K-$110K | $10-20K | ~$110-130K |
| Associate/Consultant (MBA hire) | $190-192K | Up to $60K perf + $35K signing | $260-285K |
| Engagement Manager | $200-270K | Performance bonus | Up to $350K |
| Associate Partner/Principal | ~$300-400K | Significant | $400-600K |
| Partner | $500K+ base | Profit sharing | $1M-$5M+ |

- **MBB salaries flat for 3rd consecutive year** in 2025
- Source: [CaseBasix](https://www.casebasix.com/pages/mckinsey-salary), [BusinessBecause](https://www.businessbecause.com/news/in-the-news/9655/management-consultant-salaries-2025)

### MBB Client Billing Economics
- **Typical strategy case:** $500K-$1.25M (3 months / 12 weeks)
- **McKinsey uses fixed-fee pricing**, not hourly billing
- **Hourly rates when used:** $700-$900 average for premium brands (McKinsey/BCG); up to $1,000+ for senior partners
- **Sample $1M engagement cost breakdown:**
  - 1 Partner (33% allocation): $58K
  - 1 Principal (100%): $100K
  - 2 Associates (100%): $113K combined
  - 2 Analysts (100%): $50K combined
  - 2 Support staff (10%): $4K combined
  - Personnel subtotal: $324K
  - Travel/lodging/food/overhead: $236K
  - **Total cost: ~$560K**
  - **Gross margin: ~48.5%** on $1M revenue
- Source: [RocketBlocks](https://www.rocketblocks.me/guide/business-model.php), [Slideworks](https://slideworks.io/resources/management-consulting-fees-how-mc-kinsey-prices-projects)

### Loaded Cost Multipliers (Consulting Industry)
- **Deltek report:** Fringe 35% + Overhead 25% + G&A 18% = **1.99x multiplier** on base salary
- General range: **1.25-1.4x** for basic positions; **1.5-2.0x** for specialized roles
- Overhead can run **50-250% of gross wages**
- Source: [SAP BW Consulting](https://www.sapbwconsulting.com/blog/how-to-determine-your-fully-loaded-cost-rate), [Toptal](https://www.toptal.com/freelance/don-t-be-fooled-the-real-cost-of-employees-and-consultants)

### Palantir FDE Compensation
| Component | Range |
|---|---|
| Base salary (entry) | $135K-$200K |
| Total comp (median) | $215K |
| Total comp (range) | $171K-$415K |
| Stock grants | $100K-$400K |
| Senior FDE total comp | $500K-$800K |
| European day rate (contractor) | £600-£700/day |

- Source: [Levels.fyi](https://www.levels.fyi/companies/palantir/salaries/software-engineer/title/fdse), [Glassdoor](https://www.glassdoor.com/Salary/Palantir-Technologies-Forward-Deployed-Engineer-Salaries-E236375_D_KO22,47.htm)

### Palantir FDE Business Model
- **2024 revenue:** $2.866B (28.79% YoY increase)
- **FY2025 guidance raised to 45% YoY growth** (then 53% after Q3 beats)
- **Q3 2025 TCV bookings:** $2.8B (highest ever, up 151% YoY)
- **Net dollar retention:** 134% (up 600 bps QoQ)
- **Remaining deal value:** $8.6B (up 91% YoY)
- **Customer count growth:** 45% YoY in Q3 2025; commercial customers 49%

**FDE model economics:**
- FDEs embed at client site, working exclusively on one customer on Palantir's stack
- Contracts start small (bootcamp + limited licenses); if value proven, expand
- Revenue mix tilts toward **software subscription over services** over time
- **Seven-figure ACV contracts** generally support the FDE model; sub-$100K contracts don't pencil unless R&D toward bigger deal
- Palantir is **willing to fund engineering time upfront** to land meaningful customers
- FDE helps **land bigger deals and expand them faster** -- grows a pilot to $1M+ deal in ways pure sales cannot
- Unlike consulting firms, **services are a means to drive product adoption**, not the primary revenue stream
- Source: [Palantir IR](https://investors.palantir.com/news-details/2025/Palantir-Reports-Q2-2025-U-S--Comm-Revenue-Growth-of-93-YY-and-Revenue-Growth-of-48-YY-Guides-Q3-Revenue-to-50-YY-Raises-FY-2025-Revenue-Guidance-to-45-YY-and-U-S--Comm-Revenue-Guidance-to-85-YY-Crushing-Consensus-Expectations/), [Everest Group](https://www.everestgrp.com/palantir-inside-the-category-of-one-forward-deployed-software-engineers-blog/), [a16z "Palantirization of Everything"](https://a16z.com/the-palantirization-of-everything/)

### Cost Comparison: Consultant vs. FDE vs. AI Agent
| Deployment Model | Annual Loaded Cost | What You Get |
|---|---|---|
| MBB Junior Consultant (billed) | ~$500K-$1M to client (per team, 12 weeks) | Strategy decks, analysis, recommendations |
| Palantir FDE (embedded) | $215K-$500K+ comp; supports 7-figure+ ACV contracts | Production-ready software workflows on client data |
| AI Agent (enterprise) | $85K/month avg ($1M+/year) + hidden evaluation costs | Sub-25% success on complex tasks; 95% of pilots fail to show P&L impact |

---

## ADDITIONAL NOTABLE DATA POINTS

### Agentic AI Market Size
- **2025 market value:** $4.54B
- **Projected 2033:** $98.26B (CAGR 46.87%)
- Source: [PRNewswire](https://www.prnewswire.com/news-releases/agentic-ai-market-enters-high-growth-phase-driven-by-autonomous-execution-demand-enterprise-software-fragmentation-and-rising-hitl-costs-302678866.html)

### AI Hallucination Rates (2025)
- Range: **0.7% to 29.9%** depending on model
- Some models saw up to 64% drops in hallucination rates during 2025
- RAG cuts hallucinations by 71% when properly implemented
- Legal RAG: **17-33% hallucination rate** on citations
- Source: [AboutChromebooks](https://www.aboutchromebooks.com/ai-hallucination-rates-across-different-models/)

### McDonald's AI Failure Example
- McHire.com platform (Paradox.ai) exposed personal data for ~64,000 applicants when security researchers found default admin credentials securing chatbot transcripts
- Source: [TechTarget](https://www.techtarget.com/searchenterpriseai/feature/AI-deployments-gone-wrong-The-fallout-and-lessons-learned)

### Specific ChatGPT Agent Failure
- Spent **14 minutes trying to select a value from a dropdown menu** on a real estate website
- Produces "mangled documents" with wrong citations
- Tool use creates "gibberish" in exported PDFs
- Source: [Cal Newport](https://calnewport.com/why-didnt-ai-join-the-workforce-in-2025/), Gary Marcus