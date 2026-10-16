---
name: council-feature-mockup
description: Use when the user wants a feature (or the MVP) mocked up by a discussing council of agents - "council mockup X", "have the agents design X", "feature-mockup in council mode". A UX Designer, User Advocate, Data Engineer, Architect and Skeptic debate the design, then the moderator writes the .md + .html pair exactly as /feature-mockup would and stops for review. Not for implementation.
---

# Council: feature mockup

Same job, outputs and gate as [`feature-mockup`](../feature-mockup/SKILL.md); read it first
and follow every rule (profile, file pair, three frames, verify, README row). The
difference: the design decisions in its step 1 are made by a council run under
[`.claude/council/PROTOCOL.md`](../../council/PROTOCOL.md).

**Gate:** `docs/mvp.md` is `Status: Approved`. For a backlog feature, the MVP mockup is
`Built`. Otherwise stop and say which step is missing.

**Participants:** `ux-designer`, `user-advocate`, `data-engineer`, `architect`, `skeptic`.

## 1. Brief

Do `feature-mockup` step 0 (profile) yourself if needed. Brief: the feature, its line in
`docs/mvp.md`, `PROFILE.md`, earlier mockups in `docs/design-docs/mockups/`, any reference
screenshot, and the question "What exactly should we draw, on what data, in which states?"

## 2. Round 1 — proposals (parallel)

- `ux-designer`: screens, layout per frame as ASCII, components and tokens.
- `user-advocate`: the first-time-user walkthrough, copy, a11y, required states.
- `data-engineer`: the *reference has / data has / mockup does* table and every derived-value rule.
- `architect`: feasibility against the current code; what is new vs existing.
- `skeptic`: the riskiest assumptions and what breaks.

## 3. Round 2 — critique (parallel), Round 3 if blocked

## 4. Decide and write

As moderator, write the `.md` and `.html` (feature-mockup steps 2–4), with
`Council: docs/councils/<file>` in the header, and save the transcript. Then send the
rendered screenshots to `ux-designer` and `user-advocate` for **one review pass** (parallel);
fix what they find that matches the decisions, and list the rest as Open questions.

## 5. Hand back

Report as `feature-mockup` step 5 plus where each persona landed. Wait. Change requests edit
the same pair (re-run a council only if the user asks or the change is large).
