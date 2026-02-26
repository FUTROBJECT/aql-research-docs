# Mechanism Detection Screen: Specification for Navigator v2

**Purpose:** Catch hidden risk that lives in *how* a tool works, not *what category* it belongs to. A campus life recommender and an FAQ chatbot both live in "Student-Facing Chatbot" — but one pattern-matches student behavior and the other serves static information. The governance requirements are fundamentally different.

**Position in flow:** After category-specific screening → after screening result → BEFORE risk tier confirmation. Three questions. Takes under 2 minutes. Runs for every use case regardless of initial tier assignment.

**Core principle:** Risk tier should reflect the tool's *mechanism*, not just its *category*. This screen detects three mechanism types that reliably elevate risk regardless of what the tool is called.

---

## Integration Point

```
Current flow:
  Use Case Selection → Screening → Screen Result → Dependency Profile → Risk Tier → Pillar Scoring

Updated flow:
  Use Case Selection → Screening → Screen Result → Dependency Profile → MECHANISM DETECTION → Risk Tier → Pillar Scoring
```

The mechanism screen produces two outputs:
1. **Tier adjustment** — escalates the default risk tier if mechanism flags fire
2. **Forced pillar emphasis** — flags specific pillars that must score ≥ 2 regardless of tier

Both outputs carry forward into the risk tier view, where the user sees the adjusted tier with an explanation of *why* it changed.

---

## The Three Questions

### MD-01: Behavioral Pattern-Matching

**Question:** "How does this tool decide what to show or recommend to each student?"

**What this detects:** Tools that personalize outputs based on individual student data — behavioral history, profile characteristics, usage patterns, predicted preferences. This is the mechanism that turns a neutral chatbot into an equity risk.

| Option | Label | Description | Escalation |
|--------|-------|-------------|------------|
| A | Same for everyone | Every student sees the same information, options, and interface. The tool responds to what the student asks, not who they are. | None |
| B | Student-configured | Students choose preferences or filters themselves. Personalization is driven by explicit student choice, not inferred patterns. | None |
| C | Profile-based personalization | The tool uses student data (major, enrollment history, demographics, prior interactions) to tailor what it shows. Students may not know what data drives the personalization. | **+1 tier.** Force P2 (Equity) ≥ 2. Force P7 (Transparency) ≥ 2. |
| D | Behavioral pattern-matching | The tool observes student behavior over time and adjusts recommendations, content, or interface based on inferred patterns or predicted preferences. | **+1 tier.** Force P2 (Equity) ≥ 2. Force P7 (Transparency) ≥ 2. Add equity screening flag. |
| E | Unknown | The team doesn't know how the tool personalizes. | **+1 tier.** Force P7 (Transparency) ≥ 2. Flag as investigation required. |

**What you're looking for:**

- **Option A** is genuinely low risk for personalization. A chatbot that answers "where is the library?" the same way for every student has no personalization mechanism to create differential treatment.
- **Option B** is student-directed. If the student chooses "show me STEM clubs," that's agency, not profiling. The key distinction: did the student make the choice, or did the system make it for them?
- **Option C** is where the campus life recommender lives. The tool uses student profile data to decide what to surface. The student doesn't know their major, ethnicity, or prior club attendance is shaping what they see. This creates differential treatment by design — and the differential treatment may reproduce existing patterns (including segregation) without anyone intending it.
- **Option D** is the most sophisticated and most dangerous. The tool learns from behavior: "students like you tend to click on these things." This is recommendation engine logic — the same mechanism that creates filter bubbles in social media. In a student services context, it means the tool progressively narrows what each student is exposed to based on what they've already done, reinforcing existing patterns rather than expanding opportunity.
- **Option E** is a transparency failure. If the governance team can't answer how the tool personalizes, they can't evaluate its equity implications. That's a governance gap that needs to be closed before deployment.

**Equity implications to surface when C or D is selected:**

"This tool uses student data to personalize what each student sees. This means different students receive different information, recommendations, or opportunities — and the differences are driven by patterns in data that may reflect historical inequities. Before deploying, your institution needs to answer: Could this personalization reproduce segregation, narrow opportunity for specific populations, or create a two-track experience that students can't see?"

---

### MD-02: Student Classification & Segmentation

**Question:** "Does this tool group, classify, or score individual students?"

**What this detects:** Tools that create categories of students — risk scores, behavioral clusters, predicted outcomes, segmentation groups. This is the mechanism behind early alert systems, but it also hides inside registration tools, nudge campaigns, and advising platforms that "prioritize" outreach.

| Option | Label | Description | Escalation |
|--------|-------|-------------|------------|
| A | No classification | The tool treats each interaction independently. It doesn't build student profiles, assign scores, or group students into categories. | None |
| B | Transparent categories | Students are grouped using categories they can see and understand (e.g., major, class standing, enrollment status). No inferred or predicted classifications. | None |
| C | Predictive scoring | The tool assigns scores, risk levels, or predicted outcomes to individual students based on data analysis. Students may not know they've been scored. | **+1 tier.** Force P2 (Equity) ≥ 2. Force P5 (Risk) ≥ 2. Force P7 (Transparency) ≥ 2. |
| D | Behavioral clustering | The tool groups students into segments based on behavioral patterns, predicted characteristics, or inferred attributes. Cluster membership drives what students experience. | **+1 tier.** Force P2 (Equity) ≥ 2. Force P5 (Risk) ≥ 2. Force P7 (Transparency) ≥ 2. Add equity screening flag. |
| E | Unknown | The team doesn't know whether the tool classifies students. | **+1 tier.** Force P7 (Transparency) ≥ 2. Flag as investigation required. |

**What you're looking for:**

- **Option A** means the tool is stateless with respect to student identity. It responds to inputs, not profiles. A FAFSA FAQ bot that answers questions without knowing who's asking is genuinely non-classifying.
- **Option B** uses categories the student already knows about themselves. "You're a nursing major, so here are your degree requirements" is transparent categorization. The student knows why they're seeing what they're seeing.
- **Option C** is predictive analytics territory. The tool has decided something *about* the student that the student may not know — "you have a 67% probability of not completing this semester." This score drives differential treatment: who gets outreach, who gets nudged, who gets flagged. The equity risk is that the predictive model encodes historical patterns of who succeeds and who doesn't — patterns shaped by systemic inequity, not individual capability.
- **Option D** is the most opaque. The tool has created groups that don't correspond to any visible student characteristic. "Cluster 3 students" get one experience; "Cluster 7 students" get another. Nobody — not the student, not the advisor, possibly not even the vendor — can fully explain what defines each cluster or why a student is in one rather than another.
- **Option E** is again a transparency failure that must be resolved.

**Equity implications to surface when C or D is selected:**

"This tool classifies individual students using predictive or behavioral data. Classification drives differential treatment — different students receive different outreach, different resources, or different levels of attention. Before deploying, your institution needs to answer: Has the classification been tested for disparate impact across demographics? Do students know they're being classified? Can they see and contest their classification? What happens to a student who is misclassified?"

---

### MD-03: Autonomous Action & Outreach

**Question:** "Can this tool take actions or contact students without a human initiating it for that specific student?"

**What this detects:** Tools that act on their own — sending messages, triggering workflows, escalating cases, adjusting recommendations — without a human deciding "yes, do this for this student right now." This is the mechanism that turns a passive tool into an active agent in the student's experience.

| Option | Label | Description | Escalation |
|--------|-------|-------------|------------|
| A | Student-initiated only | The tool only acts when a student asks it to. No outbound contact, no triggered workflows, no autonomous actions. | None |
| B | Staff-initiated | Staff use the tool to take actions (send messages, generate reports, update records). The tool doesn't act without a staff member deciding to use it for a specific purpose. | None |
| C | Rule-based triggers | The tool automatically takes predefined actions when conditions are met (e.g., sends a reminder when a deadline approaches, flags a student when GPA drops below threshold). Rules are set by staff but execute without per-student human review. | **+1 tier** (only if current tier is 1). Force P3 (Human Authority) ≥ 2. Force P5 (Risk) ≥ 2. |
| D | Autonomous outreach | The tool initiates contact with students, triggers intervention workflows, or takes actions based on its own analysis — without a human reviewing and approving the action for that specific student. | **+1 tier.** Force P3 (Human Authority) ≥ 2. Force P5 (Risk) ≥ 2. Force P7 (Transparency) ≥ 2. |
| E | Autonomous with cascading effects | The tool can trigger actions that themselves trigger further actions (e.g., flagging a student triggers an advisor assignment, which triggers an automated outreach email, which triggers a hold if unresponded). Multiple steps execute without human review of the chain. | **+2 tiers** (cap at Tier 3). Force P3 (Human Authority) ≥ 2. Force P5 (Risk) ≥ 2. Force P7 (Transparency) ≥ 2. Add no-go flag for review. |

**What you're looking for:**

- **Option A** is the safest pattern. The tool is a resource the student chooses to use. It doesn't reach into the student's life uninvited.
- **Option B** keeps humans in the loop per-action. A counselor uses the tool to draft an email — the counselor decides who to contact and reviews the message. The tool is an instrument, not an agent.
- **Option C** is where many "helpful" tools live. Deadline reminders, GPA alerts, registration nudges. Each individual rule may be benign, but the cumulative effect is that the institution is monitoring student behavior and acting on it without the student requesting help. The equity risk is differential targeting: which students trigger the rules, and what does it feel like to be the student who gets five automated "we're worried about you" messages in a week?
- **Option D** means the tool is making decisions about when and how to intervene in students' lives. An early alert system that auto-generates counselor outreach is doing this. A nudge campaign that decides which students need a "don't forget to register" message is doing this. The tool has become an autonomous actor in the student-institution relationship.
- **Option E** is agentic AI in the full sense. Actions cascade. The tool doesn't just flag — it initiates a chain of institutional responses. This is the highest-risk mechanism because no single human reviewed the full chain of consequences for any individual student. A misclassification in step 1 cascades through steps 2, 3, and 4 before anyone notices.

**Equity implications to surface when D or E is selected:**

"This tool can contact students or trigger institutional actions without a human approving each action for each student. This means the tool is making decisions about who receives attention and what kind — decisions that were previously made by counselors, advisors, or staff who knew the student. Before deploying, your institution needs to answer: Who is accountable when the autonomous action is wrong? Can a student opt out of automated outreach? What happens when autonomous actions compound — a student flagged by one system gets escalated by another, creating an institutional response disproportionate to the actual situation?"

---

## Escalation Logic

### Tier Adjustment Rules

Tier adjustments from mechanism detection are **additive** across all three questions but **capped at Tier 3**:

```
adjusted_tier = min(3, default_tier + MD01_escalation + MD02_escalation + MD03_escalation)
```

Examples:
- SS-04 Chatbot (default Tier 1) + profile-based personalization (MD-01 C, +1) = **Tier 2**
- SS-04 Chatbot (default Tier 1) + behavioral pattern-matching (MD-01 D, +1) + autonomous outreach (MD-03 D, +1) = **Tier 3**
- SS-08 Career Services (default Tier 1) + predictive scoring (MD-02 C, +1) = **Tier 2**
- SS-02 Early Alert (default Tier 3) + any mechanism flags = stays **Tier 3** (already max)

### Forced Pillar Requirements

Mechanism flags force minimum pillar scores independent of tier:

| Mechanism Detected | Forced Pillar Requirements |
|---|---|
| Profile-based personalization (MD-01 C) | P2 ≥ 2, P7 ≥ 2 |
| Behavioral pattern-matching (MD-01 D) | P2 ≥ 2, P7 ≥ 2 |
| Predictive scoring (MD-02 C) | P2 ≥ 2, P5 ≥ 2, P7 ≥ 2 |
| Behavioral clustering (MD-02 D) | P2 ≥ 2, P5 ≥ 2, P7 ≥ 2 |
| Autonomous outreach (MD-03 D) | P3 ≥ 2, P5 ≥ 2, P7 ≥ 2 |
| Cascading autonomous actions (MD-03 E) | P3 ≥ 2, P5 ≥ 2, P7 ≥ 2 |
| Unknown (any question) | P7 ≥ 2 |

If a forced pillar scores below the required minimum during pillar scoring, the Navigator should surface a warning: "This pillar scored below the minimum required by the tool's mechanism profile. This gap must be resolved before deployment."

### Equity Screening Flag

When MD-01 D or MD-02 D is selected, an additional equity screening question is injected into the pillar scoring for P2:

> "Has your institution tested whether this tool's personalization or classification produces different outcomes for different student populations? Specifically: Do students of color, first-generation students, Pell-eligible students, or multilingual students receive systematically different recommendations, classifications, or levels of service?"

This question does not affect scoring directly — it forces the evaluator to confront the equity implications of the mechanism before they score P2.

---

## State Model

Add to the Navigator state object:

```javascript
mechanismProfile: {
  md01: null,          // 'a', 'b', 'c', 'd', or 'e'
  md02: null,          // 'a', 'b', 'c', 'd', or 'e'
  md03: null,          // 'a', 'b', 'c', 'd', or 'e'
  tierAdjustment: 0,   // computed: sum of escalations
  adjustedTier: null,   // computed: min(3, default + adjustment)
  forcedPillars: {},    // computed: e.g., { P2: 2, P7: 2 }
  equityFlag: false,    // computed: true if MD-01 D or MD-02 D
  unknownFlags: []      // which questions answered 'e'
}
```

### Computation

```javascript
function computeMechanismProfile() {
  var mp = state.mechanismProfile;
  var esc = 0;
  var forced = {};
  var eqFlag = false;
  var unknowns = [];

  // MD-01: Behavioral Pattern-Matching
  if (mp.md01 === 'c') {
    esc += 1;
    forced.P2 = Math.max(forced.P2 || 0, 2);
    forced.P7 = Math.max(forced.P7 || 0, 2);
  } else if (mp.md01 === 'd') {
    esc += 1;
    forced.P2 = Math.max(forced.P2 || 0, 2);
    forced.P7 = Math.max(forced.P7 || 0, 2);
    eqFlag = true;
  } else if (mp.md01 === 'e') {
    esc += 1;
    forced.P7 = Math.max(forced.P7 || 0, 2);
    unknowns.push('MD-01');
  }

  // MD-02: Student Classification
  if (mp.md02 === 'c') {
    esc += 1;
    forced.P2 = Math.max(forced.P2 || 0, 2);
    forced.P5 = Math.max(forced.P5 || 0, 2);
    forced.P7 = Math.max(forced.P7 || 0, 2);
  } else if (mp.md02 === 'd') {
    esc += 1;
    forced.P2 = Math.max(forced.P2 || 0, 2);
    forced.P5 = Math.max(forced.P5 || 0, 2);
    forced.P7 = Math.max(forced.P7 || 0, 2);
    eqFlag = true;
  } else if (mp.md02 === 'e') {
    esc += 1;
    forced.P7 = Math.max(forced.P7 || 0, 2);
    unknowns.push('MD-02');
  }

  // MD-03: Autonomous Action
  if (mp.md03 === 'c') {
    if (state.useCase.default_risk_tier === 1) esc += 1;
    forced.P3 = Math.max(forced.P3 || 0, 2);
    forced.P5 = Math.max(forced.P5 || 0, 2);
  } else if (mp.md03 === 'd') {
    esc += 1;
    forced.P3 = Math.max(forced.P3 || 0, 2);
    forced.P5 = Math.max(forced.P5 || 0, 2);
    forced.P7 = Math.max(forced.P7 || 0, 2);
  } else if (mp.md03 === 'e') {
    esc += 2;
    forced.P3 = Math.max(forced.P3 || 0, 2);
    forced.P5 = Math.max(forced.P5 || 0, 2);
    forced.P7 = Math.max(forced.P7 || 0, 2);
  }

  mp.tierAdjustment = esc;
  mp.adjustedTier = Math.min(3, (state.useCase.default_risk_tier || 2) + esc);
  mp.forcedPillars = forced;
  mp.equityFlag = eqFlag;
  mp.unknownFlags = unknowns;
}
```

---

## UX Rendering

### View: Mechanism Detection (new view between Dependency Profile and Risk Tier)

**Header:** "How Does This Tool Work?"

**Subhead:** "These three questions check whether the tool uses mechanisms that elevate governance requirements — regardless of what category it falls in. A chatbot that personalizes based on student behavior needs different governance than one that answers FAQs."

**Layout:** One question per card, same interaction pattern as dependency profile questions (click to select, show description and "what you're looking for" on selection).

**Progress bar:** Shared with the overall assessment progress, positioned between dependency profile and risk tier.

### Transition to Risk Tier

When all three mechanism questions are answered, compute the mechanism profile. If the tier has been adjusted, show an interstitial result before the risk tier view:

**If tier adjusted:**

> **Mechanism Profile: Risk Tier Adjusted**
>
> Based on your answers, this tool uses [behavioral pattern-matching / predictive student scoring / autonomous outreach]. These mechanisms elevate the risk tier from **Tier [X]** to **Tier [Y]** because [specific reason].
>
> [Show which pillar minimums are now forced]
>
> [Continue to Risk Tier →]

The risk tier view then shows the *adjusted* tier as the default, with the original category-based tier noted for reference. The user can still override, but overriding *downward* from a mechanism-adjusted tier requires justification (same pattern as the existing override reason box).

**If no adjustment:**

> **Mechanism Profile: No Adjustment Needed**
>
> This tool's mechanisms don't elevate the risk tier beyond its category default. Proceeding with **Tier [X]** as assigned.
>
> [Continue to Risk Tier →]

### Integration with Profile View

The mechanism profile appears in the Governance Profile output:

- Show mechanism badges next to the tier badge (e.g., "Pattern-Matching Detected", "Predictive Scoring", "Autonomous Outreach")
- If equity flag is set, show a callout: "This tool's mechanism has equity implications that require specific attention during P2 evaluation."
- Unknown flags show as investigation items: "The governance team could not determine how this tool [personalizes / classifies / acts autonomously]. This must be resolved before deployment."

### Integration with Pillar Scoring

During pillar scoring, if a forced pillar minimum exists:

- Show a banner at the top of that pillar's scoring view: "This pillar has a minimum score of 2 required by the tool's mechanism profile. A score of 1 will be flagged as a deployment blocker."
- If the user scores below the forced minimum, show an inline warning (same pattern as existing no-go warnings): "Warning: This pillar scored below the mechanism-required minimum. This gap must be documented and resolved before deployment."
- Carry forward to the no-go checklist as a mechanism-derived flag (similar to how pillar scores currently auto-flag no-go criteria).

---

## Governance Profile & Roadmap Output

### Executive Summary Addition

Append to the executive summary template:

> "Mechanism profile: [list detected mechanisms or 'No elevated mechanisms detected']. [If adjusted:] Risk tier was elevated from Tier [X] to Tier [Y] based on mechanism detection. [If equity flag:] Equity-sensitive mechanisms detected — disaggregated impact analysis recommended before deployment."

### Roadmap Integration

For tools with mechanism flags, add a mechanism-specific section to the "Before You Deploy" requirements:

**Pattern-matching or clustering detected:**
- Conduct a personalization audit: document what data drives personalization and what different students see
- Test for differential outcomes across demographics (Pell, first-gen, multilingual, students of color)
- Establish a process for students to see and reset their personalization profile
- Review at 90 days whether personalization patterns reproduce existing inequities

**Predictive scoring detected:**
- Document the scoring model's inputs and weights (or require vendor to disclose)
- Test false positive/negative rates disaggregated by demographics
- Establish student right to see and contest their score
- Monitor whether score distributions shift over time across demographics

**Autonomous outreach detected:**
- Document the full action chain: what triggers → what happens → who's affected → who reviews
- Establish student opt-out from automated outreach without penalty
- Monitor outreach volume per student to prevent alert fatigue or stigma
- Test what happens when the autonomous action is wrong — is there a correction mechanism?

**Cascading autonomous actions detected:**
- Map the complete cascade: every action that can trigger another action
- Identify single points of failure where misclassification compounds
- Require human checkpoint before cascade progresses past [defined step]
- Conduct quarterly review of cascade outcomes disaggregated by demographics

---

## Design Principles

1. **Mechanism detection is not punishment.** Every option has a "what you're looking for" description that legitimizes the answer. A tool that uses behavioral pattern-matching isn't bad — it requires more governance. The screen detects, it doesn't judge.

2. **The tier adjustment is transparent.** The user sees exactly why the tier changed and which mechanism caused it. No black box. This builds trust in the Navigator's recommendations.

3. **"Unknown" is the most important answer.** If the governance team can't answer how the tool personalizes, classifies, or acts autonomously, that's the most critical finding. It means they're about to deploy a tool whose mechanism they don't understand. The Navigator treats this seriously but constructively — it's an investigation item, not a stop sign.

4. **Mechanism detection compounds with dependency profiling.** A tool that is high-dependency AND uses behavioral pattern-matching is qualitatively different from either characteristic alone. The Navigator's architecture now captures both dimensions independently and lets them combine in the governance profile.

5. **This solves the "Campus Life Recommender" problem at the system level.** Instead of adding named use cases for every tool that might hide equity risk, the Navigator asks three mechanism questions that surface the risk regardless of category. SS-04 stays SS-04 — but if the chatbot pattern-matches, the Navigator catches it.
