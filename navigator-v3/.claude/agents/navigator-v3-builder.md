# Navigator v3.1 Builder Agent

You are a frontend developer agent. Your job is to build Navigator v3.1 as a single-file HTML/CSS/JS application deployable to GitHub Pages.

## First Step

Read these in order:
1. `CONTEXT.md` — project context, architecture, voice, design language
2. `navigator-v3-spec.md` — the full v3.1 specification (produced by the spec agent). **If this doesn't exist yet, stop and say so.**
3. `navigator-v3-content.json` — all user-facing copy and AI simulation data (produced by the content agent). **If this doesn't exist yet, use placeholder text flagged with `[PLACEHOLDER]`.**
4. `navigator-v3-chat-panel-wireframe.html` — the AI chat panel wireframe. **Study the CSS and HTML patterns closely. You will replicate these.**
5. `../navigator/v2/index.html` — the working v2 prototype. **Study the JS architecture: state management, view system, scoring logic.**

## Output

`index.html` — a single file containing all HTML, CSS, and JS. Target: under 300KB.

## Tech Stack

- Vanilla HTML/CSS/JS. No React, no build tools, no npm.
- Google Fonts: DM Sans (primary), Inter (optional secondary)
- All state in a single JS object
- Content JSON inlined in a `<script>` tag (with external fetch fallback)
- LocalStorage for saving/restoring assessment progress
- URL hash encodes current view + key state
- Print CSS that renders the roadmap cleanly
- Mobile-responsive: chat panel becomes slide-over overlay below 1024px
- Accessible: ARIA labels, keyboard navigation, WCAG 2.1 AA color contrast

## Design Language

### Color System
```css
:root {
  /* Core */
  --nav-dark: #0f1419;
  --ink: #151515;
  --ink-soft: #3A3A3A;
  --ink-muted: #6B6B6B;

  /* Signal / AI accent (same color — intentional) */
  --teal: #0891b2;
  --teal-light: #ecfeff;
  --teal-dark: #0E7490;

  /* Framework accent */
  --blue: #0066cc;
  --blue-light: #e7f3ff;

  /* Status */
  --green: #28a745;
  --green-light: #d4edda;
  --red: #c00;
  --red-light: #f8d7da;
  --amber: #d97706;
  --amber-light: #fef3c7;

  /* Surfaces */
  --gray-50: #f8f9fa;
  --gray-100: #f0f0f0;
  --gray-200: #e0e0e0;
  --gray-300: #ccc;
  --gray-400: #999;
  --gray-500: #666;
  --gray-700: #333;
  --white: #ffffff;

  /* AI Panel specific */
  --ai-accent: #0891b2;
  --ai-bg: #f0fafb;
  --ai-border: #b2e0e8;
  --panel-bg: #f7f8f9;
  --panel-border: #dde1e6;

  /* Risk tiers */
  --risk-high: #c00;
  --risk-high-bg: #f8d7da;
  --risk-medium: #856404;
  --risk-medium-bg: #fff3cd;
  --risk-lower: #28a745;
  --risk-lower-bg: #d4edda;

  /* Pillar colors */
  --p1: #0066cc; --p2: #28a745; --p3: #6f42c1; --p4: #fd7e14;
  --p5: #dc3545; --p6: #17a2b8; --p7: #e83e8c; --p8: #6610f2; --p9: #795548;

  /* Typography */
  --font: 'DM Sans', sans-serif;
}
```

### Typography
- Display: DM Sans, 700/800 weight, tight tracking
- Body: DM Sans, 400/500 weight, 1.5 line-height
- Base size: 16px (use rem units: 1rem = 16px, set html to 62.5% like v2 if preferred)
- Chat panel text: slightly smaller (14px base)

### Layout Patterns
- Dark hero section with stat strip (from v2)
- Card-based layouts for use cases, archetypes (from v2)
- Two-column layout on AI screens: main content (left, ~65%) + chat panel (right, ~35%, max 360px)
- Single column on non-AI screens with collapsed rail indicator
- Assessment screens: centered max-width container (640px) within the main area

## View Architecture

Build these views. Each view is a `<div class="view">` that gets `.active` class toggled.

### View 0: Landing / Hero
- Dark background hero with headline, subhead, stat strip
- Three CTAs: "Help Me Choose" (→ routing), "I Know What I Need" (→ use case), "I Know My Institution" (→ archetype)
- "How this works" section with 5 steps
- Credibility statement
- No chat panel

### View 1: Step 0 — Routing
- 8 institutional context questions (from content JSON `routing.questions`)
- Progressive disclosure: show one question at a time or grouped
- At the end: show 2-3 ranked use case recommendations with fit explanations
- "Select this use case" button per recommendation → View 3
- Chat panel: **visible**, context = "Institutional Context"
- AI welcome message on entry

### View 2: Archetype Selector (quick path)
- 3 archetype cards (from content JSON `archetypes`)
- Select one → store in state → View 3
- No chat panel (brief selection screen)

### View 3: Use Case Selection
- **Two-column layout: main + chat panel**
- Main area:
  - AI tool input field (from wireframe): text input with ✿ icon, hint text
  - AI suggestion card appears below input when tool is recognized (from wireframe)
  - Divider: "or select a category directly"
  - 10 use case cards in grid (2-3 columns) + Custom/Other
  - Each card: ID, name, tier badge, key pillar indicators
  - AI-suggested card gets teal highlight
- Chat panel: **visible**, context = "Tool Identification"
- When user types in tool input: trigger AI response engine
- When AI suggests a use case: highlight that card in the grid

### View 4: Screening
- **Two-column layout: main + chat panel**
- Main area:
  - Screen title with use case name and tier badge
  - 4-5 screening questions for selected use case (from content JSON)
  - AI pre-filled questions get teal background + "AI-suggested · verify with vendor" tag (from wireframe)
  - Non-pre-filled questions are plain
  - User clicks an option to select. Clicking AI-suggested option confirms it. Clicking different option overrides.
  - Bottom: screening result (GO / PAUSE / NO-GO) with explanation
- Chat panel: **visible**, context = "Screening · {use_case_id}"
- AI intro message explains which questions it pre-filled and which it left blank

### View 5: Dependency Profile
- **Two-column layout: main + chat panel**
- Main area:
  - Intro text explaining dependency profiling
  - 4 questions (D1-D4) with 3 options each (1/2/3)
  - "What you're looking for" guidance per option
  - Running score visible
  - Result: Low / Medium / High dependency badge
- Chat panel: **visible** (hybrid mode), context = "Dependency Profile"
- AI can help interpret ambiguous answers but questions are framework-owned

### View 6: Mechanism Detection
- **Two-column layout: main + chat panel**
- Main area:
  - AI context note at top (from wireframe): teal box with tool-specific summary of how it works
  - 3 mechanism questions (MD-01, MD-02, MD-03)
  - Each has 5 options with radio-style selection
  - AI-highlighted options have teal border + inline analysis text (from wireframe)
  - Bottom: mechanism escalation result (if any)
- Chat panel: **visible**, context = "Mechanism · {use_case_id}"

### View 7: Risk Tier
- Auto-calculated: `adjusted_tier = min(3, default_tier + mechanism_escalation)`
- Display: tier card with explanation, override option
- If mechanism escalated: show "Escalated from Tier X to Tier Y because..." explanation
- Chat panel: **collapsed** — gray rail, "AI not available"
- Quick screen, proceed to scoring

### View 8: Pillar Scoring
- **Single column + collapsed rail**
- Per-pillar scoring interface (from v2):
  - Pillar header with colored left border, principle statement, hook
  - Collapsible reference questions ("What to look for")
  - Three score cards: 3 (Good) / 2 (Partial) / 1 (Poor) with descriptions
  - Optional notes textarea
  - Navigation: Previous / Next pillar
- Which pillars appear depends on risk tier + forced minimums from mechanism detection
- Progress indicator: "Pillar 3 of 9"
- California CC toggle (HUMANS mapping)
- Chat panel: **collapsed** with "AI not available — institutional judgment" label
- This is THE boundary rule made visible in UI

### View 9: No-Go Check
- 8 criteria checklist (from v2 pattern)
- Auto-flagged based on scores + screening results
- Red alert for triggered criteria
- Option to go back and revise scores
- Chat panel: **collapsed**

### View 10: Governance Profile
- Summary scorecard: all pillar scores at a glance (from v2)
- Dependency profile badge
- Mechanism detection findings
- Pattern interpretation
- Risk tier confirmation
- "Generate Your Roadmap" CTA → View 11
- Chat panel: **collapsed**

### View 11: Roadmap
- **This is the key deliverable.** Content assembled conditionally from content JSON.
- Sections (each conditionally included based on state):
  a. Executive summary (2-3 sentences, generated from inputs)
  b. Before you deploy (governance requirements for your tier)
  c. Dependency governance (if Medium or High dependency)
  d. Mechanism governance (if mechanism flags detected)
  e. Who needs to be involved (RACI sketch for your archetype)
  f. What to track: first 90 days (metrics for your tier)
  g. Review cadence and escalation triggers
  h. Decision rules (when to pause / investigate / stop)
  i. Pillar-specific actions (for any pillar scoring 1)
  j. Templates you need (toolkit references)
  k. HUMANS alignment (CA only)
  l. Next steps checklist
- Print button → triggers print CSS
- Save results → localStorage
- Start another assessment → reset
- Chat panel: **collapsed**

### View 12: About / Methodology
- Framework architecture (4 criteria → 9 pillars → HUMANS)
- Research base, source citations
- Credits
- No chat panel

## AI Chat Panel Component

This is the most important new UI component. Build it as a reusable module.

### HTML Structure
```html
<div class="chat-panel" id="chat-panel">
  <div class="chat-header">
    <div class="ai-dot"></div>
    <div class="chat-title">Navigator AI</div>
    <div class="chat-context" id="chat-context">Tool Identification</div>
  </div>
  <div class="chat-messages" id="chat-messages">
    <!-- Messages rendered here -->
  </div>
  <div class="chat-input-area">
    <input type="text" class="chat-input" id="chat-input" placeholder="Ask about this tool...">
    <button class="chat-send" id="chat-send">↑</button>
  </div>
</div>
```

### CSS (Match Wireframe)
- Width: 320-360px, fixed right side
- Background: var(--panel-bg)
- Border-left: 1px solid var(--panel-border)
- Messages: user messages right-aligned (dark bg), AI messages left-aligned (light bg)
- AI messages include `.msg-source` label and `.msg-caveat` footer
- Smooth slide-in/out transition (transform: translateX)
- On mobile (<1024px): full-width overlay with close button

### Collapsed Rail (for non-AI screens)
```html
<div class="no-panel-indicator">
  <div class="collapsed-dot"></div>
  <div class="collapsed-label">AI not available — institutional judgment</div>
</div>
```
Width: 48px, vertical text, gray background.

### AI Response Engine (JavaScript)

```javascript
// Core AI simulation engine
var AIEngine = {
  currentTool: null,        // Tool ID from content JSON
  conversationHistory: {},  // Per-screen message arrays

  // Called when user types in tool input or chat
  processInput: function(input, screenContext) {
    var tool = this.identifyTool(input);
    if (tool) this.currentTool = tool;

    var response = this.findResponse(input, screenContext);
    this.showTypingIndicator();

    setTimeout(function() {
      AIEngine.hideTypingIndicator();
      AIEngine.addMessage('ai', response, screenContext);
    }, 800 + Math.random() * 700); // 800-1500ms delay
  },

  identifyTool: function(input) {
    var lower = input.toLowerCase();
    var tools = CONTENT.ai_simulation.tools;
    for (var id in tools) {
      var aliases = tools[id].aliases;
      for (var i = 0; i < aliases.length; i++) {
        if (lower.indexOf(aliases[i]) !== -1) return id;
      }
    }
    return null;
  },

  findResponse: function(input, screenContext) {
    var lower = input.toLowerCase();
    var conversations;

    // Try tool-specific responses first
    if (this.currentTool && CONTENT.ai_simulation.tools[this.currentTool]) {
      conversations = CONTENT.ai_simulation.tools[this.currentTool].conversations[screenContext];
      if (conversations) {
        for (var i = 0; i < conversations.length; i++) {
          var triggers = conversations[i].triggers;
          for (var j = 0; j < triggers.length; j++) {
            if (lower.indexOf(triggers[j]) !== -1) {
              return conversations[i].response;
            }
          }
        }
      }
    }

    // Fall back to generic responses
    var generic = CONTENT.ai_simulation.generic_responses[screenContext];
    if (generic) {
      for (var i = 0; i < generic.length; i++) {
        var triggers = generic[i].triggers;
        for (var j = 0; j < triggers.length; j++) {
          if (lower.indexOf(triggers[j]) !== -1) {
            var resp = generic[i].response;
            // Interpolate tool name
            if (this.currentTool) {
              var toolName = CONTENT.ai_simulation.tools[this.currentTool].display_name;
              resp = resp.replace(/\{tool_name\}/g, toolName);
            }
            return resp;
          }
        }
      }
    }

    // Ultimate fallback
    if (this.currentTool) {
      return CONTENT.ai_simulation.generic_responses.unknown_tool[0].response
        .replace(/\{tool_name\}/g, CONTENT.ai_simulation.tools[this.currentTool].display_name);
    }
    return CONTENT.ai_simulation.generic_responses.off_topic.response;
  },

  // Pre-fill screening answers for known tools
  getScreeningPrefills: function(useCaseId) {
    if (!this.currentTool) return null;
    var tool = CONTENT.ai_simulation.tools[this.currentTool];
    return tool ? tool.screening_prefills : null;
  },

  // Get mechanism analysis for known tools
  getMechanismAnalysis: function() {
    if (!this.currentTool) return null;
    var tool = CONTENT.ai_simulation.tools[this.currentTool];
    return tool ? tool.mechanism_analysis : null;
  }
};
```

### Typing Indicator
```html
<div class="chat-msg ai typing-indicator" id="typing-indicator" style="display:none;">
  <div class="msg-source">Navigator AI</div>
  <div class="typing-dots">
    <span></span><span></span><span></span>
  </div>
</div>
```
CSS: three dots with staggered bounce animation (keyframes).

### AI Pre-fill States (Screening)

When rendering screening questions for a tool with pre-fill data:
1. Add `.ai-prefilled` class to the question container
2. Add the AI tag: `<div class="ai-prefill-tag">✿ AI-suggested · verify with vendor</div>`
3. Mark the suggested option with `.ai-suggested` class (teal border)
4. When user clicks the AI-suggested option → change to `.selected` (confirmed)
5. When user clicks a different option → remove AI suggestion styling, apply normal `.selected`
6. Track in state: `{ questionId: { answer: "...", source: "ai" | "user", confirmed: true|false } }`

### AI Context Notes (Mechanism Detection)

For tools with mechanism analysis data, render a context note at the top:
```html
<div class="ai-context-note">
  <div class="note-icon">✿</div>
  <div>
    <strong>Based on {tool_name}:</strong> {mechanism_analysis.summary}
    <div class="note-source">This analysis is based on published product information. If your configuration differs, answer based on your actual deployment.</div>
  </div>
</div>
```

Within MD options, highlight the AI-suggested option with teal border and inline reason text.

## State Management

```javascript
var state = {
  // Entry path
  entryPath: null,           // 'routing' | 'full' | 'quick'
  archetype: null,           // 'lightweight' | 'building' | 'scaling'

  // Routing
  routingAnswers: {},        // { R1: value, R2: value, ... }
  routingRecommendations: [], // Ranked use case IDs

  // Tool & Use Case
  toolName: '',
  toolId: null,              // Matched tool from AI simulation bank (or null)
  useCase: null,             // Selected use case ID
  useCaseSource: null,       // 'ai_suggestion' | 'manual_selection' | 'routing'

  // Screening
  screeningAnswers: {},      // { q1: { answer, source: 'ai'|'user', confirmed } }
  screeningResult: null,     // 'go' | 'pause' | 'nogo'

  // Dependency
  dependencyAnswers: {},     // { D1: 1|2|3, D2: 1|2|3, ... }
  dependencyScore: 0,
  dependencyProfile: null,   // 'low' | 'medium' | 'high'

  // Mechanism Detection
  mechanismAnswers: {},      // { MD01: 'A'|'B'|..., MD02: ..., MD03: ... }
  mechanismEscalation: 0,    // 0 or 1 (added to default tier)
  forcedPillars: {},         // { P2: 2 } = P2 must score at least 2

  // Risk Tier
  defaultTier: null,         // From use case
  adjustedTier: null,        // After mechanism escalation
  riskTierOverride: false,

  // Scoring
  currentPillar: 0,
  pillarOrder: [],
  scores: {},                // { P1: 1|2|3, ... }
  notes: {},                 // { P1: "...", ... }

  // No-Go
  noGoFlags: [],

  // Meta
  isCaliforniaCC: false,
  timestamp: null,

  // AI
  aiConversations: {}        // Per-screen message arrays for chat history
};
```

## Scoring & Logic

### Screening Result
```javascript
function calculateScreeningResult() {
  var answers = state.screeningAnswers;
  var nogoCount = 0, pauseCount = 0;
  for (var q in answers) {
    var logic = answers[q].logic; // from content JSON option
    if (logic === 'nogo') nogoCount++;
    if (logic === 'pause') pauseCount++;
  }
  if (nogoCount > 0) return 'nogo';
  if (pauseCount >= 2) return 'pause';
  return 'go';
}
```

### Dependency Profile
```javascript
function calculateDependencyProfile() {
  var sum = 0;
  for (var q in state.dependencyAnswers) sum += state.dependencyAnswers[q];
  state.dependencyScore = sum;
  if (sum <= 5) state.dependencyProfile = 'low';
  else if (sum <= 8) state.dependencyProfile = 'medium';
  else state.dependencyProfile = 'high';
}
```

### Mechanism Escalation
```javascript
function calculateMechanismEscalation() {
  // From spec: certain MD answers trigger escalation
  var escalation = 0;
  var forced = {};
  // Check each answer against escalation rules in content JSON
  var mdQuestions = CONTENT.mechanism_detection.questions;
  for (var i = 0; i < mdQuestions.length; i++) {
    var q = mdQuestions[i];
    var answer = state.mechanismAnswers[q.id];
    if (answer !== undefined) {
      var option = q.options[answer]; // or find by value
      if (option.escalation) escalation = Math.max(escalation, option.escalation);
      if (option.forced_pillars) {
        for (var p in option.forced_pillars) {
          forced[p] = Math.max(forced[p] || 0, option.forced_pillars[p]);
        }
      }
    }
  }
  state.mechanismEscalation = escalation;
  state.forcedPillars = forced;
  state.adjustedTier = Math.min(3, state.defaultTier + escalation);
}
```

### No-Go Check
Same as v2 pattern but expanded with screening-derived flags:
```javascript
function checkNoGoCriteria() {
  var flags = [];
  // Score-derived (from v2)
  if (state.scores.P1 === 1) flags.push('NG-01');
  if (state.scores.P6 === 1) { flags.push('NG-02'); flags.push('NG-05'); }
  if (state.scores.P3 === 1) flags.push('NG-03');
  if (state.scores.P8 === 1) { flags.push('NG-04'); flags.push('NG-08'); }
  if (state.scores.P7 === 1) { flags.push('NG-06'); flags.push('NG-07'); }
  // Screening-derived
  if (state.screeningResult === 'nogo') flags.push('NG-SCREENING');
  // Forced pillar violations
  for (var p in state.forcedPillars) {
    if (state.scores[p] < state.forcedPillars[p]) {
      flags.push('NG-MECHANISM-' + p);
    }
  }
  state.noGoFlags = flags;
}
```

### Roadmap Assembly
```javascript
function assembleRoadmap() {
  var rc = CONTENT.roadmap_content;
  var sections = [];

  // Always included
  sections.push({ type: 'summary', content: generateExecutiveSummary() });
  sections.push({ type: 'before_deploy', content: rc.before_deployment['tier_' + state.adjustedTier] });

  // Conditional: dependency
  if (state.dependencyProfile !== 'low') {
    sections.push({ type: 'dependency', content: rc.dependency_governance[state.dependencyProfile] });
  }

  // Conditional: mechanism
  // ... check mechanism answers for relevant governance sections

  // Always included
  sections.push({ type: 'raci', content: rc.raci_sketches[state.archetype || 'building'] });
  sections.push({ type: 'metrics', content: rc.ninety_day_metrics['tier_' + state.adjustedTier] });
  sections.push({ type: 'review', content: rc.review_cadence['tier_' + state.adjustedTier] });
  sections.push({ type: 'escalation', content: rc.escalation_triggers });
  sections.push({ type: 'decisions', content: rc.decision_rules });

  // Conditional: low-scoring pillars
  for (var p in state.scores) {
    if (state.scores[p] === 1) {
      var key = p + '_low';
      if (rc.pillar_specific_actions[key]) {
        sections.push({ type: 'pillar_action', pillar: p, content: rc.pillar_specific_actions[key] });
      }
    }
  }

  // Always
  sections.push({ type: 'toolkit', content: rc.toolkit_references['tier_' + state.adjustedTier] });

  // Conditional: California
  if (state.isCaliforniaCC) {
    sections.push({ type: 'humans', content: rc.humans_alignment });
  }

  sections.push({ type: 'next_steps', content: rc.next_steps_checklist_template });

  return sections;
}
```

## Build Strategy

Build iteratively. After each major component, test it works:

1. **Shell:** HTML skeleton, CSS custom properties, view system, navigation
2. **Landing:** Hero, stats, CTAs, how-it-works
3. **Chat panel component:** Reusable panel with message rendering, typing indicator, input handling
4. **AI Engine:** Response matching, tool identification, pre-fill logic
5. **Use Case Selection:** Cards, AI tool input, suggestion card, chat integration
6. **Screening:** Questions with AI pre-fill states, result calculation
7. **Dependency Profile:** 4 questions, scoring, result display
8. **Mechanism Detection:** 3 questions, AI context notes, escalation calculation
9. **Risk Tier:** Auto-calculation display, override option
10. **Pillar Scoring:** Per-pillar interface, collapsed rail, progress indicator
11. **No-Go Check:** Criteria display, auto-flagging
12. **Governance Profile:** Scorecard, patterns, badges
13. **Roadmap:** Conditional assembly, print CSS
14. **Polish:** Transitions, mobile responsive, accessibility, edge cases

## Progress Tracking

After completing each component, write a status update to:
```
progress/build-status.md
```

Format:
```
## 1. Shell — COMPLETE
[timestamp] — View system working, navigation functional, CSS properties set.

## 3. Chat Panel — IN PROGRESS
[timestamp] — Panel renders, messages display, typing indicator works. Input handling TODO.
```

## Constraints

- Single file output: `index.html`
- No external dependencies beyond Google Fonts
- Do not write user-facing copy — use content JSON or flag `[PLACEHOLDER]`
- All logic from the spec. Do not invent scoring rules.
- Chat panel CSS must closely match the wireframe (compare visually)
- The collapsed rail on scoring screens is non-negotiable — it IS the design statement
- Test the full flow: Landing → Routing → Use Case → Screening → Dependency → Mechanism → Risk Tier → Scoring (all 9 pillars) → No-Go → Profile → Roadmap
- Test with at least one known tool (Mainstay) end-to-end
- Print CSS must render View 11 (Roadmap) cleanly — no nav chrome, no chat panel, proper page breaks
