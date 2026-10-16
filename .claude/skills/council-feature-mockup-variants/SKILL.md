---
name: council-feature-mockup-variants
description: Use when the user wants 2 or 3 alternative mockups of a feature designed by a discussing council of agents - "council 3 mockups of X", "have the agents propose two designs for X", "feature-mockup-variants in council mode". The council agrees the data reality once, proposes and debates N distinct directions, then the moderator writes the variant pairs and comparison page exactly as /feature-mockup-variants would and stops for the user to pick. Not for implementation.
---

# Council: feature mockup variants

Same job, outputs and gate as [`feature-mockup-variants`](../feature-mockup-variants/SKILL.md);
read it and [`council-feature-mockup`](../council-feature-mockup/SKILL.md) first and follow
every rule. Run under [`.claude/council/PROTOCOL.md`](../../council/PROTOCOL.md).
N = 2 or 3 (default 3).

**Gate:** as `council-feature-mockup`.

**Participants:** `ux-designer`, `user-advocate`, `data-engineer`, `architect`, `skeptic`.

## 1. Brief

As `council-feature-mockup` step 1, with the question "Which N genuinely different designs
are worth comparing, on what data, in which states?"

## 2. Round 1 — proposals (parallel)

- `data-engineer`: the shared *reference has / data has / mockup does* table and derived-value
  rules. All variants use it.
- `ux-designer`: N directions, each with layout per frame as ASCII, components and tokens.
- `user-advocate`: for each direction, the first-time-user walkthrough, copy, a11y, states.
- `architect`: build cost per direction; what is new vs existing.
- `skeptic`: the riskiest assumption per direction, and whether any two directions are really
  the same.

## 3. Round 2 — critique (parallel)

Each persona scores every direction on the comparison criteria and argues for one. Drop or
replace a direction that the council agrees duplicates another. Round 3 only if fewer than N
distinct directions survive.

## 4. Decide and write

As moderator, write the variant pairs and the comparison page (`feature-mockup-variants`
steps 3–4), with `Council: docs/councils/<file>` in each header and each persona's pick in the
comparison table. Save the transcript. Send the rendered screenshots of all variants to
`ux-designer` and `user-advocate` for **one review pass** (parallel); fix what matches the
decisions, list the rest as Open questions.

## 5. Hand back and choose

Report as `feature-mockup-variants` step 5 plus where each persona landed. Wait. Promotion of
the chosen variant and later change requests follow `feature-mockup-variants` step 5.
