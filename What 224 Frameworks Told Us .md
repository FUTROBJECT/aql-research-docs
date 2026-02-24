# **What 224+ Frameworks Told Us**  (That Nobody Else Is Saying)

**For:** AQL Team (Amin, Hyunjun, Mimi)  
**From:** Adam  
**Date:** February 2026  
**Read time:** 5 minutes  
**Focus:** AI Governance for Student Services in California Community Colleges

---

## **The 30-Second Version**

Community colleges are invisible in global AI governance, and Student Services is where the stakes are highest and governance is weakest. AI is already making consequential decisions about students — flagging them as at-risk, guiding their financial aid, recommending their course sequences — with almost no oversight, no appeal rights, and no bias testing. The counselor shortage is driving adoption faster than governance can keep up. The vendor contracts that control these systems often don't even give colleges the right to audit what the algorithms are doing.

## Our research gives us a foundation to fix this: 14 deeply analyzed frameworks, 42 novel provisions for CC contexts, and operational models adapted from regulated industries that already govern high-stakes algorithmic decisions. Nobody else has built this. We're not filling a gap — we're building a field. 

## **How the Research Worked**

We scanned 224 AI governance frameworks across 12 global domains — from the African Union's Continental AI Strategy to Singapore's Agentic AI Addendum to the National Association of Insurance Commissioners' model bulletin. From that scan, we identified 62 high-priority candidates, then deeply analyzed 14 frameworks that had the most to offer community colleges. This research used AI-assisted discovery and extraction across all 12 domains, with human-directed analysis and judgment applied to all prioritization, gap identification, and provision development. Every recommendation below traces back to specific provisions in those 14 frameworks, cross-referenced against each other and tested for CC feasibility.

**The full research corpus is available if you want to dig into any specific claim. This document gives you the conclusions and tells you where to look if you want the evidence.**

---

##  **7 Findings That Should Shape What We Build**

### **1\. Community Colleges Are Invisible**

Of the 14 priority frameworks we analyzed, only 2 address community colleges at all (ASCCC and ATD). Federal frameworks like OMB M-25-21 mention "education" but mean research universities. International frameworks assume institutional resources CCs don't have. This isn't a gap we're filling — it's an entire market that doesn't exist yet. **We are not competing with existing CC governance frameworks. There aren't any.**

→ *Dig deeper: discovery-summary.md, project-final-summary.md (Finding 1\)*

###  **2\. Agentic AI Is Already Here — In Student Services**

Advising chatbots, early alert systems that auto-trigger interventions, financial aid bots, degree audit automation — autonomous and semi-autonomous AI is deploying faster in Student Services than anywhere else on campus. And almost nobody is governing it. Only Singapore's Agentic AI Addendum addresses governance for autonomous AI systems globally. We need provisions for autonomy limits by decision type, human accountability checkpoints, escalation requirements, and accuracy standards — and we need them before these systems proliferate further. This isn't a future risk. It's happening now at our pilot colleges.

→ *Dig deeper: analysis-summary.md (Gap 6), best-fit-elements.md (Singapore framework), aql-development-recommendations.md (Recommendation 4\)*

###  **3\. Counselor Ratios Are the Binding Constraint**

California community colleges often have counselor-to-student ratios of 1:900 or worse. That's why AI is being deployed so aggressively in advising, early alerts, and chatbots — there simply aren't enough humans. This changes the governance question fundamentally. In the classroom, the question is "are faculty being supported?" In Student Services, the question is: **are AI systems making consequential decisions about students because there aren't enough counselors to do it?** The political dynamics are also different. Counselors and advisors often have less institutional power than faculty — no equivalent of academic freedom or faculty senate governance authority. AI gets deployed *on* Student Services staff rather than *with* them.

→ *Dig deeper: analysis-summary.md, cc-provision-mapping.md*

###  **4\. AI Is Making High-Stakes Decisions About Students Without Governance**

In Student Services, AI is influencing or making decisions that affect student trajectories: early alert systems flagging students as at-risk (which can trigger interventions or inadvertently track students), financial aid chatbots providing guidance that affects eligibility, degree planning tools recommending course sequences, career services matching algorithms. These aren't academic integrity questions — they're equity questions. Did the algorithm just steer a first-generation student away from a transfer pathway? Did the chatbot give incorrect financial aid guidance to a student who doesn't know to double-check? The research from the OMB high-impact AI definition and the GAO framework is clear: any AI making consequential decisions about individuals requires human review, appeal rights, and bias testing. Most CC Student Services AI has none of these.

→ *Dig deeper: best-fit-elements.md (OMB Framework 5, GAO Framework 6), aql-development-recommendations.md*

###     **5\. Student Services Gaps Have Zero Framework Coverage**

We mapped all 14 frameworks against CC-specific governance needs. Several gaps become especially acute through a Student Services lens, and none have global framework coverage. Adult learner advising (working adults need fundamentally different AI interactions around scheduling, financial aid, and career services), transfer students (AI-driven credit evaluation and transfer advising are high-stakes decisions with no governance), accessibility (Student Services chatbots and portals have terrible accessibility track records), and dual enrollment (minors interacting with AI advising tools raises consent questions). We developed 42 novel provisions to fill these gaps across the full framework. The Student Services provisions are where the most consequential decisions intersect with the least governance.

→ *Dig deeper: gap-coverage-matrix.md, cc-provision-mapping.md*

###  **6\. The Insurance Industry Has the Best Operational Model**

This was the biggest surprise in the research, and it becomes even more relevant with a Student Services focus. The National Association of Insurance Commissioners (NAIC) model bulletin provides the clearest operational template for what a "written AI governance program" should look like — documentation standards, cross-functional governance committees, consumer/student notification requirements, third-party vendor accountability, and audit rights. The insurance lifecycle (policy → underwriting → claims → customer service) maps structurally onto the student services lifecycle (enrollment → advising → financial aid → completion). Both involve consequential decisions about individuals, vendor-provided systems, documentation requirements, and audit trails. Singapore's framework gave us the best model for governing the autonomous systems that populate Student Services — autonomy limits, human checkpoints, escalation requirements.

→ *Dig deeper: best-fit-elements.md (Framework 13: NAIC, Framework 7: Singapore)*

###  **7\. Vendor Lock-In Is the Governance Bottleneck**

Unlike classrooms where faculty choose their own tools, Student Services AI is procured institutionally — often through multi-year contracts with platforms like EAB Navigate, Starfish, Ocelot, or Ellucian products. Colleges frequently can't even access the algorithms making decisions about their students. A faculty member can stop using ChatGPT tomorrow; a college can't rip out its early alert system mid-contract. This means governance for Student Services AI is fundamentally a vendor governance problem. The IEEE 7004 RFP language and NAIC audit rights provisions become essential — not as nice-to-haves but as baseline requirements for any vendor contract. Colleges need the contractual right to audit algorithmic decisions, require bias testing, and mandate human review triggers. Without these provisions in the contract, governance is just a policy document that vendors can ignore.

→ *Dig deeper: best-fit-elements.md (IEEE 7004 procurement language, NAIC audit rights), conflict-analysis.md*

##  **5 Decisions the Research Supports**

These aren't open questions — the research points clearly in one direction for each.

| Decision | Recommendation | Confidence | Why |
| ----- | ----- | ----- | ----- |
| Where to focus governance first? | High-stakes automated decisions (advising, early alerts, financial aid) | High | OMB "high-impact AI" definition explicitly includes education; consequential student decisions require governance before general-purpose tools |
| Dedicated Chief AI Officer? | No — use existing committee structure | High | Budget-unrealistic for CCs; adapted OMB governance board model works with existing shared governance |
| Which framework foundation? | ASCCC 5 principles \+ ATD "AI Agility" \+ GAO 4 principles | High | CC-developed, equity-centered, structurally sound |
| Vendor contract language? | Adopt NAIC audit rights \+ IEEE 7004 RFP language | High | Non-negotiable for Student Services where AI is almost entirely vendor-provided |
| Tiered or one-size-fits-all? | Tiered (3 levels based on institutional maturity) | High | EDUCAUSE model adapted for CC resource variation; small colleges can start with minimum viable governance |

