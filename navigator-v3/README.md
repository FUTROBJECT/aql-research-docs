# Navigator v3.1 — Build Instructions

## What This Is

Navigator v3.1 is an AI-augmented governance assessment tool for community college Student Services AI. It combines the full v3 assessment flow (routing, screening, dependency profiling, mechanism detection, scoring, roadmap generation) with a simulated AI chat panel that demonstrates what Claude integration would look like in production.

## Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated
- This repository cloned locally
- Terminal access from the `navigator-v3/` directory

## Agent Architecture

Three agents run sequentially. Each produces an output that the next agent depends on.

```
┌─────────────┐     ┌──────────────┐     ┌──────────────┐
│  Spec Agent  │ ──→ │ Content Agent │ ──→ │ Builder Agent │
│              │     │              │     │              │
│ Reads:       │     │ Reads:       │     │ Reads:       │
│ - concept    │     │ - spec       │     │ - spec       │
│ - wireframe  │     │ - v2 content │     │ - content    │
│ - v2 spec    │     │ - wireframe  │     │ - wireframe  │
│ - v2 proto   │     │              │     │ - v2 proto   │
│              │     │ Produces:    │     │              │
│ Produces:    │     │ content.json │     │ Produces:    │
│ spec.md      │     │              │     │ index.html   │
└─────────────┘     └──────────────┘     └──────────────┘
```

## How to Run

### Step 1: Spec Agent

```bash
cd /path/to/aql-research-docs/navigator-v3
claude --agent .claude/agents/navigator-v3-spec.md
```

**Wait for it to complete.** It will produce `navigator-v3-spec.md` and write progress to `progress/spec-status.md`.

Verify the output exists before proceeding:
```bash
ls -la navigator-v3-spec.md
```

### Step 2: Content Agent

```bash
claude --agent .claude/agents/navigator-v3-content.md
```

**Wait for it to complete.** It will produce `navigator-v3-content.json` and write progress to `progress/content-status.md`.

Verify the JSON is valid:
```bash
python3 -c "import json; json.load(open('navigator-v3-content.json')); print('Valid JSON')"
```

### Step 3: Builder Agent

```bash
claude --agent .claude/agents/navigator-v3-builder.md
```

This is the longest run. It will produce `index.html` and write progress to `progress/build-status.md`.

Test the output:
```bash
open index.html  # macOS
# or
xdg-open index.html  # Linux
```

## Testing the Prototype

### Quick Smoke Test
1. Open `index.html` in a browser
2. Click "Help Me Choose" (routing path)
3. Answer 8 routing questions
4. Select a recommended use case
5. Complete screening → dependency → mechanism detection → scoring → no-go → profile → roadmap
6. Verify the roadmap generates correctly

### AI Chat Panel Test
1. On the Use Case screen, type "Mainstay" in the AI tool input
2. Verify the AI suggests SS-06 (Nudge Campaigns)
3. Accept the suggestion
4. On Screening, verify AI pre-fills appear with teal tags
5. On Mechanism Detection, verify AI context note appears
6. On Pillar Scoring, verify the chat panel is collapsed with "institutional judgment" label

### Known Tool Flows
- **Mainstay** → SS-06, Tier 2, nudge campaigns
- **EAB Navigate** → SS-02, Tier 3, early alert
- **Nectir** → SS-05, Tier 2, tutoring

## File Structure

```
navigator-v3/
├── .claude/
│   └── agents/
│       ├── navigator-v3-spec.md      ← Spec agent definition
│       ├── navigator-v3-content.md   ← Content agent definition
│       └── navigator-v3-builder.md   ← Builder agent definition
├── CONTEXT.md                        ← Shared context (all agents read this)
├── README.md                         ← This file
├── progress/                         ← Agent progress tracking (auto-created)
│   ├── spec-status.md
│   ├── content-status.md
│   └── build-status.md
│
│   ── PRODUCED BY AGENTS ──
├── navigator-v3-spec.md              ← Full specification (spec agent output)
├── navigator-v3-content.json         ← All content + AI simulation (content agent output)
├── index.html                        ← The working prototype (builder agent output)
│
│   ── EXISTING REFERENCE FILES ──
├── navigator-v3-concept.html         ← Design document (5 tabs)
├── navigator-v3-chat-panel-wireframe.html  ← AI panel wireframe (4 screens)
└── navigator-claude-integration-logic.md   ← AI boundary rules
```

## Troubleshooting

### Agent can't find source files
The agents reference files relative to `aql-research-docs/`. Make sure you're running from the `navigator-v3/` directory and the parent directory structure is intact.

### Content agent says spec doesn't exist
Run the spec agent first. The content agent depends on `navigator-v3-spec.md`.

### Builder produces [PLACEHOLDER] text
The builder will use placeholder text if the content JSON doesn't exist yet. Run the content agent first.

### JSON parse errors
If the content agent produces invalid JSON, re-run it. You can also try:
```bash
python3 -c "import json; json.load(open('navigator-v3-content.json'))"
```
to see the specific parse error.

## Design Decisions

- **Single-file HTML:** Deployable to GitHub Pages, no build step, works offline
- **Simulated AI:** Pre-scripted responses with keyword matching. Feels real without API costs.
- **DM Sans font:** Cleaner than v2's Plus Jakarta Sans, matches wireframe
- **Collapsed rail on scoring:** The boundary rule made visible. AI deliberately absent during institutional value judgments.
- **4 tool profiles:** Mainstay, EAB Navigate, Nectir, generic fallback. Enough to demonstrate the concept.

## Credits

AQL Labs / FutureObjects Research / College Futures Foundation
