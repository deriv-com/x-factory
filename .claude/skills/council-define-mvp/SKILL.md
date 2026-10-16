---
name: council-define-mvp
description: Use when the user wants the MVP defined by a discussing council of agents rather than a single pass - "council define the MVP", "have the agents debate the MVP", "define-mvp in council mode". A Product Strategist, Skeptic, Data Engineer and User Advocate debate docs/idea.md, then the moderator writes docs/mvp.md exactly as /define-mvp would and stops for review. Not for mockups or builds.
---

# Council: define the MVP

Same job, inputs, outputs and gate as [`define-mvp`](../define-mvp/SKILL.md); read that skill
first and follow every rule in it. The difference: steps 1–4 are decided by a council run
under [`.claude/council/PROTOCOL.md`](../../council/PROTOCOL.md).

**Participants:** `product-strategist`, `skeptic`, `data-engineer`, `user-advocate`.

## 1. Brief

Read `docs/idea.md` (stop as `define-mvp` says if it is missing). Write the brief:
inputs `docs/idea.md`, `AGENTS.md`, the template `define-mvp/assets/mvp.template.md`; the
question "What is the one core flow, can the real backend feed it, and how is the rest
ordered?"

## 2. Round 1 — proposals (parallel)

Ask each persona for: the feature list, their pick for the core flow as numbered steps, the
backlog order, and their done-when checks. The `data-engineer` also checks the real backend
(read-only) and maps each step to endpoint + field.

## 3. Round 2 — critique (parallel)

Share all Round 1 outputs. Focus questions: competing core flows, data gaps, anything in the
MVP that is not on the core flow, states missing from done-when.

## 4. Decide and write

Run Round 3 only for blocking disputes. Then, as moderator, write `docs/mvp.md` from the
template (steps 5 of `define-mvp`), add `Council: docs/councils/<file>` under the header, and
save the transcript. Unresolved points go to Open questions.

## 5. Hand back

Report as `define-mvp` step 6, plus one line per persona on where they landed and any
dissent. Wait for approval; the user, not the council, sets `Status: Approved` (unless
`run-pipeline` autopilot was explicitly enabled by the user).
