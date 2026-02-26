# Navigator v2: Claude Integration Logic

## The Simple Question

Where does Claude sit in the Navigator flow, and what does the delivery actually look like?

---

## Current Flow (from your User Journey diagram)

Three entry paths converge on a shared pipeline:

```
ROUTING PATH:   Landing → Step 0 (8 Qs) → Recommendations → Use Case → ...
QUICK PATH:     Landing → Archetype Selector → Use Case → ...
FULL PATH:      Landing → Use Case → ...

                              ↓ (all paths merge here)

                 Screening → Result → Dependency Profile →
                 Mechanism Detection → Risk Tier → Scoring →
                 No-Go Check → Profile → Roadmap
```

---

## Where Claude Sits vs. Where It Doesn't

```
┌─────────────────────────────────────────────────────────────────┐
│                     CLAUDE-ASSISTED NODES                       │
│                  (current knowledge of tools)                   │
│                                                                 │
│   ┌──────────┐   ┌──────────────┐   ┌───────────────┐          │
│   │  Step 0   │   │  Screening   │   │  Mechanism    │          │
│   │ (routing) │   │              │   │  Detection    │          │
│   └──────────┘   └──────────────┘   └───────────────┘          │
│                                                                 │
│   Claude identifies unfamiliar tools, maps them to framework    │
│   categories, surfaces how they actually work technically.      │
│   Framework categories stay fixed. Claude does the matching.    │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                  DETERMINISTIC FRAMEWORK NODES                  │
│                (institutional value judgments)                   │
│                                                                 │
│   ┌──────────┐  ┌──────────┐  ┌────────┐  ┌─────────────────┐  │
│   │ Risk Tier│  │ Scoring  │  │ No-Go  │  │Profile + Roadmap│  │
│   │ (logic)  │  │ (pillars)│  │ Check  │  │   (output)      │  │
│   └──────────┘  └──────────┘  └────────┘  └─────────────────┘  │
│                                                                 │
│   Visible algorithms. Contestable weights. Human-owned values.  │
│   A faculty senate can look at these and argue about them.      │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                      HYBRID NODES                               │
│                                                                 │
│   ┌──────────────────┐   ┌──────────────────┐                   │
│   │ Dependency Profile│   │ Archetype Selector│                  │
│   └──────────────────┘   └──────────────────┘                   │
│                                                                 │
│   Questions are fixed (framework-owned).                        │
│   Claude can help interpret ambiguous answers or surface         │
│   context the user might not know about their own tool.         │
└─────────────────────────────────────────────────────────────────┘
```

---

## What Claude Actually Does at Each Node

### Step 0 — Tool Recognition & Routing

User says: *"We're looking at deploying Nectir for student engagement"*
or: *"Our vendor is pitching something called Ivy.ai"*

**Claude's job:**
- Recognize the tool (even if it launched last month)
- Map it to existing use case categories (SS-01 through SS-10)
- Surface what the tool actually does vs. what the vendor says it does
- Route to the correct use case path

**Claude does NOT:**
- Decide whether the tool is appropriate
- Assign a risk tier
- Make a recommendation

**What this replaces:** A static dropdown that can only list tools you've already catalogued.

---

### Screening — Factual Assessment

User reaches screening for their selected use case.

**Claude's job:**
- Answer factual questions about the tool's behavior:
  - Does it store student data? Where?
  - Does it generate content or retrieve it?
  - Does it integrate with SIS/LMS?
  - Has it had publicized incidents?
- Pre-fill screening answers where Claude has high confidence
- Flag answers as "Claude-suggested — verify with vendor" vs. "user-confirmed"

**Claude does NOT:**
- Score the screening
- Decide pass/fail
- Override user answers

---

### Mechanism Detection — Technical Analysis

The three mechanism questions (MD-01, MD-02, MD-03) ask *how* the tool works.

**Claude's job:**
- Help users answer questions they genuinely can't answer themselves:
  - "How does this tool decide what to show each student?" → Claude can explain
    the tool's actual personalization approach based on its knowledge
  - "Does this tool classify or score students?" → Claude can identify whether
    the vendor's architecture includes predictive models
- Surface the "Unknown" answer honestly when neither Claude nor the user knows

**Claude does NOT:**
- Assign the escalation tier
- Decide the forced pillar requirements
- Those are deterministic outputs of the mechanism detection logic

---

### Nodes Where Claude Stays Out

**Risk Tier:** `adjusted_tier = min(3, default_tier + mechanism_escalation)`
This is arithmetic. It's visible. It's auditable. No AI needed.

**Pillar Scoring:** The Nine Pillars are the institution's values made explicit.
The rubrics (1/2/3) are the institution's standards. A faculty member scores these
based on their knowledge of their own institution. Claude can't do this better
than the human who works there.

**No-Go Check:** Hard lines. "FERPA violation = stop." "No student opt-out = stop."
These are institutional policy decisions. They must be visible, contestable, and
owned by the governance body. Not by a model.

**Profile + Roadmap:** Deterministic outputs from scoring. The logic is:
if score < threshold, flag gap. If gap flagged, surface template. If tier = X,
show tier-X provisions. This is just rendering.

---

## The Practical Architecture

### What Gets Delivered to Schools

```
┌──────────────────────────────────────────────────────┐
│              NAVIGATOR v2 (the tool)                 │
│                                                      │
│  ┌────────────────────────────────────────────────┐  │
│  │  FRAMEWORK LAYER (static, human-owned)         │  │
│  │                                                │  │
│  │  - 10 use case categories + default tiers      │  │
│  │  - 9 pillar scoring rubrics                    │  │
│  │  - 3 mechanism detection questions             │  │
│  │  - 4 dependency profiling questions            │  │
│  │  - 8 no-go criteria                            │  │
│  │  - Tier escalation logic (arithmetic)          │  │
│  │  - Forced pillar minimums (lookup table)       │  │
│  │  - Template library (T01-T14)                  │  │
│  │  - Roadmap generation logic                    │  │
│  │  - HUMANS framework mapping (CA only)          │  │
│  │                                                │  │
│  │  This is the governance framework.             │  │
│  │  It works WITHOUT Claude.                      │  │
│  │  Schools own it. Senates can modify it.        │  │
│  └────────────────────────────────────────────────┘  │
│                                                      │
│  ┌────────────────────────────────────────────────┐  │
│  │  AI AUGMENTATION LAYER (optional, swappable)   │  │
│  │                                                │  │
│  │  System prompt (yes, basically a claude.md)    │  │
│  │  that encodes:                                 │  │
│  │                                                │  │
│  │  - The 10 use case definitions so Claude       │  │
│  │    can map unfamiliar tools to categories      │  │
│  │  - The mechanism detection criteria so Claude   │  │
│  │    can help users answer "how does this work"  │  │
│  │  - The screening checklist so Claude can        │  │
│  │    surface factual tool information             │  │
│  │  - STRICT instructions on what Claude           │  │
│  │    CANNOT do (no scoring, no tier assignment,   │  │
│  │    no no-go decisions, no value judgments)      │  │
│  │                                                │  │
│  │  This layer ENHANCES the framework.            │  │
│  │  It does NOT replace it.                       │  │
│  │  If Anthropic disappears tomorrow, the         │  │
│  │  framework still works — just with a static    │  │
│  │  tool dropdown instead of AI routing.          │  │
│  └────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────┘
```

### The System Prompt (Sketch)

This is what the `claude.md` or system prompt would actually contain:

```
You are the AI assistant for the AQL Ethical AI Governance Navigator.

YOUR ROLE:
You help community college governance teams identify, classify, and
understand AI tools so they can evaluate them using the Navigator
framework. You are a PERCEPTION LAYER — you help users SEE tools
clearly. You are NOT a DECISION LAYER — you never make governance
judgments.

YOU CAN:
- Identify AI tools by name, vendor, or description
- Map tools to the Navigator's 10 use case categories (SS-01 to SS-10)
- Explain how a tool technically works (personalization, classification,
  autonomous action) to help users answer Mechanism Detection questions
- Surface factual information about tools (data handling, integrations,
  known incidents) to help users complete screening
- Clarify what Navigator questions are asking when users are confused
- Flag when you're uncertain: "I don't have reliable information about
  this tool's data practices — you should verify directly with the vendor"

YOU CANNOT:
- Assign or recommend risk tiers
- Score pillars
- Determine no-go outcomes
- Override or adjust framework logic
- Make recommendations about whether a tool should be adopted
- Express opinions on institutional policy decisions
- Provide legal or compliance advice

WHEN ASKED TO DO SOMETHING YOU CANNOT DO:
Explain that this is a governance decision that belongs to the
institution's evaluation team, and point to the specific Navigator
step where that decision gets made.

USE CASE CATEGORIES:
[SS-01 through SS-10 definitions inserted here]

MECHANISM DETECTION CRITERIA:
[MD-01, MD-02, MD-03 option descriptions inserted here]

SCREENING DIMENSIONS:
[Factual checklist items inserted here]

DEPENDENCY PROFILE QUESTIONS:
[Four capability/dependency questions inserted here]
```

---

## Why This Architecture, Not "Just Claude"

| Concern | "Just Claude" | Framework + Claude Layer |
|---------|---------------|--------------------------|
| Legitimacy | "The AI told us it's okay" | "Our framework scored it Tier 2; here's why" |
| Contestability | Can't argue with a prompt | Can argue with a rubric in a faculty meeting |
| Vendor lock-in | Requires Anthropic subscription | Framework works offline; AI is optional |
| Fundability | CFF funds an API subscription? | CFF funds institutional governance capacity |
| Velocity | Claude absorbs change, but opaquely | Claude absorbs tool changes; framework absorbs value changes at governance pace |
| Auditability | "What did the AI consider?" | Scoring logic is visible arithmetic |

---

## What Changes Fast vs. What Changes Slow

```
CHANGES WEEKLY                          CHANGES ANNUALLY
(Claude handles this)                   (Governance handles this)
                                        
- New AI tools launch                   - Pillar weights
- Existing tools add features           - No-go criteria
- Vendor claims shift                   - Risk tier thresholds  
- Regulatory guidance updates           - Template content
- Tool integrations change              - Forced pillar minimums
- Incident reports surface              - HUMANS mapping
                                        - Use case category definitions
        ↓                                       ↓
  AI augmentation layer               Framework layer
  (system prompt updated               (governance body approves
   by AQL as needed)                    changes through process)
```

---

## Summary

The delivery is:

1. **A standalone framework tool** (HTML/JS, deployable to GitHub Pages, works without any AI) containing all scoring logic, rubrics, templates, and roadmap generation.

2. **An optional AI augmentation layer** (yes, effectively a claude.md / system prompt) that makes Step 0, Screening, and Mechanism Detection dramatically more useful by handling tool recognition and factual technical analysis.

3. **A clear boundary** between what the AI can touch (perception of the external tool landscape) and what it can't (institutional value judgments encoded in the framework).

The framework is the product. Claude is the lens.
