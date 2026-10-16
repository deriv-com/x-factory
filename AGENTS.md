# Working in this repository

This project follows Base & Build: a working MVP first, then one feature at a time through an
approved mockup. Docs live in `docs/`: `idea.md`, `mvp.md`, `design-docs/mockups/`, `plans/`.

## Flow
1. `/define-mvp` turns `docs/idea.md` into `docs/mvp.md`. Approve before mocking up.
2. `/feature-mockup <feature>` writes a `.md` + `.html` mockup. Iterate on those files until approved.
   `/feature-mockup-variants <feature> [2|3]` writes 2–3 alternatives to compare; the picked one
   becomes the mockup pair.
3. `/build-from-mockup <feature>` builds one approved mockup and verifies it.

Council mode: `/council-define-mvp`, `/council-feature-mockup`, `/council-feature-mockup-variants`, `/council-build-from-mockup` run
the same steps as a discussion between persona agents (`.claude/agents/`, protocol in
`.claude/council/PROTOCOL.md`); transcripts go to `docs/councils/`.

Automation: `/run-pipeline` drives the whole flow (solo or council), tracks it in
`docs/pipeline.md`, and the `process-guardian` agent audits every gate. Approvals stay with
the user unless they explicitly turn on autopilot.

## Stack
- Language / framework:
- Design system:
- Backend / APIs:

## Scripts (run from the repo root)
- Dev:
- Build:
- Test:
- Lint / typecheck:

## Rules
- One feature per build request. Design changes go into the mockup first.
- Secrets live in `.env.local` (git-ignored) and in memory, never in tracked files, URLs or logs.
- Commit or push only when the user asks.
- Paste the literal output of the checks before reporting a task complete.
