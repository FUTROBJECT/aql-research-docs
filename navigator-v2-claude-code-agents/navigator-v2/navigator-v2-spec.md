# Navigator v2 — Complete Specification

**Spec Version:** 2.1
**Date:** February 22, 2026
**Produced by:** Navigator Specification Agent (Opus 4.6)

**Source files ingested:**
1. `navigator-v2/CONTEXT.md` — shared project context, framework architecture, voice guidelines
2. `navigator/index.html` — v1 Navigator prototype (full HTML/CSS/JS, data model: QUESTIONS, GAPS, PILLARS, TEMPLATES, ARCHETYPES, ROADMAP)
3. `student-services-vendor-scorecard.html` — all 9 pillars with questions, scoring rubrics, no-go criteria, score patterns, annual review
4. `cc-framework-architecture.md` — full governance structure, 9 gap provisions, risk classification, vendor management, implementation roadmap
5. `aql-point-of-view.html` — four commitments, six core principles, gap analysis (27 frameworks → 9 CC gaps)
6. `cccco-ai-mobilization-framework.html` — HUMANS framework, three-tier governance, HUMANS ↔ Pillar alignment
7. `AI Framework Update - 2026-02-09.md` — CFF update: project direction, pillar confirmation, scope decisions
8. `navigator/wireframe.jsx` — v1 wireframe (referenced, not central to v2)

9. `navigator-v2/CONTEXT.md` dependency profile system — four questions, scoring bands, design principles, voice guidance

**Missing source:** Student Services Scope Document (.docx) — not found on filesystem. Content gap compensated from vendor scorecard and framework architecture document. Flagged where this creates ambiguity.
**Missing source:** `dependency-profile-screening-questions.md` — not found. Dependency profile fully specified from CONTEXT.md which contains the complete system.

---

# Section A: Data Model

## A.1 Four Ethical Criteria (Layer 1 — Portable)

These are the portable ethical criteria. They apply to any community college system, not just California. AI implementation is ethical when it meets all four. They are the lens through which the nine pillars are evaluated.

### Criterion 1: Equitable Student Outcomes
The AI use must serve a genuine educational purpose — not just an operational one. Then the question: does it serve that purpose equitably? AI that improves aggregate completion rates while widening equity gaps is not ethical implementation. AI that serves some career pathways while neglecting others is not ethical implementation. The question isn't "does this work?" but "does this work for the students community colleges exist to serve?"

**Drives:** P2 (Equity & Differential Impact). Shapes how all other pillars are applied.

### Criterion 2: Quality Data, Governed Responsibly
AI systems are only as good as the data underneath them. Institutions using AI without understanding their data — its gaps, its biases, its limitations — are building on sand. Ethical implementation requires data stewardship: knowing what you have, protecting what's sensitive, and being honest about what your data can and cannot support.

**Drives:** P6 (Data Stewardship & System Integrity).

### Criterion 3: Ethics & Safety Foundation
Human authority over high-stakes decisions. Transparency about when AI is used and how. Students and faculty have rights that don't disappear because a vendor promises efficiency. Safety is a precondition calibrated to the stakes — higher-stakes uses require more transparency and more paths for challenge.

**Drives:** P3 (Human Authority), P7 (Transparency & Contestability), P4 (Student and Faculty Agency).

### Criterion 4: Thoughtful, Multi-Year Approach
Governance that evolves as AI evolves, that learns from implementation, that builds institutional capacity over time. Speed through structure, not speed despite it. Institutions keep sovereignty over their AI decisions rather than giving it away through opaque contracts or platform lock-in.

**Drives:** P9 (Institutional Capacity & Continuous Governance).

**Cross-cutting pillars:** P1 (Purpose), P5 (Risk), P8 (Vendor Accountability) serve all four criteria — they are the operational pillars that execute the ethical criteria across every evaluation.

---

## A.2 Nine Operational Pillars (Layer 2 — Portable)

### P1: Purpose & Educational Legitimacy
- **Color:** `#0066cc`
- **Criteria Mapping:** All four (operational pillar)
- **HUMANS Mapping:** Not directly mapped (AQL-original)
- **Principle:** Every AI deployment must serve a genuine educational purpose and protect the meaning of credentials. AI use is justified by learning outcomes, not efficiency alone.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 1.1 | What specific student outcome or educational purpose does this tool serve? Can you name it? | A concrete answer tied to learning, completion, transfer, or career readiness — not "operational efficiency" or "innovation." If the team can't articulate the educational purpose in one sentence, the tool doesn't have one. |
| 1.2 | Does this tool align with the institution's mission and strategic plan? | Connection to stated institutional priorities. Not a solution looking for a problem. Maps to existing student success initiatives. |
| 1.3 | Where on the student journey does this solve a problem? (enrollment, persistence, completion, transfer, career placement) | Clear placement on the guided pathway. The tool addresses a known friction point, not a hypothetical one. Evidence that the problem exists at your institution. |
| 1.4 | Does the tool protect credential integrity? Could AI-generated outputs substitute for competency demonstration? | For tutoring/learning tools: students still demonstrate mastery. For advising: recommendations support informed student choice, not automated credential assembly. For CTE: licensure competency requirements preserved. |
| 1.5 | Has an industry advisory committee or CTE program review validated this tool's relevance? (for CTE-adjacent use cases) | Employer and industry input on whether the tool builds workforce-relevant skills. Alignment with career cluster competencies. |

**Scoring Rubric:**
- **3:** Clear educational purpose tied to student outcomes. Aligned with institutional mission. Mapped to specific student journey stage. Credential integrity preserved. Industry validation where relevant.
- **2:** Educational purpose stated but not evidence-backed. General alignment with mission. Journey placement reasonable but not validated locally. Credential impact not fully assessed.
- **1:** No clear educational purpose — tool is efficiency-driven or vendor-pushed. No connection to institutional priorities. Credential integrity risk unaddressed.

**Source:** IEAIED Req. 1, ATD Action Area 1, SACSCOC/C-RAC, Advance CTE (Perkins V).

---

### P2: Equity & Differential Impact
- **Color:** `#28a745`
- **Criteria Mapping:** Criterion 1 (primary)
- **HUMANS Mapping:** U (Universal Support), A (Algorithmic Discrimination)
- **Principle:** AI governance must center equity and account for differential impacts on diverse CC student populations. Drawing on the Kapor Center justice lens, this pillar ensures AI does not create new barriers or reinforce existing ones.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 2.1 | Has this tool been tested with student populations similar to ours? (Pell-eligible, first-gen, working adults, multilingual, students with disabilities) | Vendor can name specific institutions, student demographics, and outcomes. Not just "we serve higher ed." |
| 2.2 | Are error rates, recommendation accuracy, or response quality consistent across student demographics? | Vendor provides disaggregated performance data. If they can't, that's a red flag — they haven't measured it. |
| 2.3 | Has a differential impact analysis been conducted? Who might be harmed by this tool's errors or limitations? | Vendor or internal team has identified which populations face higher risk from tool errors. Not just "it works for everyone." Specific harm scenarios articulated. |
| 2.4 | Does the tool work effectively for multilingual students? In what languages? Is it real-time or pre-translated? | Actual language coverage and quality, not just "we support translation." Test with your student language mix. |
| 2.5 | Does the tool meet accessibility standards? (WCAG 2.1 AA, screen reader compatibility, keyboard navigation) | Documented accessibility compliance. VPAT or equivalent. Tested with assistive technology users. |
| 2.6 | What is the cost model for students? Are there paywalls, premium tiers, or features that require devices/bandwidth some students lack? | No paywall barriers. Works on mobile. Low bandwidth mode. No premium tier that creates a two-track system. |
| 2.7 | Does the tool serve all career pathways equitably, or is it optimized for specific programs? | CTE pathways covered, not just transfer/STEM. If advising-focused, it should know your full program catalog. |

**Scoring Rubric:**
- **3:** Disaggregated performance data for CC-like populations. Differential impact analysis conducted. Tested with multilingual, first-gen, Pell-eligible students. Accessible. No cost barriers. All pathways covered.
- **2:** Equity acknowledged as priority but data limited. Willing to conduct bias audit post-deployment. Accessibility documented. Cost model reasonable.
- **1:** No disaggregated data. No differential impact analysis. Equity not addressed in product design. Accessibility unclear. Cost barriers exist.

**Source:** Kapor Foundation (justice lens), NAIC (bias definition), OMB M-25-21 (civil rights safeguards), ASCCC (equity-centered AI policy for CCC).

---

### P3: Human Authority & Decision Accountability
- **Color:** `#6f42c1`
- **Criteria Mapping:** Criterion 3 (primary)
- **HUMANS Mapping:** H (Human-Centered)
- **Principle:** Humans — not algorithms — make consequential decisions about students. Formal governance structures ensure authority, documentation, and accountability for AI-influenced decisions.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 3.1 | Does this tool make decisions that affect student access, standing, or progress — or does it recommend to a human who decides? | Clear distinction between AI-as-recommendation and AI-as-decision. If the tool auto-acts (flags a student, changes a pathway, sends an alert), that's a consequential decision even if a human could theoretically override. |
| 3.2 | Can staff override, modify, or reject AI recommendations before they reach students? | Override built into workflow, not buried in admin settings. Staff see the AI recommendation and can approve, edit, or reject before action. |
| 3.3 | For high-risk use cases: is there a defined escalation path when AI output is uncertain, contradictory, or flagged? | Defined thresholds. When confidence is low or the case is edge, the system routes to a human, not a default action. |
| 3.4 | Does the tool create a decision audit trail? Can the institution document who approved what AI-influenced decision? | Logged decisions with timestamps, the AI recommendation, and the human action taken. |
| 3.5 | Who is accountable when the AI is wrong? Is that defined in the contract? | Clear liability allocation. Not "institution assumes all risk" buried in Terms of Service. |

**Scoring Rubric:**
- **3:** AI recommends; humans decide. Override built into workflow. Escalation paths defined. Full audit trail. Liability allocated in contract.
- **2:** AI acts with human review possible but not required. Override exists but isn't default. Some audit logging. Liability partially addressed.
- **1:** AI makes consequential decisions autonomously. Override technically possible but impractical. No audit trail. Vendor disclaims all liability.

**Source:** OMB M-25-21, Singapore Agentic AI, GAO, SACSCOC/C-RAC.

---

### P4: Student and Faculty Agency
- **Color:** `#fd7e14`
- **Criteria Mapping:** Criterion 3
- **HUMANS Mapping:** H (Human-Centered), U (Universal Support)
- **Principle:** Students and faculty are empowered participants in AI governance, not subjects of it. Faculty set academic AI policy; students exercise informed autonomy — with special provisions for the 70%+ adjunct workforce and adult learner populations.

**Questions — Student Agency:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 4.1 | Does the tool help students learn to navigate AI, or does it just deliver AI-generated answers? | Skill-building design: Socratic mode, guided problem-solving. Student learns the process, not just the result. |
| 4.2 | Can students opt out of AI interaction and access a human alternative without penalty or delay? | Real opt-out, not a buried setting. Human alternative is accessible, not a worse experience. |
| 4.3 | Does the tool give students visibility into and control over their own data and AI profile? | Students can see what the system "thinks" about them and contest it. |
| 4.4 | Does the tool recognize prior AI experience that adult learners bring from their workplaces? | Acknowledges that a 35-year-old returning student may use AI at work daily. Respects adult learner autonomy. |

**Questions — Faculty Agency:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 4.5 | Can faculty configure, restrict, or turn off AI features for their courses and advisees? | Granular faculty control. Not admin-only settings. Faculty set AI behavior per course or section. |
| 4.6 | Does the vendor provide training that is accessible to adjunct/part-time faculty? (async, under 30 minutes, no cost) | Training included in contract. Async options that fit adjunct schedules. Compensated governance participation addressed. |
| 4.7 | Does the tool evaluate, score, or surveil faculty performance? | Faculty are users and configurers, not subjects. |
| 4.8 | Does the tool's deployment plan respect the collegial consultation process and shared governance? | Academic senate consulted before institution-wide deployment. Not a top-down IT rollout. |

**Scoring Rubric:**
- **3:** Skill-building design for students. Real opt-out with human alternative. Adult learner autonomy respected. Granular faculty configuration. Adjunct-accessible training included. No faculty surveillance. Shared governance respected.
- **2:** Some skill-building features. Opt-out exists. Faculty configuration available. Training provided but not adjunct-optimized.
- **1:** Pure output delivery. No meaningful opt-out. Admin-only configuration. No adjunct provisions. Faculty performance tracked. Top-down deployment assumed.

**Source:** ASCCC (Title 5 "10+1"), ATD Action Areas 4-5, IEAIED Req. 5, Oregon State Bloom's Taxonomy, UNESCO Competency Frameworks.

---

### P5: Risk Proportionality & Harm Mitigation
- **Color:** `#dc3545`
- **Criteria Mapping:** All four (operational pillar)
- **HUMANS Mapping:** S (Safety & Security)
- **Principle:** Governance intensity matches risk level. Low-impact AI gets lightweight review; high-impact AI (agentic systems, consequential decisions) gets full governance — with harm mitigation built into every deployment.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 5.1 | Has the tool been classified by risk tier (high / medium / lower)? Does governance intensity match? | Risk tier is documented and agreed upon. High-risk tools get full governance; lower-risk tools get lightweight review. |
| 5.2 | What are the autonomy limits? Is this tool informational, recommendatory, or consequential? | Informational = lowest governance. Recommendatory = moderate (human reviews). Consequential = highest (human must approve). |
| 5.3 | If this is an agentic AI system, what bounds are placed on its autonomy? | Whitelisted actions only. Logging of all tool usage. Anomaly detection. No unbounded autonomous action. |
| 5.4 | What is the harm scenario? If this tool fails, what is the worst realistic outcome for a student? | Team has articulated the worst case and mitigation is planned. |
| 5.5 | Are staff trained on automation bias? | Plan for maintaining critical review even when the tool performs well. |
| 5.6 | Is there a process for emerging technology review? | Vendor updates trigger risk reassessment. New capabilities don't auto-deploy. |

**Scoring Rubric:**
- **3:** Risk tier documented. Autonomy limits defined. Agentic bounds in place. Harm scenarios articulated with mitigation plans. Automation bias training planned. Emerging tech review process exists.
- **2:** Risk tier acknowledged. Some autonomy limits. Harm scenarios partially explored. Training planned. No formal emerging tech review.
- **1:** No risk classification. No autonomy limits. Harm scenarios not considered. No automation bias awareness. Vendor features auto-deploy without review.

**Source:** Singapore Agentic AI Framework, NIST AI 600-1, OMB M-25-21, HEAT-AI, GAO.

---

### P6: Data Stewardship & System Integrity
- **Color:** `#17a2b8`
- **Criteria Mapping:** Criterion 2 (primary)
- **HUMANS Mapping:** M (Managed Privacy)
- **Principle:** Student data is a public trust. AI systems must meet data stewardship standards that protect privacy, ensure integrity, and maintain institutional control over how data is used.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 6.1 | What student data does this tool collect, access, or generate? Provide a complete data inventory. | Specific data fields, not categories. |
| 6.2 | Is any student data used to train or improve the vendor's AI models? | Explicit contractual commitment: no training on student data without consent. |
| 6.3 | What happens to student data when the contract ends? | Defined deletion timeline. Data export in standard format. No vendor retention. |
| 6.4 | Is the tool FERPA compliant? Does the vendor sign a FERPA-compliant data sharing agreement? | Written FERPA compliance. Vendor defined as "school official" with legitimate educational interest. |
| 6.5 | What is the data provenance for the AI's training data? | Vendor describes training data sources. No scraping of student data without consent. |
| 6.6 | How does the tool handle data quality issues? (incomplete records, outdated SIS data, transfer students) | Graceful handling of messy real-world CC data. Flags low-confidence recommendations. |
| 6.7 | Does the tool integrate with existing institutional systems through secure, documented protocols? | Standard integration methods (API, LTI, SAML/SSO). No shadow data stores. Aligned with CCCCO DGAW standards. |
| 6.8 | Does the institution retain the right to audit the vendor's data practices? | Contractual audit rights not blocked by IP claims. |

**Scoring Rubric:**
- **3:** Complete data inventory. No training on student data (contractual). Defined deletion/portability. FERPA agreement signed. Provenance documented. Secure integration. Audit rights in contract.
- **2:** Data inventory on request. Training opt-out available. FERPA compliant. Some provenance. Integration functional. Audit possible but not contractual.
- **1:** Data practices vague. Student data may train models. No clear deletion terms. FERPA undocumented. No audit rights. Integration undocumented or insecure.

**Source:** IEEE P7004, NAIC, NIST 600-1, GAO Principle 2, Alabama Template.

---

### P7: Transparency & Contestability
- **Color:** `#e83e8c`
- **Criteria Mapping:** Criterion 3
- **HUMANS Mapping:** N (Notice & Explanation)
- **Principle:** Students and faculty have the right to know when AI influences decisions that affect them — and the right to contest those decisions through meaningful processes.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 7.1 | Is it clear to students when they are interacting with AI vs. a human? | Visible, plain-language disclosure at point of interaction. |
| 7.2 | Can students understand *why* the AI gave a particular recommendation? | Explainability at student-appropriate level. |
| 7.3 | Does the vendor disclose what data the AI uses to generate recommendations? | Student can see what data informed the AI output. |
| 7.4 | Does the system support an appeals/contestability process? | Right to human review of any AI-influenced consequential decision. Clear escalation pathway. |
| 7.5 | Is there documentation of how the AI model works accessible to non-technical staff? | Advisors and student services staff can explain the tool to students. |
| 7.6 | Does the vendor provide a "model card" or equivalent? | Standardized reporting on capability, limitations, and known biases. |
| 7.7 | Does the institution publicly disclose which AI systems are in use for Student Services? | Public-facing list of AI tools in student-facing processes. |

**Scoring Rubric:**
- **3:** Clear disclosure. Explainable recommendations. Data sources visible. Meaningful contestability. Plain-language documentation. Model card published. Public AI inventory.
- **2:** Disclosure present but not prominent. Some explainability. Appeals through existing processes. Documentation technical. Model card on request.
- **1:** No disclosure. AI operates invisibly. No explainability. No appeals pathway. No documentation. No model card. No public disclosure.

**Source:** NAIC, CHAI (Model Cards), NIST 600-1, IEAIED Req. 7-8, ASCCC, OMB M-25-21.

---

### P8: Vendor Accountability & Institutional Sovereignty
- **Color:** `#6610f2`
- **Criteria Mapping:** All four (operational pillar)
- **HUMANS Mapping:** S (Safety & Security)
- **Principle:** CCs are buyers, not builders, of AI. Vendor relationships must protect institutional sovereignty, ensure accountability, and leverage collective bargaining power across the system.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 8.1 | Does the contract include performance benchmarks and remedies for non-performance? | Defined SLAs. Remedies for non-performance. |
| 8.2 | What is the exit strategy? Can the institution leave without losing data or paying punitive fees? | Data portability. Transition support. No lock-in. |
| 8.3 | Can the institution conduct or require independent bias audits? | Vendor supports third-party audits. Doesn't block with IP claims. |
| 8.4 | How does the vendor handle model updates? Advance notice and testing ability? | Update notification. Staging environment. No silent model changes. |
| 8.5 | Is this tool available through FoundationCCC/CollegeBuys or other consortium contracts? | Collective bargaining power leveraged. |
| 8.6 | Does the vendor have an incident response process? | Defined timeline. Root cause analysis. Corrective action plan. |
| 8.7 | What does total cost of ownership look like over 3 years? | Transparent pricing. No hidden fees. |

**Scoring Rubric:**
- **3:** Performance SLAs with remedies. Clean exit. Independent audits supported. Advance update notification. Consortium terms leveraged. Incident response defined. Transparent cost.
- **2:** Some performance terms. Exit possible. Audits on request. Updates communicated. Incident reporting exists.
- **1:** No performance guarantees. Punitive exit terms. Audits blocked. Silent updates. No incident process. Hidden costs.

**Source:** NAIC, GAO, NIST 600-1, IEAIED, SREB, NACUBO/E&I Cooperative.

---

### P9: Institutional Capacity & Continuous Governance
- **Color:** `#795548`
- **Criteria Mapping:** Criterion 4 (primary)
- **HUMANS Mapping:** Not directly mapped (AQL-original — identified gap in HUMANS)
- **Principle:** Governance must be achievable at every institutional scale. Tiered implementation ensures resource-constrained colleges can begin with minimum viable governance and grow over time.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 9.1 | Does the institution have a governance structure that can oversee this tool? | Someone is named, a review cycle exists, a process for decisions. Minimum viable governance. |
| 9.2 | Will this tool be included in the institution's annual AI inventory? | Inventory maintained with risk tiers and scorecard results. |
| 9.3 | Is there a plan to rescore this tool on a regular cycle? | Annual for high-risk. Every two years for medium/lower. Trigger-based for changes. |
| 9.4 | Does the tool generate reporting that supports accreditation documentation? | Usage data, outcome data, and governance documentation exportable. |
| 9.5 | Does the institution have the staff capacity to implement and sustain this tool? | Implementation plan matches real institutional resources. |
| 9.6 | Are there shared resources from consortia, the Chancellor's Office, or peer institutions? | Not reinventing governance alone. |

**Scoring Rubric:**
- **3:** Governance structure in place. AI inventory maintained. Regular rescore cycle. Accreditation-ready reporting. Capacity assessed honestly. Shared resources leveraged.
- **2:** Some governance exists. Inventory planned. Rescoring acknowledged but not scheduled.
- **1:** No governance structure. No inventory. No review cycle. No accreditation planning. Operating in isolation.

**Source:** SACSCOC/C-RAC, EDUCAUSE, CHAI, WCET, ATD, Local Government AI Handbook, OMB M-25-21.

---

## A.3 Criteria → Pillar → HUMANS Mapping Table

| Criterion | Pillar | HUMANS Letter | Role |
|-----------|--------|---------------|------|
| 1. Equitable Student Outcomes | **P2** (primary) | U, A | Shapes how all pillars are applied |
| 2. Quality Data, Governed Responsibly | **P6** (primary) | M | Foundation layer |
| 3. Ethics & Safety Foundation | **P3**, P7, P4 | H, N | Precondition, calibrated to stakes |
| 4. Thoughtful, Multi-Year Approach | **P9** (primary) | — | Sovereignty and sustainability |
| Cross-cutting | P1, P5, P8 | S (partial) | Operational across all criteria |

**HUMANS gap:** The CCCCO HUMANS framework does not address institutional capacity building (Criterion 4 / P9). Non-California colleges skip HUMANS and still have a complete framework. California colleges should understand this gap exists.

---

## A.4 Student Services Use Cases

| ID | Use Case | Default Risk Tier | Key Pillars | Equity Considerations | Governance Requirements |
|----|----------|------------------|-------------|----------------------|------------------------|
| SS-01 | AI Advising / Guided Pathways Assistant | 3 (High) | P1, P2, P3, P5 | Recommendations affect student trajectory; errors compound for first-gen and Pell-eligible students; pathway bias across career clusters | All 9 pillars scored. Human-in-the-loop required. Appeals process required. Bias audit before deployment and annually. Any pillar scoring 1 = documented mitigation or no-go. |
| SS-02 | Early Alert / Student Risk System | 3 (High) | P2, P3, P5, P7 | Risk profiling creates surveillance dynamic; disparate impact on students of color; stigma from false positives | All 9 pillars scored. Disaggregated false-positive analysis required. Student notification and contestability mandatory. |
| SS-03 | Financial Aid Triage & FAFSA Support | 3 (High) | P3, P5, P6 | Automated decisions on access to resources; errors disproportionately affect low-income students; undocumented student data sensitivity | All 9 pillars scored. No automated denial without human review. FERPA + state data privacy compliance. |
| SS-04 | Student-Facing Chatbot / Digital Front Door | 1 (Low) | P1, P7, P8 | Multilingual coverage gaps; accessibility barriers; students may not know they're interacting with AI | Score P1, P2, P6, P7, P8 minimum. Others recommended. Escalation to human required. |
| SS-05 | AI Course Tutoring Assistant (e.g., Nectir) | 2 (Medium) | P1, P4, P5 | Hallucination risk; Socratic vs. answer mode affects learning; faculty configuration critical; accessibility | All 9 pillars scored. P2 and P6 must score ≥ 2. Faculty configuration and override required. |
| SS-06 | Multilingual Support / Translation Services | 2 (Medium) | P2, P7 | Quality varies by language; cultural appropriateness; may create false confidence in accuracy | All 9 pillars scored. P2 and P6 must score ≥ 2. |
| SS-07 | Basic Needs Support & Resource Navigation | 1 (Low) | P6, P7 | Sensitive data (food insecurity, housing, immigration status); stigma risk; privacy paramount | Score P1, P2, P6, P7, P8 minimum. Data sensitivity demands P6 emphasis regardless of tier. |
| SS-08 | Career Services AI (resume, interview prep) | 1 (Low) | P1, P2 | Pathway bias across career clusters; equity across CTE and transfer; accessibility | Score P1, P2, P6, P7, P8 minimum. |
| SS-09 | Student Journey Mapping / Friction Detection | 2 (Medium) | P5, P6, P7 | PII; aggregation vs. individual tracking; who has access to journey data; surveillance risk | All 9 pillars scored. P2 and P6 must score ≥ 2. |
| SS-10 | Registration & Enrollment Support | 2 (Medium) | P1, P3, P5 | Automated enrollment decisions affect access; waitlist prioritization; equity across program availability | All 9 pillars scored. P2 and P6 must score ≥ 2. |
| SS-XX | Custom / Other | User assigns | User selects | User describes | Based on assigned tier |

### Screening Questions Per Use Case

Each use case has 4-5 screening questions used in Step 1 (Identify) to produce a GO / PAUSE / NO-GO recommendation. These questions are derived from the AQL POV's legitimacy questions, the framework architecture's risk assessment protocol, and the scorecard's risk tier definitions.

#### SS-01: AI Advising / Guided Pathways Assistant

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Does this tool make or influence decisions about which courses, pathways, or programs a student should pursue? | Yes (consequential) / No (informational only) | Yes → confirms High risk |
| 2 | Has your institution identified a specific student journey friction point this tool addresses? (e.g., excess unit accumulation, transfer pathway confusion) | Yes, with data / Yes, anecdotally / No | No → PAUSE (no evidence of need) |
| 3 | Will a human counselor review AI pathway recommendations before they reach students? | Always / Sometimes / Never | Never → NO-GO |
| 4 | Has the vendor provided disaggregated accuracy data across student demographics (Pell, first-gen, multilingual)? | Yes / Partial / No | No → PAUSE (equity risk unassessed) |
| 5 | Does the tool cover your full program catalog including CTE pathways, or is it optimized for transfer? | Full catalog / Transfer-focused / Unknown | Transfer-focused or Unknown → PAUSE |

#### SS-02: Early Alert / Student Risk System

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Does this system flag individual students as "at risk" and trigger interventions? | Yes / No | Yes → confirms High risk |
| 2 | Can students see their own risk profile and contest it? | Yes / No / Unknown | No → PAUSE (transparency gap) |
| 3 | Has a differential impact analysis been done for false positive rates across demographics? | Yes / Planned / No | No → PAUSE (15-30% false positive rates disproportionately flag ESL and disability populations) |
| 4 | Is there a defined escalation path when the system flags a student? (Who contacts them? How?) | Defined / Informal / None | None → NO-GO |
| 5 | Does your institution have the counseling capacity to follow up on system-generated alerts? | Yes / Strained / No | No → PAUSE (tool without capacity creates false accountability) |

#### SS-03: Financial Aid Triage & FAFSA Support

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Does this tool make decisions that affect whether a student receives financial aid? | Yes / It recommends; humans decide / No | Yes (automated decisions) → NO-GO without human-in-the-loop |
| 2 | Does the tool access sensitive financial data (FAFSA, tax information, income verification)? | Yes / No | Yes → confirms High risk, mandatory P6 emphasis |
| 3 | Is there a FERPA-compliant data sharing agreement with the vendor? | Yes / In progress / No | No → NO-GO |
| 4 | Can the tool handle the complexity of California financial aid (Cal Grant, AB 540, BOG waivers)? | Yes / Partially / No / Not applicable | Partially or No (for CA colleges) → PAUSE |
| 5 | If a student is incorrectly denied or delayed aid due to the system, is there a clear appeal process? | Yes / No | No → NO-GO |

#### SS-04: Student-Facing Chatbot / Digital Front Door

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Does this chatbot provide general information only, or does it access individual student records? | General info only / Accesses student records | Accesses records → upgrade to Tier 2 |
| 2 | Is there a clear escalation path to a human when the chatbot can't answer? | Yes, prominent / Buried in menus / No | No → PAUSE |
| 3 | In how many languages does the chatbot operate? | 1 (English only) / 2-3 / 4+ | English only → PAUSE (equity gap for CC populations) |
| 4 | Does the chatbot clearly identify itself as AI to the student? | Yes / No / Unclear | No → NO-GO (transparency requirement) |

#### SS-05: AI Course Tutoring Assistant (e.g., Nectir)

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Can faculty configure the tutor's behavior (Socratic mode, answer restrictions, knowledge scope) per course? | Yes / Limited / No | No → PAUSE (faculty agency gap) |
| 2 | What happens when the tutor doesn't know the answer? | Acknowledges limitation / Hallucinates a plausible answer / Unknown | Hallucinates → PAUSE (harm risk) |
| 3 | Does the tool help students build capability, or does it just deliver answers? | Skill-building design / Answer delivery / Mixed | Answer delivery → PAUSE (capability dependency risk) |
| 4 | Is the tutor accessible to students with disabilities (screen reader, keyboard navigation)? | Yes / Partial / No / Unknown | No → PAUSE |
| 5 | Does the vendor use student interaction data to train their AI models? | No (contractual) / Yes / Unknown | Yes → NO-GO ("Students are not training data") |

#### SS-06: Multilingual Support / Translation Services

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Is this tool translating general institutional materials, or student-specific communications? | General / Student-specific | Student-specific → upgrade to Tier 2 or 3 depending on content |
| 2 | Has the translation quality been validated by native speakers for your top 5 student languages? | Yes / Partially / No | No → PAUSE |
| 3 | Does the tool handle culturally sensitive content appropriately (not just literal translation)? | Yes / Unknown | Unknown → PAUSE |
| 4 | Is there a human review process for high-stakes translated content (financial aid, academic standing)? | Yes / No | No for high-stakes → NO-GO |

#### SS-07: Basic Needs Support & Resource Navigation

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Does the tool collect data about students' basic needs (food insecurity, housing, immigration status)? | Yes / No | Yes → P6 emphasis regardless of tier |
| 2 | Is this data shared with any external parties (other agencies, vendors)? | No / Yes, with consent / Yes, without explicit consent | Without consent → NO-GO |
| 3 | Can students access resources without disclosing personal hardship details to the AI? | Yes / No | No → PAUSE (stigma risk) |
| 4 | Does the tool connect to local resources that are actually available at your institution? | Yes, locally configured / Generic national database | Generic → PAUSE (referrals to non-existent services harm trust) |

#### SS-08: Career Services AI (resume, interview prep)

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Does the tool recommend career pathways, or help with job readiness skills (resume, interview)? | Pathway recommendations / Job readiness / Both | Pathway recommendations → consider upgrading to Tier 2 |
| 2 | Does the tool serve CTE pathways and trade careers as well as transfer/professional careers? | Yes / Mostly professional/transfer / Unknown | Mostly professional → PAUSE (equity across pathways) |
| 3 | Does the tool steer students toward specific employers or programs? | No / Yes, disclosed / Yes, undisclosed | Undisclosed → NO-GO (hidden commercial interests) |
| 4 | Is the resume/interview content culturally responsive? | Yes / Generic / Unknown | Generic or Unknown → PAUSE |

#### SS-09: Student Journey Mapping / Friction Detection

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Does this tool track individual students or analyze aggregate patterns? | Individual tracking / Aggregate only / Both | Individual → confirms Tier 2; both → consider Tier 3 |
| 2 | Who has access to the journey data? | Counselors only / Administrators / Faculty / Vendors | Vendors → PAUSE (data governance concern) |
| 3 | Can students see their own journey data and understand how it's being used? | Yes / No | No → PAUSE |
| 4 | Are the analytics used to make decisions about individual students (intervention, advising)? | Yes / No | Yes → upgrade to Tier 3 |
| 5 | Does the institution have clear data retention policies for journey data? | Yes / No | No → PAUSE |

#### SS-10: Registration & Enrollment Support

| # | Question | Response Options | Logic |
|---|----------|-----------------|-------|
| 1 | Does this tool make decisions about course enrollment, waitlist priority, or registration access? | Yes / It recommends; humans decide / Information only | Yes → upgrade to Tier 3 |
| 2 | Could AI errors result in a student being enrolled in the wrong course or missing a registration window? | Yes / Low likelihood / No | Yes → confirms Tier 2+ |
| 3 | Is there a human override when the system encounters edge cases (prerequisite exceptions, special admits)? | Yes / No | No → PAUSE |
| 4 | Does the tool work for all registration scenarios (late registration, concurrent enrollment, non-credit)? | Yes / Most / No | No → PAUSE |

---

## A.5 No-Go Criteria

Eight hard stops. If any is triggered, the assessment displays a red banner alert. The tool should not be deployed without resolving the condition.

| # | ID | Statement | Pillar | Rationale | Detection Method |
|---|-----|-----------|--------|-----------|-----------------|
| 1 | NG-01 | No clear educational purpose | P1 | If it doesn't serve education, it doesn't belong in Student Services | P1 score = 1, OR screening question indicates no educational purpose |
| 2 | NG-02 | Students are not training data | P6 | Vendor uses student data to train AI models without contractual prohibition | Explicit yes/no question in no-go checklist |
| 3 | NG-03 | No human override for consequential decisions | P3 | Violates OMB high-impact AI requirements and accreditation expectations | P3 score = 1 AND risk tier = High |
| 4 | NG-04 | Vendor blocks independent bias audits | P8 | "Independent verification is the only way to verify AI is not biased" (GAO) | Explicit yes/no question in no-go checklist |
| 5 | NG-05 | No FERPA-compliant data sharing agreement | P6 | Legal requirement, not optional | Explicit yes/no question in no-go checklist |
| 6 | NG-06 | No student disclosure of AI use | P7 | Students have a right to know | P7 score = 1 OR explicit no-go question |
| 7 | NG-07 | Decisions without recourse are not governance | P7 | No contestability pathway for AI-influenced decisions | P7 score = 1 OR explicit no-go question |
| 8 | NG-08 | Vendor lock-in undermines institutional sovereignty | P8 | Exit terms require forfeiting student data or impose punitive switching costs | Explicit yes/no question in no-go checklist |

**Implementation:** A dedicated "No-Go Checklist" step runs after pillar scoring. Eight yes/no questions map directly to the 8 criteria. No-go criteria #1, #3, #6, and #7 can also be inferred from pillar scores. Criteria #2, #4, #5, and #8 require explicit yes/no answers because pillar-level scores are not granular enough to detect these specific conditions.

---

## A.6 Archetype Definitions

### Lightweight
- **Description:** Small or rural. Limited IT. 1-2 people wearing many hats. High reliance on external support.
- **Characteristics:** No formal AI governance yet. First tool evaluation. Need minimum viable process. Under 5,000 students. May not have dedicated IT director.
- **Starting Recommendations:**
  - Start with one Tier 1 or Tier 2 use case
  - Use provided templates directly (no customization needed)
  - Quarterly review cycle
  - Focus scoring on 5 mandatory lower-risk pillars: P1, P2, P6, P7, P8
  - Simplified guidance text
  - Annual review checklist: minimum items only
- **Represents:** ~40-50 of California's 116 CCs

### Building
- **Description:** Mid-size. Some analytics/data capability. Emerging AI interest. Has IT director and IR capacity.
- **Characteristics:** Some governance exists. AI committee or task force forming. Evaluating medium- or high-risk tools. Need comprehensive evaluation with guidance.
- **Starting Recommendations:**
  - 2-3 use cases across risk tiers
  - Cross-functional AI working group meets quarterly
  - Begin disaggregated tracking
  - All 9 pillars active, all questions visible
  - Full scoring rubrics displayed
  - No-go criteria prominently displayed
- **Represents:** ~25-30 similar colleges

### Scaling
- **Description:** Large, higher volume. Dedicated technical bench. May have data warehouse, analytics team, innovation office.
- **Characteristics:** Mature governance. Multiple tools deployed. Need annual review cycle and portfolio-level pattern analysis.
- **Starting Recommendations:**
  - Portfolio approach across risk tiers
  - Formal AI governance with project owners
  - Bias audits for Tier 3 use cases
  - Standing committee with reporting structure
  - Annual review mode as primary entry point
  - Comparative scoring across multiple tools
  - Export/report generation for governance committee and accreditation
- **Represents:** ~5-10 similar colleges

---

## A.7 Annual Review Checklist Structure

Once deployed, rescore each tool: annually for high-risk, every 2 years for medium/lower. Trigger-based for vendor changes, incidents, or new capabilities.

| # | Review Area | Pillar(s) | Review Questions |
|---|-------------|-----------|-----------------|
| 1 | Educational outcomes | P1 | Is the tool still serving its stated educational purpose? Has the student outcome improved? Still aligned with institutional priorities? |
| 2 | Equity outcomes | P2 | Usage rates and outcomes equitable across student cohorts? Demographic-disaggregated review conducted? Any cohort underserved or disproportionately flagged? |
| 3 | Decision quality | P3 | Override rate? Staff using overrides frequently? Any decision accountability failures? |
| 4 | Student/faculty experience | P4 | Student satisfaction, confusion, avoidance, trust? Faculty finding tool helpful or burdensome? Adjunct access working? |
| 5 | Risk reassessment | P5 | Vendor added new capabilities or agentic features? Risk tier update needed? Near-miss incidents? |
| 6 | Data practices | P6 | Changes to vendor data practices? Data quality issues? Privacy audit results? |
| 7 | Incidents & appeals | P7 | AI failures, errors, complaints? Resolution quality? Complaint/appeal volume? Contestability process breakdowns? |
| 8 | Vendor performance | P8 | SLAs being met? Vendor acquired or ownership changed? Cost tracking to projection? Exit still feasible? |
| 9 | Governance health | P9 | Governance structure still functioning? AI inventory current? Shared resources leveraged? Ready for next tier of maturity? |

---

# Section B: Step 1 — Identify Flow

## B.1 Use Case Selector Interface

**Purpose:** User identifies which Student Services AI use case they are considering or already deploying.

**Interface spec:**
- Grid/card layout displaying all 10 use cases (SS-01 through SS-10)
- Each card shows:
  - Use case ID and name
  - One-line description
  - Default risk tier badge (color-coded: red = High, yellow = Medium, green = Low)
  - Key pillar icons (2-3 most relevant pillars)
- "Custom / Other" option (SS-XX) with:
  - Free-text input for use case description
  - Dropdown for user-assigned risk tier
  - Multi-select for relevant pillars
- **Selection behavior:** User selects exactly one use case → proceeds to screening

**Data source for cards:** `use_cases` array in content JSON.

## B.2 Screening Questions Per Use Case

After use case selection, user answers 4-5 screening questions specific to that use case (detailed in Section A.4).

**Interface spec:**
- One question per screen (or all visible with clear visual separation)
- Each question has 2-4 response options (radio buttons or cards)
- Response options have associated logic values for GO/PAUSE/NO-GO determination
- Sidebar shows use case profile: name, risk tier badge, key pillars, equity flag

**For custom use cases (SS-XX):** Display a generic set of 5 screening questions:
1. Does this tool make or influence decisions that affect student access, standing, or progress?
2. Does this tool access individual student records or sensitive data?
3. Is there a clear educational purpose tied to student outcomes?
4. Will a human review AI outputs before they reach students?
5. Has the vendor provided information about how the tool performs across diverse student populations?

## B.3 Prioritization Logic: Impact × Risk × Feasibility

Not scored numerically in the Navigator UI. Instead, the screening questions implicitly evaluate three dimensions:

- **Impact:** Does this tool address a known student journey friction point? (Questions about educational purpose, specific need)
- **Risk:** What is the consequence of failure? (Questions about decision type, data sensitivity, human override)
- **Feasibility:** Does the institution have the capacity to govern this tool? (Questions about counseling capacity, human review bandwidth, existing processes)

The screening output is qualitative, not a numeric score. It maps to three outcomes.

## B.4 GO / PAUSE / NO-GO Decision Logic

**GO:** No screening questions triggered PAUSE or NO-GO conditions. The use case appears viable for evaluation. Proceed to Step 2 (Evaluate).

**PAUSE:** One or more screening answers indicate concern but not a hard stop. Display:
- Which specific concerns were flagged
- What conditions would need to change before proceeding
- Option to proceed to evaluation anyway (concerns carry forward and display in the summary)
- Option to select a different use case

**NO-GO:** One or more screening answers hit a hard stop condition. Display:
- Which specific condition was triggered
- Why this is a no-go (plain language, not jargon)
- What would need to change (actionable: "Require human review for all AI-influenced decisions" not "Address governance gap")
- Suggestion of alternative use cases at lower risk tiers
- Cannot proceed to evaluation for this use case without revising the condition

**Threshold rules per screening question:**
- Response options tagged with `go`, `pause`, or `nogo` logic
- Any single `nogo` response → NO-GO for the assessment
- Two or more `pause` responses → PAUSE recommendation
- One `pause` response → GO with flagged concern
- All `go` responses → GO

## B.5 Quick-Start Archetype Self-Selection (Alternative Entry Point)

**Purpose:** Users who know their institutional profile can skip the full screening and jump to evaluation with pre-configured settings.

**Interface spec:**
- 3 archetype cards (Lightweight / Building / Scaling) displayed on landing or as an alternative CTA
- Each card shows: name, tagline, characteristics, "This sounds like us" CTA
- User selects archetype → stored in state → proceeds to Use Case Selector (same as full path, but with archetype-informed defaults)

**Pre-configuration effects of archetype selection:**
- **Lightweight:** Default use case filter shows Tier 1 and Tier 2 use cases first. Scoring UI uses simplified guidance. Non-mandatory pillars visually de-emphasized.
- **Building:** All use cases shown equally. Full scoring interface. No simplification.
- **Scaling:** Annual review mode offered as alternative to new evaluation. Previous assessments surfaced from localStorage.

**Where paths converge:** Both entry points arrive at the same Use Case Selector (View 2a). The quick path simply pre-stores the archetype. From Use Case Selector onward, the flow is identical: screening → dependency profile → risk tier → pillar scoring.

## B.6 Dependency Profile Questions (Universal — All Use Cases)

**Placement in flow:** After screening questions produce a GO or PAUSE (user proceeds), and before risk tier confirmation in Step 2. This is a distinct interaction step — not combined with screening.

**Purpose:** Assess whether the tool builds capability or creates dependency. Four universal questions apply to every use case, regardless of risk tier.

**Interface spec:**
- Displayed as a separate screen (View 3b) after the GO/PAUSE result
- Header: "Understanding Dependency" or equivalent from content JSON
- Intro text: "These four questions help you understand whether this tool builds capability or creates dependency. There are no wrong answers — but there are answers you should know before you deploy."
- Four questions (D1–D4), each with 3 response options scored 1/2/3
- Each response option shows its label + description + "What you're looking for" guidance text
- Score calculated live as user answers (visible running total: "X of 12")
- After all 4 answered → dependency profile result displayed inline:
  - Badge (green/yellow/red) + profile label + one-sentence interpretation
  - "Continue to Evaluation →" button

**Questions:** See Section F.1 for full question text, response options, and scoring.

**For quick path (archetype pre-selected):** Dependency questions are still asked. They are not abbreviated. Dependency applies universally — it is not archetype-dependent.

**For NO-GO screening result:** Dependency questions are not shown. If the screening produces a NO-GO, the flow stops at the NO-GO explanation. Dependency profiling only occurs for tools that pass screening.

---

# Section C: Step 2 — Evaluate Flow

## C.1 Risk Tier Assignment

**Trigger:** User has completed screening and dependency profiling (Step 1). Both use case and dependency profile are stored in state.

**Interface spec:**
- Display the auto-assigned risk tier based on use case default (from use case table in A.4)
- Show tier definition, governance intensity requirements, and examples
- Visual: color-coded tier badge (red/yellow/green) with tier name
- Two user actions:
  - **Accept** → proceed to pillar scoring
  - **Override** → select different tier with mandatory text justification

**Override rules:**
- Upward override (Low → Medium, Medium → High) always permitted
- Downward override (High → Medium, Medium → Low) permitted only with mandatory text justification that becomes part of the assessment record
- Override reason stored in state and displayed in summary

## C.2 Per-Pillar Scoring Interface

**Core interaction:** For each pillar, user reads the questions and guidance, then assigns a single score (1, 2, or 3) for the pillar as a whole. Users do NOT score each question individually.

**Interface spec per pillar:**
- **Header:** Pillar number, name, color bar
- **Principle statement:** Italic, one sentence
- **Hook line:** One punchy line (from content JSON)
- **Questions:** Displayed as a reference table with "What You're Looking For" guidance
- **Scoring rubric:** Three descriptions (3 = what good looks like, 2 = partial, 1 = what bad looks like) displayed side-by-side or stacked
- **Score selector:** Three large clickable options (1 / 2 / 3)
- **Optional notes field:** Free text for the user to record observations
- **Source note:** Collapsed/expandable, showing framework citations

**Navigation:**
- Next Pillar / Previous Pillar buttons
- Progress indicator: "Pillar 3 of 9" with progress bar
- Running score visible in sidebar/header (total so far / total possible)

**California toggle:** When enabled (set once, persists), each pillar displays its HUMANS mapping in a badge or sidebar note.

## C.3 Mandatory vs. Recommended Pillars by Risk Tier

| Pillar | Tier 1 (Low) | Tier 2 (Medium) | Tier 3 (High) |
|--------|-------------|-----------------|---------------|
| P1: Purpose | **Mandatory** | **Mandatory** | **Mandatory** |
| P2: Equity | **Mandatory** | **Mandatory** (must score ≥ 2) | **Mandatory** (must score ≥ 2) |
| P3: Human Authority | Recommended | **Mandatory** | **Mandatory** |
| P4: Student & Faculty Agency | Recommended | **Mandatory** | **Mandatory** |
| P5: Risk Proportionality | Recommended | **Mandatory** | **Mandatory** |
| P6: Data Stewardship | **Mandatory** | **Mandatory** (must score ≥ 2) | **Mandatory** (must score ≥ 2) |
| P7: Transparency | **Mandatory** | **Mandatory** | **Mandatory** |
| P8: Vendor Accountability | **Mandatory** | **Mandatory** | **Mandatory** |
| P9: Institutional Capacity | Recommended | **Mandatory** | **Mandatory** |

**Display behavior:**
- **Mandatory pillars:** Full display, required score before proceeding
- **Recommended pillars:** Visually lighter styling, collapsible, can be skipped (scored as null/N/A in summary)
- **Minimum score requirements** (P2 ≥ 2, P6 ≥ 2 for Tier 2/3): If user scores below threshold, show inline warning: "For [tier] tools, this pillar should score at least 2. Consider whether your mitigation plan addresses this gap."

## C.4 No-Go Trigger Logic

**When triggered:** Red banner interrupts the flow. Full stop. Explains why. Provides actionable guidance.

**Trigger points:** No-go checks run in two places:
1. **Inline during pillar scoring:** If P1 = 1 → immediate NG-01 alert. If P3 = 1 on High-risk tool → immediate NG-03 alert.
2. **Dedicated No-Go Checklist:** After all pillar scoring is complete, 8 yes/no questions are presented:

| # | No-Go Question | Maps To |
|---|----------------|---------|
| 1 | Does this tool have a clear educational purpose tied to student outcomes? | NG-01 (inverted: "No" = trigger) |
| 2 | Has the vendor contractually committed that student data will not be used to train their AI models? | NG-02 (inverted) |
| 3 | Can a human override or reject AI recommendations before they affect students? | NG-03 (inverted, for High-risk only) |
| 4 | Does the vendor allow independent bias audits without blocking access? | NG-04 (inverted) |
| 5 | Is there a FERPA-compliant data sharing agreement in place or planned? | NG-05 (inverted) |
| 6 | Are students informed when AI is being used in their interaction? | NG-06 (inverted) |
| 7 | Can students appeal or contest AI-influenced decisions? | NG-07 (inverted) |
| 8 | Can the institution exit the vendor relationship without losing student data or facing punitive costs? | NG-08 (inverted) |

**Display when triggered:**
- Red banner: "[NO-GO CONDITION]: [Statement]"
- Why: Plain-language explanation
- What to do: Specific, actionable steps (e.g., "Require contractual prohibition on training. If the vendor won't agree, walk away.")
- The assessment is NOT invalidated — user proceeds to summary, but no-go alerts display prominently at the top

## C.5 Score Aggregation and Pattern Interpretation

**Total score:** Sum of all scored pillars (out of 27 if all 9 scored, or proportional if some recommended pillars skipped).

**Pattern interpretation rules** (from vendor scorecard):

| Pattern | Interpretation | Action |
|---------|---------------|--------|
| Any pillar = 1 on High-Risk tool | Do not deploy without documented mitigation plan approved by governance committee. Score of 1 on P2, P3, or P5 for high-risk = no-go unless mitigations are substantial. | No-go or documented mitigation |
| P1 = 1 | If you can't articulate the educational purpose, don't buy it. | No-go |
| Multiple pillars = 2 | Proceed with conditions. Document what the institution will do to compensate for vendor gaps. | Proceed with conditions |
| All pillars ≥ 2 | Proceed with standard governance. Include in annual AI inventory. Monitor per risk tier schedule. | Proceed |
| Strong P6 & P8, weak P4 & P7 | Vendor is technically sound but product wasn't designed with students as participants. Institution must add the student-facing layer. | Institutional supplementation needed |
| Strong P4 & P7, weak P6 | Vendor markets well but hasn't done the data governance work. Attractive front end, uncertain foundation. | Data governance investigation needed |
| P9 = 1 | Not about the vendor — about institutional readiness. Build governance capacity before deploying, not after. | Build governance capacity first |
| High Dependency + Tier 3 | Tool replaces capability and makes consequential decisions. Maximum governance combination. Requires all high-dependency protections plus capability impact tracking. | Full dependency governance + capability tracking |
| High Dependency + weak P4 | Tool replaces capability and doesn't empower students/faculty. Double dependency risk: institutional and individual. | Investigate whether navigate-with configuration exists |
| Medium/High Dependency + P8 = 1 | Dependency on a vendor that doesn't meet accountability standards. Institutional vulnerability. | Resolve vendor accountability before deepening dependency |

**Dependency profile display in Governance Profile (View 5):**
- Dependency badge (green/yellow/red) displayed alongside risk tier badge
- Dependency score (e.g., "8 of 12") with profile label
- If Medium or High: specific governance requirements previewed (see Section F.3)
- If High + Tier 3: capability impact tracking flagged prominently

## C.6 Vendor Accountability Questions Calibrated to Risk Tier

Standard vendor questions (P8) apply to all tiers. Additional questions are triggered by risk tier:

**Tier 1 (Low) — minimum vendor accountability:**
- Basic evaluation checklist (P8 Q8.1, 8.2, 8.7)
- Contract addendum with AI terms (Q8.5)

**Tier 2 (Medium) — enhanced vendor accountability:**
- All Tier 1 questions plus:
- Bias audit capability (Q8.3)
- Model update notification (Q8.4)
- Incident response (Q8.6)

**Tier 3 (High) — full vendor accountability:**
- All Tier 2 questions plus:
- Independent third-party audits required (not just supported)
- Performance SLAs with defined remedies
- Exit strategy with data portability timeline
- Consortium contract verification (Q8.5)
- Total cost of ownership analysis (Q8.7)

---

# Section D: Steps 3-4 — Roadmap Output

## D.1 Content Assembly Logic

The roadmap is the key deliverable. It is conditionally assembled from five inputs:

```
ROADMAP = f(archetype, use_case, risk_tier, pillar_scores, dependency_profile)
```

**Assembly rules:**
1. **Archetype** determines: RACI structure, governance complexity, language simplicity, output length
2. **Use case** determines: which specific governance requirements apply, which templates are referenced
3. **Risk tier** determines: pre-deployment requirements, measurement intensity, review cadence
4. **Pillar scores** determine: which pillar-specific remediation actions surface (any pillar scoring 1 triggers its remediation block)
5. **Dependency profile** determines: which dependency governance requirements are conditionally inserted (see Section F.3). Low = no additions. Medium = 3 requirements. High = 4 requirements (capability impact tracking conditional on Tier 3).

**Dependency governance insertion point:** The dependency governance subsection appears in the roadmap between "Review Cadence" and "Decision Rules." It is omitted entirely for Low Dependency profiles.

**Output length guidance:**
- Lightweight archetype + Low risk tier + Low dependency ≈ 2 pages printed
- Building archetype + Medium risk tier + Medium dependency ≈ 4–5 pages printed
- Scaling archetype + High risk tier + High dependency ≈ 6–7 pages printed

## D.2 Archetype × Risk Tier Roadmap Definitions

### Lightweight × Tier 1 (Low)

**Pre-deployment governance requirements:**
- Designate a person responsible for this tool (can be added to existing role)
- Complete the basic vendor evaluation checklist
- Add tool to AI inventory (or create inventory starting with this tool)
- Post student-facing AI disclosure notice
- Confirm tool does not use student data for model training

**RACI sketch:**
| Role | Responsible | Accountable | Consulted | Informed |
|------|-------------|-------------|-----------|----------|
| Tool oversight | Designated staff member | IT Director or VPSS | Academic Senate rep | Faculty using tool |
| Student disclosure | Student Services lead | VPSS | Equity officer | Students |
| Vendor relationship | IT or procurement | CIO/designee | — | Governance body |

**90-day measurement starter:**
- Usage data: how many students interacted, frequency, drop-off points
- Student satisfaction: brief survey at 30 and 90 days
- Escalation tracking: how many queries escalated to human, resolution rate
- Accessibility: any reported access barriers

**Review cadence:** Every 2 years (or trigger-based: vendor changes, incidents, new capabilities)

**Escalation triggers:**
- Student complaint volume exceeds baseline
- Tool accuracy falls below vendor SLA
- Vendor changes data practices or adds features without notice

**Decision rules:**
- **Pause when:** 3+ student complaints about accuracy or accessibility in a 30-day period
- **Investigate when:** Vendor announces model update or new capability
- **Stop when:** Any no-go criterion becomes true post-deployment

**Toolkit PDF references:**
- AI Inventory Template
- AI Tool Evaluation Checklist
- Student AI Rights Notice

**HUMANS mapping (CA only):** Display which HUMANS letters this tool touches (typically N and S for Tier 1) with brief compliance note.

---

### Lightweight × Tier 2 (Medium)

**Pre-deployment governance requirements:**
- Everything in Tier 1, plus:
- Score all 9 pillars (P2 and P6 must score ≥ 2)
- Confirm faculty can configure/override AI features
- Establish escalation path for AI errors
- Plan adjunct faculty orientation (≤ 30 minutes)

**RACI sketch:**
| Role | Responsible | Accountable | Consulted | Informed |
|------|-------------|-------------|-----------|----------|
| Tool oversight | Designated staff + faculty rep | VPSS | Academic Senate, IT | All affected faculty |
| Student disclosure | Student Services lead | VPSS | Equity officer, faculty | Students, counselors |
| Faculty configuration | Department chair | Academic Senate rep | IT | Adjunct faculty |
| Equity review | IR/Equity officer | VPSS | Faculty, students | Board |

**90-day measurement starter:**
- All Tier 1 metrics, plus:
- Disaggregated usage by student demographics (Pell, first-gen, multilingual)
- Faculty configuration uptake: how many faculty customized settings
- Override rate: how often staff override AI recommendations
- Error rate tracking with demographic breakdowns

**Review cadence:** Annual

**Escalation triggers:**
- Tier 1 triggers, plus:
- Disaggregated outcomes show differential impact
- Override rate > 30% (suggests AI quality issues)
- Faculty report tool is burdensome rather than helpful
- Adjunct faculty not receiving training or tool access

**Decision rules:**
- **Pause when:** P2 (Equity) or P6 (Data) conditions deteriorate post-deployment
- **Investigate when:** Differential outcomes emerge across student demographics
- **Stop when:** Any no-go criterion becomes true; bias audit reveals systematic disparate impact

**Toolkit PDF references:**
- All Tier 1 templates, plus:
- Faculty AI Training Outline (with 30-min adjunct orientation)
- Vendor Contract AI Addendum
- High-Impact AI Assessment Protocol (adapted for medium risk)

---

### Building × Tier 2 (Medium)

**Pre-deployment governance requirements:**
- All Tier 1 and Tier 2 requirements, plus:
- AI governance committee or working group reviews assessment
- Stage-gate sign-off before deployment
- Incident response protocol established
- Data lifecycle requirements documented in vendor contract
- Faculty workshop on tool configuration (60-90 min)

**RACI sketch:**
| Role | Responsible | Accountable | Consulted | Informed |
|------|-------------|-------------|-----------|----------|
| Governance review | AI working group chair | VPSS or CIO | Academic Senate, equity officer | Board |
| Tool oversight | Project owner (named) | AI working group | Faculty reps, IT, IR | Affected departments |
| Student disclosure | Student Services lead | VPSS | Student government | Students |
| Faculty onboarding | Faculty development lead | Academic Senate rep | Vendor, IT | All affected faculty |
| Data governance | IR/Data officer | CIO | Legal, DGAW (CA) | Vendor |
| Equity monitoring | IR/Equity officer | AI working group | Faculty, student reps | Board |

**90-day measurement starter:**
- All Tier 2 metrics, plus:
- Bias audit baseline: pre-deployment demographic analysis
- Decision audit trail: sample review of AI recommendations vs. human actions
- Student awareness: percentage of students who know AI is used in their interaction
- Governance health: committee meeting frequency and attendance

**Review cadence:** Annual with quarterly check-ins

**Decision rules:**
- **Pause when:** Committee identifies unresolved equity concern; vendor misses SLA
- **Investigate when:** Outcome data shows widening gaps; student complaints follow a demographic pattern
- **Stop when:** No-go criterion triggered; governance committee votes to suspend

**Toolkit PDF references:**
- All Tier 1/2 templates, plus:
- AI Governance Committee Charter
- AI Incident Response Protocol
- Annual AI Governance Report template

---

### Building × Tier 3 (High)

**Pre-deployment governance requirements:**
- All Building × Tier 2 requirements, plus:
- Full governance committee review and approval
- Bias audit completed before deployment
- Human-in-the-loop workflow documented and tested
- Appeals/contestability process established and published
- Staff training on automation bias
- Student notification and opt-out mechanisms in place

**RACI sketch:**
| Role | Responsible | Accountable | Consulted | Informed |
|------|-------------|-------------|-----------|----------|
| Governance approval | AI committee (vote) | VPSS + Academic Senate | CIO, legal, equity, students | Board, all faculty |
| Human oversight | Named decision reviewer | VPSS or designee | Counselors, advisors | Students |
| Bias audit | IR/External auditor | AI committee | Vendor, equity officer | Board |
| Appeals process | Student Services dean | VPSS | Legal, student government | Students |
| Ongoing monitoring | Project owner | AI committee | IR, faculty, IT | Board |

**90-day measurement starter:**
- All Building × Tier 2 metrics, plus:
- Appeal/contestability: number of student appeals, resolution time, outcomes
- Human override quality: sample review of overridden decisions
- Bias audit findings: initial audit results with action plan
- Automation bias indicators: staff override rate trends (declining = potential concern)
- Student opt-out rate: how many students choose human alternative

**Review cadence:** Annual with quarterly monitoring reports to committee

**Escalation triggers:**
- All previous triggers, plus:
- Student appeal volume exceeds established threshold
- Bias audit reveals systematic disparate impact
- Human override rate drops below 5% (possible automation bias)
- Vendor acquired or changes ownership

**Decision rules:**
- **Pause when:** Bias audit findings require remediation; student appeal outcomes indicate systematic error
- **Investigate when:** Override rate drops significantly; new demographic data reveals previously undetected disparity
- **Stop when:** No-go criterion triggered; bias audit reveals unremediated discriminatory impact; vendor fails to maintain contractual commitments

**Toolkit PDF references:**
- All Building × Tier 2 templates, plus:
- High-Impact AI Assessment Protocol (full)
- Student AI Documentation Form
- Student Capability Assessment Protocol

---

### Scaling × Tier 3 (High)

**Pre-deployment governance requirements:**
- All Building × Tier 3 requirements, plus:
- Portfolio-level analysis: how does this tool interact with existing AI tools?
- Cross-tool data governance review (data flows between systems)
- Consortium contract verification (FoundationCCC/CollegeBuys)
- Faculty-led AI research plan (action research on tool effectiveness)
- Student advisory panel input on deployment plan

**RACI sketch:**
| Role | Responsible | Accountable | Consulted | Informed |
|------|-------------|-------------|-----------|----------|
| Portfolio governance | AI governance committee (standing) | VP Academic Affairs + VPSS | All VPs, Senate, CIO | Board, system office |
| Human oversight | Dedicated oversight lead | VPSS | Counseling dept, faculty | Students |
| Bias audit | External auditor (contracted) | AI committee | Vendor, IR, equity | Board, public (published) |
| Student voice | Student advisory panel | Student government | Dean of Students | All students |
| Cross-tool coordination | CIO/Data officer | AI committee | All tool project owners | IT staff |
| System coordination | Designated liaison | VP or designee | CCCCO, consortia | AI committee |

**90-day measurement starter:**
- All Building × Tier 3 metrics, plus:
- Portfolio-level metrics: cross-tool impact analysis, resource utilization across AI tools
- System-level coordination: contributions to CCCCO knowledge base, consortium participation
- Faculty research: action research findings on AI tool effectiveness
- Student capability assessment: learning outcomes measured with and without AI support

**Review cadence:** Annual comprehensive review with quarterly monitoring and monthly governance meetings

**Decision rules:**
- All Building × Tier 3 rules, plus:
- **Pause when:** Portfolio analysis reveals tool conflict or data governance gap across systems
- **Investigate when:** Cross-tool patterns emerge (e.g., students flagged by multiple AI systems creating compound effects)
- **Stop when:** Accreditation concern raised; system-level policy change conflicts with deployment

**Toolkit PDF references:**
- All previous templates, plus:
- Annual AI Governance Report (comprehensive)
- AI Portfolio Documentation template
- Cross-Institutional Framework Coordination guide

---

### Remaining combinations

The following archetype × tier combinations use the closest defined combination above as a base, with adjustments:

| Combination | Base | Adjustments |
|-------------|------|-------------|
| Lightweight × Tier 3 | Building × Tier 3 | Simplified RACI (fewer roles). Shared-service model for bias audit. Consortium resources emphasized. Longer timelines for compliance. |
| Scaling × Tier 1 | Building × Tier 2 | Annual review mode as primary focus (tool already deployed). Portfolio-level analysis emphasis. Comparative scoring against existing tools. |
| Scaling × Tier 2 | Building × Tier 2 + Scaling × Tier 3 | Full governance with portfolio integration. Cross-tool data governance. Standing committee oversight. |

---

## D.3 Pillar-Specific Remediation Actions

When a pillar scores 1, the roadmap surfaces a specific remediation action. These are direct instructions.

| Pillar | Low Score (1) Action |
|--------|---------------------|
| P1 | Before deploying, articulate the specific educational purpose in one sentence tied to a student outcome. If you cannot, this tool does not belong in Student Services. Document the student journey friction point it addresses with institutional data. |
| P2 | Before deploying, conduct a disaggregated impact analysis across Pell, first-gen, undocumented, and multilingual populations. Request vendor performance data broken down by demographics. If vendor cannot provide it, plan a post-deployment bias audit within the first semester. |
| P3 | Before deploying, build human override into the workflow — not as an admin setting, but as a required step before AI recommendations reach students. For high-risk tools: define who reviews, when, and document the decision. Require a named human accountable for every AI-influenced consequential decision. |
| P4 | Before deploying, ensure faculty can configure AI features per course. Plan a 30-minute adjunct orientation. Confirm students can opt out and access a human alternative without penalty. If the tool surveys or tracks faculty behavior, negotiate removal of those features. |
| P5 | Before deploying, articulate the worst-case harm scenario for a student. Define autonomy limits (informational / recommendatory / consequential). Plan automation bias training for all staff who use the tool. Set up a horizon-scanning process so vendor updates trigger governance review. |
| P6 | Before deploying, get the vendor to sign a FERPA-compliant data sharing agreement. Require contractual prohibition on training with student data. Document the complete data inventory (every field collected). Define data deletion timeline for contract end. Secure audit rights in the contract. |
| P7 | Before deploying, implement student-facing AI disclosure at the point of interaction. Build a contestability process students can actually use. Publish a plain-language description of the tool. Add this tool to the institution's public AI inventory. |
| P8 | Before deploying, negotiate: performance SLAs with remedies, data portability on exit, advance notice of model updates, incident reporting timeline. Check FoundationCCC/CollegeBuys for existing contracts. If the vendor blocks audits or imposes punitive exit terms, consider alternatives. |
| P9 | Before deploying this tool, build minimum viable governance: designate a person responsible, create an AI inventory, establish a review cycle. If the institution doesn't have governance capacity, build it first — don't add tools to an ungoverned environment. |

---

## D.4 Output Format Requirements

**Print/download format:**
- "Print" button triggers print CSS
- Clean layout: no navigation chrome, no scroll overflow, proper page breaks between sections
- Header: Tool name, use case, risk tier, institution name (if entered), assessment date
- Sections print in order: Executive Summary → Before You Deploy → Who's Involved → What to Track → Review Cadence → Dependency Governance (Medium/High only) → Decision Rules → Templates → HUMANS (CA only) → Next Steps Checklist
- Footer: "Generated by the AI Governance Navigator — AQL Labs / FutureObjects Research / College Futures Foundation"

**Shareable URL:** Assessment state encoded in URL hash for sharing (without localStorage dependency).

**"Save Your Results":** Saves complete state to localStorage keyed by tool name + timestamp.

**"Edit Your Inputs":** Returns to any previous step. Changes cascade: if risk tier changes, pillar requirements update; if pillar scores change, roadmap regenerates; if dependency answers change, dependency governance section regenerates.

---

# Section E: Navigation Map

## E.1 All Views/Screens

| View # | Name | Purpose |
|--------|------|---------|
| 1 | Landing / Hero | Entry point. Two CTAs, stat strip, how-it-works |
| 2a | Use Case Selector (full path) | Select from 10 Student Services use cases |
| 2b | Archetype Selector (quick path) | Self-select Lightweight / Building / Scaling |
| 3 | Screening (Step 1) | 4-5 screening questions → GO / PAUSE / NO-GO |
| 3b | Dependency Profile (Step 1) | 4 universal dependency questions → Low / Medium / High profile |
| 4 | Pillar Scoring (Step 2) | Per-pillar scoring interface (1-3 per pillar) |
| 4b | No-Go Checklist | 8 yes/no no-go questions after pillar scoring |
| 5 | Governance Profile (Step 2 output) | Summary scorecard + dependency badge with pattern interpretation |
| 6 | Your Roadmap (Steps 3-4 output) | Conditionally assembled roadmap with dependency governance — the key deliverable |
| 7 | About / Methodology | Framework architecture, research base, credits |

## E.2 URL Hash-Based Navigation States

```
#landing                        → View 1
#archetype                      → View 2b
#use-case                       → View 2a
#screening/{use-case-id}        → View 3
#dependency/{use-case-id}       → View 3b
#scoring/{pillar-id}            → View 4
#nogo-check                     → View 4b
#profile                        → View 5
#roadmap                        → View 6
#about                          → View 7
```

State is also encoded in the hash for shareability:
```
#profile?uc=SS-01&tier=3&arch=building&scores=3,2,3,2,2,3,2,2,2&dep=2,1,2,3&ca=1
```
The `dep` parameter encodes the four dependency answers (D1,D2,D3,D4) as comma-separated scores.

## E.3 Two Entry Points and Convergence

```
FULL PATH                               QUICK PATH
=========                               ==========
View 1: Landing                         View 1: Landing
    |                                       |
    | "Start Assessment"                    | "I Know What I Need"
    v                                       v
View 2a: Use Case Selector             View 2b: Archetype Selector
    |                                       |
    | select use case                       | select archetype
    v                                       v
View 3: Screening                       View 2a: Use Case Selector
    |                                       | (archetype stored in state)
    | GO → continues                        | select use case
    | PAUSE → option to continue            v
    | NO-GO → stops here                View 3: Screening (abbreviated)
    v                                       | (fewer questions, archetype-informed)
                                            v
              ┌─────────────────────────────┘
              |
              v
        PATHS CONVERGE HERE
              |
              v
View 3b: Dependency Profile
    |
    | 4 universal questions (D1-D4)
    | dependency score + profile result
    v
View 4: Risk Tier Confirmation
    |
    | auto-assigned, option to override
    v
View 4: Pillar Scoring (Step 2)
    |
    | score each pillar 1-3
    v
View 4b: No-Go Checklist
    |
    | 8 yes/no questions
    v
View 5: Governance Profile
    |
    | review scores + patterns + dependency badge
    | "Generate Your Roadmap"
    v
View 6: Your Roadmap
    |
    | includes dependency governance (Medium/High)
    | print / save / edit / start another
    v
[End / Loop back]
```

**Quick path abbreviation:** When archetype is pre-selected:
- Lightweight: Screening questions simplified (fewer questions, focused on Tier 1/2 concerns)
- Building: Full screening retained
- Scaling: Screening asks whether this is a new tool or annual review of existing tool; if annual review, pre-populates previous scores from localStorage

## E.4 Back/Edit Flow

Users can navigate backward at any point and revise inputs. Changes cascade forward:

| If user changes... | Then... |
|--------------------|---------|
| Use case | Risk tier resets to default. Screening questions change. Dependency answers cleared. Pillar scores cleared. |
| Risk tier (override) | Mandatory/recommended pillar display updates. Existing pillar scores preserved. Dependency profile preserved. |
| Archetype | Display complexity adjusts. Scores preserved. Dependency preserved. Roadmap regenerates. |
| Any dependency answer | Dependency score recalculates. Profile may change. Roadmap dependency governance section regenerates. Pillar scores preserved. |
| Any pillar score | Summary updates. Pattern interpretation recalculates (including dependency-aware patterns). Roadmap regenerates. |
| No-go checklist answer | No-go alerts update. Roadmap regenerates. |
| California toggle | HUMANS mapping shows/hides across scoring and roadmap. |

**"Edit Your Inputs" from View 6 (Roadmap):**
- Dropdown: "Go back to: Use Case / Dependency Profile / Risk Tier / Pillar Scoring / No-Go Checklist"
- User selects destination, edits, then proceeds forward again
- All downstream views regenerate based on new inputs

## E.5 State Object Structure

```javascript
var state = {
  // Entry path
  entryPath: 'full' | 'quick',
  archetype: null | 'lightweight' | 'building' | 'scaling',

  // Step 1: Identify
  useCase: {
    id: 'SS-01',        // or 'SS-XX' for custom
    name: '',
    customDescription: '', // only for SS-XX
    defaultRiskTier: 3
  },
  screeningAnswers: {
    q1: 'response_value',
    q2: 'response_value',
    // ...
  },
  screeningResult: 'go' | 'pause' | 'nogo',
  screeningFlags: [],    // array of flagged concerns

  // Step 1b: Dependency Profile
  dependencyProfile: {
    answers: {
      D1: null,          // 1, 2, or 3
      D2: null,
      D3: null,
      D4: null
    },
    totalScore: null,    // 4-12 (computed from sum of D1-D4)
    profile: null        // 'low' (4-5) | 'medium' (6-8) | 'high' (9-12) (computed)
  },

  // Step 2: Evaluate
  riskTier: 3,           // 1, 2, or 3
  riskTierOverride: false,
  riskTierOverrideReason: '',
  pillarScores: {
    P1: null, P2: null, P3: null, P4: null, P5: null,
    P6: null, P7: null, P8: null, P9: null
  },
  pillarNotes: {
    P1: '', P2: '', P3: '', P4: '', P5: '',
    P6: '', P7: '', P8: '', P9: ''
  },
  noGoFlags: {
    NG01: false, NG02: false, NG03: false, NG04: false,
    NG05: false, NG06: false, NG07: false, NG08: false
  },

  // Metadata
  toolName: '',          // user-entered tool name (e.g., "Nectir")
  isCalifornia: false,
  assessmentDate: '',
  institutionName: '',   // optional

  // Computed (derived, not stored)
  totalScore: 0,
  scoredPillars: 0,
  patterns: [],          // matched interpretation patterns (includes dependency-aware patterns)
  dependencyGovernance: [],  // assembled dependency governance requirements based on profile + tier
  roadmapSections: {}    // assembled roadmap content (includes dependency governance subsection)
};
```

## E.6 LocalStorage Structure

```json
{
  "navigatorV2": {
    "assessments": {
      "{toolName}-{timestamp}": {
        // Full state object from E.5
      }
    },
    "preferences": {
      "isCalifornia": true,
      "archetype": "building",
      "institutionName": "Merced College"
    }
  }
}
```

Preferences persist across assessments. Each assessment is keyed by tool name + ISO timestamp for unique identification and comparison.

---

# Section F: Capability & Dependency Profile System

**Novel governance dimension.** Of 224 frameworks reviewed across 12 global domains, zero include dependency profiling or capability impact assessment. This is what makes the AQL framework unique. The dependency profile answers: **does this tool build capability or replace it?**

## F.1 The Four Questions

These four questions apply to every use case. They are asked after screening questions (Step 1) and before risk tier confirmation (Step 2). They produce a dependency profile — not a gate. The profile is descriptive, not judgmental. High dependency is a finding, not a failure.

### Question D1: Disappearance Test

**"What happens if this tool disappears tomorrow?"**

| Score | Response | What You're Looking For |
|-------|----------|------------------------|
| 1 — Low | Students/staff lose a convenience but can still complete the task | The task can be done without the tool. The tool speeds it up, reduces friction, or improves quality — but the underlying capability remains. Example: a chatbot that answers FAQs; staff can answer the same questions. |
| 2 — Medium | Students/staff would struggle significantly and need time to rebuild | Some processes have been restructured around the tool. Removing it would require rebuilding workflows, retraining staff, or manually replicating what the tool automated. Doable, but disruptive. Example: an early alert system that replaced manual advisor check-ins. |
| 3 — High | Students/staff would be unable to perform the task at all | The tool is the process. Without it, the institution lacks the knowledge, staff, or infrastructure to perform the function. Example: a financial aid triage system that replaced the counselor-driven workflow entirely. |

### Question D2: Capability Trajectory

**"After a year of use, will users be better at this task without the tool, about the same, or less capable?"**

| Score | Response | What You're Looking For |
|-------|----------|------------------------|
| 1 — Capability building | Better — the tool teaches the process or builds transferable skills | Socratic tutoring that builds problem-solving skills. Guided pathways assistant that teaches students to read degree audits. The tool is a scaffold, not a crutch. |
| 2 — Neutral | About the same — the tool handles a task without changing underlying ability | Translation service that handles communications without teaching staff the language. Neither builds nor erodes. |
| 3 — Erosion risk | Less capable — the tool replaces practice or judgment that would otherwise develop | Advisors who stop learning degree requirements because the system handles it. Students who can't navigate FAFSA because the tool always did it for them. |

### Question D3: Navigate-With vs. Navigate-For

**"Does the tool show users how to navigate this process, or does it navigate for them?"**

| Score | Response | What You're Looking For |
|-------|----------|------------------------|
| 1 — Navigate-with | Shows how — walks through steps, builds ability to do it independently | Tool explains why a course is recommended, walks through degree requirements, teaches the student to evaluate options. Transparency by design. |
| 2 — Configurable | Mix — some features explain, some execute, or it depends on configuration | Tool has both guided mode and auto-pilot mode. Faculty or admin can configure which mode is default. Some interactions explain, others just execute. |
| 3 — Navigate-for | Navigates for them — users input need, tool produces outcome directly | Student enters "I need financial aid help" and receives a completed application plan. No visibility into the process, logic, or alternatives. |

### Question D4: Exit Design

**"Is there a point where users are expected to do this without the tool?"**

| Score | Response | What You're Looking For |
|-------|----------|------------------------|
| 1 — Independence designed | Yes — explicit milestone or transition where tool is removed or reduced | After two semesters, students are expected to navigate degree audits independently. Tool use decreases as student progresses. Deliberate fade. |
| 2 — Parallel systems | Not explicitly — but tool supplements rather than replaces existing process | Advisors still do manual advising; the tool is an additional resource. If the tool disappeared, the original process still exists. No formal exit plan, but also no full replacement. |
| 3 — Permanent infrastructure | No — the tool is the process now, no plan for users to perform without it | The institution eliminated the manual process when they deployed the tool. There is no "without the tool" plan. This is permanent infrastructure. |

---

## F.2 Scoring and Profile Bands

**Score calculation:** Sum of D1 + D2 + D3 + D4. Range: 4–12.

| Score Range | Profile | Badge Color | Meaning |
|-------------|---------|-------------|---------|
| 4–5 | **Low Dependency** | Green | Builds or preserves capability. Standard governance. The tool augments human capacity without replacing it. |
| 6–8 | **Medium Dependency** | Yellow | Mixed characteristics. Some capability-building, some replacement. Include capability checks at review points. |
| 9–12 | **High Dependency** | Red | Replaces capability. Not a disqualifier — but requires specific protections. The institution is making a consequential decision about how work gets done. |

**Display:** The profile result is shown immediately after the four questions are answered, before proceeding to risk tier confirmation. Display includes:
- Dependency score (e.g., "8 of 12")
- Profile label and badge (e.g., "Medium Dependency" in yellow)
- One-sentence interpretation (from content JSON)
- "What this means" paragraph (from content JSON)
- Link forward: "Continue to Evaluation →"

---

## F.3 Governance Requirements Per Dependency Profile

### F.3.1 Low Dependency (4–5)

**Additional governance requirements:** None beyond standard. The tool operates in a capability-preserving mode.

**Roadmap additions:** None. Standard review cadence applies.

**Review consideration:** At annual review, re-ask D2 (capability trajectory). If the answer has shifted from "better" or "same" toward "less capable," reassess the dependency profile.

---

### F.3.2 Medium Dependency (6–8)

**Additional governance requirements (3 items):**

1. **Configuration review:** Verify tool is deployed in its most capability-building mode. If the tool has a Socratic/guided mode and an auto-pilot mode, document which is the default and why. Review at 6-month mark.

2. **6-month capability check:** Can users still perform the core task with reduced AI support? Test this — don't assume. Reduce AI availability for a cohort or a period and observe. If users cannot perform, escalate to governance committee.

3. **Alternative maintenance:** Non-AI process must remain documented and periodically tested. If the tool disappeared tomorrow, there is a written process that staff can follow. This process is tested at least annually (walkthrough, not just on paper).

**Roadmap additions:** These three requirements are inserted as a "Dependency Governance" subsection in the roadmap, between "Review Cadence" and "Decision Rules."

---

### F.3.3 High Dependency (9–12)

**Additional governance requirements (4 items, plus Tier 3 conditional):**

1. **Dependency acknowledgment:** Document the decision to deploy a high-dependency tool. Record: who made the decision, the rationale, the alternatives considered, and why dependency is accepted. This becomes part of the governance record. This is not a gate — it is a mirror.

2. **Vendor lock-in assessment:** Evaluate data portability, exit costs, and what happens if the vendor disappears or is acquired. For high-dependency tools, vendor lock-in is institutional vulnerability. Document: Can student data be exported in a standard format? What is the exit timeline? What would replacement cost?

3. **12-month sunset evaluation:** At the 12-month mark, answer: Is the dependency justified by outcomes? Has the dependency widened or narrowed? Are there equity implications — do some student populations experience more dependency than others? Is the cost-benefit still favorable? Document findings and present to governance committee.

4. **Capability impact tracking (Tier 3 only):** For high-risk, high-dependency tools: measure whether staff/advisor capability has declined since deployment. Compare decision quality, advising accuracy, or process knowledge against pre-deployment baseline. If capability has declined significantly, governance committee must decide: accept the dependency, invest in capability rebuilding, or reconsider the tool.

**Roadmap additions:** All four requirements inserted as a "Dependency Governance" subsection. Capability impact tracking appears only when both risk tier = 3 AND dependency profile = High.

---

## F.4 Interaction with Risk Tiers

The dependency profile is orthogonal to the risk tier. A tool can be low-risk and high-dependency, or high-risk and low-dependency. The combination determines governance intensity:

| | Low Dependency (4–5) | Medium Dependency (6–8) | High Dependency (9–12) |
|---|---|---|---|
| **Tier 1 (Low Risk)** | Standard governance | + Configuration review, 6-month capability check, alternative maintenance | + Dependency acknowledgment, vendor lock-in assessment, 12-month sunset evaluation |
| **Tier 2 (Medium Risk)** | Standard governance for tier | + All Medium Dependency requirements | + All High Dependency requirements |
| **Tier 3 (High Risk)** | Standard governance for tier | + All Medium Dependency requirements | + All High Dependency requirements + Capability impact tracking |

**Key design point:** Tier 3 + High Dependency is the maximum governance combination. This is appropriate for tools like early alert systems that both make consequential decisions (high risk) and replace the counselor's independent judgment (high dependency).

**Illustrative examples:**

| Use Case | Likely Risk Tier | Likely Dependency | Why |
|----------|-----------------|-------------------|-----|
| SS-04: FAQ Chatbot | Tier 1 | Low (4–5) | Informational only. Staff can answer the same questions. |
| SS-05: Nectir Tutoring (Socratic mode) | Tier 2 | Low (4–5) | Builds student capability by design. |
| SS-06: Translation Services | Tier 2 | High (9–12) | Permanent infrastructure for Mixtec speakers. Valid and appropriate dependency. |
| SS-01: AI Advising (auto-pathways) | Tier 3 | High (9–12) | Consequential decisions + replaces advisor judgment over time. |
| SS-02: Early Alert (with human follow-up) | Tier 3 | Medium (6–8) | High-stakes flagging but counselors still do the advising. |

---

## F.5 Design Principles

1. **These are not gates.** The four questions produce a profile, not a GO/NO-GO. Profiles incentivize awareness; gates incentivize dishonesty. No institution should feel pressure to game their answers.

2. **"Permanent infrastructure" is valid.** A translation tool for a Mixtec speaker is permanent and appropriate. A financial aid triage system for a resource-constrained college may be permanent and appropriate. The framework respects this. It requires the choice to be conscious, not the choice to be temporary.

3. **"What you're looking for" text legitimizes every answer.** After each question, guidance text explains what each response means and why every option is reasonable. No answer is punished. The user should never feel that they're being judged for selecting "3."

4. **Patterns emerge through use.** After profiling 3–4 tools, leaders will notice: "all our AI tools are navigate-for, not navigate-with." Or: "we haven't designed independence into any of our deployments." That pattern observation is worth more than any individual profile score.

5. **Dependency is not risk.** A high-dependency, low-risk tool (e.g., translation services) requires different governance than a high-risk, low-dependency tool (e.g., a tutoring assistant that builds skills). The framework treats these as independent dimensions that combine, not collapse.

---

## F.6 Voice Guidance for Dependency Profile

The dependency questions should feel like a colleague asking practical questions, not a theorist testing your educational philosophy.

**Section intro text:** "These four questions help you understand whether this tool builds capability or creates dependency. There are no wrong answers — but there are answers you should know before you deploy."

**Per-question framing:** Each question displays a "What you're looking for" block after the response options. This text legitimizes every response:
- For D1 score = 3: "Some tools become essential infrastructure. That's not wrong — but you should know it before you commit."
- For D2 score = 3: "Capability erosion is a real risk with tools that do the thinking. It doesn't mean don't use it — it means track it."
- For D3 score = 3: "Navigate-for tools are efficient. But they also mean users never learn the process. Name that trade-off."
- For D4 score = 3: "Permanent infrastructure is a valid choice. Translation for a Mixtec speaker is permanent and appropriate. What matters is that the choice is conscious."

**Profile result framing:**
- **Low Dependency:** "This tool builds or preserves capability. Standard governance applies."
- **Medium Dependency:** "This tool has mixed characteristics — some capability-building, some replacement. Your roadmap will include capability checks at key review points."
- **High Dependency:** "This tool replaces capability. That's not a failure — but it is a consequential decision that requires specific protections. Your roadmap will include dependency governance requirements."

---

## F.7 Data Model Additions for Dependency Profile

### Content JSON Schema Addition

```json
{
  "dependency_profile": {
    "section_intro": "",
    "questions": [
      {
        "id": "D1",
        "label": "Disappearance Test",
        "question": "",
        "options": [
          { "score": 1, "label": "", "description": "", "what_youre_looking_for": "" },
          { "score": 2, "label": "", "description": "", "what_youre_looking_for": "" },
          { "score": 3, "label": "", "description": "", "what_youre_looking_for": "" }
        ]
      }
    ],
    "profiles": {
      "low": { "label": "", "badge_color": "green", "interpretation": "", "what_this_means": "" },
      "medium": { "label": "", "badge_color": "yellow", "interpretation": "", "what_this_means": "" },
      "high": { "label": "", "badge_color": "red", "interpretation": "", "what_this_means": "" }
    },
    "governance_requirements": {
      "low": [],
      "medium": [
        { "id": "DEP-M1", "requirement": "", "timing": "", "description": "" },
        { "id": "DEP-M2", "requirement": "", "timing": "", "description": "" },
        { "id": "DEP-M3", "requirement": "", "timing": "", "description": "" }
      ],
      "high": [
        { "id": "DEP-H1", "requirement": "", "timing": "", "description": "" },
        { "id": "DEP-H2", "requirement": "", "timing": "", "description": "" },
        { "id": "DEP-H3", "requirement": "", "timing": "", "description": "" },
        { "id": "DEP-H4", "requirement": "", "timing": "", "description": "", "conditional": "tier_3_only" }
      ]
    }
  }
}
```

### State Object Additions

```javascript
// Added to state object (E.5)
dependencyProfile: {
  answers: {
    D1: null, // 1, 2, or 3
    D2: null,
    D3: null,
    D4: null
  },
  totalScore: null,     // 4-12 (computed)
  profile: null         // 'low' | 'medium' | 'high' (computed)
}
```

---

# Appendix: Decision Flags

Items requiring team decision before the builder agent can implement:

| # | Decision Needed | Location | Recommendation |
|---|-----------------|----------|---------------|
| 1 | Should downward risk tier override be allowed? | C.1, B.2 | Allow with mandatory text justification that becomes part of the assessment record |
| 2 | How should no-go criteria #2, #4, #5, #8 be captured? | C.4 | Dedicated "No-Go Checklist" step with 8 yes/no questions after pillar scoring |
| 3 | Should the quick path have abbreviated screening? | E.3 | Yes — Lightweight gets fewer screening questions; Scaling gets "new vs. annual review" fork |
| 4 | How should custom use cases (SS-XX) handle screening? | B.2 | Generic 5-question screening set provided |
| 5 | Should the Governance Profile (View 5) be a separate view or combined with Roadmap? | E.1 | Separate — the profile is the "diagnosis," the roadmap is the "prescription." Users need to absorb the diagnosis before seeing the roadmap. |
| 6 | Student Services Scope Document not found | A.4 | Content gap compensated from scorecard and architecture doc. If the scope doc surfaces, screening questions for SS-06 through SS-10 may need refinement. |
| 7 | Should dependency profile questions appear on the same screen as screening questions or a separate screen? | F.1, E.3 | Separate screen. Screening is use-case-specific; dependency is universal. A visual break signals the shift from "is this viable?" to "what kind of tool is this?" |
| 8 | Should dependency profile be re-scored at annual review? | F.3, A.7 | Yes. Re-ask all four questions at each review cycle. Dependency can shift as institutional reliance deepens or as the tool adds features. |

---

*End of specification. All six sections (A through F) complete.*
