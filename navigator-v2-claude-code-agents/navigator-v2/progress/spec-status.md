# Navigator v2 Spec — Progress

## Section A: Data Model — COMPLETE
2026-02-21 — Produced complete data model: 4 ethical criteria with descriptions and pillar mappings; 9 pillars with all questions (54 total), scoring rubrics (1-3), and source citations; Criteria → Pillar → HUMANS mapping table; 10 Student Services use cases with descriptions, default risk tiers, key pillars, equity considerations, governance requirements, and 4-5 screening questions each (40+ screening questions total); 8 no-go criteria with descriptions, rationale, and detection methods; 3 archetype definitions (Lightweight/Building/Scaling) with characteristics and starting recommendations; annual review checklist with 9 review areas mapped to pillars. Flagged: Student Services Scope Document (.docx) not found; compensated from scorecard and architecture doc. HUMANS gap noted for P9/Criterion 4.

## Section B: Identify Flow — COMPLETE
2026-02-21 — Produced: use case selector interface spec (10 cards + custom option with free-text and tier assignment); screening questions per use case (4-5 per use case, totaling 40+ questions with explicit GO/PAUSE/NO-GO logic per response option); generic screening set for custom use cases; prioritization logic (impact × risk × feasibility as qualitative dimensions); GO/PAUSE/NO-GO decision logic with threshold rules (any nogo → NO-GO, 2+ pause → PAUSE, 1 pause → GO with flag); quick-start archetype self-selection with pre-configuration effects for each archetype; convergence point specification.

## Section C: Evaluate Flow — COMPLETE
2026-02-21 — Produced: risk tier assignment with auto-assign from use case defaults and override rules (upward always allowed, downward with mandatory justification); per-pillar scoring interface spec (principle → hook → questions → rubric → score selector → notes); mandatory vs. recommended pillars per risk tier table with minimum score thresholds (P2 ≥ 2, P6 ≥ 2 for Tier 2/3); no-go trigger logic (inline alerts during scoring + dedicated 8-question no-go checklist post-scoring); score aggregation and 7 pattern interpretation rules from vendor scorecard; vendor accountability questions calibrated to 3 risk tiers.

## Section D: Roadmap Output — COMPLETE
2026-02-21 — Produced: content assembly logic (archetype × use case × risk tier × pillar scores); 5 detailed archetype × risk tier combinations (Lightweight×T1, Lightweight×T2, Building×T2, Building×T3, Scaling×T3) each with: pre-deployment governance requirements, RACI sketch, 90-day measurement starter, review cadence, escalation triggers, decision rules (pause/investigate/stop), toolkit PDF references, HUMANS mapping note; 3 remaining combinations defined by base + adjustments; 9 pillar-specific remediation actions for low scores (direct instructions); output length guidance (2-6 pages); print/download format requirements; shareable URL spec; edit/regeneration flow.

## Section E: Navigation Map — COMPLETE
2026-02-21 — Produced: 8 views/screens with purposes; URL hash-based navigation states with shareable state encoding; two entry points (full path vs. quick path) mapped through convergence; quick path abbreviation rules per archetype; back/edit flow with cascade rules (what changes when each input is revised); complete state object structure (JavaScript); LocalStorage structure (JSON schema with assessment keying and preference persistence). Also produced Appendix of 6 decision flags requiring team input before builder implementation.

## Section F: Capability & Dependency Profile System — COMPLETE
2026-02-22 — Produced complete dependency profile specification: 4 questions (Disappearance Test, Capability Trajectory, Navigate-With vs. Navigate-For, Exit Design) each with 3 response tiers (1/2/3) and "What You're Looking For" guidance; scoring bands (4-5 Low / 6-8 Medium / 9-12 High); governance requirements per profile (Low = none additional, Medium = 3 requirements including configuration review + 6-month capability check + alternative maintenance, High = 4 requirements including dependency acknowledgment + vendor lock-in assessment + 12-month sunset evaluation + capability impact tracking for Tier 3); risk tier × dependency profile interaction matrix; 5 design principles (not gates, permanent infrastructure is valid, legitimize every answer, patterns emerge through use, dependency is not risk); voice guidance with per-question framing and profile result copy; content JSON schema addition for dependency_profile section; state object additions. Added 2 new decision flags to Appendix (#7 separate screen for dependency questions, #8 re-scoring at annual review).

## Section B: Identify Flow — UPDATED
2026-02-22 — Added B.6: Dependency Profile Questions step (4 universal questions asked after screening, before risk tier). Updated flow to show dependency as distinct step between screening result and evaluation. Updated quick path to include dependency questions for all archetypes.

## Section C: Evaluate Flow — UPDATED
2026-02-22 — Added dependency badge to governance profile output (View 5). Updated C.5 score aggregation to include dependency profile in pattern interpretation. Added dependency-aware pattern: High Dependency + declining capability = escalation trigger.

## Section D: Roadmap Output — UPDATED
2026-02-22 — Updated content assembly formula to include dependency_profile as fifth input variable. Added dependency governance subsection insertion logic per profile level. Updated all archetype × tier combinations to reference conditional dependency requirements. Added dependency-specific escalation triggers and decision rules.

## Section E: Navigation Map — UPDATED
2026-02-22 — Added View 3b (Dependency Profile) to views table and navigation flow. Updated URL hash states to include #dependency/{use-case-id}. Updated two-path flow diagram to show dependency questions between screening and pillar scoring. Updated state object with dependencyProfile fields (answers D1-D4, totalScore, profile). Updated back/edit cascade rules for dependency changes. Updated shareable URL encoding to include dependency scores.

---

**All six sections (A through F) COMPLETE.** Spec updated with dependency profile system integrated across all sections. Ready for content agent and builder agent consumption.
