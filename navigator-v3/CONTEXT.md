# Navigator v3.1: Shared Context

Read this entire file before doing anything else. This is the shared reference for all Navigator v3.1 work.

---

## What We're Building

Navigator v3.1 is a fresh, complete interactive web tool that combines:
1. The **full v3 assessment flow** (routing → screening → dependency → mechanism detection → scoring → roadmap)
2. The **AI chat panel wireframe** (contextual AI assistant that appears on appropriate screens and disappears on others)
3. **Simulated AI responses** that feel real without requiring an actual LLM connection

This is a **fresh build**, not a patch on v2. But it inherits v2's design language, content baseline, and proven patterns.

---

## Source Files (Read All Before Starting)

These files are your primary references. They live in the same `aql-research-docs/` directory:

### Design & Architecture References
- `navigator-v3/navigator-v3-concept.html` — The complete v3 design document. 5 tabs: Vision, Framework Architecture, User Journey, AI Integration, Content Architecture. **This is the blueprint.** Read all 5 tabs.
- `navigator-v3/navigator-v3-chat-panel-wireframe.html` — The AI chat panel wireframe. 4 interactive screens showing exactly how the AI panel appears across Use Case Selection, Screening, Mechanism Detection, and Pillar Scoring. **This is the UI reference.**
- `navigator-v3/navigator-claude-integration-logic.md` — Where Claude sits vs. where it doesn't. The boundary rule. System prompt sketch. **This defines the AI's permissions.**

### v2 Baseline (Inherit From These)
- `navigator/v2/index.html` — The working v2 prototype (124KB). Study its design language: Plus Jakarta Sans + Inter fonts, teal signal color (#0891B2), dark hero, card-based layouts, score button patterns. **Inherit the visual DNA.**
- `navigator-v2-claude-code-agents/navigator-v2/navigator-v2-content.json` — The v2 content JSON (~106KB). Contains all 10 use cases with screening questions, 9 pillars with scoring rubrics, no-go criteria, archetypes, pattern interpretation. **This is the content baseline.**
- `navigator-v2-claude-code-agents/navigator-v2/navigator-v2-spec.md` — The v2 specification. **Reference for logic patterns.**
- `navigator-v2-claude-code-agents/navigator-v2/CONTEXT.md` — The v2 shared context. **Read for voice, tone, and design principles.**

### Framework Research (For Content Accuracy)
- `What_224_Frameworks_Told_Us.html` — Research summary
- `navigator-crosswalk-combined.html` — Framework crosswalk
- `cccco-ai-mobilization-framework.html` — California HUMANS framework

---

## The Complete v3.1 Flow

Three entry paths converge on a shared pipeline:

```
ROUTING PATH:   Landing → Step 0 (8 Qs) → Recommendations → Use Case → ...
QUICK PATH:     Landing → Archetype Selector → Use Case → ...
FULL PATH:      Landing → Use Case Selector → ...

                              ↓ (all paths merge here)

                 Screening → Dependency Profile → Mechanism Detection →
                 Risk Tier (auto-calculated) → Pillar Scoring →
                 No-Go Check → Governance Profile → Roadmap
```

### Screen Inventory (12+ views)

| # | Screen | AI Panel | Purpose |
|---|--------|----------|---------|
| 1 | Landing / Hero | Hidden | Entry point, 3 CTAs, stats, how-it-works |
| 2 | Step 0: Routing | Visible | 8 institutional context questions → ranked use case recommendations |
| 3 | Use Case Selection | Visible | 10 use case cards + AI tool input + suggestion card |
| 4 | Screening | Visible | 4-5 questions per use case, AI pre-fills where confident |
| 5 | Dependency Profile | Visible (hybrid) | 4 universal questions (D1-D4), produces Low/Med/High profile |
| 6 | Mechanism Detection | Visible | MD-01/02/03, AI context notes + option highlighting |
| 7 | Risk Tier | Collapsed | Auto-calculated: `adjusted_tier = min(3, default_tier + mechanism_escalation)` |
| 8 | Pillar Scoring | Collapsed | 9 pillars, 1-3 scoring, "AI not available — institutional judgment" |
| 9 | No-Go Check | Collapsed | 8 hard-stop criteria |
| 10 | Governance Profile | Collapsed | Scorecard, patterns, dependency badge |
| 11 | Roadmap | Collapsed | Conditionally assembled deliverable |
| 12 | About / Methodology | Hidden | Framework explanation, research base, credits |

---

## Where AI Sits vs. Where It Doesn't

This is the core architectural principle. Read the integration logic doc for the full rationale.

### AI-Assisted Nodes (Perception Layer)
- **Step 0 — Tool Recognition & Routing:** Claude identifies tools, maps to categories, surfaces how they work
- **Screening — Factual Assessment:** Claude pre-fills factual answers ("Does it store PII?"), flags confidence level
- **Mechanism Detection — Technical Analysis:** Claude explains how the tool works, highlights likely mechanism options

### Deterministic Framework Nodes (Human-Owned)
- **Risk Tier:** Arithmetic. Visible. Auditable. No AI.
- **Pillar Scoring:** Institutional value judgments. Faculty scores these.
- **No-Go Check:** Hard lines. Policy decisions. Must be contestable.
- **Profile + Roadmap:** Deterministic outputs from scoring.

### The Boundary Rule
AI sits behind nodes requiring *current knowledge about external world* (what tools exist, how they work).
AI stays out of nodes requiring *institutional value judgments* (what's acceptable, how to weight priorities).
The first category changes weekly. The second changes deliberately through governance.

---

## Simulated AI Architecture

Since we can't connect to an actual LLM, the AI chat panel uses a **pre-scripted response engine** that feels real:

### Response Bank Structure
Content JSON includes an `ai_simulation` section:
```json
{
  "ai_simulation": {
    "tools": {
      "mainstay": {
        "display_name": "Mainstay",
        "suggested_use_case": "SS-06",
        "suggested_use_case_reason": "...",
        "screening_prefills": { ... },
        "mechanism_analysis": { ... },
        "conversations": {
          "use_case": [ { "trigger": "...", "response": "..." }, ... ],
          "screening": [ ... ],
          "mechanism": [ ... ]
        }
      },
      "eab_navigate": { ... },
      "nectir": { ... }
    },
    "generic_responses": {
      "use_case": [ ... ],
      "screening": [ ... ],
      "mechanism": [ ... ],
      "unknown_tool": [ ... ]
    },
    "system_messages": {
      "welcome": "...",
      "screening_intro": "...",
      "mechanism_intro": "...",
      "panel_collapsed": "AI not available — institutional judgment"
    }
  }
}
```

### Making It Feel Real
1. **Typing delay:** 800ms-1500ms "thinking" animation before responses appear
2. **Tool-specific responses:** When user mentions "Mainstay", responses reference actual product behavior
3. **Honest gaps:** Some pre-fills deliberately left blank with "I don't have reliable information" messages
4. **Caveat messages:** Every AI response ends with verification prompt
5. **Context awareness:** Chat header changes per screen ("Tool Identification" → "Screening · SS-06")
6. **Conversation continuity:** Messages persist across screens

### Keyword Matching Logic
```
1. User types message
2. Extract keywords (tool names, question topics, "how", "what", "why" patterns)
3. Check: is current tool in the tools bank? → use tool-specific responses
4. Match keywords against conversation triggers for current screen context
5. If match → return matched response with typing delay
6. If no match → return generic response for current screen, interpolating tool name
```

### Pre-scripted Tool Examples (4 fully-developed flows)
- **Mainstay** — Nudge campaigns (SS-06), Tier 2. From the wireframe. Complete conversation for all AI screens.
- **EAB Navigate** — Early alert (SS-02), Tier 3. High-risk flow with complex mechanism detection.
- **Nectir** — AI tutoring (SS-05), Tier 2. Medium-risk flow.
- **Generic/Unknown** — Fallback responses that reference "your tool" and still guide the user helpfully.

---

## Design Language

### Inherit from v2
- **Fonts:** Plus Jakarta Sans (display), Inter (body)
- **Colors:** Teal signal (#0891B2), dark hero (#0C0C0C), orange accent (#D97706)
- **Patterns:** Card-based layouts, score buttons (1/2/3), risk tier badges, stat strip
- **Nav:** Fixed dark top bar, view-based SPA with hash routing

### Add from wireframe
- **Chat panel:** Right sidebar, 320px wide, slides in/out with transition
- **AI accent:** Teal (#0891B2) for AI elements — same as signal color, keeps it cohesive
- **AI states:** Pre-fill tag ("AI-suggested · verify with vendor"), context notes, suggestion cards
- **Collapsed rail:** Gray strip on right with "AI not available" when panel is hidden
- **Chat typography:** DM Sans for chat panel specifically (or use Inter for consistency — builder decides)

### Font Decision
Use **DM Sans** throughout v3.1 (matching the wireframe). It's a cleaner, more modern choice than Plus Jakarta Sans and works well at both display and body sizes. This is a fresh build, so we're not locked to v2's font stack.

---

## Voice and Tone

Same as v2: **WARM AND BLUNT.**

A smart colleague who did the research, tells you what matters, and hands you exactly what you need — warmly, directly, and without wasting your time.

See the v2 CONTEXT.md for the full voice mandate. The v3.1 addition:

### AI Voice (for simulated chat responses)
- First person but never casual: "I" not "we"
- Confident when factual, honest when uncertain
- Always ends with actionable next step or verification prompt
- Never makes governance judgments: "This is a governance decision that belongs to your evaluation team"
- Uses the tool's actual name, not generics: "Mainstay uses behavioral messaging" not "This type of tool uses..."

---

## Technical Stack

- Single-file HTML/CSS/JS (no build tools, no framework, no CDN dependencies beyond Google Fonts)
- All state in a single JS object, serializable to localStorage
- URL hash-based navigation with deep-linking support
- Print CSS for roadmap export
- Mobile-responsive (cards stack, chat panel becomes overlay on mobile)
- Accessible: ARIA labels, keyboard navigation, WCAG 2.1 AA

---

## Use Cases (v3.1 Updated)

| ID | Use Case | Default Tier | Key Change from v2 |
|----|----------|-------------|---------------------|
| SS-01 | AI Advising / Guided Pathways Assistant | 3 (High) | Same |
| SS-02 | Early Alert / Student Risk System | 3 (High) | Same |
| SS-03 | Financial Aid Triage & FAFSA Support | 3 (High) | Same |
| SS-04 | Student-Facing Chatbot / Digital Front Door | 1 (Low) | Same |
| SS-05 | AI Course Tutoring Assistant | 2 (Medium) | Renamed from "AI Tutoring / Learning Support" |
| SS-06 | Nudge Campaigns / Behavioral Messaging | 2 (Medium) | **NEW** — was "Multilingual Support" in v2 |
| SS-07 | AI Tutoring / Learning Support | 2 (Medium) | Renumbered |
| SS-08 | Basic Needs Support & Resource Navigation | 1 (Low) | Renumbered |
| SS-09 | Career Services AI | 1 (Low) | Renumbered |
| SS-10 | Student Journey Mapping / Friction Detection | 2 (Medium) | Same |
| SS-XX | Custom / Other | User assigns | Same |

**Note:** Cross-reference the v3 concept document Tab 5 (Content Architecture) for the definitive use case list. If there's a conflict between v2 content JSON and v3 concept, the v3 concept takes priority.

---

## Dependency Profile (New in v3.1)

4 universal questions that apply to every use case, asked after screening and before mechanism detection.

- **D1:** "What happens if this tool disappears tomorrow?" (1=convenience loss, 2=significant struggle, 3=unable to perform)
- **D2:** "After a year, will users be better at this task without the tool, same, or less capable?" (1=better, 2=same, 3=less)
- **D3:** "Does the tool show users how to navigate, or navigate for them?" (1=shows how, 2=mix, 3=navigates for)
- **D4:** "Is there a point where users are expected to do this without the tool?" (1=yes, 2=not explicitly, 3=no)

Sum → Low (4-5) / Medium (6-8) / High (9-12). Profile drives additional roadmap sections.

---

## Mechanism Detection (New in v3.1)

3 questions that detect hidden risk in *how* the tool works:

- **MD-01: Behavioral Pattern-Matching** — How does the tool decide what to show each student? (5 options: A=same for everyone, B=student-configured, C=profile-based, D=behavioral pattern-matching, E=unknown)
- **MD-02: Student Classification** — Does this tool classify, score, or categorize students? (5 options)
- **MD-03: Autonomous Action** — Does this tool take actions without human approval? (5 options)

Escalation logic: certain answers trigger tier escalation and forced pillar minimums.

---

## What This Is NOT

- Not a restatement of ethical principles
- Not a comprehensive AI policy guide
- Not a procurement checklist
- Not a faculty-facing tool (for institutional leadership)
- Not covering instruction, HR, finance, or operations (Student Services only)
- Not connected to a live LLM (simulated AI only in v3.1)
