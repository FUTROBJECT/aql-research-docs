# Navigator v2: Shared Context

Read this entire file before doing anything else. This is the shared reference for all Navigator v2 work.

---

## What We're Building

The June deliverable to College Futures Foundation is two things:

1. **The Navigator** — an interactive web tool where leadership identifies a Student Services AI use case, evaluates it against governance pillars, and receives a generated roadmap tailored to their institution. One thing you click through.

2. **The Governance Toolkit PDF** — a complete reference document with all templates, playbooks, and measurement guidance. One thing you download.

Both scoped exclusively to **Student Services** use cases across community colleges. These agents build the Navigator.

---

## The Five-Step Flow

```
STEP 1: IDENTIFY → "What Student Services use case are you considering?"
  User selects from 10 use cases or describes custom
  4-5 use-case-specific screening questions
  4 dependency profile questions (applies to every use case)
  Output: GO / PAUSE / NO-GO recommendation + dependency profile (Low/Medium/High)

STEP 2: EVALUATE → "Is this tool ready for your students?"
  Risk tier confirmed or adjusted
  Per-pillar scoring (1-3) with visible rubrics
  No-go criteria checked (8 hard stops)
  Output: Governance profile with pattern interpretation + dependency badge

STEPS 3-4: YOUR ROADMAP → "Based on your profile, here's what to do."
  Generated from: archetype + use case + risk tier + pillar scores + dependency profile
  Downloadable/printable summary
  Lightweight/Low = ~2 pages, Scaling/High = ~6 pages
  Dependency-specific governance requirements conditionally inserted
```

### Two Entry Points (Same Destination)

**Full path:** Select use case → screening questions → dependency profile → risk tier → pillar scoring → profile → roadmap
**Quick path:** Self-select archetype → select use case → dependency profile → abbreviated scoring → roadmap

---

## Three-Layer Framework Architecture

**Layer 1: Four Ethical Criteria (Portable — any CC system)**
1. Equitable Student Outcomes
2. Quality Data, Governed Responsibly
3. Ethics & Safety Foundation
4. Thoughtful, Multi-Year Approach

**Layer 2: Nine Operational Pillars (Portable)**
P1: Purpose & Educational Legitimacy
P2: Equity & Differential Impact
P3: Human Authority & Decision Accountability
P4: Student & Faculty Agency
P5: Risk Proportionality & Harm Mitigation
P6: Data Stewardship & System Integrity
P7: Transparency & Contestability
P8: Vendor Accountability & Institutional Sovereignty
P9: Institutional Capacity & Continuous Governance

**Layer 3: CCCCO HUMANS Framework (California Only)**
H-U-M-A-N-S is binding for all 116 CCC colleges. Navigator maps pillars to HUMANS letters. Non-California colleges skip this and still have a complete framework.

Gap: HUMANS does not address institutional capacity building (Criterion 4 / Pillar 9).

---

## Student Services Use Cases

| ID | Use Case | Default Risk Tier |
|----|----------|------------------|
| SS-01 | AI Advising / Guided Pathways Assistant | 3 (High) |
| SS-02 | Early Alert / Student Risk System | 3 (High) |
| SS-03 | Financial Aid Triage & FAFSA Support | 3 (High) |
| SS-04 | Student-Facing Chatbot / Digital Front Door | 1 (Low) |
| SS-05 | AI Course Tutoring Assistant (e.g., Nectir) | 2 (Medium) |
| SS-06 | Multilingual Support / Translation Services | 2 (Medium) |
| SS-07 | Basic Needs Support & Resource Navigation | 1 (Low) |
| SS-08 | Career Services AI (resume, interview prep) | 1 (Low) |
| SS-09 | Student Journey Mapping / Friction Detection | 2 (Medium) |
| SS-10 | Registration & Enrollment Support | 2 (Medium) |
| SS-XX | Custom / Other (user describes) | User assigns |

---

## Archetypes

**Lightweight** — Small or rural. Limited IT. 1-2 people wearing many hats. High reliance on external support.
- Start with one Tier 1 or Tier 2 use case
- Use provided templates directly
- Quarterly review cycle

**Building** — Mid-size. Some analytics/data capability. Emerging AI interest. Has IT director and IR capacity.
- 2-3 use cases across risk tiers
- Cross-functional AI working group meets quarterly
- Begin disaggregated tracking

**Scaling** — Large, higher volume. Dedicated technical bench. May have data warehouse, analytics team, innovation office.
- Portfolio approach across risk tiers
- Formal AI governance with project owners
- Bias audits for Tier 3 use cases
- Standing committee with reporting structure

---

## Risk Tiers

**Tier 1 (Low):** Informational only. No decisions affecting access. No sensitive data. Example: FAQ chatbot.
**Tier 2 (Medium):** Touches advising or instructional core. Human reviews outputs. Accesses student records. Example: tutoring assistant.
**Tier 3 (High):** Affects enrollment, financial aid, academic standing. Automated or semi-automated decisions. Sensitive data. Example: early alert system.

---

## Capability & Dependency Profile

This is a novel governance dimension. Of 224 frameworks reviewed, zero include dependency profiling or capability impact assessment. This is what makes the AQL framework unique.

The dependency profile answers: **does this tool build capability or replace it?**

### The Four Questions (apply to every use case, after screening, before risk tier)

**Q1: "What happens if this tool disappears tomorrow?"**
- Students/staff lose a convenience but can still complete the task (1 — Low)
- Students/staff would struggle significantly and need time to rebuild (2 — Medium)
- Students/staff would be unable to perform the task at all (3 — High)

**Q2: "After a year of use, will users be better at this task without the tool, about the same, or less capable?"**
- Better — the tool teaches the process or builds transferable skills (1 — Capability building)
- About the same — the tool handles a task without changing underlying ability (2 — Neutral)
- Less capable — the tool replaces practice or judgment that would otherwise develop (3 — Erosion risk)

**Q3: "Does the tool show users how to navigate this process, or does it navigate for them?"**
- Shows how — walks through steps, builds ability to do it independently (1 — Navigate-with)
- Mix — some features explain, some execute, or it depends on configuration (2 — Configurable)
- Navigates for them — users input need, tool produces outcome directly (3 — Navigate-for)

**Q4: "Is there a point where users are expected to do this without the tool?"**
- Yes — explicit milestone or transition where tool is removed or reduced (1 — Independence designed)
- Not explicitly — but tool supplements rather than replaces existing process (2 — Parallel systems)
- No — the tool is the process now, no plan for users to perform without it (3 — Permanent infrastructure)

### Scoring (sum of 4 questions, range 4-12)

| Score | Profile | Meaning |
|-------|---------|---------|
| 4-5 | **Low Dependency** | Builds or preserves capability. Standard governance. |
| 6-8 | **Medium Dependency** | Mixed characteristics. Include capability checks at review points. |
| 9-12 | **High Dependency** | Replaces capability. Not a disqualifier — requires specific protections. |

### What Each Profile Triggers in the Roadmap

**Low (4-5):** Standard review cadence. No additional requirements.

**Medium (6-8):**
- Configuration review: verify tool deployed in capability-building mode
- 6-month capability check: can users still perform with reduced AI support?
- Alternative maintenance: non-AI process documented and periodically tested

**High (9-12):**
- Dependency acknowledgment: document the decision, who made it, rationale
- Vendor lock-in assessment: data portability, exit costs, what if vendor disappears?
- 12-month sunset evaluation: is dependency justified by outcomes? Equity implications?
- Capability impact tracking (Tier 3 only): has staff/advisor capability declined?

### Design Principles

- **These are not gates.** They produce a profile, not GO/NO-GO. Profiles incentivize awareness; gates incentivize dishonesty.
- **"Permanent infrastructure" is valid.** A translation tool for a Mixtec speaker is permanent and appropriate. The framework respects that — it requires the choice to be conscious.
- **"What you're looking for" text legitimizes every answer.** No one feels punished for honesty.
- **Patterns emerge through use.** After profiling 3-4 tools, leaders notice: "all our AI tools are navigate-for, not navigate-with." That observation is worth more than theory.

---

## Voice and Tone

### Two Sources to Study

**SOURCE 1: v1 Navigator** (read the full index.html)
- Direct and confident. "If you can't articulate the educational purpose, don't buy it."
- Practitioner-facing. Uses "you" and "your institution."
- Sharp anchor lines. "Students are not training data." "Decisions without recourse are not governance."
- No jargon inflation. "Who is accountable when the AI is wrong?"
- Scoring rubrics use parallel structure. The "3" describes good. The "1" describes bad. Same grammar.
- Headers are functional. "Step 0: Determine Risk Tier" not "Understanding Your Risk Profile."
- Concretely specific. Names tools (Nectir, EAB Navigate), regulations (FERPA, AB 2370), institutions.

**SOURCE 2: Rewiring America "Go Electric"** (fetch https://www.rewiringamerica.org/go-electric)
- Journey framing. The user is navigating, not being audited.
- Benefits-first. What you gain before what you risk.
- Short rhythmic hooks. Triads. "Start swapping. Empower others. Learn why."
- Concrete specificity. Every claim lands with a number.
- The tool does the work. "Generate a free, personalized plan in just a few minutes."
- Warmth. "We've got you covered."

### The v2 Synthesis: WARM AND BLUNT

A smart colleague who did the research, tells you what matters, and hands you exactly what you need — warmly, directly, and without wasting your time.

1. Journey framing replaces compliance framing. The Navigator is a map, not a test.
2. Benefits-first, then stakes. "Know where you're strong and where students need protection."
3. Short rhythmic hooks. Pillar names stay. Add one-line hooks.
4. Concrete specificity. Numbers, names, regulations. Never vague.
5. No-go lines stay sharp. "Students are not training data." Frame them supportively: "These are the lines. Everything else, we can work with."
6. The tool does the work. "Answer a few questions. Get a governance roadmap tailored to your institution."

**Do NOT borrow from Rewiring America:**
- Puns. The stakes are too serious.
- Consumer marketing energy. We're protecting students, not selling a lifestyle upgrade.
- General-public reading level. Write for VPSSs, deans, IT directors, faculty leaders.

### Voice for Dependency Profile Specifically

The dependency questions should feel like a colleague asking practical questions, not a theorist testing your educational philosophy.

- Intro text: "These four questions help you understand whether this tool builds capability or creates dependency. There are no wrong answers — but there are answers you should know before you deploy."
- "What you're looking for" text after each question legitimizes every response option. No answer is punished.
- The profile result is descriptive, not judgmental. "High dependency" is a finding, not a failure.

---

## Why This Exists

Of 224 AI governance frameworks reviewed across 12 global domains, only 2 directly address community colleges. CCs serve nearly half of all US undergraduates, disproportionately serve historically marginalized populations, and are the primary workforce training pipeline.

## What This Is NOT

- Not a restatement of ethical principles (HUMANS already exists)
- Not a comprehensive AI policy guide (ASCCC does that)
- Not a procurement checklist (Calbright/FoundationCCC cover that)
- Not a faculty-facing tool (this is for institutional leadership)
- Not covering instruction, HR, finance, or operations (Student Services only)
