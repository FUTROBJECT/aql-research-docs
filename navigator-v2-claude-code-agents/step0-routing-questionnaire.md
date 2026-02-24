# Step 0: Student Services Use Case Routing Questionnaire
## Draft for Review — February 2026

---

## What This Does

A VPSS or dean arrives at the Navigator and says: "We want to do something with AI in Student Services but we don't know where to start." These 8 questions identify their institutional context and route them to 2-3 recommended use cases, ranked by fit.

Each question maps to specific use cases. The combination of answers produces a weighted recommendation: "Based on your answers, start here."

This is **Step 0** — it comes before the use case selector (Step 1), screening (Step 2), and scoring (Step 3). Users who already know what they're evaluating can skip to Step 1. Users who need help figuring out where to start begin here.

---

## The 8 Questions

### Q1: Where are students getting stuck?

*Pick up to three. This tells us where AI could have the biggest impact for your students.*

- [ ] Students can't get advising appointments when they need them
- [ ] Students are falling off track and we don't catch it early enough
- [ ] Financial aid is confusing and students abandon applications
- [ ] Students can't get answers outside business hours
- [ ] Students need help in courses but tutoring isn't available or accessible
- [ ] Language barriers prevent students from accessing services
- [ ] Students don't know what support services exist or how to find them
- [ ] Career planning feels disconnected from what students are studying

**Mapping:**
| Selection | Points toward |
|-----------|--------------|
| Advising appointments | SS-01 (Advising/Pathways) |
| Falling off track | SS-02 (Early Alert) |
| Financial aid confusion | SS-03 (Financial Aid) |
| No answers after hours | SS-04 (Chatbot/Front Door) |
| Tutoring access | SS-05 (Tutoring Assistant) |
| Language barriers | SS-06 (Multilingual Support) |
| Don't know services exist | SS-07 (Basic Needs) + SS-04 (Chatbot) |
| Career disconnection | SS-08 (Career Services) |

---

### Q2: How many students does your college serve?

*This helps us calibrate recommendations to your scale.*

- Under 5,000 (headcount)
- 5,000 – 15,000
- 15,000 – 30,000
- Over 30,000

**Mapping:**
| Selection | Effect |
|-----------|--------|
| Under 5,000 | Weight toward Tier 1 use cases (SS-04, SS-07, SS-08). Flag that Tier 3 use cases may exceed capacity. |
| 5,000 – 15,000 | All use cases feasible. Weight toward medium-complexity. |
| 15,000 – 30,000 | Weight toward use cases with scale payoff (SS-01, SS-02, SS-04). |
| Over 30,000 | Strong case for SS-02 (Early Alert) and SS-01 (Advising) where human-only isn't scaling. |

---

### Q3: What does your data situation look like?

*Be honest. This is the most common reason AI tools underperform — they need data you don't have or can't trust.*

- We have a functioning SIS and can pull clean enrollment and student demographic data
- We have that, plus advising records, financial aid data, and some learning analytics
- We have rich data across multiple systems but they don't talk to each other well
- We're still working on getting reliable data out of our core systems

**Mapping:**
| Selection | Effect |
|-----------|--------|
| Functioning SIS, clean basics | Eligible for SS-04 (Chatbot), SS-06 (Multilingual), SS-07 (Basic Needs), SS-08 (Career). Flag data readiness risk for SS-01, SS-02, SS-03. |
| SIS + advising + financial aid | All use cases feasible. SS-01, SS-02, SS-03 become realistic. |
| Rich but siloed | Technical integration is the bottleneck, not data availability. Recommend starting with use cases that don't require cross-system data (SS-04, SS-05, SS-06). |
| Still working on basics | Strongly weight toward use cases with minimal data requirements (SS-04, SS-06, SS-07, SS-08). Flag that Tier 3 use cases are premature. |

---

### Q4: What's your staffing reality for Student Services technology?

*This determines how much governance infrastructure you can realistically maintain.*

- We have dedicated IT staff who support Student Services tools
- IT handles everything centrally; Student Services has no dedicated tech support
- We rely heavily on vendor support and system-level resources
- One or two people wear all the hats

**Mapping:**
| Selection | Archetype | Effect |
|-----------|-----------|--------|
| Dedicated SS tech staff | Scaling | Can handle Tier 2-3 use cases with proper governance |
| Central IT only | Building | Can handle Tier 1-2; Tier 3 needs careful scoping |
| Vendor/system dependent | Lightweight | Start with Tier 1; strong vendor accountability needed |
| One or two people | Lightweight | Tier 1 only to start; templates over custom governance |

---

### Q5: What are your biggest equity gaps right now?

*Pick up to two. This helps us recommend use cases that address your specific equity priorities.*

- [ ] Completion rates differ significantly by race/ethnicity
- [ ] First-generation students are less likely to persist
- [ ] Students working full-time or with caregiving responsibilities can't access services during business hours
- [ ] Multilingual students don't receive adequate support in their language
- [ ] Pell-eligible students have lower completion rates
- [ ] Students with disabilities face access barriers in current systems
- [ ] Transfer rates differ significantly across student populations

**Mapping:**
| Selection | Points toward |
|-----------|--------------|
| Completion gaps by race | SS-02 (Early Alert) — but flag equity audit requirement |
| First-gen persistence | SS-01 (Advising) + SS-07 (Basic Needs) |
| Working/caregiving access | SS-04 (Chatbot) + SS-06 (Multilingual) — after-hours access |
| Multilingual gaps | SS-06 (Multilingual) — strong signal |
| Pell completion gaps | SS-03 (Financial Aid) + SS-02 (Early Alert) |
| Disability access barriers | SS-04 (Chatbot) — if accessible; flag accessibility governance |
| Transfer rate gaps | SS-01 (Advising/Pathways) + SS-10 (Registration) |

---

### Q6: Is AI already being used informally in Student Services at your college?

*This tells us whether governance needs to catch up to reality or get ahead of it.*

- Yes — staff and/or students are already using AI tools (ChatGPT, Copilot, vendor-embedded AI) without formal governance
- Somewhat — a few people are experimenting but it's not widespread
- No — AI isn't really being used in Student Services yet
- We don't know — and that's part of the problem

**Mapping:**
| Selection | Effect |
|-----------|--------|
| Yes, already happening | Urgency is high. Recommend starting with whatever's already in use — govern what exists before adding more. Prioritize SS-04 (Chatbot) if that's what's deployed. |
| Somewhat | Moderate urgency. Good moment to formalize around a specific use case. |
| Not yet | Opportunity to get governance right before deployment. Can be strategic about where to start. |
| Don't know | Start with an inventory. The Navigator assessment itself becomes the first governance act. Recommend low-risk SS-04 or SS-07 as the first formal use case. |

---

### Q7: Does your college already have any AI governance in place?

*Even informal structures count — an AI committee, a policy statement, a procurement checklist.*

- We have a formal AI governance committee or policy
- We have something informal — an ad hoc group, a dean who's paying attention, some guidelines
- Nothing specific to AI, but we have general technology governance processes
- No governance structure that addresses AI

**Mapping:**
| Selection | Archetype | Effect |
|-----------|-----------|--------|
| Formal governance | Scaling | Can pursue Tier 2-3 use cases. The Navigator adds operational tools to existing structure. |
| Informal | Building | The Navigator formalizes what they've started. Good fit for structured assessment. |
| General tech governance | Building | Existing processes provide foundation. Extend rather than build from scratch. |
| Nothing | Lightweight | The Navigator IS the starting point. Begin with Tier 1, use provided templates. |

---

### Q8: What's driving this? Why are you looking at AI for Student Services now?

*Understanding your motivation helps us recommend a starting point that builds momentum.*

- Leadership is asking for an AI strategy and we need to show progress
- We've seen a specific tool or heard about a peer institution's success
- Student demand — students expect AI-enabled services
- Enrollment/retention pressure — we need to do more with less
- Equity imperative — current approaches aren't reaching all students
- System-level directive — CCCCO or district is requiring AI governance

**Mapping:**
| Selection | Effect |
|-----------|--------|
| Leadership wants strategy | Recommend a visible, lower-risk win first (SS-04 Chatbot). Build governance credibility before tackling Tier 3. |
| Specific tool/peer success | Route directly to the relevant use case. They've already identified the starting point — validate it through the Navigator. |
| Student demand | Weight toward student-facing tools: SS-04, SS-05, SS-06. |
| Enrollment/retention | Weight toward SS-01 (Advising), SS-02 (Early Alert), SS-10 (Registration). |
| Equity imperative | Weight toward use cases addressing their Q5 equity gaps. Flag dependency profile importance. |
| System directive | Emphasize HUMANS alignment. California-specific path. |

---

## How Scoring Works

Each use case accumulates points based on the user's answers across all 8 questions. The algorithm:

1. **Q1 (bottlenecks)** provides the strongest signal — direct mapping to use cases, each selection = 3 points to the mapped use case(s)
2. **Q2 (size)** modifies feasibility — filters out or boosts use cases based on scale
3. **Q3 (data)** acts as a feasibility gate — use cases requiring rich data get flagged or downranked if data isn't ready
4. **Q4 (staffing)** determines archetype and filters by tier appropriateness
5. **Q5 (equity gaps)** adds 2 points to use cases that address the selected gaps
6. **Q6 (current AI use)** adjusts urgency and may override ranking ("govern what's already happening first")
7. **Q7 (governance)** confirms archetype and adjusts recommended starting complexity
8. **Q8 (motivation)** provides final weighting toward use cases that match the institutional moment

### Output

After 8 questions, the user sees:

**Your Recommended Starting Points**

Ranked list of 2-3 use cases with:
- Use case name and one-line description
- Why it fits: "You told us [specific answers]. This use case addresses [connection]."
- Risk tier badge
- Data readiness flag (green/yellow/red based on Q3)
- "Evaluate This Use Case →" button (routes to Step 1 with use case pre-selected)

**Your Institutional Profile**
- Archetype: Lightweight / Building / Scaling (derived from Q2 + Q4 + Q7)
- Equity priority: [derived from Q5]
- Urgency level: [derived from Q6]
- Data readiness: [derived from Q3]

**Example output:**

> ### Your Top Starting Points
>
> **1. Student-Facing Chatbot / Digital Front Door** (Tier 1 — Low Risk)
> You said students can't get answers outside business hours and your working students can't access services during the day. A chatbot addresses both — and at Tier 1, it's governance-light enough to match your current capacity.
> [Evaluate This Use Case →]
>
> **2. Multilingual Support / Translation Services** (Tier 2 — Medium Risk)
> Language barriers showed up in both your bottleneck and equity responses. Your SIS data is clean enough to support this. Medium governance lift.
> [Evaluate This Use Case →]
>
> **3. Consider Later: Early Alert System** (Tier 3 — High Risk)
> Your completion gaps suggest this would have high impact, but your data situation and staffing point to starting with Tier 1-2 first. Revisit when your data systems are integrated and you've built governance capacity through your first use case.

---

## Design Notes

**Why 8 questions, not 10:** The v1 had 10 but several were about general institutional AI posture (detection policy, faculty AI use). Since we've narrowed to Student Services, some of those don't apply. 8 is enough to route accurately without feeling like a survey.

**Why multi-select on Q1 and Q5:** These are the questions where multiple answers produce the most useful signal. Limiting to single-select would force false choices.

**Why "Consider Later" in the output:** Some use cases are right for the institution but wrong for right now. Saying "not yet, and here's why" is more useful than hiding them. It also prevents the user from going straight to Tier 3 when they lack the infrastructure.

**Connection to the Navigator flow:** The "Evaluate This Use Case →" button pre-selects the use case in Step 1 and carries the archetype and institutional profile into the assessment. The user doesn't re-answer capacity questions — that context travels with them.

**Skippable:** Users who already know their use case bypass Step 0 entirely and go straight to Step 1 (use case selector) or the archetype quick-start.
