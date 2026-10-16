---
name: council-build-from-mockup
description: Use when the user wants an approved mockup built with a discussing council of agents planning and reviewing - "council build X", "build X with the agents", "build-from-mockup in council mode". An Architect, QA Engineer, UX Designer and Skeptic debate the build plan, the moderator implements, then QA and UX review the result before reporting. Not for design changes.
---

# Council: build from mockup

Same job, outputs and gate as [`build-from-mockup`](../build-from-mockup/SKILL.md); read it
first and follow every rule. The council runs under
[`.claude/council/PROTOCOL.md`](../../council/PROTOCOL.md) twice: once to plan, once to
review. Only the moderator writes code.

**Gate:** both mockup files say `Status: Approved` (step 1 of the base skill).

**Participants:** `architect`, `qa-engineer`, `ux-designer`, `skeptic`.

## 1. Plan council

Brief: the mockup pair, `PROFILE.md`, `docs/mvp.md`, `AGENTS.md`, and the relevant code.
Round 1 (parallel):
- `architect`: Files and Order sections.
- `qa-engineer`: Coverage map and Proof (tests + browser checks per annotation and state).
- `ux-designer`: component/token mapping per annotation; anything hard to match.
- `skeptic`: Risks, especially data and regressions of the core flow.

Round 2 critique; Round 3 only if blocked. Write `docs/plans/YYYY-MM-DD-<feature>.md` with
`Council: docs/councils/<file>` in the header. If the council concludes the mockup cannot be
built as drawn, stop and report (the fix goes through the mockup, per the base skill).

## 2. Build and verify

Do base-skill steps 3–4 yourself: implement, run the checks, drive the app, screenshot the
three sizes and every state.

## 3. Review council

Send `qa-engineer` and `ux-designer` (parallel) the plan, the literal check output and the
screenshot paths. QA grades each Coverage line pass/fail/unverified; UX lists visual
departures frame by frame. Fix every fail, re-verify, and repeat the review at most twice.
Append the review rounds to the same transcript.

## 4. Report

Report as base-skill step 5 (including literal check output), plus the review verdicts.
Set `Status: Built` only when QA has no fails left. Do not commit unless asked.
