# Navigator v2: Build Instructions (Updated)

## What Changed

This update adds the **Capability & Dependency Profile** — a novel governance dimension that asks whether AI tools build or erode the capabilities of the people they serve. Four concrete questions produce a dependency profile (Low/Medium/High) that triggers specific governance requirements in the roadmap output.

Files changed:
- `navigator-v2/CONTEXT.md` — added full dependency profile system
- `.claude/agents/navigator-spec.md` — added Section F, updated Sections B/C/D/E
- `.claude/agents/navigator-builder.md` — added dependency UI to Views 3/5/6, updated state object
- `.claude/agents/navigator-content.md` — added `dependency_profile` to JSON schema, added copy guidance

## Directory Structure

```
.claude/agents/
├── navigator-spec.md        ← Agent 1: Research & specification (6 sections, A-F)
├── navigator-builder.md     ← Agent 2: Frontend developer
└── navigator-content.md     ← Agent 3: Content & copy writer

navigator-v2/
├── CONTEXT.md               ← Shared reference (all agents read this first)
├── progress/
│   ├── spec-status.md       ← Agent 1 progress
│   ├── builder-status.md    ← Agent 2 progress
│   └── content-status.md    ← Agent 3 progress
├── navigator-v2-spec.md     ← Agent 1 output
├── navigator-v2-content.json← Agent 3 output
└── index.html               ← Agent 2 output (the Navigator)
```

## Execution Sequence

### Phase 1: Specification

```
claude --agent navigator-spec
```

Prompt:
> Read your agent definition and navigator-v2/CONTEXT.md. Ingest all source files listed. Produce navigator-v2/navigator-v2-spec.md following sections A through F. Update progress after each section.

Check progress:
```bash
cat navigator-v2/progress/spec-status.md
```

All six sections (A-F) should show COMPLETE before proceeding.

### Phase 2: Content and Build

Run content first if possible (so the builder has real copy):

```
claude --agent navigator-content
```

Prompt:
> Read your agent definition, navigator-v2/CONTEXT.md, and navigator-v2/navigator-v2-spec.md. Complete the three-step voice mandate. Then produce navigator-v2/navigator-v2-content.json including the dependency_profile section. Update progress after each section.

Then the builder:

```
claude --agent navigator-builder
```

Prompt:
> Read your agent definition, navigator-v2/CONTEXT.md, and navigator-v2/navigator-v2-spec.md. Build navigator-v2/index.html with all seven views including dependency profile in Views 3, 5, and 6. Use content JSON if available, otherwise use v1 scaffolding with [PLACEHOLDER] flags. Update progress after each view.

### Phase 3: Integration

If the builder started before content was ready:

```
claude --agent navigator-builder
```

Prompt:
> Content JSON is now available at navigator-v2/navigator-v2-content.json. Replace all [PLACEHOLDER] text in index.html. Verify all views render correctly. Test print CSS on View 6. Verify dependency profile flows through from View 3 to View 6.

## Testing

Open `navigator-v2/index.html` in a browser. Walk through:

1. **Full path:** Landing → SS-01 (Advising) → Screening → Dependency questions → Score pillars → Profile → Roadmap → Print
2. **Quick path:** Landing → "Building" archetype → SS-04 (Chatbot) → Dependency questions → Abbreviated scoring → Roadmap
3. **No-go test:** Trigger a no-go criterion → verify red banner stops progression
4. **Dependency Low:** Answer all 4 dependency questions with score=1 → verify green badge, minimal roadmap additions
5. **Dependency High:** Answer all 4 with score=3 → verify red badge, full dependency governance section in roadmap
6. **Dependency High + Tier 3:** SS-02 (Early Alert) + all dependency scores=3 → verify capability impact tracking appears
7. **CA toggle:** Enable California → verify HUMANS mapping in scoring and roadmap
8. **Print test:** View 6 → print → clean layout, dependency section included
9. **Save/restore:** Complete assessment → close → reopen → verify state restores including dependency profile

## Source Files Needed

- [ ] v1 Navigator `index.html`
- [ ] Student Services vendor scorecard `.html`
- [ ] Framework Architecture Table `.docx`
- [ ] Student Services Scope Document `.docx`
- [ ] CCCCO AI Mobilization Framework extraction `.html`
- [ ] AQL POV document
- [ ] CFF update document (2026-02-09)
- [ ] Dependency Profile spec (`dependency-profile-screening-questions.md`)
