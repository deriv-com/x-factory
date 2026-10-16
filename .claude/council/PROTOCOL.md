# Council protocol

A council is a short, structured discussion between persona agents (`.claude/agents/`),
run by the main session acting as **moderator**. Personas only think and read; the moderator
alone writes files and code. The council replaces the "think" part of a phase skill, never
its gates: every rule, output file and approval step of the base skill still applies.

## Roles

- **Moderator** (main session): frames the question, launches rounds, keeps time, decides,
  writes the outputs. Never silently drops an objection: it is accepted, rejected with a
  reason, or turned into an open question.
- **Personas**: one Agent call each, `subagent_type` = the persona name. Each has its own
  behaviour; do not ask a persona to play another role.

## Rounds

Run personas of the same round **in parallel** (one message, several Agent calls).

1. **Brief** (moderator). Write the question, the inputs (file paths to read), the base skill's
   required output, and constraints. Every persona gets the same brief.
2. **Round 1 — Proposals.** Each persona answers independently, without seeing the others.
3. **Round 2 — Critique.** Each persona gets all Round 1 outputs (verbatim, labelled by
   persona) and answers: what they agree with, what they object to and why, and what they now
   change in their own position.
4. **Round 3 — Converge** (only if Round 2 left a blocking disagreement, max one extra round).
   Send just the disputed points to the involved personas plus the skeptic; ask for a final
   position and the evidence that would settle it.
5. **Decision** (moderator). Synthesize: decisions, rejected options with reasons, open
   questions for the user. Evidence beats seniority; data beats opinion.

Hard limit: 3 rounds. Unresolved points become numbered Open questions for the user.

## Persona output format

```
### <Persona name> — Round <n>
**Position:** one or two sentences.
**Points:**
1. <claim> — evidence: <file:line, endpoint+field, or "assumption">
**Risks / objections:** ...
**Changed my mind on:** (Round 2+) ...
**Must-haves for me to sign off:** ...
```

Keep each answer under ~400 words.

## Transcript

Save every council to `docs/councils/YYYY-MM-DD-<phase>-<feature>.md`:

```
# Council: <phase> — <feature>
Date · Mode · Participants · Base skill
## Brief
## Round 1 … ## Round 2 … (## Round 3)
## Decision
- Decisions (with who argued for them)
- Rejected (with reason)
- Open questions for the user
```

Link the transcript from the phase output (mvp.md, mockup .md, or build plan) under a
`Council:` line in its header.
