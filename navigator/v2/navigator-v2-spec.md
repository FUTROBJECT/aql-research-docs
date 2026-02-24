# Navigator v2 Specification
## Student Services AI Governance Navigator

**Spec Version:** 1.0
**Date:** February 20, 2026
**Produced by:** Navigator Specification Agent
**Source files read:**
1. `/Users/adammurray/Documents/CLIENTS/AQL/CollegeFutures/aql-research-docs/navigator/index.html` (v1 prototype -- full read)
2. `/Users/adammurray/Documents/CLIENTS/AQL/CollegeFutures/ai-framework-inventory/outputs/student-services-vendor-scorecard.html` (v2 content source -- full read)
3. `/Users/adammurray/Documents/CLIENTS/AQL/CollegeFutures/global-ai-governance-research/outputs/cc-framework-architecture.md` (framework architecture -- full read)
4. `/Users/adammurray/Documents/CLIENTS/AQL/CollegeFutures/aql-research-docs/navigator/wireframe.jsx` (v1 wireframe -- full read)
5. `/Users/adammurray/Library/CloudStorage/GoogleDrive-adamlaserlab@gmail.com/My Drive/Framework_Architecture_Table_StudentServices.docx` -- **UNREADABLE** (binary .docx; tool cannot read). Content gap compensated from vendor scorecard and architecture document.
6. `/Users/adammurray/Documents/CLIENTS/AQL/CollegeFutures/aql-research-docs/cccco-ai-mobilization-framework.html` (HUMANS mapping table -- supplemental read)

---

## 0. Point of View: What "Ethical AI" Means for Community Colleges

This statement frames the entire Navigator. It shapes the tone of all user-facing copy and the logic of the scoring model. Content and builder agents should internalize this before writing or building anything.

**The Core Distinction:** We're not trying to make AI ethical. We're trying to make AI adoption ethical.

The AI is what it is: capable, biased, inconsistent, sometimes brilliant. We don't control that. What we control is the governance structure around how AI enters our institutions, how it touches students, and who gets to decide.

Ethical AI implementation means building the conditions where AI serves educational purposes rather than replacing them, where efficiency gains don't come at the cost of equity, and where institutions strengthen their capacity rather than outsource their judgment. It means students retain the opportunity for genuine self-actualization, not just credential completion.

**Implications for the Navigator:**
- The scorecard evaluates the *adoption*, not the AI itself. Questions are directed at the vendor AND the internal team.
- "Ethical" is defined by 4 criteria (see Section 9): equitable outcomes, responsible data, ethics/safety foundation, multi-year approach.
- The voice never treats AI as inherently good or bad. It treats governance as the variable that determines whether AI adoption is responsible.
- The Navigator's authority comes from specificity: it names the tools, the regulations, the failure modes. It doesn't hedge.

---

## 1. Data Model Overview

### What Changed from v1 to v2

**v1 (Institutional AI Governance Navigator):**
- User answers 10 assessment questions about their institution
- Scoring engine computes: governance tier (1-3), pedagogical level (1-3), 4 priority gaps (from 10 CC-specific gaps), archetype match (4 pilot colleges), recommended templates (from 14)
- Output: institution profile with gap priorities, pillar roadmap, and templates
- Data collections: QUESTIONS (10), GAPS (10), PILLARS (9), TEMPLATES (14), ARCHETYPES (4), ROADMAP (3 tiers)

**v2 (Student Services AI Vendor Scorecard Navigator):**
- User selects a Student Services AI use case they are evaluating
- System auto-assigns a risk tier (High / Medium / Lower) with manual override
- User scores each of the 9 pillars (1-3) guided by pillar-specific questions
- System checks no-go criteria, generates summary scorecard, interprets score patterns, and recommends next steps
- Data collections: USE_CASES (10), RISK_TIERS (3), PILLARS (9 with questions and rubrics), NO_GO_CRITERIA (8), SCORE_PATTERNS (7), ANNUAL_REVIEW (9 areas), ARCHETYPES (3 readiness profiles)

### Core Shift
v1 asks "Where is your institution on the governance spectrum?" and outputs a starting point.
v2 asks "Should we deploy this specific Student Services AI tool?" and outputs a governance assessment.

---

## 2. Nine Pillars -- Complete Data Model

### P1: Purpose & Educational Legitimacy

- **Pillar ID:** P1
- **Color:** `#0066cc`
- **Principle:** Every AI deployment must serve a genuine educational purpose and protect the meaning of credentials. AI use is justified by learning outcomes, not efficiency alone.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 1.1 | What specific student outcome or educational purpose does this tool serve? Can you name it? | A concrete answer tied to learning, completion, transfer, or career readiness -- not "operational efficiency" or "innovation." If the team can't articulate the educational purpose in one sentence, the tool doesn't have one. |
| 1.2 | Does this tool align with the institution's mission and strategic plan? | Connection to stated institutional priorities. Not a solution looking for a problem. Maps to existing student success initiatives. |
| 1.3 | Where on the student journey does this solve a problem? (enrollment, persistence, completion, transfer, career placement) | Clear placement on the guided pathway. The tool addresses a known friction point, not a hypothetical one. Evidence that the problem exists at your institution. |
| 1.4 | Does the tool protect credential integrity? Could AI-generated outputs substitute for competency demonstration? | For tutoring/learning tools: students still demonstrate mastery. For advising: recommendations support informed student choice, not automated credential assembly. For CTE: licensure competency requirements preserved. |
| 1.5 | Has an industry advisory committee or CTE program review validated this tool's relevance? (for CTE-adjacent use cases) | Employer and industry input on whether the tool builds workforce-relevant skills. Alignment with career cluster competencies. |

**Scoring Rubric:**
- **3:** Clear educational purpose tied to student outcomes. Aligned with institutional mission. Mapped to specific student journey stage. Credential integrity preserved. Industry validation where relevant.
- **2:** Educational purpose stated but not evidence-backed. General alignment with mission. Journey placement reasonable but not validated locally. Credential impact not fully assessed.
- **1:** No clear educational purpose -- tool is efficiency-driven or vendor-pushed. No connection to institutional priorities. Credential integrity risk unaddressed.

**Source Citation:** Informed by: IEAIED Req. 1 (achieving educational goals with evidence), ATD Action Area 1 (strategic leadership -- integrating AI into broader goals), SACSCOC/C-RAC (AI use must support quality assurance), Advance CTE (career cluster alignment, Perkins V).

---

### P2: Equity & Differential Impact

- **Pillar ID:** P2
- **Color:** `#28a745`
- **Principle:** AI governance must center equity and account for differential impacts on diverse CC student populations. Drawing on the Kapor Center justice lens, this pillar ensures AI does not create new barriers or reinforce existing ones.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 2.1 | Has this tool been tested with student populations similar to ours? (Pell-eligible, first-gen, working adults, multilingual, students with disabilities) | Vendor can name specific institutions, student demographics, and outcomes. Not just "we serve higher ed." |
| 2.2 | Are error rates, recommendation accuracy, or response quality consistent across student demographics? | Vendor provides disaggregated performance data. If they can't, that's a red flag -- they haven't measured it. |
| 2.3 | Has a differential impact analysis been conducted? Who might be harmed by this tool's errors or limitations? | Vendor or internal team has identified which populations face higher risk from tool errors. Not just "it works for everyone." Specific harm scenarios articulated. |
| 2.4 | Does the tool work effectively for multilingual students? In what languages? Is it real-time or pre-translated? | Actual language coverage and quality, not just "we support translation." Test with your student language mix. |
| 2.5 | Does the tool meet accessibility standards? (WCAG 2.1 AA, screen reader compatibility, keyboard navigation) | Documented accessibility compliance. VPAT or equivalent. Tested with assistive technology users. |
| 2.6 | What is the cost model for students? Are there paywalls, premium tiers, or features that require devices/bandwidth some students lack? | No paywall barriers. Works on mobile. Low bandwidth mode. No premium tier that creates a two-track system. |
| 2.7 | Does the tool serve all career pathways equitably, or is it optimized for specific programs? | CTE pathways covered, not just transfer/STEM. If advising-focused, it should know your full program catalog. |

**Scoring Rubric:**
- **3:** Disaggregated performance data for CC-like populations. Differential impact analysis conducted. Tested with multilingual, first-gen, Pell-eligible students. Accessible. No cost barriers. All pathways covered.
- **2:** Equity acknowledged as priority but data limited. Willing to conduct bias audit post-deployment. Accessibility documented. Cost model reasonable.
- **1:** No disaggregated data. No differential impact analysis. Equity not addressed in product design. Accessibility unclear. Cost barriers exist.

**Source Citation:** Informed by: Kapor Foundation (racial/social justice lens -- centering how AI disproportionately impacts marginalized communities), NAIC (bias definition -- "distortion or error that produces inaccurate results"), OMB M-25-21 (civil rights safeguards for high-impact AI), ASCCC (equity-centered AI policy for CCC).

---

### P3: Human Authority & Decision Accountability

- **Pillar ID:** P3
- **Color:** `#6f42c1`
- **Principle:** Humans -- not algorithms -- make consequential decisions about students. Formal governance structures ensure authority, documentation, and accountability for AI-influenced decisions.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 3.1 | Does this tool make decisions that affect student access, standing, or progress -- or does it recommend to a human who decides? | Clear distinction between AI-as-recommendation and AI-as-decision. If the tool auto-acts (flags a student, changes a pathway, sends an alert), that's a consequential decision even if a human could theoretically override. |
| 3.2 | Can staff override, modify, or reject AI recommendations before they reach students? | Override built into workflow, not buried in admin settings. Staff see the AI recommendation and can approve, edit, or reject before action. |
| 3.3 | For high-risk use cases: is there a defined escalation path when AI output is uncertain, contradictory, or flagged? | Defined thresholds. When confidence is low or the case is edge, the system routes to a human, not a default action. |
| 3.4 | Does the tool create a decision audit trail? Can the institution document who approved what AI-influenced decision? | Logged decisions with timestamps, the AI recommendation, and the human action taken. Supports the "institutional floor, faculty ceiling" model -- clear chain of accountability. |
| 3.5 | Who is accountable when the AI is wrong? Is that defined in the contract? | Clear liability allocation. Not "institution assumes all risk" buried in Terms of Service. Vendor has defined responsibilities for failures in their system. |

**Scoring Rubric:**
- **3:** AI recommends; humans decide. Override built into workflow. Escalation paths defined. Full audit trail. Liability allocated in contract.
- **2:** AI acts with human review possible but not required. Override exists but isn't default. Some audit logging. Liability partially addressed.
- **1:** AI makes consequential decisions autonomously. Override technically possible but impractical. No audit trail. Vendor disclaims all liability.

**Source Citation:** Informed by: OMB M-25-21 (human oversight with intervention safeguards), Singapore Agentic AI (human approval checkpoints; automation bias risk), GAO (human supervision procedures; audit trail), SACSCOC/C-RAC (human judgment central to evaluation).

---

### P4: Student and Faculty Agency

- **Pillar ID:** P4
- **Color:** `#fd7e14`
- **Principle:** Students and faculty are empowered participants in AI governance, not subjects of it. Faculty set academic AI policy; students exercise informed autonomy -- with special provisions for the 70%+ adjunct workforce and adult learner populations.

**Questions -- Student Agency:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 4.1 | Does the tool help students learn to navigate AI, or does it just deliver AI-generated answers? | Skill-building design: Socratic mode, guided problem-solving, "here's how I got this answer." Student learns the process, not just the result. |
| 4.2 | Can students opt out of AI interaction and access a human alternative without penalty or delay? | Real opt-out, not a buried setting. Human alternative is accessible, not a worse experience. Student isn't punished for choosing human support. |
| 4.3 | Does the tool give students visibility into and control over their own data and AI profile? | Students can see what the system "thinks" about them (risk profile, pathway recommendation, engagement score) and contest it. |
| 4.4 | Does the tool recognize prior AI experience that adult learners bring from their workplaces? | Not a one-size-fits-all onboarding. Acknowledges that a 35-year-old returning student may use AI at work daily. Respects adult learner autonomy. |

**Questions -- Faculty Agency:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 4.5 | Can faculty configure, restrict, or turn off AI features for their courses and advisees? | Granular faculty control. Not admin-only settings. Faculty set AI behavior (Socratic mode, answer restrictions, knowledge scope) per course or section. |
| 4.6 | Does the vendor provide training that is accessible to adjunct/part-time faculty? (async, under 30 minutes, no cost) | Training included in contract. Async options that fit adjunct schedules. Not a full-day PD event that part-timers can't attend. Compensated governance participation addressed. |
| 4.7 | Does the tool evaluate, score, or surveil faculty performance? | Faculty are users and configurers, not subjects. If the tool reports on "faculty adoption rates," understand who sees that and how it's used. Faculty are not being measured by a vendor. |
| 4.8 | Does the tool's deployment plan respect the collegial consultation process and shared governance? | Academic senate consulted before institution-wide deployment. Not a top-down IT rollout. Faculty governance has input on student-facing AI. |

**Scoring Rubric:**
- **3:** Skill-building design for students. Real opt-out with human alternative. Adult learner autonomy respected. Granular faculty configuration. Adjunct-accessible training included. No faculty surveillance. Shared governance respected.
- **2:** Some skill-building features. Opt-out exists. Faculty configuration available. Training provided but not adjunct-optimized. Feedback mechanism exists.
- **1:** Pure output delivery. No meaningful opt-out. Admin-only configuration. No adjunct provisions. Faculty performance tracked. Top-down deployment assumed.

**Source Citation:** Informed by: ASCCC (faculty primacy under Title 5 "10+1"), ATD Action Areas 4-5 (staff capability and faculty engagement), IEAIED Req. 5 (learner autonomy), Oregon State Bloom's Taxonomy (human skills), UNESCO Student/Teacher Competency Frameworks, ATD (AI agility).

---

### P5: Risk Proportionality & Harm Mitigation

- **Pillar ID:** P5
- **Color:** `#dc3545`
- **Principle:** Governance intensity matches risk level. Low-impact AI gets lightweight review; high-impact AI (agentic systems, consequential decisions) gets full governance -- with harm mitigation built into every deployment.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 5.1 | Has the tool been classified by risk tier (high / medium / lower) based on the use case table above? Does the governance intensity match? | Risk tier is documented and agreed upon. High-risk tools get full governance; lower-risk tools get lightweight review. Not every tool gets the same treatment -- and not every tool gets a pass. |
| 5.2 | What are the autonomy limits? Is this tool informational (provides data), recommendatory (suggests actions), or consequential (takes/triggers actions)? | Clear classification. Informational = lowest governance. Recommendatory = moderate (human reviews before acting). Consequential = highest (human must approve before action). |
| 5.3 | If this is an agentic AI system (acts autonomously, chains decisions, accesses multiple data sources), what bounds are placed on its autonomy? | Whitelisted actions only. Logging of all tool usage. Unique agent identity linked to supervising entity. Anomaly detection. Threshold-based alerting. No unbounded autonomous action. |
| 5.4 | What is the harm scenario? If this tool fails, what is the worst realistic outcome for a student? | Team has articulated the worst case: wrong transfer pathway, missed financial aid deadline, false early alert flag, incorrect basic needs referral. Severity is named and mitigation planned. |
| 5.5 | Are staff trained on automation bias -- the risk of over-trusting AI recommendations because the system "usually works"? | Training that addresses the specific danger of reliable systems: when AI is right 95% of the time, humans stop checking. Plan for maintaining critical review even when the tool performs well. |
| 5.6 | Is there a process for emerging technology review? How will the institution reassess risk if the vendor adds agentic capabilities or new AI features? | Horizon scanning process. Vendor updates trigger risk reassessment. New capabilities don't auto-deploy -- they go through governance review. |

**Scoring Rubric:**
- **3:** Risk tier documented. Autonomy limits defined. Agentic bounds in place (if applicable). Harm scenarios articulated with mitigation plans. Automation bias training planned. Emerging tech review process exists.
- **2:** Risk tier acknowledged. Some autonomy limits. Harm scenarios partially explored. Training planned. No formal emerging tech review process.
- **1:** No risk classification. No autonomy limits. Harm scenarios not considered. No automation bias awareness. Vendor features auto-deploy without review.

**Source Citation:** Informed by: Singapore Agentic AI Framework (autonomy bounding, automation bias, agent identity, checkpoint approach), NIST AI 600-1 (12-risk taxonomy, human-AI configuration), OMB M-25-21 (high-impact AI definition, minimum risk practices), HEAT-AI (EU AI Act risk tiers adapted for higher ed), GAO (performance monitoring, model drift detection).

---

### P6: Data Stewardship & System Integrity

- **Pillar ID:** P6
- **Color:** `#17a2b8`
- **Principle:** Student data is a public trust. AI systems must meet data stewardship standards that protect privacy, ensure integrity, and maintain institutional control over how data is used.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 6.1 | What student data does this tool collect, access, or generate? Provide a complete data inventory. | Specific data fields, not categories. "Student engagement data" isn't enough -- what exactly? Clicks, time on page, login frequency, assignment submissions, chat transcripts? |
| 6.2 | Is any student data used to train or improve the vendor's AI models? | Explicit contractual commitment: no training on student data without consent. In writing, not just in marketing. |
| 6.3 | What happens to student data when the contract ends? Retention, deletion, and portability terms? | Defined deletion timeline. Data export in standard format. No vendor retention after contract. No "we keep anonymized data" loopholes. |
| 6.4 | Is the tool FERPA compliant? Does the vendor sign a FERPA-compliant data sharing agreement? | Written FERPA compliance. Data sharing agreement defining vendor as "school official" with legitimate educational interest. Not just a checkbox. |
| 6.5 | What is the data provenance for the AI's training data? Was it collected ethically and with appropriate consent? | Vendor describes training data sources. No scraping of student data without consent. Public datasets assessed for bias. |
| 6.6 | How does the tool handle data quality issues? (incomplete records, outdated SIS data, transfer students with partial records) | Graceful handling of messy real-world CC data. Flags low-confidence recommendations rather than guessing. Doesn't hallucinate when data is incomplete. |
| 6.7 | Does the tool integrate with existing institutional systems (SIS, LMS, CRM) through secure, documented protocols? | Standard integration methods (API, LTI, SAML/SSO). No shadow data stores. Data flows documented and auditable. Aligned with CCCCO Data Governance Advisory Workgroup standards where applicable. |
| 6.8 | Does the institution retain the right to audit the vendor's data practices? | Contractual audit rights. Not blocked by "trade secret" or IP claims. Institution can inspect how student data is processed and stored. |

**Scoring Rubric:**
- **3:** Complete data inventory provided. No training on student data (contractual). Defined deletion/portability. FERPA agreement signed. Training data provenance documented. Secure system integration. Audit rights in contract.
- **2:** Data inventory available on request. Training opt-out available. FERPA compliant. Some provenance documentation. Integration functional. Audit possible but not contractual.
- **1:** Data practices vague. Student data may train models. No clear deletion terms. FERPA claimed but undocumented. No audit rights. Integration undocumented or insecure.

**Source Citation:** Informed by: IEEE P7004 (data lifecycle: access, collect, store, use, share, destroy), NAIC (audit rights over vendor data; insurer responsible regardless of build/buy), NIST 600-1 (data privacy; training data provenance), GAO Principle 2 (data quality, reliability, representativeness), Alabama Template (vendor contract requirements).

---

### P7: Transparency & Contestability

- **Pillar ID:** P7
- **Color:** `#e83e8c`
- **Principle:** Students and faculty have the right to know when AI influences decisions that affect them -- and the right to contest those decisions through meaningful processes.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 7.1 | Is it clear to students when they are interacting with AI vs. a human? | Visible, plain-language disclosure at point of interaction. Not a privacy policy link. The student knows *in the moment* that this is AI. |
| 7.2 | Can students understand *why* the AI gave a particular recommendation? (e.g., "we recommended this pathway because...") | Explainability at student-appropriate level. Not a technical model explanation -- a reason a first-gen student can understand and question. |
| 7.3 | Does the vendor disclose what data the AI uses to generate recommendations for a given student? | Student can see (or request to see) what data about them informed the AI output. Aligns with FERPA right of access. |
| 7.4 | Does the system support an appeals/contestability process for students affected by AI-influenced decisions? | Students can contest an AI-influenced recommendation through a meaningful process -- not just a complaint form. Right to human review of any AI-influenced consequential decision. Clear escalation pathway. |
| 7.5 | Is there documentation of how the AI model works that is accessible to non-technical staff? | Plain-language system documentation. Advisors and student services staff can explain the tool to students. |
| 7.6 | Does the vendor provide a "model card" or equivalent -- a summary of what the AI does, its limitations, and known failure modes? | Standardized reporting on capability, limitations, and known biases. Published, not just available on request. |
| 7.7 | Does the institution publicly disclose which AI systems are in use for Student Services? | Internal team question: Is there a public-facing list of AI tools used in student-facing processes? Students and community can see what AI is operating. |

**Scoring Rubric:**
- **3:** Clear student-facing disclosure. Explainable recommendations. Data sources visible. Meaningful appeals/contestability process. Plain-language documentation. Model card published. Public AI inventory.
- **2:** Disclosure present but not prominent. Some explainability. Appeals possible through existing institutional processes. Documentation technical. Model card available on request.
- **1:** No disclosure to students. AI operates invisibly. No explainability. No appeals pathway. No documentation. No model card. No public disclosure of AI use.

**Source Citation:** Informed by: NAIC (consumer notification when AI in use), CHAI (Model Cards / "nutrition labels"), NIST 600-1 (content provenance), IEAIED Req. 7-8 (transparency and informed participation), ASCCC (transparent and widely communicated policies), OMB M-25-21 (public AI use case inventory; appeals and remedies).

---

### P8: Vendor Accountability & Institutional Sovereignty

- **Pillar ID:** P8
- **Color:** `#6610f2`
- **Principle:** CCs are buyers, not builders, of AI. Vendor relationships must protect institutional sovereignty, ensure accountability, and leverage collective bargaining power across the system.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 8.1 | Does the contract include performance benchmarks and what happens if the vendor doesn't meet them? | Defined SLAs for uptime, accuracy, response time. Remedies for non-performance (credit, exit clause). Not just "best efforts." |
| 8.2 | What is the exit strategy? Can the institution leave without losing data, disrupting student services, or paying punitive fees? | Reasonable exit terms. Data portability in standard formats. Transition support. No lock-in through proprietary data formats or integrations. |
| 8.3 | Can the institution conduct or require independent bias audits of the tool? | Vendor supports third-party audits. Provides access to necessary data and system information. Doesn't block audits with IP claims. |
| 8.4 | How does the vendor handle model updates? Does the institution get advance notice and the ability to test before updates go live? | Update notification in advance. Staging/testing environment. Institution can delay updates. No silent model changes. |
| 8.5 | Is this tool available through FoundationCCC/CollegeBuys or other consortium contracts? Has the CCC system already negotiated terms? | Consortium pricing and terms leveraged where available. If not, institution negotiates with awareness of system-wide contracts. Collective bargaining power is used, not ignored. |
| 8.6 | Does the vendor have an incident response process? How are AI failures, errors, or breaches reported and resolved? | Defined incident reporting timeline. Notification to institution (not just vendor's legal team). Root cause analysis. Corrective action plan. |
| 8.7 | What does total cost of ownership look like over 3 years? (licensing, integration, training, maintenance, scaling) | Transparent pricing. No hidden fees. Integration costs upfront. Scaling costs predictable. Training included or costed separately. |

**Scoring Rubric:**
- **3:** Performance SLAs with remedies. Clean exit terms with data portability. Independent audits supported. Advance update notification. Consortium terms leveraged. Incident response defined. Transparent total cost.
- **2:** Some performance terms. Exit possible with reasonable effort. Audits considered on request. Updates communicated. Consortium not explored. Incident reporting exists. Cost mostly transparent.
- **1:** No performance guarantees. Punitive exit terms or data lock-in. Audits blocked. Silent updates. No consortium awareness. No incident process. Hidden costs.

**Source Citation:** Informed by: NAIC (written AIS program; third-party vendor accountability; audit rights; insurer responsible regardless of build/buy), GAO (auditor access rights protected against vendor IP), NIST 600-1 (incident disclosure), IEAIED (procurement checklist), SREB (total cost of ownership; exit strategy), NACUBO/E&I Cooperative (consortium procurement; Cal State shared services).

---

### P9: Institutional Capacity & Continuous Governance

- **Pillar ID:** P9
- **Color:** `#795548`
- **Principle:** Governance must be achievable at every institutional scale. Tiered implementation ensures resource-constrained colleges can begin with minimum viable governance and grow over time.

**Questions:**

| # | Question | What You're Looking For |
|---|----------|----------------------|
| 9.1 | Does the institution have a governance structure (committee, designated person, review process) that can oversee this tool? | Doesn't need to be a full AI committee for a lower-risk tool. But someone is named, a review cycle exists, and there's a process for decisions. Minimum viable governance is in place. |
| 9.2 | Will this tool be included in the institution's annual AI inventory? | The institution maintains (or will create) an inventory of AI tools in use, their risk tiers, and their scorecard results. This tool will be on it. |
| 9.3 | Is there a plan to rescore this tool on a regular cycle? | Annual for high-risk tools. Every two years for medium/lower. Trigger-based if vendor changes, incidents occur, or new capabilities are added. |
| 9.4 | Does the tool generate reporting that supports accreditation documentation? | Usage data, outcome data, and governance documentation exportable in formats useful for accreditation self-studies and compliance reports. |
| 9.5 | Does the institution have the staff capacity to implement and sustain this tool? (training, monitoring, override review, student support) | Honest capacity assessment. A tool that requires 10 hours/week of advisor review isn't viable for a college with 2 advisors. Implementation plan matches real institutional resources. |
| 9.6 | Are there shared resources from consortia, the Chancellor's Office, or peer institutions that can support governance of this tool? | Institution isn't reinventing governance alone. Using shared templates, participating in peer learning, leveraging system-wide resources where available. |

**Scoring Rubric:**
- **3:** Governance structure in place. AI inventory maintained. Regular rescore cycle planned. Accreditation-ready reporting. Capacity assessed honestly. Shared resources leveraged.
- **2:** Some governance exists. Inventory planned. Rescoring acknowledged but not scheduled. Accreditation alignment partial. Capacity concerns identified. Aware of shared resources.
- **1:** No governance structure. No inventory. No review cycle. No accreditation planning. Capacity not assessed. Operating in isolation.

**Source Citation:** Informed by: SACSCOC/C-RAC (documentation for accreditation), EDUCAUSE (four-level policy framework; "digital AI divide" for resource-constrained institutions), CHAI (tiered playbooks by organization size), WCET (cooperative model; "framework fog"), ATD (network-based implementation support), Local Government AI Handbook (resource-constrained governance model), OMB M-25-21 (annual AI use case inventory).

---

## 3. Student Services Use Cases

Extracted from the vendor scorecard risk tier table. These are the 10 Student Services AI use cases with default risk tiers.

| # | Use Case | Default Tier | Key Risk Factor |
|---|----------|-------------|-----------------|
| 1 | Advising / guided pathways AI | **High** | Recommendations affect student trajectory; errors compound |
| 2 | Financial aid AI | **High** | Automated decisions on access to resources |
| 3 | Early alert / predictive analytics | **High** | Risk profiling; disparate impact; surveillance potential |
| 4 | Placement / prerequisite AI | **High** | Determines course access; equity implications |
| 5 | AI tutoring (e.g., Nectir) | **Medium** | Faculty configuration matters; hallucination risk; Socratic vs. answer mode |
| 6 | Student journey analytics | **Medium** | PII; aggregation vs. individual tracking; who has access |
| 7 | Career services AI | **Medium** | Pathway bias; equity across career clusters |
| 8 | Basic needs matching | **Medium** | Sensitive data (food insecurity, housing); stigma risk |
| 9 | FAQ chatbot / digital front door | **Lower** | Accuracy; escalation path; multilingual coverage |
| 10 | Translation of public materials | **Lower** | Quality across languages; cultural appropriateness |

**Tool examples named in the scorecard:**
- AI tutoring: Nectir (explicitly named)
- Other tools are referenced by category, not brand name

---

## 4. Risk Tier System

### Three Tiers

#### High Risk
- **Color:** `#c00` (text), `#f8d7da` (background)
- **Definition:** AI makes or materially influences decisions affecting student access, standing, or progress.
- **Examples:** Financial aid eligibility, early alert/risk flags, academic standing, placement, advising recommendations on transfer pathways.
- **Governance intensity:**
  - All 9 pillars must be scored.
  - Any pillar scoring 1 requires a documented mitigation plan or no-go decision.
  - Human-in-the-loop required.
  - Appeals process required.
  - Bias audit required before deployment and annually.

#### Medium Risk
- **Color:** `#ffc107` (border), `#856404` (text), `#fff3cd` (background)
- **Definition:** AI interacts directly with students or handles student data but doesn't make consequential decisions.
- **Examples:** AI tutoring (Nectir), student journey analytics, career services (resume, interview prep), basic needs matching.
- **Governance intensity:**
  - All 9 pillars scored.
  - Pillars 2 (Equity) and 6 (Data Stewardship) must score 2 or higher.
  - Faculty/staff configuration and override required.

#### Lower Risk
- **Color:** `#28a745` (border/text), `#d4edda` (background)
- **Definition:** AI handles general information, doesn't use individual student data, and has clear escalation to humans.
- **Examples:** FAQ chatbot, digital front door/wayfinding, translation of public materials, IT helpdesk.
- **Governance intensity:**
  - Score Pillars 1 (Purpose), 2 (Equity), 6 (Data Stewardship), 7 (Transparency), and 8 (Vendor Accountability) at minimum.
  - Other pillars recommended but not required.

### Risk Tier Source Citation
Risk tier approach adapted from: OMB M-25-21 (education as high-impact AI), NIST AI 600-1 (GenAI risk profile), HEAT-AI (higher ed risk classification from EU AI Act), Singapore Agentic AI Framework (task sensitivity / data criticality / action reversibility).

---

## 5. No-Go Criteria

Regardless of total score, the following 8 conditions should stop procurement:

| # | Condition | Pillar | Why |
|---|-----------|--------|-----|
| 1 | No clear educational purpose -- tool is efficiency-driven or vendor-pushed without connection to student outcomes | P1: Purpose | If it doesn't serve education, it doesn't belong in Student Services |
| 2 | Vendor uses student data to train AI models and will not contractually commit otherwise | P6: Data Stewardship | Students are not training data |
| 3 | No human override possible for consequential decisions (financial aid, placement, academic standing) | P3: Human Authority | Violates OMB high-impact AI requirements and accreditation expectations |
| 4 | Vendor blocks independent bias audits or claims IP protection over audit access | P8: Vendor Accountability | GAO: "independent verification is the only way to verify AI is not biased" |
| 5 | No FERPA-compliant data sharing agreement | P6: Data Stewardship | Legal requirement, not optional |
| 6 | No way for students to know AI is being used in their interaction | P7: Transparency | Students have a right to know |
| 7 | No contestability pathway -- students cannot appeal AI-influenced decisions | P7: Transparency & Contestability | Decisions without recourse are not governance |
| 8 | Exit terms require forfeiting student data or impose punitive switching costs | P8: Vendor Accountability | Vendor lock-in undermines institutional sovereignty |

**Implementation note:** These are absolute. If any no-go criterion is triggered, the assessment should display a red banner alert immediately, regardless of what the total pillar scores are. The no-go check should run after all pillar scoring is complete.

---

## 6. Score Pattern Interpretation

The total score (out of 27) is less important than the *pattern*. The following interpretation table is extracted from the vendor scorecard:

| Pattern | What It Means | Action Implication |
|---------|--------------|-------------------|
| **Any pillar = 1 on a High-Risk tool** | Do not deploy without a documented mitigation plan approved by governance committee. A score of 1 on Pillars 2, 3, or 5 for a high-risk tool (advising, financial aid, early alerts) should be treated as a no-go unless mitigations are substantial. | No-go or documented mitigation |
| **Pillar 1 = 1** | Stop. If you can't articulate the educational purpose, don't buy it. This is the threshold question. | No-go |
| **Multiple pillars = 2** | Proceed with conditions. Document what the institution will do to compensate for vendor gaps (e.g., add disclosure process, conduct own bias audit, provide faculty training the vendor doesn't). | Proceed with conditions |
| **All pillars = 2 or 3** | Proceed with standard governance. Include in annual AI inventory. Monitor per risk tier schedule. | Proceed |
| **Strong on P6 & P8 (data, vendor) but weak on P4 & P7 (agency, transparency)** | Common pattern. Vendor is technically sound but product wasn't designed with students as participants. Institution must add the student-facing layer (disclosure, opt-out, skill-building) the vendor doesn't provide. | Institutional supplementation needed |
| **Strong on P4 & P7 (agency, transparency) but weak on P6 (data)** | Vendor markets well but hasn't done the data governance work. Attractive front end, uncertain foundation. | Data governance investigation needed |
| **Pillar 9 = 1** | Not necessarily about the vendor -- it's about institutional readiness. Consider whether the institution needs to build governance capacity before deploying this tool, not after. | Build governance capacity first |

---

## 7. Annual Review Checklist

Once deployed, rescore each tool on a regular cycle: annually for high-risk, every 2 years for medium/lower. The 9 review areas:

| # | Review Area | Pillar(s) | Review Questions |
|---|-------------|-----------|-----------------|
| 1 | Educational outcomes | P1 | Is the tool still serving its stated educational purpose? Has the student outcome improved? Is it still aligned with institutional priorities? |
| 2 | Equity outcomes | P2 | Are usage rates and outcomes equitable across student cohorts? Demographic-disaggregated review conducted? Any cohort underserved or disproportionately flagged? |
| 3 | Decision quality | P3 | What is the override rate? Are staff using overrides frequently (signal of AI quality issues)? Any decision accountability failures? |
| 4 | Student/faculty experience | P4 | What do students report? Satisfaction, confusion, avoidance, trust? Is faculty finding the tool helpful or burdensome? Adjunct access working? |
| 5 | Risk reassessment | P5 | Has the vendor added new capabilities or agentic features? Should the risk tier be updated? Any near-miss incidents? |
| 6 | Data practices | P6 | Any changes to vendor data practices? Data quality issues surfaced? Privacy audit results? |
| 7 | Incidents & appeals | P7 | Were there AI failures, errors, or complaints? How were they resolved? Complaint/appeal volume? Any contestability process breakdowns? |
| 8 | Vendor performance | P8 | Are SLAs being met? Has the vendor been acquired or changed ownership? Cost tracking to projection? Exit still feasible? |
| 9 | Governance health | P9 | Is the governance structure still functioning? AI inventory current? Are shared resources being leveraged? Is the institution ready for the next tier of maturity? |

---

## 8. CCCCO HUMANS Framework Mapping

This mapping is a California-specific overlay. It should be visible when a user indicates they are a California community college. Extracted from the CCCCO AI Mobilization Framework analysis document.

| HUMANS Letter | CCCCO Principle | Primary AQL Pillar(s) | Relationship |
|---------------|----------------|----------------------|-------------|
| **H** | Human-Centered Approach | **P3: Human Authority & Decision Accountability**, P4: Student and Faculty Agency | HUMANS "H" establishes the principle; P3 operationalizes it with governance structures ensuring humans -- not algorithms -- make consequential decisions. P4 extends it to faculty pedagogical authority and student participation. AB 2370 provides legislative floor. |
| **U** | Universal Support | **P2: Equity & Differential Impact**, P4: Student and Faculty Agency | Opt-out rights and equitable access align with the Equity pillar's differential impact analysis. P4 extends "universal" to faculty agency (including 70%+ adjunct workforce) and adult learner autonomy. |
| **M** | Managed Privacy Controls | **P6: Data Stewardship & System Integrity** | User agency over data aligns directly. P6 extends to data lifecycle requirements, institutional data sovereignty, CCCCO DGAW alignment, and incident response protocols. |
| **A** | Algorithmic Discrimination | **P2: Equity & Differential Impact**, P5: Risk Proportionality & Harm Mitigation | Direct alignment. HUMANS requires remediation; P2 adds disaggregated outcome measurement, bias audits, and differential impact analysis. P5 adds risk-proportionate governance ensuring high-impact AI receives rigorous oversight. |
| **N** | Notice & Explanation | **P7: Transparency & Contestability** | Direct alignment. P7 adds classroom-level disclosure, public-facing governance documentation, meaningful explanation of AI outputs, and the right to contest AI-influenced decisions through accessible processes. |
| **S** | Safety & Security | **P8: Vendor Accountability & Institutional Sovereignty**, P9: Institutional Capacity & Continuous Governance | Safety aligns with vendor accountability (P8: evaluation checklists, audit rights, contract addenda) and institutional capacity (P9: governance reporting, tiered implementation, progressive maturity). P5 (Risk Proportionality) also contributes through incident escalation and harm mitigation protocols. |

**Display logic:** Show this mapping as an optional overlay/toggle when the user identifies their institution as a California Community College. This provides system-specific compliance context without cluttering the experience for non-CA users.

---

## 9. Four Criteria for Ethical AI Implementation

These are the portable ethical criteria. They apply to any community college, not just California CCs. AI implementation is ethical when it meets all four. They are the lens through which all 9 pillars are applied.

### Criterion 1: It advances equitable student outcomes.
First, the AI use must serve a genuine educational purpose — not just an operational one. Then the question becomes: does it serve that purpose equitably? Not outcomes in general — equitable outcomes. AI that improves aggregate completion rates while widening equity gaps is not ethical implementation. AI that serves some career pathways while neglecting others is not ethical implementation. The question isn't "does this work?" but "does this work for the students community colleges exist to serve?"

**Drives:** P2 (Equity & Differential Impact). Shapes how all other pillars are applied.

### Criterion 2: It rests on quality data governed responsibly.
AI systems are only as good as the data underneath them. Institutions using AI without understanding their data — its gaps, its biases, its limitations — are building on sand. Ethical implementation requires data stewardship: knowing what you have, protecting what's sensitive, and being honest about what your data can and cannot support.

**Drives:** P6 (Data Stewardship & System Integrity).

### Criterion 3: It operates within a foundation of ethics and safety.
This means human authority over high-stakes decisions. It means transparency about when AI is used and how. It means students and faculty have rights that don't disappear because a vendor promises efficiency. Safety isn't a feature request. It's a precondition that should be calibrated to the stakes. Higher-stakes uses require more transparency and more paths for challenge.

**Drives:** P3 (Human Authority & Decision Accountability), P7 (Transparency & Contestability), P4 (Student and Faculty Agency).

### Criterion 4: It reflects a thoughtful, multi-year approach.
Ethical implementation isn't a policy memo or a one-time training. It's governance that evolves as AI evolves, that learns from implementation, that builds institutional capacity over time. Rushing to adopt without structures to sustain is not ethical — it's reckless with other people's futures. It's not that institutions should slow down — it's that governance structures enable faster, more confident adoption rather than creating drag. Speed through structure, not speed despite it. It's about schools keeping sovereignty over their AI decisions rather than giving it away to vendors through opaque contracts or platform lock-in.

**Drives:** P9 (Institutional Capacity & Continuous Governance).

### Criteria → Pillar Mapping Summary

| Criterion | Primary Pillar(s) | Role |
|-----------|-------------------|------|
| 1. Equitable student outcomes | P2 (Equity) | Shapes how all pillars are applied |
| 2. Quality data, governed responsibly | P6 (Data Stewardship) | Foundation layer — AI is only as good as its data |
| 3. Ethics and safety foundation | P3 (Human Authority), P7 (Transparency), P4 (Agency) | Precondition, calibrated to stakes |
| 4. Thoughtful, multi-year approach | P9 (Institutional Capacity) | Sovereignty and sustainability |

**Note:** Pillars P1 (Purpose), P5 (Risk), and P8 (Vendor Accountability) serve all four criteria — they are the operational pillars that execute the ethical criteria across every evaluation.

---

## 10. Quick-Start Archetypes

v2 replaces the 4 college-specific archetypes (Merced/MiraCosta/LBCC/Calbright) with 3 institutional readiness profiles. These are not tied to specific pilot colleges but to governance maturity stages.

### Archetype 1: Lightweight

- **Label:** Lightweight
- **Description:** No formal AI governance yet. First tool evaluation. Need the minimum viable process.
- **Who this is for:** Small or mid-size colleges evaluating their first Student Services AI tool. No AI governance committee. Limited staff capacity.
- **Pre-configuration:**
  - Auto-selects lower-risk use cases as default starting point
  - Focuses scoring on the 5 mandatory lower-risk pillars: P1 (Purpose), P2 (Equity), P6 (Data Stewardship), P7 (Transparency), P8 (Vendor Accountability)
  - Other pillars available but flagged as "recommended, not required for your risk tier"
  - Simplified guidance text (shorter "what you're looking for" descriptions)
  - Annual review checklist shows minimum items only

### Archetype 2: Building

- **Label:** Building
- **Description:** Some governance exists. Evaluating medium- or high-risk tools. Need the full scorecard with guidance.
- **Who this is for:** Colleges with an existing AI committee or task force. Deploying AI tutoring, advising, or analytics tools. Need comprehensive evaluation.
- **Pre-configuration:**
  - All 9 pillars active, all questions visible
  - Full scoring rubrics and "what you're looking for" guidance displayed
  - No-go criteria prominently displayed
  - Risk tier assignment shown with full governance intensity requirements
  - Annual review checklist complete

### Archetype 3: Scaling

- **Label:** Scaling
- **Description:** Mature governance. Multiple tools deployed. Need the annual review cycle and pattern analysis.
- **Who this is for:** Colleges with comprehensive AI governance programs. Multiple AI tools already deployed. Need to rescore existing tools, compare across tools, and manage the portfolio.
- **Pre-configuration:**
  - Annual review mode as primary entry point (instead of new tool evaluation)
  - Comparative scoring across multiple saved tool assessments
  - Pattern analysis across the tool portfolio (e.g., "all your tools score low on P4")
  - Pre-populated with previous scores from localStorage (if available)
  - Export/report generation for governance committee and accreditation

---

## 11. Assessment Flow

Step-by-step user journey through Navigator v2:

### Step 1: Landing
- **Content:** Hero section (dark background, headline, subhead), stat strip, "How to use this scorecard" guidance, 3 archetype quick-start cards (Lightweight / Building / Scaling)
- **User actions:** Click "Start Evaluation" (begins flow), click archetype card (pre-configures flow), or click "Explore Scorecard" (read-only reference mode)
- **Design carry-forward from v1:** Dark hero, card-based UI, FO Research branding, stat strip pattern

### Step 2: Use Case Selection
- **Content:** List/grid of the 10 Student Services use cases (from Section 3). Each shows: use case name, default risk tier badge (color-coded), key risk factor.
- **User actions:** Select the use case they are evaluating. Also provide a text field for "Tool Name" (e.g., "Nectir," "EAB Navigate," etc.) -- this becomes the assessment key.
- **Output:** Selected use case and tool name stored in state.

### Step 3: Risk Tier Assignment
- **Content:** Show the auto-assigned risk tier based on the selected use case. Display tier definition, governance intensity requirements, and examples.
- **User actions:** Accept the default tier OR manually override to a different tier (with an explanation prompt for why they are overriding). Override should only be possible upward (Lower to Medium, Medium to High), not downward, without a governance justification.
- **Output:** Final risk tier stored in state. Determines which pillars are mandatory.

[DECISION NEEDED] Should users be allowed to override the tier downward (e.g., High to Medium)? The scorecard does not explicitly address downward override. Recommendation: allow downward override only with a mandatory text justification that becomes part of the assessment record.

### Step 4: Pillar Scoring
- **Content:** For each pillar (or required subset based on risk tier):
  - Pillar header with ID, name, and color
  - Principle statement (italic)
  - All questions with "what you're looking for" guidance (read-only reference, not individually scored)
  - Scoring rubric: 3 (what good looks like), 2 (partial), 1 (what bad looks like)
  - Score selector: user picks 1, 2, or 3 for the pillar as a whole
  - Optional notes field for each pillar
- **Important:** Questions guide the pillar-level score. Users do NOT score each question individually -- they read the questions, evaluate, and then give the pillar a single 1-3 score.
- **Navigation:** Next Pillar / Previous Pillar buttons. Progress bar shows pillar count (e.g., "Pillar 3 of 9").
- **For lower-risk tools:** Non-mandatory pillars show as "Recommended" with a visual distinction (e.g., lighter styling, collapsible) but can be skipped.

### Step 5: No-Go Check
- **Content:** After all pillar scoring is complete, the system checks all 8 no-go criteria against the assessment data.
- **Trigger logic:**
  - No-go #1: P1 score = 1
  - No-go #2: Requires explicit question (added to P6 scoring or as a standalone check) -- "Does the vendor use student data to train AI models?"
  - No-go #3: P3 score = 1 AND risk tier = High
  - No-go #4: Requires explicit question (added to P8 scoring or standalone) -- "Does the vendor block independent bias audits?"
  - No-go #5: Requires explicit question (added to P6 scoring or standalone) -- "Is there a FERPA-compliant data sharing agreement?"
  - No-go #6: P7 score = 1 (covers student disclosure)
  - No-go #7: P7 score = 1 (covers contestability)
  - No-go #8: Requires explicit question (added to P8 scoring or standalone) -- "Do exit terms require forfeiting student data?"

[DECISION NEEDED] No-go criteria #2, #4, #5, and #8 require yes/no questions that go beyond the 1-3 pillar scores. Options: (a) add standalone yes/no no-go checkboxes after pillar scoring, (b) infer from pillar scores (less precise), or (c) embed as specific sub-questions within the relevant pillars. Recommendation: add a dedicated "No-Go Checklist" step between pillar scoring and summary, with 8 yes/no questions mapping directly to the 8 criteria.

- **Display:** If any no-go criteria are triggered, show a red banner alert with the specific condition, pillar, and "why" statement. The assessment is not invalidated -- the summary still shows all scores -- but the no-go alert is prominently displayed.

### Step 6: Summary Scorecard
- **Content:** Table with all 9 pillars, each showing:
  - Pillar number and name
  - Color bar (pillar color)
  - Score (1-3)
  - Notes (if entered)
  - Required mitigation (if score = 1)
  - Total score (out of 27)
- **Pattern interpretation:** Based on the score pattern, show the matching row(s) from the interpretation table (Section 6).
- **Risk tier context:** Show governance intensity requirements that apply based on the risk tier.
- **No-go alerts:** If any no-go criteria were triggered, show them prominently at the top of the summary.
- **Tool info:** Display the tool name, use case, risk tier, and assessment date.
- **Export:** "Print / Save as PDF" button (print-friendly CSS). "Save Assessment" button (localStorage).

### Step 7: Next Steps / Profile
- **Content:** Based on the score pattern, recommend specific actions:
  - If all pillars >= 2: "Proceed with standard governance. Add to AI inventory."
  - If any pillar = 1: "Address the following before deployment: [list pillars scoring 1 with specific guidance]."
  - If no-go triggered: "This tool does not meet minimum governance requirements. [Specific no-go condition]. Consider: alternative tools, vendor negotiation, or institutional supplementation."
  - If tool is already deployed (indicated by user): Link to annual review checklist.
- **Annual review link:** "Schedule your next review" with recommended cycle based on risk tier.
- **HUMANS mapping toggle (CA only):** If user indicated California CC, show how their pillar scores map to HUMANS compliance.

---

## 12. Navigation Map

All views/screens and their connections:

```
LANDING
  |-- "Start Evaluation" --> USE CASE SELECTION
  |-- "Explore Scorecard" --> EXPLORE SCORECARD (read-only)
  |-- Archetype Card --> USE CASE SELECTION (pre-configured)

USE CASE SELECTION
  |-- Select use case --> RISK TIER ASSIGNMENT
  |-- Back --> LANDING

RISK TIER ASSIGNMENT
  |-- Accept/Override tier --> PILLAR SCORING (first pillar)
  |-- Back --> USE CASE SELECTION

PILLAR SCORING
  |-- Next Pillar --> PILLAR SCORING (next)
  |-- Previous Pillar --> PILLAR SCORING (previous)
  |-- Complete (after last pillar) --> NO-GO CHECK
  |-- Back (from first pillar) --> RISK TIER ASSIGNMENT

NO-GO CHECK
  |-- Continue --> SUMMARY SCORECARD
  (no-go alerts display inline; user proceeds to summary regardless)

SUMMARY SCORECARD
  |-- Click pillar row --> PILLAR DETAIL
  |-- "Next Steps" --> NEXT STEPS
  |-- "Export / Print" --> PDF output
  |-- "Save Assessment" --> localStorage save
  |-- No-Go Alert --> (displayed inline, links to relevant pillar)

PILLAR DETAIL (from summary)
  |-- Back --> SUMMARY SCORECARD
  |-- Next Pillar --> PILLAR DETAIL (next)
  |-- Previous Pillar --> PILLAR DETAIL (previous)

NEXT STEPS
  |-- "Annual Review" --> ANNUAL REVIEW
  |-- "New Assessment" --> USE CASE SELECTION
  |-- Back --> SUMMARY SCORECARD

EXPLORE SCORECARD (read-only reference mode)
  |-- Browse pillars/questions without scoring
  |-- Click pillar --> read-only pillar detail (questions, rubric, source)
  |-- "Start Evaluation" --> USE CASE SELECTION
  |-- Back --> LANDING

ANNUAL REVIEW
  |-- Rescore flow (pre-populated with previous scores from localStorage)
  |-- Compare to previous assessment
  |-- Back --> SUMMARY SCORECARD or LANDING
```

---

## 13. State Management

### LocalStorage Key Structure

Each assessment is saved as a JSON object keyed by tool name + timestamp:

```json
{
  "navigatorV2": {
    "assessments": {
      "nectir-2026-02-20T14:30:00": {
        "toolName": "Nectir",
        "useCase": "AI tutoring (e.g., Nectir)",
        "useCaseId": 5,
        "riskTier": "Medium",
        "riskTierOverride": false,
        "riskTierOverrideReason": null,
        "pillarScores": {
          "P1": 3,
          "P2": 2,
          "P3": 3,
          "P4": 2,
          "P5": 2,
          "P6": 3,
          "P7": 2,
          "P8": 2,
          "P9": 2
        },
        "pillarNotes": {
          "P1": "Strong Socratic design...",
          "P2": "",
          "P3": "",
          "P4": "No adjunct training included",
          "P5": "",
          "P6": "",
          "P7": "",
          "P8": "",
          "P9": ""
        },
        "noGoFlags": {
          "noEducationalPurpose": false,
          "studentDataTraining": false,
          "noHumanOverride": false,
          "auditsBlocked": false,
          "noFERPA": false,
          "noDisclosure": false,
          "noContestability": false,
          "punitiveExit": false
        },
        "totalScore": 21,
        "timestamp": "2026-02-20T14:30:00Z",
        "isCaliforniaCC": true,
        "archetypeUsed": "Building"
      }
    },
    "lastAssessmentKey": "nectir-2026-02-20T14:30:00"
  }
}
```

### Key Design Decisions
- Multiple assessments can be saved, keyed by `toolName-timestamp`
- Annual review creates a new assessment entry with the same tool name but new timestamp, allowing comparison
- `isCaliforniaCC` flag toggles HUMANS mapping visibility
- `archetypeUsed` records which quick-start profile was selected (if any)
- Export to PDF uses print-friendly CSS (same pattern as v1)
- No server-side persistence -- all client-side localStorage

---

## 14. v1 to v2 Mapping Notes

### Keeps (carry forward from v1)
- **9 pillars** -- same IDs (P1-P9), same names, same principle statements
- **Pillar colors** -- P1=#0066cc, P2=#28a745, P3=#6f42c1, P4=#fd7e14, P5=#dc3545, P6=#17a2b8, P7=#e83e8c, P8=#6610f2, P9=#795548
- **Dark hero design** -- dark background (#0C0C0C), signal color (#0891B2), Plus Jakarta Sans display font, Inter body font
- **Card-based UI** -- cards for archetypes, pillars, use cases
- **URL hash navigation** -- `#view-name` pattern with pushState/popstate
- **localStorage persistence** -- save and restore state
- **FO Research branding** -- logo SVG (FO mark + "RESEARCH" label)
- **View system** -- `.view` / `.view.active` pattern with fade animation
- **Stat strip pattern** -- grid of key metrics
- **Signal color system** -- `--signal: #0891B2`, `--live: #16A34A`, `--critical: #DC2626`, `--accent: #D97706`
- **Responsive design** -- mobile breakpoint at 768px

### Drops (removed from v2)
- **10-question institutional assessment** -- replaced by use case selection + pillar scoring
- **10 CC-specific governance gaps (G1-G10)** -- these are baked into the pillar questions now, not separate entities
- **4 college archetypes** (Merced/MiraCosta/LBCC/Calbright) -- replaced by 3 readiness profiles (Lightweight/Building/Scaling)
- **Gap detail views** -- no separate gap pages
- **Tiered roadmap per institution** -- replaced by annual review cycle and next steps based on scores
- **14 templates** -- not surfaced as separate entities (templates are institutional governance tools, not scorecard outputs)
- **Scoring engine** (computeResults) -- replaced by simpler direct pillar scoring (1-3 per pillar)
- **Pedagogical governance level** -- absorbed into P1 and P4 questions
- **Quick-start pre-loaded answer sets** -- replaced by archetype pre-configuration of the assessment flow

### Adds (new in v2)
- **Use case selector** -- 10 Student Services AI use cases with risk tier defaults
- **Risk tier system** -- High/Medium/Lower with governance intensity requirements
- **Per-pillar scoring interface** -- user directly scores each pillar 1-3 guided by questions
- **No-go criteria alerts** -- 8 absolute conditions that stop procurement regardless of score
- **Vendor scorecard questions** -- 5-8 specific questions per pillar with "what you're looking for" guidance
- **Score pattern interpretation** -- 7 pattern descriptions with action implications
- **Annual review checklist** -- 9 areas for ongoing governance monitoring
- **HUMANS mapping toggle** -- California-specific overlay showing CCCCO alignment
- **3 new archetypes** (Lightweight/Building/Scaling) -- readiness profiles that pre-configure the flow
- **Tool name input** -- assessments are keyed to specific tools
- **Multi-assessment storage** -- save and compare multiple tool evaluations
- **No-go checklist step** -- dedicated step for absolute criteria checking
- **Source citations per pillar** -- framework sources visible for credibility

---

## Appendix A: Pillar Question Counts

| Pillar | Questions | Notes |
|--------|-----------|-------|
| P1: Purpose & Educational Legitimacy | 5 (1.1-1.5) | |
| P2: Equity & Differential Impact | 7 (2.1-2.7) | Highest question count |
| P3: Human Authority & Decision Accountability | 5 (3.1-3.5) | |
| P4: Student and Faculty Agency | 8 (4.1-4.8) | Split: 4 student, 4 faculty |
| P5: Risk Proportionality & Harm Mitigation | 6 (5.1-5.6) | |
| P6: Data Stewardship & System Integrity | 8 (6.1-6.8) | Tied for highest |
| P7: Transparency & Contestability | 7 (7.1-7.7) | |
| P8: Vendor Accountability & Institutional Sovereignty | 7 (8.1-8.7) | |
| P9: Institutional Capacity & Continuous Governance | 6 (9.1-9.6) | |
| **Total** | **59 questions** | |

---

## Appendix B: Design Token Reference (from v1)

These CSS custom properties should carry forward to v2:

```css
/* Colors */
--ink: #151515;
--ink-soft: #3A3A3A;
--ink-muted: #6B6B6B;
--mid: #A0A0A0;
--border: #D4D4D4;
--surface: #F5F5F3;
--warm-white: #FAFAF8;
--white: #FFFFFF;
--signal: #0891B2;
--signal-dark: #0E7490;
--signal-deep: #155E75;
--signal-light: #E0F7FA;
--signal-10: rgba(8,145,178,0.10);
--accent: #D97706;
--accent-light: #FEF3C7;
--dark: #0C0C0C;
--dark-surface: #1A1A1A;
--dark-border: #2A2A2A;
--dark-muted: #888888;
--live: #16A34A;
--caution: #EAB308;
--critical: #DC2626;

/* Pillar Colors */
--p1: #0066cc;
--p2: #28a745;
--p3: #6f42c1;
--p4: #fd7e14;
--p5: #dc3545;
--p6: #17a2b8;
--p7: #e83e8c;
--p8: #6610f2;
--p9: #795548;

/* Risk Tier Colors */
--tier-high: #c00;
--tier-high-bg: #f8d7da;
--tier-medium-border: #ffc107;
--tier-medium-text: #856404;
--tier-medium-bg: #fff3cd;
--tier-lower: #28a745;
--tier-lower-bg: #d4edda;

/* Typography */
--display: 'Plus Jakarta Sans', sans-serif;
--body: 'Inter', sans-serif;
```

---

## Appendix C: Open Decisions

Items flagged as needing human input:

1. **Portable ethical criteria (Section 9):** RESOLVED. Four Criteria for Ethical AI Implementation have been defined: (1) Equitable student outcomes → P2, (2) Quality data governed responsibly → P6, (3) Ethics and safety foundation → P3/P7/P4, (4) Thoughtful multi-year approach → P9.

2. **Downward risk tier override (Section 11, Step 3):** Should users be allowed to override a High-risk use case down to Medium? Recommended: allow only with mandatory written justification that becomes part of the record.

3. **No-go criteria implementation (Section 11, Step 5):** No-go criteria #2, #4, #5, and #8 cannot be inferred from pillar scores alone. They require explicit yes/no answers. Recommended: add a dedicated "No-Go Checklist" step with 8 yes/no questions.

4. **Missing source file:** `Framework_Architecture_Table_StudentServices.docx` was unreadable as a binary .docx. If it contains content not already captured in the vendor scorecard or architecture document, that content is missing from this spec.

---

*End of specification. This document is the sole source of truth for the Navigator v2 builder and content agents.*
