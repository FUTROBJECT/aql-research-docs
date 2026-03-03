# Navigator v3.1 Spec Agent

You are a research and specification agent. Your job is to read all source material and produce a single structured specification document for Navigator v3.1.

## First Step

Read these in order:
1. `CONTEXT.md` — the shared project context (read first, it tells you what to read next)
2. `navigator-v3-concept.html` — the full v3 design document (all 5 tabs). This is your primary blueprint.
3. `navigator-v3-chat-panel-wireframe.html` — the AI chat panel wireframe (4 screens). This defines the UI patterns.
4. `navigator-claude-integration-logic.md` — the AI boundary rules and system prompt sketch.
5. `../navigator-v2-claude-code-agents/navigator-v2/navigator-v2-spec.md` — the v2 specification (inherit logic patterns)
6. `../navigator-v2-claude-code-agents/navigator-v2/navigator-v2-content.json` — the v2 content (understand existing data model)
7. `../navigator/v2/index.html` — the working v2 prototype (understand current implementation)

Use `find`, `ls`, and `cat` to locate files if paths aren't exact. The files are in the `aql-research-docs/` directory tree.

## Output

Produce `navigator-v3-spec.md` with these eight sections:

### Section A: Data Model

All data structures the application needs:

- 4 ethical criteria with descriptions
- 9 pillars with: all questions, scoring rubrics (1-3 scale), source citations, forced minimums from mechanism detection
- Criteria → Pillar → HUMANS mapping table
- 11 use cases (SS-01 through SS-10 + custom) with: description, default risk tier, key pillars, equity flag, 4-5 screening questions each, AI pre-fill data structure
- 8 routing questions with scoring logic and feasibility matrix (from v3 concept Tab 3)
- 4 dependency profile questions (D1-D4) with scoring bands
- 3 mechanism detection questions (MD-01, MD-02, MD-03) with 5 options each, escalation logic, forced pillar requirements
- 8 no-go criteria with descriptions and detection logic
- 3 archetype definitions with characteristics
- Scoring interpretation patterns
- Roadmap content assembly rules

### Section B: Step 0 — Routing Flow

The institutional context questionnaire that produces ranked use case recommendations:

- 8 questions (from v3 concept) with response options and scoring
- 5-phase algorithm: signal collection → feasibility gating → archetype derivation → contextual overrides → ranking
- Output: 2-3 ranked use case recommendations with fit explanations
- How AI panel assists during routing (tool recognition, unfamiliar tool mapping)
- Fallback: if routing is skipped, user selects use case directly (same as v2)

### Section C: Step 1 — Identify Flow

Use case selection and screening:

- Use case selector interface (10 cards + custom + AI tool input field)
- AI suggestion card behavior (from wireframe): user describes tool → AI suggests category → user accepts or overrides
- Screening questions per use case (from v2 content JSON, updated per v3 concept)
- AI pre-fill logic: which answers Claude would pre-fill for known tools, confidence tagging, "verify with vendor" states
- GO / PAUSE / NO-GO decision logic

### Section D: Dependency Profile

The 4 universal dependency questions:

- Question definitions (D1-D4 from CONTEXT.md)
- Scoring: sum of 4 questions, range 4-12
- Bands: Low (4-5), Medium (6-8), High (9-12)
- What each band triggers in the roadmap
- AI panel behavior: hybrid node (questions fixed, AI can help interpret ambiguous answers)

### Section E: Mechanism Detection

The 3 mechanism questions that detect hidden risk:

- MD-01: Behavioral Pattern-Matching (5 options, from wireframe)
- MD-02: Student Classification (5 options, from v3 concept)
- MD-03: Autonomous Action (5 options, from v3 concept)
- Escalation logic: which answers trigger tier escalation
- Forced pillar requirements: which answers force specific pillar minimums
- Equity screening flag: which combinations trigger additional equity review
- AI panel behavior: context notes explaining how the tool works, option highlighting
- Tier calculation: `adjusted_tier = min(3, default_tier + mechanism_escalation)`

### Section F: Step 2 — Evaluate Flow

Pillar scoring and no-go check:

- Risk tier display (auto-calculated, override option with "override" badge)
- Per-pillar scoring interface (1-3 with visible rubrics)
- Which pillars mandatory vs. recommended per tier
- Forced pillar minimums from mechanism detection integrated
- No-go trigger logic (8 criteria, two detection paths: screening-derived + score-derived)
- AI panel: **collapsed** on all scoring screens with "AI not available — institutional judgment" rail
- California CC toggle for HUMANS mapping

### Section G: Output Flow (Profile + Roadmap)

- Governance Profile: scorecard, pattern interpretation, dependency badge, mechanism flags
- Roadmap assembly logic (from v3 concept):
  ```
  Archetype + Use Case + Risk Tier + Dependency Profile + Pillar Scores = Roadmap
  ```
- For each combination, define: pre-deployment requirements, RACI sketch, 90-day metrics, review cadence, escalation triggers, decision rules, pillar-specific remediation, toolkit refs, HUMANS alignment (CA only)
- Print/export format
- AI panel: collapsed on output screens

### Section H: AI Simulation Engine

This is the spec for the simulated AI behavior:

- Response bank data structure (per-screen, per-tool, per-topic)
- Keyword matching algorithm (how user input maps to pre-scripted responses)
- Pre-fill logic (which screening/mechanism answers get AI suggestions for which tools)
- Typing animation timing (800ms-1500ms delay)
- Context awareness (chat header updates, conversation persistence across screens)
- 4 tool profiles to develop: Mainstay (SS-06), EAB Navigate (SS-02), Nectir (SS-05), generic fallback
- Fallback behavior when tool is unknown or question is off-topic
- Chat panel UI states: visible (with messages), visible (empty/welcome), collapsed (rail only), hidden (landing/about)

### Section I: Navigation Map

- All views/screens and connections
- URL hash navigation states
- Three entry points and where they converge
- Back/edit flow
- State management schema (complete JS object structure)
- localStorage save/restore
- Mobile responsive behavior (chat panel as overlay)

## Progress Tracking

After completing each section, write a status update to:
```
progress/spec-status.md
```

Create the `progress/` directory if it doesn't exist.

Format:
```
## Section A: Data Model — COMPLETE
[timestamp] — Summary of decisions, gaps flagged.

## Section B: Routing Flow — IN PROGRESS
[timestamp] — Current status.
```

## Constraints

- Read-only for all source files. Do not modify them.
- Your only outputs are `navigator-v3-spec.md` and the progress file.
- If you find ambiguity or missing information, flag with `[DECISION NEEDED: description]` rather than guessing.
- Do not write user-facing copy. That's the content agent's job.
- When the v3 concept and v2 spec conflict, the v3 concept takes priority.
- When the wireframe and v3 concept conflict on UI patterns, the wireframe takes priority (it's more recent).
- Be specific about the AI simulation engine. The builder agent needs exact data structures and matching logic, not hand-waving.
