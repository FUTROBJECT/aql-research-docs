# Navigator v3.1 — Complete Specification

**Version:** 3.1
**Date:** February 28, 2026
**Status:** Spec — for content agent and builder agent consumption
**Sources:** navigator-v3-concept.html (all 5 tabs), navigator-v3-chat-panel-wireframe.html (4 screens), navigator-claude-integration-logic.md, navigator-v2-spec.md, navigator-v2-content.json, navigator v2 index.html, CONTEXT.md

---

## Section A: Data Model

All data structures the application needs. Content is a single JSON object inlined in the HTML with a fallback `fetch()` for external `navigator-v3-content.json`.

---

### A.1 Four Ethical Criteria

| # | Criterion | Drives | Description |
|---|-----------|--------|-------------|
| 1 | Equitable Student Outcomes | P2 (primary); shapes all others | AI that improves aggregate rates while widening equity gaps is not ethical. |
| 2 | Quality Data, Governed Responsibly | P6 (primary) | Data stewardship: knowing what you have, protecting what's sensitive, being honest about limitations. |
| 3 | Ethics & Safety Foundation | P3, P7, P4 | Human authority, transparency, agency. Safety calibrated to stakes. |
| 4 | Thoughtful, Multi-Year Approach | P9 (primary) | Governance that evolves, builds capacity, keeps institutional sovereignty. |

Cross-cutting pillars (serve all four criteria): P1 (Purpose), P5 (Risk), P8 (Vendor Accountability).

---

### A.2 Nine Operational Pillars

Each pillar has: ID, name, color, principle statement, hook line, criteria mapping, HUMANS mapping, questions array, and a 3-point scoring rubric (3 = Good, 2 = Partial, 1 = Poor).

#### P1: Purpose & Educational Legitimacy
- **Color:** `#0066cc`
- **Criteria:** All four (operational pillar)
- **HUMANS:** Not directly mapped (AQL-original)
- **Principle:** Every AI deployment must serve a genuine educational purpose and protect the meaning of credentials.
- **Hook:** "If it doesn't serve students, it doesn't belong here."
- **Questions (5):** 1.1–1.5 covering educational purpose, mission alignment, student journey placement, credential integrity, CTE/industry validation.
- **Scoring:**
  - **3 (Good):** Clear educational purpose tied to outcomes, mission-aligned, journey-mapped, credential integrity preserved.
  - **2 (Partial):** Purpose stated but not evidence-backed.
  - **1 (Poor):** No clear educational purpose, efficiency-driven or vendor-pushed.
- **Source:** IEAIED Req. 1, ATD Action Area 1, SACSCOC/C-RAC, Advance CTE (Perkins V)

#### P2: Equity & Differential Impact
- **Color:** `#28a745`
- **Criteria:** Criterion 1 (primary)
- **HUMANS:** U (Universal Support), A (Algorithmic Discrimination)
- **Principle:** AI governance must center equity and account for differential impacts on diverse CC student populations.
- **Hook:** "If it doesn't work for all your students, it doesn't work."
- **Questions (7):** 2.1–2.7 covering CC-population testing, disaggregated error rates, differential impact analysis, multilingual support, accessibility/WCAG 2.1 AA, cost model/paywalls, CTE pathway equity.
- **Scoring:**
  - **3 (Good):** Disaggregated data for CC-like populations, differential impact done, tested with target groups, accessible, no cost barriers.
  - **2 (Partial):** Equity acknowledged but data limited.
  - **1 (Poor):** No disaggregated data, equity not addressed.
- **Source:** Kapor Foundation, NAIC, OMB M-25-21, ASCCC

#### P3: Human Authority & Decision Accountability
- **Color:** `#6f42c1`
- **Criteria:** Criterion 3 (primary)
- **HUMANS:** H (Human-Centered)
- **Principle:** Humans — not algorithms — make consequential decisions about students.
- **Hook:** "Who is accountable when the AI is wrong?"
- **Questions (5):** 3.1–3.5 covering decision vs. recommendation distinction, staff override capability, escalation paths, decision audit trail, contractual liability.
- **Scoring:**
  - **3 (Good):** AI recommends/humans decide, override built-in, escalation defined, full audit trail, liability in contract.
  - **2 (Partial):** AI acts with optional review, some audit.
  - **1 (Poor):** AI decides autonomously, no audit trail, vendor disclaims liability.
- **Source:** OMB M-25-21, Singapore Agentic AI, GAO, SACSCOC/C-RAC

#### P4: Student & Faculty Agency
- **Color:** `#fd7e14`
- **Criteria:** Criterion 3
- **HUMANS:** H (Human-Centered), U (Universal Support)
- **Principle:** Students and faculty are empowered participants in AI governance, not subjects of it.
- **Hook:** "Your students are adults. Your faculty run the classroom. Respect both."
- **Questions (8):** 4.1–4.8 — Student Agency (skill-building vs. answer delivery, opt-out with human alternative, data/profile visibility, adult learner recognition) + Faculty Agency (per-course configuration, adjunct-accessible training, no faculty surveillance, shared governance respect).
- **Scoring:**
  - **3 (Good):** Skill-building design, real opt-out, adult autonomy, granular faculty config, adjunct training, no surveillance, shared governance.
  - **2 (Partial):** Some features present.
  - **1 (Poor):** Pure output delivery, no opt-out, admin-only config, faculty tracked.
- **Source:** ASCCC (Title 5 "10+1"), ATD, IEAIED Req. 5, Oregon State Bloom's, UNESCO

#### P5: Risk Proportionality & Harm Mitigation
- **Color:** `#dc3545`
- **Criteria:** All four (operational pillar)
- **HUMANS:** S (Safety & Security)
- **Principle:** Governance intensity matches risk level.
- **Hook:** "What's the worst that happens to a student if this tool fails?"
- **Questions (6):** 5.1–5.6 covering risk tier classification, autonomy limits, agentic bounds, harm scenarios, automation bias training, emerging tech review.
- **Scoring:**
  - **3 (Good):** Risk tier documented, limits defined, harm scenarios with mitigation, bias training, emerging tech process.
  - **2 (Partial):** Acknowledged but partial.
  - **1 (Poor):** No classification, no limits, no harm consideration.
- **Source:** Singapore Agentic AI, NIST AI 600-1, OMB M-25-21, HEAT-AI, GAO

#### P6: Data Stewardship & System Integrity
- **Color:** `#17a2b8`
- **Criteria:** Criterion 2 (primary)
- **HUMANS:** M (Managed Privacy)
- **Principle:** Student data is a public trust.
- **Hook:** "Your data, your rules. Not the vendor's."
- **Questions (8):** 6.1–6.8 covering data inventory, training on student data, data at contract end, FERPA compliance, training data provenance, data quality handling, secure integration, audit rights.
- **Scoring:**
  - **3 (Good):** Complete inventory, no training on student data (contractual), defined deletion, FERPA signed, provenance documented, secure integration, audit rights.
  - **2 (Partial):** Inventory on request, training opt-out, FERPA compliant.
  - **1 (Poor):** Vague practices, student data may train models, no deletion terms.
- **Source:** IEEE P7004, NAIC, NIST 600-1, GAO Principle 2, Alabama Template

#### P7: Transparency & Contestability
- **Color:** `#e83e8c`
- **Criteria:** Criterion 3
- **HUMANS:** N (Notice & Explanation)
- **Principle:** Right to know when AI influences decisions; right to contest.
- **Hook:** "Decisions without recourse are not governance."
- **Questions (7):** 7.1–7.7 covering AI vs. human disclosure, explainability, data source disclosure, appeals/contestability, non-technical documentation, model card, public AI inventory.
- **Scoring:**
  - **3 (Good):** Clear disclosure, explainable, data visible, meaningful contestability, documentation, model card, public inventory.
  - **2 (Partial):** Disclosure present but not prominent, some explainability.
  - **1 (Poor):** No disclosure, invisible AI, no appeals, no documentation.
- **Source:** NAIC, CHAI, NIST 600-1, IEAIED Req. 7-8, ASCCC, OMB M-25-21

#### P8: Vendor Accountability & Institutional Sovereignty
- **Color:** `#6610f2`
- **Criteria:** All four (operational pillar)
- **HUMANS:** S (Safety & Security)
- **Principle:** CCs are buyers, not builders. Vendor relationships must protect sovereignty.
- **Hook:** "You're signing the contract. Make sure it protects your students, not just the vendor."
- **Questions (7):** 8.1–8.7 covering performance SLAs, exit strategy, independent bias audits, model update handling, consortium contracts, incident response, 3-year TCO.
- **Scoring:**
  - **3 (Good):** SLAs with remedies, clean exit, audits supported, advance notice, consortium terms, incident response, transparent cost.
  - **2 (Partial):** Some terms.
  - **1 (Poor):** No guarantees, punitive exit, audits blocked, silent updates, hidden costs.
- **Source:** NAIC, GAO, NIST 600-1, IEAIED, SREB, NACUBO/E&I

#### P9: Institutional Capacity & Continuous Governance
- **Color:** `#795548`
- **Criteria:** Criterion 4 (primary)
- **HUMANS:** Not directly mapped (AQL-original — HUMANS gap)
- **Principle:** Governance must be achievable at every institutional scale.
- **Hook:** "Don't add tools to an ungoverned environment. Build the floor first."
- **Questions (6):** 9.1–9.6 covering governance structure, AI inventory, rescore cycle, accreditation reporting, staff capacity, shared consortium resources.
- **Scoring:**
  - **3 (Good):** Governance in place, inventory maintained, regular rescore, accreditation-ready, capacity assessed, shared resources.
  - **2 (Partial):** Some governance, planned.
  - **1 (Poor):** No governance, no inventory, no review, operating in isolation.
- **Source:** SACSCOC/C-RAC, EDUCAUSE, CHAI, WCET, ATD, Local Government AI Handbook, OMB M-25-21

**Total: 59 questions across 9 pillars.**

---

### A.3 Criteria → Pillar → HUMANS Mapping Table

| Criterion | Primary Pillar(s) | HUMANS Letter(s) |
|-----------|-------------------|-------------------|
| 1. Equitable Student Outcomes | P2 | U, A |
| 2. Quality Data, Governed Responsibly | P6 | M |
| 3. Ethics & Safety Foundation | P3, P7, P4 | H, N |
| 4. Thoughtful, Multi-Year Approach | P9 | (AQL-original — gap) |

| HUMANS Letter | Full Name | Navigator Pillar(s) |
|---------------|-----------|---------------------|
| H | Human-Centered | P3, P4 |
| U | Universal Support | P2, P4 |
| M | Managed Privacy | P6 |
| A | Algorithmic Discrimination | P2 |
| N | Notice & Explanation | P7 |
| S | Safety & Security | P5, P8 |

Cross-cutting pillars P1 (Purpose), P5 (Risk), P8 (Vendor) serve all four criteria.
Gap: HUMANS does not address institutional capacity building (Criterion 4 / P9).

---

### A.4 Eleven Use Cases

**v3.1 definitive list** (from CONTEXT.md; takes priority over v3 concept when conflicts arise):

| ID | Use Case | Default Tier | Key Pillars | Equity Flag |
|----|----------|-------------|-------------|-------------|
| SS-01 | AI Advising / Guided Pathways Assistant | 3 (High) | P1, P2, P3, P5 | Recommendations affect trajectory. Errors compound for first-gen and Pell-eligible. |
| SS-02 | Early Alert / Student Risk System | 3 (High) | P2, P3, P5, P7 | Risk profiling creates surveillance dynamic. Disparate impact on students of color. |
| SS-03 | Financial Aid Triage & FAFSA Support | 3 (High) | P3, P5, P6 | Automated decisions on resource access. Errors disproportionately affect low-income. |
| SS-04 | Student-Facing Chatbot / Digital Front Door | 1 (Low) | P1, P7, P8 | Multilingual coverage gaps. Accessibility barriers. |
| SS-05 | AI Course Tutoring Assistant | 2 (Medium) | P1, P4, P5 | Hallucination risk. Socratic vs. answer mode affects learning. |
| SS-06 | Nudge Campaigns / Behavioral Messaging | 2 (Medium) | P2, P6, P7 | Student data drives outreach. Opt-out critical. Profiling risk. |
| SS-07 | AI Tutoring / Learning Support | 2 (Medium) | P1, P4, P5 | General tutoring across subjects. Faculty configuration. Dependency risk. |
| SS-08 | Basic Needs Support & Resource Navigation | 1 (Low) | P6, P7 | Sensitive data (food insecurity, housing, immigration). Privacy paramount. |
| SS-09 | Career Services AI | 1 (Low) | P1, P2 | Pathway bias across career clusters. Equity across CTE and transfer. |
| SS-10 | Student Journey Mapping / Friction Detection | 2 (Medium) | P5, P6, P7 | PII. Aggregation vs. individual tracking. Surveillance risk. |
| SS-XX | Custom / Other | User assigns | User selects | User describes equity considerations. |

**Changes from v2:**
- SS-05: Renamed from "AI Tutoring / Learning Support" to "AI Course Tutoring Assistant"
- SS-06: **NEW** — Nudge Campaigns / Behavioral Messaging (replaces "Multilingual Support / Translation Services")
- SS-07: AI Tutoring / Learning Support (renumbered; general tutoring, distinct from SS-05 course-specific)
- SS-08: Basic Needs Support & Resource Navigation (was SS-07 in v2)
- SS-09: Career Services AI (was SS-08 in v2)
- SS-10: Student Journey Mapping / Friction Detection (was SS-09 in v2)
- Registration & Enrollment (was SS-10 in v3 concept) has been dropped from the v3.1 use case list.

#### Screening Questions Per Use Case

**SS-01: AI Advising / Guided Pathways Assistant (5 questions)**
1. Does this tool make or influence decisions about which courses, pathways, or programs a student should pursue? — Yes/consequential (GO) / No/informational (GO). Yes confirms High risk.
2. Has your institution identified a specific student journey friction point? — Yes with data (GO) / Yes anecdotally (GO) / No (PAUSE).
3. Will a human counselor review AI pathway recommendations before they reach students? — Always (GO) / Sometimes (PAUSE) / Never (NO-GO).
4. Has vendor provided disaggregated accuracy data across demographics? — Yes (GO) / Partial (PAUSE) / No (PAUSE).
5. Does tool cover full program catalog including CTE, or transfer-optimized? — Full (GO) / Transfer-focused (PAUSE) / Unknown (PAUSE).

**SS-02: Early Alert / Student Risk System (5 questions)**
1. Does system flag individual students as "at risk" and trigger interventions? — Yes (GO, confirms High) / No (GO).
2. Can students see their own risk profile and contest it? — Yes (GO) / No (PAUSE) / Unknown (PAUSE).
3. Differential impact analysis done for false positive rates? — Yes (GO) / Planned (PAUSE) / No (PAUSE).
4. Defined escalation path when system flags a student? — Defined (GO) / Informal (PAUSE) / None (NO-GO).
5. Counseling capacity to follow up on alerts? — Yes (GO) / Strained (PAUSE) / No (PAUSE).

**SS-03: Financial Aid Triage & FAFSA Support (5 questions)**
1. Does tool make decisions affecting whether student receives financial aid? — Yes/automated (NO-GO without human-in-the-loop) / Recommends (GO) / Info only (GO).
2. Access sensitive financial data? — Yes (GO, confirms High, mandatory P6) / No (GO).
3. FERPA-compliant data sharing agreement? — Yes (GO) / In progress (PAUSE) / No (NO-GO).
4. Handle California financial aid complexity? — Yes (GO) / Partially (PAUSE) / No (PAUSE for CA) / N/A non-CA (GO).
5. Clear appeal process for incorrect denial/delay? — Yes (GO) / No (NO-GO).

**SS-04: Student-Facing Chatbot / Digital Front Door (4 questions)**
1. General info only or accesses student records? — General (GO) / Records (GO, upgrade to Tier 2).
2. Clear escalation path to human? — Prominent (GO) / Buried (PAUSE) / No (PAUSE).
3. How many languages? — English only (PAUSE) / 2-3 (GO) / 4+ (GO).
4. Chatbot clearly identifies itself as AI? — Yes (GO) / No (NO-GO) / Unclear (PAUSE).

**SS-05: AI Course Tutoring Assistant (5 questions)**
1. Faculty can configure behavior per course? — Yes (GO) / Limited (PAUSE) / No (PAUSE).
2. What happens when tutor doesn't know answer? — Acknowledges limitation (GO) / Hallucinates (PAUSE) / Unknown (PAUSE).
3. Build capability or deliver answers? — Skill-building (GO) / Answer delivery (PAUSE) / Mixed (GO).
4. Accessible to students with disabilities? — Yes (GO) / Partial (PAUSE) / No (PAUSE) / Unknown (PAUSE).
5. Vendor uses student interaction data to train models? — No/contractual (GO) / Yes (NO-GO) / Unknown (PAUSE).

**SS-06: Nudge Campaigns / Behavioral Messaging (4 questions)**
(From wireframe — new use case in v3.1)
1. Does this tool access personally identifiable student data (PII)? — Yes/accesses student records (GO, confirms data access) / Yes/limited to directory info (GO) / No/anonymous only (GO).
2. Can students opt out of AI-initiated contact? — Yes/opt-out available (GO) / Partial/some messages mandatory (PAUSE) / No opt-out (NO-GO) / Unknown (PAUSE).
3. Is the content of outgoing messages AI-generated or template-based? — Template only/staff write all messages (GO) / AI-generated with staff review (GO) / Fully AI-generated (PAUSE) / Unknown (PAUSE).
4. Does the vendor use student interaction data to train or improve their models? — No/contractually prohibited (GO) / Aggregated/anonymized only (PAUSE) / Yes/individual data used (NO-GO) / Unknown (PAUSE).

**SS-07: AI Tutoring / Learning Support (5 questions)**
(Inherits from v2 SS-05, adapted for general tutoring context)
1. Faculty can configure behavior per course? — Yes (GO) / Limited (PAUSE) / No (PAUSE).
2. What happens when tutor doesn't know answer? — Acknowledges limitation (GO) / Hallucinates (PAUSE) / Unknown (PAUSE).
3. Build capability or deliver answers? — Skill-building (GO) / Answer delivery (PAUSE) / Mixed (GO).
4. Accessible to students with disabilities? — Yes (GO) / Partial (PAUSE) / No (PAUSE) / Unknown (PAUSE).
5. Vendor uses student interaction data to train models? — No/contractual (GO) / Yes (NO-GO) / Unknown (PAUSE).

**SS-08: Basic Needs Support & Resource Navigation (4 questions)**
1. Collects data about basic needs? — Yes (GO, P6 emphasis) / No (GO).
2. Data shared with external parties? — No (GO) / Yes with consent (GO) / Yes without consent (NO-GO).
3. Can students access resources without disclosing hardship to AI? — Yes (GO) / No (PAUSE).
4. Connects to local resources actually available? — Yes/locally configured (GO) / Generic national database (PAUSE).

**SS-09: Career Services AI (4 questions)**
1. Career pathway recommendations or job readiness? — Pathways (GO, consider Tier 2 upgrade) / Readiness (GO) / Both (GO).
2. Serves CTE/trade careers equitably? — Yes (GO) / Mostly professional/transfer (PAUSE) / Unknown (PAUSE).
3. Steers students toward specific employers? — No (GO) / Yes disclosed (GO) / Yes undisclosed (NO-GO).
4. Resume/interview content culturally responsive? — Yes (GO) / Generic (PAUSE) / Unknown (PAUSE).

**SS-10: Student Journey Mapping / Friction Detection (5 questions)**
1. Individual tracking or aggregate? — Individual (GO, confirms Tier 2) / Aggregate (GO) / Both (GO, consider Tier 3).
2. Who has access? — Counselors (GO) / Admins (GO) / Faculty (GO) / Vendors (PAUSE).
3. Students see own journey data? — Yes (GO) / No (PAUSE).
4. Analytics used for individual student decisions? — Yes (GO, upgrade to Tier 3) / No (GO).
5. Clear data retention policies? — Yes (GO) / No (PAUSE).

**SS-XX: Custom / Other (5 generic questions)**
1. Affects student access, standing, or progress? — Yes (GO, High risk indicator) / No (GO).
2. Accesses student records or sensitive data? — Yes (GO, P6 emphasis) / No (GO).
3. Clear educational purpose? — Yes (GO) / No (PAUSE).
4. Human reviews AI outputs before they reach students? — Yes (GO) / No (PAUSE for high-risk).
5. Vendor provided performance data across diverse populations? — Yes (GO) / No (PAUSE).

#### AI Pre-fill Data Structure

For known tools, the content JSON includes pre-filled screening answers:

```json
{
  "screening_prefills": {
    "tool_name": "Mainstay",
    "use_case": "SS-06",
    "prefills": {
      "q1": {
        "value": "yes_student_records",
        "confidence": "high",
        "source": "Published product documentation",
        "caveat": null
      },
      "q2": {
        "value": "yes_opt_out",
        "confidence": "high",
        "source": "Published product documentation",
        "caveat": null
      },
      "q3": {
        "value": null,
        "confidence": null,
        "source": null,
        "caveat": "I don't have reliable information about whether Mainstay's messages are template-based or AI-generated in your specific configuration."
      },
      "q4": {
        "value": "aggregated_anonymized",
        "confidence": "medium",
        "source": "Published data practices",
        "caveat": "Verify the specific language in your contract — 'aggregated' can mean different things."
      }
    }
  }
}
```

---

### A.5 Routing Questions (Step 0)

8 questions with scoring logic — see Section B for full detail.

---

### A.6 Dependency Profile Questions (D1–D4)

4 universal questions — see Section D for full detail.

---

### A.7 Mechanism Detection Questions (MD-01, MD-02, MD-03)

3 mechanism questions with escalation logic — see Section E for full detail.

---

### A.8 Eight No-Go Criteria

| ID | Statement | Hook | Pillar | Detection |
|----|-----------|------|--------|-----------|
| NG-01 | No clear educational purpose. | "If you can't articulate the educational purpose, don't buy it." | P1 | P1 score = 1 OR screening indicates no purpose. |
| NG-02 | Students are not training data. | "Vendors that train models on student data are extracting value from the most vulnerable populations in higher education." | P6 | Explicit yes/no in no-go checklist. |
| NG-03 | No human override for consequential decisions. | "When AI makes decisions about financial aid, enrollment, or academic standing without human review, students lose recourse." | P3 | P3 score = 1 AND risk tier = High. |
| NG-04 | Vendor blocks independent bias audits. | "Vendors who block audits behind IP claims are choosing their property over your students' civil rights." | P8 | Explicit yes/no in no-go checklist. |
| NG-05 | No FERPA-compliant data sharing agreement. | "This is a legal requirement, not a best practice." | P6 | Explicit yes/no in no-go checklist. |
| NG-06 | No student disclosure of AI use. | "Students have a right to know when AI influences decisions that affect them. Period." | P7 | P7 score = 1 OR explicit no-go question. |
| NG-07 | Decisions without recourse are not governance. | "If a student cannot contest an AI-influenced decision, you have automation, not governance." | P7 | P7 score = 1 OR explicit no-go question. |
| NG-08 | Vendor lock-in undermines institutional sovereignty. | "If you can't leave without losing your students' data or paying punitive switching costs, the vendor is governing you." | P8 | Explicit yes/no in no-go checklist. |

**Dual detection:** No-go criteria trigger both by explicit checklist answers AND by score-derived signals. Score-derived flags auto-set at render time with amber warning note explaining the trigger, radio buttons disabled.

**No-Go Detection Map:**

| No-Go | Checklist Detection | Score-Derived Detection |
|-------|---------------------|------------------------|
| NG-01 | User answers "No" | P1 = 1 (auto-flag) |
| NG-02 | User answers "No" | — |
| NG-03 | User answers "No" | P3 = 1 AND Tier 3 (auto-flag) |
| NG-04 | User answers "No" | — |
| NG-05 | User answers "No" | — |
| NG-06 | User answers "No" | P7 = 1 (auto-flag) |
| NG-07 | User answers "No" | P7 = 1 (auto-flag) |
| NG-08 | User answers "No" | — |

---

### A.9 Three Archetypes

#### Lightweight — "Start small. Start now."
- **Profile:** Small or rural. Limited IT. 1–2 people wearing many hats. Under 5,000 students. No formal AI governance yet.
- **You might be this if:** No dedicated IT director; first AI tool evaluation; need minimum viable governance.
- **Starting rec:** One Tier 1 or 2 use case. Use templates directly. Quarterly review. Score 5 mandatory pillars (P1, P2, P6, P7, P8).
- **Represents:** ~40–50 of California's 116 CCs.

#### Building — "Structure enables innovation."
- **Profile:** Mid-size. Some analytics/data capability. IT director and IR. AI committee forming.
- **You might be this if:** AI happening but governance hasn't caught up; some governance but informal; faculty interested but need guardrails.
- **Starting rec:** 2–3 use cases across tiers. Cross-functional AI working group quarterly. Begin disaggregated tracking. All 9 pillars active.
- **Represents:** ~25–30 similar colleges.

#### Scaling — "Govern the portfolio, not just the tool."
- **Profile:** Large. Dedicated technical bench. Data warehouse, analytics team, innovation office. Mature governance. Multiple tools deployed.
- **You might be this if:** Multiple AI tools deployed; need annual review and portfolio coordination.
- **Starting rec:** Portfolio approach. Formal governance with project owners. Bias audits for Tier 3. Standing committee.
- **Represents:** ~5–10 similar colleges.

---

### A.10 Risk Tier System

| Tier | Label | Description | Required Pillars | Example |
|------|-------|-------------|------------------|---------|
| 1 | Lower Risk | Informational only. No decisions affecting access. No sensitive data. | P1, P2, P6, P7, P8 mandatory. P3, P4, P5, P9 recommended. | FAQ chatbot |
| 2 | Medium Risk | Touches advising or instructional core. Human reviews outputs. Accesses student records. | All 9 mandatory. P2 and P6 must ≥ 2. | Tutoring assistant |
| 3 | High Risk | Affects enrollment, financial aid, academic standing. Automated/semi-automated decisions. Sensitive data. | All 9 mandatory. P2 and P6 ≥ 2. Full governance review required. | Early alert system |

**Override mechanism:** Users can override the default tier. Lowering requires documented reason. Lowering from a mechanism-adjusted tier requires justification.

---

### A.11 Scoring Interpretation Patterns

| # | Pattern | Interpretation | Action Class |
|---|---------|---------------|--------------|
| 1 | Any pillar = 1 on High-Risk tool | Critical governance gap. For P2, P3, or P5 = effectively no-go. | nogo |
| 2 | P1 = 1 | No clear educational purpose. | nogo |
| 3 | Multiple pillars = 2 (≥3) | Tool meets basics but has gaps the institution must compensate for. | caution |
| 4 | All pillars ≥ 2 | Solid baseline. Tool and governance aligned. | proceed |
| 5 | Strong P6 & P8, weak P4 & P7 | Vendor technically sound but not designed with students as participants. | insight |
| 6 | Strong P4 & P7, weak P6 | Vendor markets well but hasn't done data governance work. | insight |
| 7 | P9 = 1 | Institutional readiness gap. Build governance first. | insight |
| 8 | High Dependency + Tier 3 | Maximum governance combination. Full dependency protections. | insight |
| 9 | High Dependency + weak P4 | Double dependency risk — institutional and individual. | insight |
| 10 | Med/High Dependency + P8 = 1 | Dependency on vendor that doesn't meet accountability standards. | insight |

**Tier Benchmarks by Archetype:**
- **Lightweight:** Minimum viable = 5 mandatory pillars scored, no no-go, P1 ≥ 2. Good = 5 pillars ≥ 2. Strong = all pillars ≥ 2.
- **Building:** Minimum viable = all 9 scored, P2 & P6 ≥ 2, no no-go. Good = all ≥ 2, committee reviewed. Strong = most at 3, documented mitigation for any 2.
- **Scaling:** Minimum viable = all 9 scored, no pillar at 1, P2 & P6 ≥ 2. Good = most at 3, portfolio complete, annual review active. Strong = all at 3, cross-tool governance, system-level contributions.

---

### A.12 Roadmap Content Assembly Rules

See Section G for complete detail.

**Assembly formula:**
```
ROADMAP = f(archetype, use_case, risk_tier, dependency_profile, pillar_scores, mechanism_profile)
```

**12 Sections:** Executive Summary, No-Go Conditions, Before You Deploy, Pillar-Specific Remediation, Who's Involved (RACI), 90-Day Metrics, Review Cadence, Dependency Governance, Escalation Triggers, Decision Rules, Toolkit References, HUMANS Alignment (CA only), Next Steps Checklist.

---

## Section B: Step 0 — Routing Flow

The institutional context questionnaire that produces ranked use case recommendations.

---

### B.1 Eight Routing Questions

| # | Question | Type | Signal | Role |
|---|----------|------|--------|------|
| Q1 | Where are students getting stuck? | Multi-select (up to 3) | Direct mapping: +3 pts per selection to mapped use cases | Primary use case signal |
| Q2 | How many students do you serve? | Single-select | Scale modifier / filter | Archetype validation (soft) |
| Q3 | What's your data situation? | Single-select | Feasibility gate: GREEN/YELLOW/RED per use case | Flags/downranks data-dependent use cases |
| Q4 | Staffing reality for Student Services tech? | Single-select | Archetype primary / tier ceiling | Tier ceiling + archetype derivation |
| Q5 | Biggest equity gaps? | Multi-select (up to 2) | Equity boost: +2 pts per selection | Weight toward equity-aligned use cases |
| Q6 | Is AI already being used informally? | Single-select | Urgency override | May override ranking ("govern what exists first") |
| Q7 | Any AI governance in place? | Single-select | Archetype adjust: +/−1 step | Adjusts archetype, feeds back to tier ceiling |
| Q8 | What's driving this? | Single-select | Contextual boost: +2 pts | Matches institutional moment |

**Q1 Options** (multi-select, up to 3):
Each option maps to one or more use cases via `q1_map` in the scoring data.

**Q3 Data Readiness Flags:**
Each use case has a data readiness rating per Q3 answer:
- GREEN: Data ready for this use case
- YELLOW: Data partially ready, proceed with caution
- RED: Data not ready, move to "Consider Later"

**Q4 Staffing → Tier Ceiling:**
- Dedicated staff → Tier 3 max (Scaling archetype signal)
- Central IT → Tier 2 max (Building archetype signal)
- Vendor-dependent / 1–2 people → Tier 1 max (Lightweight archetype signal)

---

### B.2 Five-Phase Routing Algorithm

```
Phase 1 — Signal Scoring (Inputs: Q1, Q5)
  for each use_case (SS-01 through SS-10): score = 0
    Q1 selections: +3 pts to each mapped use case
    Q5 selections: +2 pts to each mapped use case
    cap: max 5 pts per use case

Phase 2 — Feasibility Gating (Inputs: Q3, Q4)
  Q3 data readiness → GREEN/YELLOW/RED flag per use case
  Q4 staffing → tier ceiling (dedicated=T3, central=T2, vendor-dep=T1)
  RED flag OR use_case_tier > ceiling → "Consider Later"

Phase 3 — Archetype Derivation (Inputs: Q4, Q7, Q2)
  Q4 primary: dedicated → Scaling, central → Building, vendor/1-2 → Lightweight
  Q7 adjusts +/-1: Building + formal governance → Scaling, etc.
  Q2 validates: flags unusual combos (e.g., <5K + Scaling)
  derived archetype OVERRIDES raw Q4 tier ceiling

Phase 4 — Contextual Overrides (Inputs: Q6, Q8)
  Q6 "already happening" → boost deployed tools to top
  Q6 "don't know" → +2 to SS-04, add "start with AI inventory"
  Q8 motivation: +2 pts to motivation-matched use cases

Phase 5 — Ranking & Output (Inputs: all phases)
  final_score = min(raw_signal, 5) + overrides
  sort: final_score desc → risk_tier asc → data_flag (G > Y > R)
  classify:
    GREEN + within ceiling = Recommended
    YELLOW or at ceiling = Possible (caveats)
    RED or above ceiling = Consider Later
  output: top 2-3 Recommended + "Why it fits" from Q1/Q5/Q8
  fallback: if no use case scores > 0, recommend SS-04 (Chatbot)
```

---

### B.3 Output: Routing Results Screen

**Components:**
1. **Ranked recommendations (2–3):** Use case name, one-liner, risk tier badge, data readiness flag, "Why it fits" narrative, "Evaluate This Use Case →" button.
2. **Consider Later (0–2):** Use cases that would have high impact but aren't feasible yet, with explanation.
3. **Institutional Profile:** Archetype (from Q4+Q7+Q2), equity priority (from Q5), urgency (from Q6), data readiness (from Q3).

"Why it fits" text assembled from user's specific Q1 + Q5 + Q8 answers — not generic descriptions.

**Default fallback:** If no use case scores above 0, SS-04 (Chatbot) is recommended as default starting point.

---

### B.4 AI Panel During Routing

**AI Panel State:** Visible
**Header context:** "Tool Identification"

The AI chat panel assists during routing by:
- Recognizing unfamiliar tools by name or description
- Mapping tools to use case categories
- Surfacing what the tool actually does vs. what the vendor says

The AI does NOT:
- Recommend whether the tool is appropriate
- Assign archetypes
- Override the routing algorithm

---

### B.5 Skipping Step 0

Users who already know their use case skip Step 0 entirely:
- **Full Path:** Landing → Use Case Selector directly
- **Quick Path:** Landing → Archetype Selector → Use Case Selector

---

## Section C: Step 1 — Identify Flow

Use case selection and screening.

---

### C.1 Use Case Selector Interface

**Layout:** 10 use case cards + 1 Custom card in a responsive 2-column grid.

**Card contents:**
- Use case ID badge (e.g., "SS-01")
- Use case name
- Risk tier badge (color-coded: red = High, amber = Medium, green = Lower)
- One-liner description
- Key pillar badges
- Equity flag text

**Card sorting:** By risk tier: High (Tier 3) first, then Medium (Tier 2), then Lower (Tier 1), then Custom.

**Selection behavior:** Single selection — one use case at a time. Clicking a card selects it.

**Custom card (SS-XX):** Dashed border, gray text, "You assign tier" badge.

---

### C.2 AI Tool Input Field

**Position:** Above the use case grid, inside a teal-bordered (`--ai-accent`) container.
**Design:** Teal background (`--ai-bg`), teal border, 8px radius.
**Label:** Teal icon (flower ✿) + "Describe your tool"
**Input:** Full-width text field with placeholder "Enter a tool name, vendor, or description."
**Hint text:** "Enter a tool name, vendor, or description. The AI assistant will suggest a category."

**Behavior:**
1. User types tool name/description
2. System checks keyword bank for known tools
3. If match found → AI Suggestion Card appears below input
4. If no match → generic response in chat panel

---

### C.3 AI Suggestion Card

**Position:** Below the AI tool input, above the "or select a category directly" divider.
**Design:** White background, teal border, 6px radius.

**Contents:**
- Label: "AI SUGGESTION" (teal, uppercase, 8pt)
- Suggestion: e.g., "SS-06: Nudge Campaigns / Behavioral Messaging" (bold)
- Reason: Plain-language explanation of why this category fits (8.5pt, gray)
- Action: "Select →" button (teal background, white text)

**Side effect:** When suggestion card appears, the corresponding use case card in the grid below gets highlighted (teal border + teal background).

**Override:** If user ignores the AI suggestion and clicks a different card, that selection takes priority.

---

### C.4 Screening Questions

After use case selection, user answers 4–5 screening questions.

**Presentation:** One question per card, all visible on screen (not one-at-a-time). Each question card shows the question text with radio-button options.

**AI Pre-fill Logic:** For known tools, certain answers are pre-filled:
- Card gets teal border + teal background (class `ai-prefilled`)
- Tag inside card: "AI-suggested — verify with vendor" (flower icon, teal, uppercase, 7.5pt)
- Suggested option gets teal highlighting (class `ai-suggested`): teal border, teal 8% opacity background, teal text, font-weight 600
- Questions where AI has no reliable info are left blank (no pre-fill)

**User interaction:**
- Clicking an AI-suggested option confirms it → changes to solid selected state
- Clicking a different option overrides the AI suggestion
- Unconfirmed AI suggestions carry through to profile as "AI-suggested, unverified"

---

### C.5 GO / PAUSE / NO-GO Decision Logic

```
if (nogo_count > 0) → result = 'nogo'
else if (pause_count >= 2) → result = 'pause'
else if (pause_count == 1) → result = 'go' (with flagged concern)
else → result = 'go'
```

**GO display:** No red flags. Proceed to dependency profile.
**PAUSE display:** Flagged concerns (not deal-breakers). User can proceed (flags carry forward) or select different use case.
**NO-GO display:** Hard stop. Shows trigger, reasoning, remediation, and alternative lower-risk use cases. User can "Continue Anyway" — the tool advises but doesn't block.

Flags carry into the governance profile and are referenced in the roadmap.

---

### C.6 AI Panel During Screening

**AI Panel State:** Visible
**Header context:** "Screening — SS-{XX}" (with use case ID)
**Input placeholder:** "Ask about screening..."

**Behavior:**
- AI provides context about pre-filled answers on panel load
- AI explains which questions it left blank and why
- AI can discuss specific screening questions when asked
- Responses include caveats and verification prompts

---

## Section D: Dependency Profile

Four universal dependency questions asked after screening and before mechanism detection.

---

### D.1 Question Definitions

| ID | Question | What It Measures | Response Tiers |
|----|----------|------------------|----------------|
| D1 | **Disappearance Test:** "What happens if this tool disappears tomorrow?" | Operational fragility | 1 = Convenience lost, can still complete task / 2 = Significant disruption, workarounds exist / 3 = Service stops, unable to perform |
| D2 | **Capability Trajectory:** "After a year of use, will users be better at this task without the tool, same, or less capable?" | Skill direction | 1 = Better — capability building / 2 = Same — neutral / 3 = Less capable — erosion risk |
| D3 | **Navigate-With vs. Navigate-For:** "Does the tool show users how to navigate, or navigate for them?" | Agency level | 1 = Navigate-with, explains why / 2 = Mix/configurable / 3 = Navigate-for, users input need, tool produces outcome |
| D4 | **Exit Design:** "Is there a point where users are expected to do this without the tool?" | Reversibility | 1 = Independence designed, explicit milestone / 2 = Parallel systems, supplements / 3 = Permanent infrastructure, tool is the process |

Each question includes a "What you're looking for" description that legitimizes all answers.

---

### D.2 Scoring

**Sum of 4 questions. Range: 4–12.**

| Score Range | Profile | Badge Color | Governance Response |
|-------------|---------|-------------|---------------------|
| 4–5 | Low Dependency | Green | No additional governance required. Standard review cadence. |
| 6–8 | Medium Dependency | Yellow/Amber | Configuration review required. 6-month capability check. Alternative maintenance plan. |
| 9–12 | High Dependency | Red | Dependency acknowledgment. Vendor lock-in assessment. 12-month sunset evaluation. Capability impact tracking (Tier 3 only). |

---

### D.3 Governance Requirements Per Profile

**Low (4–5):** No additional requirements. Standard review cadence.

**Medium (6–8) — 3 requirements:**
- DEP-M1: Configuration review (before deployment + 6-month mark)
- DEP-M2: 6-month capability check
- DEP-M3: Alternative maintenance (ongoing, tested annually)

**High (9–12) — 4 requirements:**
- DEP-H1: Dependency acknowledgment (before deployment)
- DEP-H2: Vendor lock-in assessment (before deployment)
- DEP-H3: 12-month sunset evaluation
- DEP-H4: Capability impact tracking (Tier 3 only, ongoing)

---

### D.4 Dependency × Risk Tier Interaction

| | Low Dep (4–5) | Medium Dep (6–8) | High Dep (9–12) |
|---|---|---|---|
| Tier 1 | Standard | + DEP-M1,M2,M3 | + DEP-H1,H2,H3 |
| Tier 2 | Standard | + DEP-M1,M2,M3 | + DEP-H1,H2,H3 |
| Tier 3 | Standard | + DEP-M1,M2,M3 | + DEP-H1,H2,H3,H4 |

---

### D.5 Design Principles

1. **Not gates.** Profiles, not GO/NO-GO. No dependency score blocks deployment.
2. **Permanent infrastructure is valid.** High dependency is honest, not wrong.
3. **Legitimize every answer.** "What you're looking for" text for each tier.
4. **Patterns emerge through use.** After profiling 3–4 tools, leaders notice patterns.
5. **Dependency is not risk.** Orthogonal independent dimensions.

---

### D.6 AI Panel During Dependency Profile

**AI Panel State:** Visible (hybrid node)
**Header context:** "Dependency — SS-{XX}"

The questions are fixed (framework-owned). AI can help interpret ambiguous answers or surface context the user might not know about their own tool's integration depth.

AI does NOT score dependency or assign the profile level.

---

## Section E: Mechanism Detection

Three mechanism questions that detect hidden risk in how the tool works. Runs for every use case, after dependency profiling and before risk tier confirmation.

---

### E.1 MD-01: Behavioral Pattern-Matching

**Question:** "How does this tool decide what to show or recommend to each student?"
**Detects:** Behavioral pattern-matching — tools that personalize outputs based on individual student data.

| Option | Label | Description | Escalation | Forced Pillars | Equity Flag |
|--------|-------|-------------|------------|----------------|-------------|
| A | Same for everyone | Every student sees the same information. | None | — | — |
| B | Student-configured | Students choose preferences themselves. | None | — | — |
| C | Profile-based personalization | Tool uses student data (major, demographics, prior interactions) to tailor what it shows. Students may not know what drives the personalization. | +1 tier | P2 ≥ 2, P7 ≥ 2 | — |
| D | Behavioral pattern-matching | Tool observes behavior over time and adjusts based on inferred patterns. | +1 tier | P2 ≥ 2, P7 ≥ 2 | Yes |
| E | Unknown | The team doesn't know how the tool personalizes. | +1 tier | P7 ≥ 2 | — |

---

### E.2 MD-02: Student Classification

**Question:** "Does this tool group, classify, or score individual students?"
**Detects:** Student classification & segmentation — tools that create categories of students.

| Option | Label | Description | Escalation | Forced Pillars | Equity Flag |
|--------|-------|-------------|------------|----------------|-------------|
| A | No classification | Tool does not categorize students. | None | — | — |
| B | Self-selected groups | Students choose their own groups. | None | — | — |
| C | Predictive scoring | Tool assigns risk scores, predicted outcomes, or performance categories. | +1 tier | P2 ≥ 2, P5 ≥ 2, P7 ≥ 2 | — |
| D | Behavioral clustering | Tool groups students based on observed behavior patterns. | +1 tier | P2 ≥ 2, P5 ≥ 2, P7 ≥ 2 | Yes |
| E | Unknown | The team doesn't know if the tool classifies students. | +1 tier | P7 ≥ 2 | — |

---

### E.3 MD-03: Autonomous Action

**Question:** "Can this tool take actions or contact students without a human initiating it?"
**Detects:** Autonomous action & outreach — tools that act on their own.

| Option | Label | Description | Escalation | Forced Pillars | Equity Flag |
|--------|-------|-------------|------------|----------------|-------------|
| A | No autonomous action | Tool only responds to human-initiated requests. | None | — | — |
| B | Human-triggered automation | Staff set up the action; tool executes on schedule. | None | — | — |
| C | Rule-based triggers | Tool monitors conditions and acts when thresholds are met. | +1 tier (only if currently Tier 1) | P3 ≥ 2, P5 ≥ 2 | — |
| D | Autonomous outreach | Tool decides when and how to contact students based on its own analysis. | +1 tier | P3 ≥ 2, P5 ≥ 2, P7 ≥ 2 | — |
| E | Cascading actions | Tool can trigger sequences of actions across systems without per-action human approval. | +2 tiers (cap at 3) | P3 ≥ 2, P5 ≥ 2, P7 ≥ 2 | No-go flag for review |

---

### E.4 Escalation Logic

```javascript
// Escalation accumulator
var esc = 0, forced = {}, eqFlag = false, unknowns = [];

// MD-01: Behavioral Pattern-Matching
if (md01 === 'c') { esc += 1; forced.P2 = 2; forced.P7 = 2; }
if (md01 === 'd') { esc += 1; forced.P2 = 2; forced.P7 = 2; eqFlag = true; }
if (md01 === 'e') { esc += 1; forced.P7 = 2; unknowns.push('MD-01'); }

// MD-02: Student Classification
if (md02 === 'c') { esc += 1; forced.P2 = 2; forced.P5 = 2; forced.P7 = 2; }
if (md02 === 'd') { esc += 1; forced.P2 = 2; forced.P5 = 2; forced.P7 = 2; eqFlag = true; }
if (md02 === 'e') { esc += 1; forced.P7 = 2; unknowns.push('MD-02'); }

// MD-03: Autonomous Action
if (md03 === 'c' && default_tier === 1) { esc += 1; forced.P3 = 2; forced.P5 = 2; }
if (md03 === 'd') { esc += 1; forced.P3 = 2; forced.P5 = 2; forced.P7 = 2; }
if (md03 === 'e') { esc += 2; forced.P3 = 2; forced.P5 = 2; forced.P7 = 2; }

// Calculate adjusted tier
adjusted_tier = Math.min(3, default_tier + esc);
```

Tier adjustments are **additive** across all three questions but **capped at Tier 3**.

---

### E.5 Forced Pillar Requirements Table (Summary)

| Mechanism Detected | Forced Pillar Minimums |
|-------------------|------------------------|
| Profile-based personalization (MD-01 C) | P2 ≥ 2, P7 ≥ 2 |
| Behavioral pattern-matching (MD-01 D) | P2 ≥ 2, P7 ≥ 2 |
| Predictive scoring (MD-02 C) | P2 ≥ 2, P5 ≥ 2, P7 ≥ 2 |
| Behavioral clustering (MD-02 D) | P2 ≥ 2, P5 ≥ 2, P7 ≥ 2 |
| Rule-based triggers (MD-03 C, Tier 1 only) | P3 ≥ 2, P5 ≥ 2 |
| Autonomous outreach (MD-03 D) | P3 ≥ 2, P5 ≥ 2, P7 ≥ 2 |
| Cascading actions (MD-03 E) | P3 ≥ 2, P5 ≥ 2, P7 ≥ 2 |
| Unknown (any question) | P7 ≥ 2 |

---

### E.6 Equity Screening Flag

When MD-01 D (behavioral pattern-matching) or MD-02 D (behavioral clustering) is selected, an additional equity screening question is injected into the P2 (Equity) pillar scoring:

> "Has your institution tested whether this tool's personalization or classification produces different outcomes for different student populations?"

---

### E.7 AI Panel During Mechanism Detection

**AI Panel State:** Visible
**Header context:** "Mechanism — SS-{XX}"
**Input placeholder:** "Ask about mechanisms..."

**AI Context Note** (inline, not in chat panel):
- Position: Top of mechanism detection area
- Design: Teal background, teal border, 6px radius
- Icon: 20px teal circle with flower symbol
- Content: Plain-language summary of how the tool works technically
- Source note: "This analysis is based on published product information. If your configuration differs, answer based on your actual deployment."

**Option-Level AI Highlighting:**
Within mechanism options, the AI-suggested option gets teal border/background with a small teal annotation explaining why.

Example for Mainstay on MD-01:
- Option C highlighted: "AI analysis suggests this option — Mainstay uses enrollment data and milestone proximity to personalize messages."

**AI does NOT:**
- Assign the escalation tier
- Set forced pillar minimums
- Those are deterministic outputs of the mechanism logic

---

### E.8 Tier Adjustment Interstitial

If tier is adjusted after mechanism detection:
- Show interstitial explaining: original tier, each mechanism that triggered escalation, adjusted tier
- "Continue →" button proceeds to Risk Tier screen

If no adjustment needed:
- Brief "No Adjustment Needed" confirmation before Risk Tier screen

---

## Section F: Step 2 — Evaluate Flow

Pillar scoring and no-go check.

---

### F.1 Risk Tier Display

**Position:** After mechanism detection.
**Content:** Shows the risk tier — which may now reflect mechanism-adjusted values.

**Three tier cards** in a 3-column grid:
- Tier 1 (green border when active)
- Tier 2 (amber border when active)
- Tier 3 (red border when active)

The mechanism-adjusted tier is pre-selected. Each card shows: tier label, description, governance requirements summary.

**Override:** User can override tier. Lowering from a mechanism-adjusted tier requires justification text. Override badge shows on profile.

**SS-XX Gating:** For Custom/Other:
- Required textarea: "Describe the worst realistic outcome for a student if this tool fails, gives bad advice, or is misused."
- Tier cards grayed out (opacity 0.4, pointer-events: none) until textarea has ≥ 20 characters
- Worst-case text stored in `state.customWorstCase`

---

### F.2 Pillar Scoring Interface

One pillar per screen, scored sequentially.

**Each pillar screen shows:**
1. **Pillar header:** Color bar (4px, pillar color), pillar ID, pillar name, principle statement (italic), hook line (bold, pillar color)
2. **HUMANS badge** (California only): Letter badge next to pillar name
3. **Mechanism forced minimum banner** (if applicable): Warning banner if mechanism detection flagged this pillar, showing minimum required score
4. **Reference questions:** Collapsed by default inside "What to look for (N reference questions)" accordion. Questions are guidance, not scored individually.
5. **Score cards:** Three columns (1/2/3) with:
   - Score number (20pt, bold, color-coded: 1 = red, 2 = amber, 3 = green)
   - Label (Good/Partial/Poor)
   - Description text
   - 4px top border in score color
6. **Notes textarea:** "Notes (optional)" with placeholder "Add notes about your scoring rationale..."
7. **Progress bar:** Pillar N of total

**Equity screening injection:** If MD-01 D or MD-02 D was selected, an additional equity question is injected into the P2 scoring view.

**Inline no-go warning:** If P1 = 1, or P3 = 1 on High-Risk, immediate inline warning appears.

**Scoring below forced minimum:** If user scores below a mechanism-forced minimum, a warning appears but does not block — the score is recorded with a flag.

---

### F.3 Mandatory vs. Recommended Pillars

| Pillar | Tier 1 | Tier 2 | Tier 3 |
|--------|--------|--------|--------|
| P1 | Mandatory | Mandatory | Mandatory |
| P2 | Mandatory | Mandatory (≥ 2) | Mandatory (≥ 2) |
| P3 | Recommended | Mandatory | Mandatory |
| P4 | Recommended | Mandatory | Mandatory |
| P5 | Recommended | Mandatory | Mandatory |
| P6 | Mandatory | Mandatory (≥ 2) | Mandatory (≥ 2) |
| P7 | Mandatory | Mandatory | Mandatory |
| P8 | Mandatory | Mandatory | Mandatory |
| P9 | Recommended | Mandatory | Mandatory |

Tier 1: Score P1, P2, P6, P7, P8 mandatory (5 pillars). P3, P4, P5, P9 recommended (can skip).
Tier 2/3: All 9 mandatory.

---

### F.4 No-Go Check

**Position:** After all pillar scoring.

8 yes/no questions. "No" triggers a flag with remediation action.

**Auto-flagging from pillar scores** (at render time):
- P1 = 1 → auto-flag NG-01
- P3 = 1 AND Tier 3 → auto-flag NG-03
- P7 = 1 → auto-flag NG-06, NG-07

Auto-flagged items:
- Show warning note explaining the score-derived trigger
- Radio buttons grayed out (pointer-events: none, opacity: 0.5), pre-set to "No"
- Styled with amber border/background (distinguished from user-flagged items which get red border)

All 8 criteria must be answered before continuing (auto-flagged items count as answered).

The tool flags and documents but does not block.

---

### F.5 AI Panel During Evaluation

**AI Panel State:** Collapsed on ALL scoring screens
**Collapsed rail:** 48px wide strip on right side
**Design:**
- Gray background (`gray-50`)
- Gray dot (8px circle, `gray-300` — NOT teal, deliberately inactive)
- Vertical text: "AI not available — institutional judgment" (`writing-mode: vertical-rl`, 7.5pt, gray-400)

This is the boundary rule made visible. The AI is intentionally absent during pillar scoring and no-go checks because these are institutional value judgments.

---

## Section G: Output Flow (Profile + Roadmap)

---

### G.1 Governance Profile Screen

The payoff screen. Shows everything the user needs.

**Hero section:**
- Tool name
- Use case name
- Risk tier badge (mechanism-adjusted if applicable, with "Adjusted from Tier X" note)
- Archetype badge
- Dependency badge (Low/Medium/High with color)
- Mechanism badges (e.g., "Pattern-Matching Detected", "Predictive Scoring", "Autonomous Outreach")
- Override note if tier was manually changed

**Worst-case callout (SS-XX only):** Caution-bordered callout showing the user's worst-case harm scenario text.

**Score summary:** Total score / possible, no-go flag count.

**No-go banners:** Red banners for each triggered no-go with remediation action.

**Pillar table:** All scored pillars with:
- Color bar (4px, pillar color)
- Pillar name
- Score (1/2/3, color-coded)
- Status label (Good/Partial/Poor)
- HUMANS badge (California only)
- Forced minimum indicator (if mechanism-flagged and score is below)

**Mechanism profile:** Detected mechanisms with tier adjustment explanation, forced pillar minimums, equity flags, unknown investigation items.

**Dependency profile:** Profile level, score, individual D1–D4 answers.

**Pattern interpretation:** Matched patterns from scoring interpretation engine with interpretation text and action recommendations.

**Primary actions:**
- Generate Roadmap
- Save Assessment (localStorage)
- Print/Export
- Edit Scores (returns to scoring)

**Export bar:**
- Export JSON (downloads `navigator_[name]_[date].json`)
- Copy Shareable Link (base64-encodes state to URL)
- Import Assessment (file picker for JSON import)

---

### G.2 Roadmap Assembly Logic

```
Archetype + Use Case + Risk Tier + Dependency Profile + Pillar Scores + Mechanism Profile = Roadmap
```

---

### G.3 Roadmap Sections (12)

**1. Executive Summary**
Template:
```
"This assessment evaluated [TOOL_NAME] ([USE_CASE]) at [INSTITUTION_NAME] on [DATE].
The tool was classified as Risk Tier [TIER] with a [DEPENDENCY_PROFILE] dependency profile,
and evaluated by a [ARCHETYPE] institution. Total governance score: [SCORE]/[POSSIBLE]
across [SCORED_COUNT] pillars. Dependency score: [DEPENDENCY_SCORE]/12.
[NO_GO_COUNT] no-go criteria triggered. Recommendation: [RECOMMENDATION]."
```

**2. No-Go Conditions (if any)**
Red banners with remediation for each triggered no-go.

**3. Before You Deploy — Pre-deployment Requirements**
- **Tier 1 (5 items):** Designate person, basic vendor checklist, add to AI inventory, post AI disclosure, confirm no training on student data.
- **Tier 2 (8 items):** All Tier 1 + score all 9 pillars (P2/P6 ≥ 2), faculty config/override, escalation path, adjunct orientation (≤ 30 min).
- **Tier 3 (11 items):** All Tier 2 + full governance committee review, pre-deployment bias audit, human-in-the-loop documented/tested, appeals process published, automation bias training, student notification and opt-out.

**4. Pillar-Specific Remediation**
Actions for any pillar scoring 1:
- P1: Articulate educational purpose in one sentence.
- P2: Conduct disaggregated impact analysis. Request vendor demographic data.
- P3: Build human override into workflow. Named human for every consequential decision.
- P4: Faculty per-course config. 30-min adjunct orientation. Student opt-out with human alternative.
- P5: Articulate worst-case harm. Define autonomy limits. Automation bias training.
- P6: FERPA agreement signed. Contractual training prohibition. Complete data inventory.
- P7: AI disclosure at point of interaction. Contestability process. Public AI inventory.
- P8: Negotiate SLAs, data portability, update notice. Check FoundationCCC/CollegeBuys.
- P9: Designate person, create AI inventory, establish review cycle. Build governance first.

**5. Who's Involved (RACI)**
- **Lightweight (3 roles):** Tool oversight, student disclosure, vendor relationship. One person can wear multiple hats.
- **Building (6 roles):** Governance review, tool oversight, student disclosure, faculty onboarding, data governance, equity monitoring.
- **Scaling (6 roles):** Portfolio governance, human oversight, bias audit, student voice, cross-tool coordination, system coordination. Standing committee.

**6. 90-Day Metrics**
- **Tier 1 (4):** Usage data, student satisfaction (30/90 day surveys), escalation tracking, accessibility barriers.
- **Tier 2 (8):** All Tier 1 + disaggregated usage by demographics, faculty config uptake, override rate, error rates by demographics.
- **Tier 3 (11):** All Tier 2 + appeals volume/resolution, human override quality review, bias audit findings, automation bias indicators (declining override rate), student opt-out rate.

**7. Review Cadence**
- Tier 1: Every 2 years (or trigger-based)
- Tier 2: Annual + quarterly check-ins
- Tier 3: Annual comprehensive + quarterly monitoring + monthly governance meetings

**8. Dependency Governance** (Medium/High only; omitted for Low)
Insertion point: between Review Cadence and Decision Rules.
- **Medium:** DEP-M1 (configuration review), DEP-M2 (6-month capability check), DEP-M3 (alternative maintenance)
- **High:** DEP-H1 (dependency acknowledgment), DEP-H2 (vendor lock-in assessment), DEP-H3 (12-month sunset evaluation), DEP-H4 (capability impact tracking, Tier 3 only)

**9. Escalation Triggers (10)**
- Student complaint volume exceeds baseline
- Tool accuracy below SLA
- Vendor changes data practices/features without notice
- Disaggregated outcomes show differential impact
- Override rate > 30% (AI quality issues)
- Faculty report tool burdensome
- Student appeal volume exceeds threshold
- Bias audit reveals systematic disparate impact
- Human override rate drops below 5% (possible automation bias)
- Vendor acquired or changes ownership

**10. Decision Rules**
- **Pause when:** 3+ complaints in 30 days; P2/P6 conditions deteriorate; unresolved equity concern; vendor misses SLA; bias audit remediation needed; portfolio tool conflict.
- **Investigate when:** Model update announced; differential outcomes emerge; override rate drops; new demographic disparity found; cross-tool flagging patterns.
- **Stop when:** Any no-go becomes true post-deployment; unremediated discriminatory bias; vendor fails commitments; accreditation concern; system-level policy conflict.

**11. Toolkit References**
- **Tier 1 (3):** AI Inventory Template, AI Tool Evaluation Checklist, Student AI Rights Notice
- **Tier 2 (6):** All Tier 1 + Faculty AI Training Outline, Vendor Contract AI Addendum, High-Impact AI Assessment Protocol
- **Tier 3 (11):** All Tier 2 + AI Governance Committee Charter, AI Incident Response Protocol, Annual AI Governance Report, Student AI Documentation Form, Student Capability Assessment Protocol

**12. HUMANS Alignment (California only)**
Maps each HUMANS letter to Navigator pillars. Notes the HUMANS gap (P9 / Criterion 4).

**13. Next Steps Checklist**
```
Based on your assessment, here are your immediate next steps:
[ ] Address any no-go conditions before proceeding
[ ] Complete pre-deployment governance requirements for your risk tier
[ ] Assign roles per the RACI structure
[ ] Set up 90-day measurement baseline
[ ] Schedule first review per your cadence
[ ] Download relevant templates from the Governance Toolkit
[ ] Share this assessment with your governance body
```

---

### G.4 Roadmap Scaling by Archetype × Tier

| | Tier 1 (Lower) | Tier 2 (Medium) | Tier 3 (High) |
|--|----------------|-----------------|----------------|
| **Lightweight** | ~2 pages. 5 pre-deploy items. 3-role RACI. 4 metrics. | ~3 pages. Full pre-deploy. 3-role RACI. Extended metrics. | ~4 pages. Full pre-deploy. All sections. Simplified RACI. |
| **Building** | ~3 pages. 6-role RACI. Standard metrics. | ~4 pages. Full governance. 6-role RACI. Disaggregated metrics. | ~5 pages. Full governance. Bias audit. All sections. |
| **Scaling** | ~3 pages. 6-role RACI. Portfolio context. | ~5 pages. Standing committee. Cross-tool coordination. | ~6 pages. Full portfolio governance. External audit. System coordination. |

---

### G.5 Print/Export Format

**Print CSS:** Hides nav, buttons, interactive elements. Shows profile + roadmap views. Proper page breaks. Clean layout.
**Header:** Tool name, use case, risk tier, institution name, assessment date.
**Footer:** "Generated by the AI Governance Navigator — AQL Labs / FutureObjects Research / College Futures Foundation"

---

### G.6 AI Panel on Output Screens

**AI Panel State:** Collapsed — same 48px rail with "AI not available — institutional judgment."

---

## Section H: AI Simulation Engine

The spec for simulated AI behavior. Pre-scripted responses with keyword matching that feel real without an actual LLM connection.

---

### H.1 Response Bank Data Structure

```json
{
  "ai_simulation": {
    "tools": {
      "mainstay": {
        "display_name": "Mainstay",
        "keywords": ["mainstay", "behavioral messaging", "nudge"],
        "suggested_use_case": "SS-06",
        "suggested_use_case_reason": "Mainstay uses behavioral messaging with personalized nudges based on student enrollment data. While marketed as a 'chatbot,' its primary mechanism is proactive outreach, not reactive Q&A. This is closer to SS-06 than SS-04.",
        "screening_prefills": {
          "q1": { "value": "yes_student_records", "confidence": "high" },
          "q2": { "value": "yes_opt_out", "confidence": "high" },
          "q3": { "value": null, "confidence": null, "caveat": "I don't have reliable information about whether Mainstay's messages are template-based or AI-generated in your specific configuration." },
          "q4": { "value": "aggregated_anonymized", "confidence": "medium", "caveat": "Verify the specific language in your contract." }
        },
        "mechanism_analysis": {
          "context_note": "This tool uses student enrollment data and behavioral signals to personalize outgoing messages. It groups students into segments based on enrollment status, milestone proximity, and past response patterns. Messages are sent automatically based on configured triggers.",
          "md01_suggestion": "c",
          "md01_reason": "Mainstay uses enrollment data and milestone proximity to personalize messages.",
          "md02_suggestion": null,
          "md03_suggestion": null
        },
        "conversations": {
          "use_case": [
            {
              "triggers": ["mainstay", "chatbot", "engagement", "retention"],
              "response": "Mainstay markets itself as a 'chatbot,' but its core mechanism is proactive behavioral messaging, not reactive Q&A. It sends personalized nudges to students based on enrollment data, deadlines, and behavioral signals.\n\nIn the Navigator, that's **SS-06: Nudge Campaigns / Behavioral Messaging** (Tier 2), not SS-04: Student-Facing Chatbot (Tier 1). The distinction matters because nudge systems access student data to *initiate* contact, while FAQ chatbots only *respond* to student queries.",
              "caveat": "This classification is based on Mainstay's published product description. Verify with your vendor contact that this matches the specific product configuration they're offering you."
            },
            {
              "triggers": ["screening", "watch for", "look for"],
              "response": "For SS-06 specifically, the screening will ask about:\n\n- What student data triggers the nudges\n- Whether students can opt out\n- Whether message content is AI-generated or template-based\n- Whether the system escalates to human staff\n\nI can help with factual answers about Mainstay's capabilities when you reach that step. The screening questions will appear next.",
              "caveat": null
            }
          ],
          "screening": [
            {
              "triggers": ["pre-fill", "prefill", "suggest", "answers"],
              "response": "I've pre-filled answers I'm confident about based on Mainstay's published information. Look for the teal-highlighted options.\n\nI left **Question 3** blank — I don't have reliable information about whether Mainstay's messages are template-based or AI-generated in your specific configuration. This is worth asking your vendor contact directly.",
              "caveat": null
            },
            {
              "triggers": ["data training", "training data", "question 4", "data practices"],
              "response": "Mainstay's published data practices state they use aggregated, anonymized interaction data to improve their models, but do not train on individual student data. Their standard contract includes this provision.\n\nI suggested 'Aggregated/anonymized only' but this is a **PAUSE**-level answer for SS-06. The screening will flag it. You should verify the specific language in your contract — 'aggregated' can mean different things.",
              "caveat": "If your institution requires zero data use for model training, ask Mainstay whether they offer a contractual opt-out from aggregated training."
            }
          ],
          "mechanism": [
            {
              "triggers": ["c or d", "difference", "option c", "option d", "profile", "behavioral"],
              "response": "The distinction is between **static profile data** (Option C) and **learned behavior patterns** (Option D).\n\n**Option C** means the tool personalizes based on data that already exists in your SIS: major, enrollment status, how close they are to a deadline. The student's profile drives what they see.\n\n**Option D** means the tool *watches what students do over time* — which messages they open, which links they click, how quickly they respond — and adjusts future messages based on those behavioral patterns.\n\nMainstay's base product uses enrollment data and configured triggers (Option C). However, their 'Behavioral Intelligence' add-on analyzes response patterns to optimize message timing and content, which would be Option D.",
              "caveat": "Ask your vendor: are we getting the base product or the Behavioral Intelligence tier? The governance requirements are different."
            }
          ]
        }
      },
      "eab_navigate": {
        "display_name": "EAB Navigate",
        "keywords": ["eab", "navigate", "eab navigate", "early alert", "predictive"],
        "suggested_use_case": "SS-02",
        "suggested_use_case_reason": "EAB Navigate is a student success management platform that uses predictive analytics to identify at-risk students and coordinate interventions. This is SS-02: Early Alert / Student Risk System (Tier 3, High Risk).",
        "screening_prefills": {
          "q1": { "value": "yes_flags_at_risk", "confidence": "high" },
          "q2": { "value": "no", "confidence": "medium", "caveat": "EAB Navigate's standard configuration does not expose risk scores to students. Verify whether your implementation includes student-facing dashboards." },
          "q3": { "value": "planned", "confidence": "medium", "caveat": "EAB has published aggregate accuracy data but institution-specific disaggregated false positive analysis typically requires local implementation." },
          "q4": { "value": "defined", "confidence": "high" },
          "q5": { "value": null, "confidence": null, "caveat": "Counseling capacity is an institutional question — I can't assess your staffing levels." }
        },
        "mechanism_analysis": {
          "context_note": "EAB Navigate uses predictive models trained on historical student data to assign risk scores. It categorizes students into risk tiers, triggers automated alerts to advisors, and can initiate outreach campaigns based on behavioral patterns and enrollment milestones.",
          "md01_suggestion": "d",
          "md01_reason": "EAB Navigate uses behavioral pattern-matching — it observes student behavior over time (login patterns, course engagement, grade trends) and adjusts risk predictions based on inferred patterns.",
          "md02_suggestion": "c",
          "md02_reason": "EAB Navigate assigns predictive risk scores to individual students based on historical data models.",
          "md03_suggestion": "c"
        },
        "conversations": {
          "use_case": [
            {
              "triggers": ["eab", "navigate", "early alert", "risk", "predictive"],
              "response": "EAB Navigate is a student success management platform centered on predictive analytics. It assigns risk scores to students based on historical data patterns, coordinates advisor interventions, and can trigger automated outreach.\n\nIn the Navigator, that's **SS-02: Early Alert / Student Risk System** (Tier 3, High Risk). This is the highest governance tier because the tool makes or influences decisions about student interventions based on algorithmic risk assessment.",
              "caveat": "EAB Navigate's feature set varies by contract tier. Verify which modules your institution is licensing."
            }
          ],
          "screening": [
            {
              "triggers": ["prefill", "suggest", "screening"],
              "response": "I've pre-filled what I can based on EAB Navigate's published capabilities. Key gaps:\n\n- **Question 2** (student visibility): I marked 'No' because the standard config doesn't show risk scores to students, but your implementation may differ.\n- **Question 5** (counseling capacity): This is about your institution, not the tool. I can't assess your staffing.\n\nFor a Tier 3 tool, every screening answer matters. Verify each one.",
              "caveat": null
            }
          ],
          "mechanism": [
            {
              "triggers": ["mechanism", "how does it work", "pattern", "risk score"],
              "response": "EAB Navigate hits multiple mechanism flags:\n\n- **MD-01 (D):** Behavioral pattern-matching — it observes student behavior over time and adjusts predictions.\n- **MD-02 (C):** Predictive scoring — it assigns risk scores to individual students.\n- **MD-03:** Depends on your configuration. The platform can send automated alerts (C) or initiate outreach campaigns (D).\n\nSince SS-02 is already Tier 3, mechanism detection won't escalate the tier further. But the forced pillar minimums (P2 ≥ 2, P5 ≥ 2, P7 ≥ 2) will apply, and the equity screening flag will trigger additional review during P2 scoring.",
              "caveat": "The mechanism profile for EAB Navigate is complex. Document each mechanism answer carefully — they'll drive specific governance requirements in your roadmap."
            }
          ]
        }
      },
      "nectir": {
        "display_name": "Nectir",
        "keywords": ["nectir", "tutoring", "tutor", "course assistant"],
        "suggested_use_case": "SS-05",
        "suggested_use_case_reason": "Nectir is an AI tutoring assistant designed for integration with specific courses. Faculty configure it per-course, and it uses a Socratic approach to build student capability rather than deliver answers. This is SS-05: AI Course Tutoring Assistant (Tier 2).",
        "screening_prefills": {
          "q1": { "value": "yes_faculty_config", "confidence": "high" },
          "q2": { "value": "acknowledges_limitation", "confidence": "high" },
          "q3": { "value": "skill_building", "confidence": "high" },
          "q4": { "value": null, "confidence": null, "caveat": "Accessibility compliance varies by implementation. Verify WCAG 2.1 AA status with vendor." },
          "q5": { "value": "no_contractual", "confidence": "medium", "caveat": "Verify the specific data training terms in your contract." }
        },
        "mechanism_analysis": {
          "context_note": "Nectir provides AI-powered tutoring within specific courses. Faculty configure the tool's behavior, knowledge boundaries, and pedagogical approach per course. The tool uses a Socratic method that guides students toward understanding rather than providing direct answers.",
          "md01_suggestion": "b",
          "md01_reason": "Nectir responds to what students ask within faculty-configured course boundaries. Personalization is student-driven, not profile-based.",
          "md02_suggestion": "a",
          "md03_suggestion": "a"
        },
        "conversations": {
          "use_case": [
            {
              "triggers": ["nectir", "tutoring", "tutor", "course"],
              "response": "Nectir is an AI tutoring assistant designed for course-level integration. Faculty configure its knowledge boundaries and pedagogical approach per course.\n\nIn the Navigator, that's **SS-05: AI Course Tutoring Assistant** (Tier 2, Medium Risk). The medium risk comes from its role in the instructional core and the need for faculty configuration to prevent hallucination and ensure pedagogical alignment.",
              "caveat": "Nectir's features may vary by version. Confirm which capabilities your institution is evaluating."
            }
          ],
          "screening": [
            {
              "triggers": ["prefill", "screening", "suggest"],
              "response": "Nectir pre-fills well because its design philosophy is well-documented:\n\n- Faculty configuration: Yes (core feature)\n- Hallucination handling: Acknowledges limitations (documented approach)\n- Capability building: Socratic method (documented)\n\nI left **Question 4** (accessibility) blank — verify WCAG 2.1 AA compliance directly.\n\nThis is a relatively clean screening profile for a Tier 2 tool.",
              "caveat": null
            }
          ],
          "mechanism": [
            {
              "triggers": ["mechanism", "how", "personalize"],
              "response": "Nectir has a clean mechanism profile:\n\n- **MD-01 (B):** Student-configured — students drive the interaction within faculty-set boundaries.\n- **MD-02 (A):** No classification — it doesn't score or categorize students.\n- **MD-03 (A):** No autonomous action — it only responds to student-initiated queries.\n\nNo mechanism escalation expected. Tier stays at 2. No forced pillar minimums from mechanisms.",
              "caveat": null
            }
          ]
        }
      }
    },
    "generic_responses": {
      "use_case": [
        {
          "triggers": ["what", "which", "category", "use case"],
          "response": "I can help classify your tool. The Navigator has 10 Student Services use cases, ranging from Tier 1 (Lower Risk, like chatbots) to Tier 3 (High Risk, like early alert systems).\n\nTell me the tool name or describe what it does, and I'll suggest which category fits best.",
          "caveat": null
        },
        {
          "triggers": ["help", "don't know", "unsure"],
          "response": "If you're not sure which category fits, describe what the tool does in plain language:\n- Who uses it? (students, advisors, staff)\n- What does it do? (answer questions, send messages, make recommendations)\n- What student data does it access?\n\nI'll match it to the closest Navigator use case.",
          "caveat": null
        }
      ],
      "screening": [
        {
          "triggers": ["help", "what does this mean", "explain"],
          "response": "Each screening question checks whether basic governance conditions are in place for this use case. Your answers determine whether the tool gets a GO (proceed to evaluation), PAUSE (concerns to address), or NO-GO (hard stop until resolved).\n\nAsk me about any specific question and I'll explain what it's looking for.",
          "caveat": null
        }
      ],
      "mechanism": [
        {
          "triggers": ["help", "explain", "what", "how"],
          "response": "These three questions detect hidden risk in *how* your tool works — not what category it belongs to. A chatbot with behavioral profiling has different governance requirements than one without.\n\nIf you're unsure about any option, selecting 'Unknown' is the honest answer. The Navigator treats unknowns seriously — they trigger investigation requirements, not penalties.",
          "caveat": null
        }
      ],
      "unknown_tool": [
        {
          "triggers": [],
          "response": "I don't have specific information about this tool in my database. That's okay — the Navigator works for any Student Services AI tool.\n\nYou can:\n1. Select a use case category that best matches what the tool does\n2. Use SS-XX (Custom/Other) if none of the 10 categories fit\n3. Ask me to help classify it based on what you know about the tool",
          "caveat": "For tools I don't have in my database, I can't pre-fill screening answers or provide mechanism analysis. You'll need to answer based on vendor documentation and your own knowledge."
        }
      ]
    },
    "system_messages": {
      "welcome": "I'm here to help you identify and understand the AI tool you're evaluating. Describe the tool or enter its name, and I'll help classify it.",
      "screening_intro": "I've pre-filled answers I'm confident about. Look for the teal highlights. You can accept, override, or ask me about any question.",
      "mechanism_intro": "These questions detect how the tool works technically. I've provided context based on what I know about this tool.",
      "panel_collapsed": "AI not available — institutional judgment",
      "tool_identified": "I've identified your tool and suggested a use case category. You can accept the suggestion or choose a different category."
    }
  }
}
```

---

### H.2 Keyword Matching Algorithm

```
1. User types message in chat input
2. Normalize input: lowercase, trim whitespace
3. Extract keywords:
   a. Check for tool names (exact match in tools bank)
   b. Check for question topics ("how", "what", "why" patterns)
   c. Check for screen-specific terms
4. Determine context: current screen (use_case, screening, mechanism)
5. Resolution order:
   a. Is current tool in the tools bank? → use tool-specific conversations
   b. Match keywords against trigger arrays for current screen context
   c. If match found → return first matching response
   d. If no match → return generic response for current screen
   e. If no screen match → return unknown_tool fallback
6. Interpolate tool name: replace "{tool_name}" with current tool's display_name
7. Apply typing delay (see H.4)
8. Display response with source label and optional caveat
```

**Trigger matching:** Check if any trigger keyword appears as a substring in the normalized input. First match wins.

---

### H.3 Pre-fill Logic

When a known tool is identified:

1. Look up `tools[tool_key].screening_prefills`
2. For each question in the current use case's screening:
   - If prefill value is non-null → apply pre-fill styling (teal card, tag, suggested option)
   - If prefill value is null → leave question unstyled (no AI suggestion)
3. Prefill confidence levels:
   - `high`: AI is confident in this answer
   - `medium`: AI suggests this answer but caveats apply
   - `null`: AI has no reliable information

For mechanism detection:
1. Look up `tools[tool_key].mechanism_analysis`
2. Display `context_note` as inline AI Context Note
3. For each MD question:
   - If suggestion is non-null → highlight that option with teal border and annotation text
   - If suggestion is null → no highlighting

---

### H.4 Typing Animation

- **Delay:** Random between 800ms and 1500ms before response appears
- **Animation:** Three-dot "thinking" indicator (pulsing dots) in the chat panel during delay
- **Implementation:** `setTimeout` with random duration: `800 + Math.random() * 700`
- The typing indicator appears as an AI message bubble with animated dots

---

### H.5 Context Awareness

**Chat header updates per screen:**
| Screen | Header Title | Header Context |
|--------|-------------|----------------|
| Use Case Selection | Navigator AI | Tool Identification |
| Screening | Navigator AI | Screening — SS-{XX} |
| Mechanism Detection | Navigator AI | Mechanism — SS-{XX} |
| Pillar Scoring | (collapsed) | (collapsed rail) |
| All others | (hidden or collapsed) | — |

**Conversation persistence:** Messages persist across screens. When user navigates from Use Case to Screening, prior chat messages remain visible.

**Chat input placeholder variation:**
- Use Case Selection: "Ask about this tool..."
- Screening: "Ask about screening..."
- Mechanism Detection: "Ask about mechanisms..."

---

### H.6 Tool Profiles Summary

| Tool | Display Name | Use Case | Tier | Key Mechanism | Complete Flow |
|------|-------------|----------|------|---------------|---------------|
| mainstay | Mainstay | SS-06 | 2 | Profile-based personalization (MD-01 C) | Yes — all AI screens |
| eab_navigate | EAB Navigate | SS-02 | 3 | Behavioral pattern-matching + predictive scoring | Yes — complex mechanism |
| nectir | Nectir | SS-05 | 2 | Clean profile (no escalation) | Yes — clean flow |
| (unknown) | (generic) | (any) | (any) | N/A | Fallback responses |

---

### H.7 Chat Panel UI States

| State | Width | When | Contents |
|-------|-------|------|----------|
| **Visible (with messages)** | 340px | Use Case, Screening, Mechanism (after interaction) | Header + messages + input |
| **Visible (welcome)** | 340px | Use Case, Screening, Mechanism (before interaction) | Header + welcome message + input |
| **Collapsed (rail)** | 48px | Pillar Scoring, No-Go Check, Governance Profile, Roadmap | Gray dot + vertical "AI not available" text |
| **Hidden** | 0px | Landing, About/Methodology | Panel not rendered |

---

### H.8 Chat Message Styling

**User messages:**
- Blue background (`--blue` / `#0066cc`)
- White text
- Right-aligned
- Max-width: 92%
- Bottom-right radius: 3px (sharp corner)

**AI messages:**
- White background
- Gray-700 text
- Left-aligned
- 1px solid border
- Bottom-left radius: 3px (sharp corner)
- Source label: "Navigator AI" (teal, 8pt, font-weight 600)
- Optional caveat section: separated by thin gray top border, italic, 8pt, gray-400

---

## Section I: Navigation Map

---

### I.1 All Views/Screens

| # | View ID | Screen | AI Panel | Hash |
|---|---------|--------|----------|------|
| 1 | `landing` | Landing / Hero | Hidden | `#landing` |
| 2 | `routing` | Step 0: Routing Questionnaire | Visible | `#routing` |
| 3 | `routing-results` | Step 0: Results / Recommendations | Visible | `#routing-results` |
| 4 | `archetype` | Archetype Selector (Quick Path) | Hidden | `#archetype` |
| 5 | `use-case` | Use Case Selection | Visible | `#use-case` |
| 6 | `screening` | Screening Questions | Visible | `#screening/{use-case-id}` |
| 7 | `screening-result` | Screening Result (GO/PAUSE/NO-GO) | Visible | `#screening-result` |
| 8 | `dependency` | Dependency Profile | Visible (hybrid) | `#dependency/{use-case-id}` |
| 9 | `mechanism` | Mechanism Detection | Visible | `#mechanism/{use-case-id}` |
| 10 | `mechanism-result` | Mechanism Result (Tier Adjustment) | Visible | `#mechanism-result` |
| 11 | `risk-tier` | Risk Tier Confirmation | Collapsed | `#risk-tier` |
| 12 | `scoring` | Pillar Scoring | Collapsed | `#scoring/{pillar-id}` |
| 13 | `nogo-check` | No-Go Checklist | Collapsed | `#nogo-check` |
| 14 | `profile` | Governance Profile | Collapsed | `#profile` |
| 15 | `roadmap` | Roadmap | Collapsed | `#roadmap` |
| 16 | `about` | About / Methodology | Hidden | `#about` |

---

### I.2 Three Entry Points

```
ROUTING PATH:   Landing → Step 0 (8 Qs) → Recommendations → Use Case → ...
QUICK PATH:     Landing → Archetype Selector → Use Case → ...
FULL PATH:      Landing → Use Case Selector → ...

                              ↓ (all paths merge here)

                 Screening → Screening Result → Dependency Profile →
                 Mechanism Detection → Mechanism Result →
                 Risk Tier → Pillar Scoring → No-Go Check →
                 Governance Profile → Roadmap
```

**Landing CTAs:**
1. "Help Me Choose" → Routing Path (Step 0)
2. "I Know What I Need" / "Start Your Assessment" → Full Path (Use Case Selector)
3. "I Know My Institution" → Quick Path (Archetype Selector)

---

### I.3 URL Hash Navigation

```
#landing
#routing
#routing-results
#archetype
#use-case
#screening/{use-case-id}
#screening-result
#dependency/{use-case-id}
#mechanism/{use-case-id}
#mechanism-result
#risk-tier
#scoring/{pillar-id}     (e.g., #scoring/P1, #scoring/P2, ...)
#nogo-check
#profile
#roadmap
#about
```

**Shareable state URL:**
`#profile?state={base64_encoded_state}`

Capped at 8,000 chars; falls back to JSON export if too large. On init, checks for `state` URL param, decodes and loads assessment, navigates to profile, then cleans URL with `replaceState`.

---

### I.4 Back/Edit Flow

| Change | Effect |
|--------|--------|
| Use case | Risk tier resets, screening questions change, dependency cleared, mechanism cleared, pillar scores cleared |
| Risk tier (override) | Mandatory/recommended pillar display updates, existing scores preserved, dependency preserved |
| Archetype | Display complexity adjusts, scores preserved, roadmap regenerates |
| Dependency answer | Score recalculates, profile may change, roadmap dependency section regenerates, pillar scores preserved |
| Mechanism answer | Escalation recalculates, tier may adjust, forced pillars update, pillar scores preserved |
| Pillar score | Summary updates, patterns recalculate, roadmap regenerates |
| No-go answer | Alerts update, roadmap regenerates |
| California toggle | HUMANS mapping shows/hides across scoring and roadmap |

---

### I.5 State Management Schema

```javascript
var state = {
  // Entry context
  entryPath: null,           // 'routing' | 'full' | 'quick'

  // Routing (Step 0)
  routingAnswers: {},         // { Q1: [...], Q2: '...', ... Q8: '...' }
  routingResults: null,       // { recommended: [], consider_later: [], profile: {} }
  currentRoutingQ: 0,         // Progress index

  // Institution
  institutionName: '',
  archetype: null,            // 'lightweight' | 'building' | 'scaling'
  isCalifornia: false,

  // Tool & Use Case
  toolName: '',
  toolKey: null,              // Key into ai_simulation.tools (e.g., 'mainstay')
  useCase: null,              // { id: 'SS-06', name: '...', defaultRiskTier: 2 }
  customDescription: '',      // Only for SS-XX
  customWorstCase: '',        // Only for SS-XX

  // Screening
  screeningAnswers: {},       // { q1: 'value', q2: 'value', ... }
  screeningPrefills: {},      // { q1: { value, confirmed: bool }, ... }
  screeningResult: null,      // 'go' | 'pause' | 'nogo'
  screeningFlags: [],         // Array of flagged concerns

  // Dependency Profile
  dependencyProfile: {
    answers: { D1: null, D2: null, D3: null, D4: null },
    totalScore: null,         // 4-12
    profile: null             // 'low' | 'medium' | 'high'
  },

  // Mechanism Detection
  mechanismProfile: {
    answers: { MD01: null, MD02: null, MD03: null },
    tierAdjustment: 0,        // Total escalation amount
    adjustedTier: null,       // min(3, defaultTier + tierAdjustment)
    forcedPillars: {},         // { P2: 2, P5: 2, P7: 2, ... }
    equityFlag: false,
    unknownFlags: [],          // ['MD-01', 'MD-02', ...]
    noGoFlag: false            // True if MD-03 E selected
  },

  // Risk Tier
  riskTier: null,             // 1 | 2 | 3 (final, after mechanism + override)
  riskTierOverride: false,
  riskTierOverrideReason: '',

  // Pillar Scoring
  pillarScores: {
    P1: null, P2: null, P3: null, P4: null, P5: null,
    P6: null, P7: null, P8: null, P9: null
  },
  pillarNotes: {
    P1: '', P2: '', P3: '', P4: '', P5: '',
    P6: '', P7: '', P8: '', P9: ''
  },
  currentPillar: 0,           // Index into pillarOrder
  pillarOrder: [],             // Ordered pillar IDs for scoring

  // No-Go
  noGoFlags: {
    NG01: false, NG02: false, NG03: false, NG04: false,
    NG05: false, NG06: false, NG07: false, NG08: false
  },
  noGoAutoFlags: [],           // Score-derived auto-flags

  // AI Simulation
  chatMessages: [],            // Array of { role: 'user'|'ai', text: '', caveat: '', screen: '' }

  // Computed (derived at render time)
  totalScore: 0,
  scoredPillars: 0,
  patterns: [],

  // Meta
  assessmentDate: '',
  timestamp: null              // ISO string for save key
};
```

---

### I.6 localStorage Save/Restore

**Key format:** `nav3_{toolName}_{timestamp}`

```javascript
// Save
function saveAssessment() {
  state.timestamp = new Date().toISOString();
  var key = 'nav3_' + state.toolName.replace(/\s+/g, '_') + '_' + Date.now();
  localStorage.setItem(key, JSON.stringify(state));
}

// Load all saved assessments
function loadAssessments() {
  var assessments = [];
  for (var i = 0; i < localStorage.length; i++) {
    var key = localStorage.key(i);
    if (key.indexOf('nav3_') === 0) {
      try { assessments.push(JSON.parse(localStorage.getItem(key))); } catch(e) {}
    }
  }
  return assessments;
}
```

**Preferences persistence:**
```json
{
  "nav3_prefs": {
    "isCalifornia": true,
    "archetype": "building",
    "institutionName": "Merced College"
  }
}
```

---

### I.7 Three Persistence Mechanisms

1. **localStorage:** Quick save/load within same browser. Key prefix `nav3_`.
2. **JSON export/import:** Serializes full state to downloadable `.json` file. Import validates presence of `useCase` or `pillarScores` before merging.
3. **Shareable URL:** Base64-encodes state into `?state=` URL parameter (capped at 8,000 chars; falls back to export). On init, checks for `state` param, decodes, loads, navigates to profile, cleans URL with `replaceState`.

---

### I.8 Mobile Responsive Behavior

**Breakpoint:** 768px

**Below 768px:**
- Chat panel becomes overlay (full-width slide-in from right) with close button
- Toggle button appears in main content area to open chat
- All grids collapse to single column
- Score buttons stack vertically
- Typography scale drops ~40%
- Section padding: 2.4rem (from 6rem)
- Assessment works one-question-per-screen on mobile

**Chat panel on mobile:**
- Positioned as fixed overlay when open
- 100% width
- Close button (X) in header
- Same message area and input as desktop

---

### I.9 Design Tokens (v3.1)

```css
/* Font — DM Sans for all text in v3.1 (fresh build, not locked to v2 stack) */
--font: 'DM Sans', sans-serif;

/* Colors — inherited from v2 + wireframe additions */
--signal: #0891B2;           /* Primary / AI accent */
--signal-dark: #0E7490;
--signal-deep: #155E75;
--signal-light: #E0F7FA;
--signal-10: rgba(8,145,178,0.10);

--accent: #D97706;           /* Orange accent */
--accent-light: #FEF3C7;

--dark: #0C0C0C;             /* Dark hero */
--dark-surface: #1A1A1A;
--dark-border: #2A2A2A;

--ink: #151515;
--ink-soft: #3A3A3A;
--ink-muted: #6B6B6B;

--surface: #F5F5F3;
--white: #FFFFFF;

/* AI-specific colors (from wireframe) */
--ai-accent: #0891B2;        /* Same as signal — keeps cohesive */
--ai-bg: #f0fafb;            /* AI element backgrounds */
--ai-border: #b2e0e8;        /* AI element borders */

/* Chat panel */
--panel-bg: #f7f8f9;
--panel-border: #dde1e6;
--blue: #0066cc;             /* User messages */

/* Score/tier colors */
--risk-high: #c00;
--risk-high-bg: #f8d7da;
--risk-medium: #856404;
--risk-medium-bg: #fff3cd;
--risk-lower: #28a745;
--risk-lower-bg: #d4edda;

/* Pillar colors */
--p1: #0066cc; --p2: #28a745; --p3: #6f42c1; --p4: #fd7e14;
--p5: #dc3545; --p6: #17a2b8; --p7: #e83e8c; --p8: #6610f2;
--p9: #795548;
```

---

### I.10 Accessibility Requirements

- Keyboard navigable: All interactive elements focusable, logical tab order
- ARIA labels on interactive elements (buttons, inputs, score selections)
- Color contrast: WCAG 2.1 AA on critical elements
- Screen reader compatible: Semantic HTML, descriptive labels
- Score buttons: Labeled with both number and description for screen readers
- Chat panel: ARIA live region for new messages

---

### I.11 About / Methodology Screen

**Content:**
- Framework description: Three-layer model (Criteria → Pillars → HUMANS)
- Research base: 224+ frameworks scanned, 12 global domains, 62 first cut, 14 deeply analyzed
- Gap analysis: Only 2 of 224+ directly address community colleges
- 23 source citations
- Built by: AQL Labs / FutureObjects Research, commissioned by College Futures Foundation
- AI Mode disclosure: Framework operates without AI; AI augmentation layer is optional

---

## Appendix: Decision Log

### Resolved Decisions

1. **Use case list:** CONTEXT.md v3.1 list takes priority. SS-06 is Nudge Campaigns / Behavioral Messaging (NEW). Registration & Enrollment (was SS-10 in concept) has been dropped.

2. **Font:** DM Sans throughout v3.1 (from CONTEXT.md). Replaces v2's Plus Jakarta Sans + Inter stack.

3. **SS-06 screening questions:** Sourced from wireframe (4 questions about PII access, opt-out, message generation, data training).

4. **SS-07 (AI Tutoring / Learning Support) screening questions:** Inherits from v2's SS-05 questions, as SS-07 is the general tutoring use case that was renumbered.

5. **AI panel chat panel width:** 340px (from wireframe CSS, overrides CONTEXT.md's 320px).

6. **Collapsed rail width:** 48px (from wireframe).

7. **Chat message styling:** Per wireframe — max-width 92%, user messages blue/right-aligned, AI messages white/left-aligned with source label and optional caveat.

### Open Questions

None identified. All source materials are consistent on core logic. Minor discrepancies between CONTEXT.md and concept on use case numbering have been resolved using CONTEXT.md as authoritative.

---

*End of specification. This document is consumed by the content agent (to produce navigator-v3-content.json) and the builder agent (to produce index.html).*
