---
name: run-pipeline
description: Use when the user wants the whole X-Factory flow driven for them - "run the pipeline", "take the idea to a built MVP", "automate define-mvp, mockup and build", "continue the pipeline", "what's next", or "where are we". Orchestrates /define-mvp -> /feature-mockup -> /build-from-mockup (solo mode) or their council-* versions (council mode) for the MVP and then each backlog feature, keeps docs/pipeline.md as the tracker, and has the process-guardian agent audit every gate.
---

# Run the pipeline

You are the **conductor**. You do not replace the phase skills; you run them in order, one
item at a time, and make sure nothing skips a step. The approval gates belong to the user.

## Modes

Ask once (or take it from the request / `docs/pipeline.md`):

- **Mode**: `solo` runs `define-mvp`, `feature-mockup`, `build-from-mockup`.
  `council` runs `council-define-mvp`, `council-feature-mockup`, `council-build-from-mockup`.
  Can be set per phase (e.g. council for mockups, solo for builds).
- **Autopilot**: `off` (default) stops at every approval for the user. `on` only when the user
  says so in chat: the council's decision stands in for approval, every auto-approval is
  logged as `Approved (autopilot)`, and the run still stops on any blocker, data gap, failed
  check or guardian violation. Never assume autopilot.

## The loop

1. **Load state.** Create `docs/pipeline.md` from
   [`assets/pipeline.template.md`](assets/pipeline.template.md) if missing; seed rows from
   the backlog in `docs/mvp.md` once it exists. Launch the `process-guardian` agent and read
   its audit. Fix the tracker to match the files on disk (files win).
2. **Pick the next step** — the first that is true:
   - no `docs/idea.md` content → ask the user to fill it; stop.
   - `docs/mvp.md` missing or not `Approved` → define-mvp phase.
   - MVP row not mockup-`Approved` → mockup phase for "the MVP".
   - MVP row not `Built` → build phase for "the MVP".
   - next backlog row (in `docs/mvp.md` order) not `Built` → its mockup, then its build.
   - all rows `Built` → report done.
3. **Run the phase** by invoking the phase skill for the chosen mode via the Skill tool,
   with the item as argument. Follow that skill fully, including its own stop points.
4. **Gate.** After the phase:
   - Autopilot off and the phase ends in "wait for review" → update the tracker, report, stop.
     When the user next says "approved" (or asks for changes), apply it through the same
     phase skill, then resume the loop at step 1.
   - Autopilot on → set the status with `(autopilot)`, continue.
5. **Audit.** Launch `process-guardian` again. Any violation → stop and report it with the fix.
6. **Record.** Update the row and append a Log line: date, phase, item, result, transcript.
   Then loop to step 2.

## Rules

- One item through one phase at a time. Never mock up feature N+1 while feature N is unbuilt.
- Never build without `Status: Approved` on both mockup files; never mark `Built` without the
  base skill's verification and literal check output.
- A build that finds the mockup cannot be built as drawn sends the item back to the mockup
  phase (`Build: Blocked`, note the reason).
- The user can say "pause", "switch to council/solo", "skip <item>" (moves it to the end of
  the backlog with a note) or "status" (run step 1 and report the audit table) at any time.
- Commit or push only when the user asks.

## Report (every stop)

The guardian's table, what just happened, and the one next step the user must take
(usually: review and approve `<file>`).
