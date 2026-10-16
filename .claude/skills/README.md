# Skills

Claude Code skills that run the Base & Build loop. They ship in this template's
`.claude/skills/`; to reuse them elsewhere, copy the skill folders into that project's
`.claude/skills/`.

| Skill | Step | What it does |
|---|---|---|
| [`define-mvp`](define-mvp/SKILL.md) | 2 | Reads `docs/idea.md`, checks the real backend, writes `docs/mvp.md`: core flow, data check, ordered backlog, done-when checks. |
| [`feature-mockup`](feature-mockup/SKILL.md) | 3–4 | Writes and iterates a `.md` + `.html` mockup (desktop, mobile portrait, mobile landscape) for the MVP or a feature. |
| [`feature-mockup-variants`](feature-mockup-variants/SKILL.md) | 3–4 | Writes 2–3 distinct mockup variants plus a comparison page; the picked one becomes the normal mockup pair. |
| [`build-from-mockup`](build-from-mockup/SKILL.md) | 3–4 | Builds one approved mockup, verifies it on real data at all three sizes, reports. |

## Council mode

Same phases, decided by a discussion between persona agents (`.claude/agents/`) under
[`.claude/council/PROTOCOL.md`](../council/PROTOCOL.md): proposals, critique, decision.
Transcripts land in `docs/councils/`. The original skills above stay unchanged.

| Skill | Council |
|---|---|
| [`council-define-mvp`](council-define-mvp/SKILL.md) | product-strategist, skeptic, data-engineer, user-advocate |
| [`council-feature-mockup`](council-feature-mockup/SKILL.md) | ux-designer, user-advocate, data-engineer, architect, skeptic |
| [`council-feature-mockup-variants`](council-feature-mockup-variants/SKILL.md) | ux-designer, user-advocate, data-engineer, architect, skeptic (2–3 directions) |
| [`council-build-from-mockup`](council-build-from-mockup/SKILL.md) | architect, qa-engineer, ux-designer, skeptic (plan + review) |

## Pipeline

| Skill | What it does |
|---|---|
| [`run-pipeline`](run-pipeline/SKILL.md) | Drives define-mvp → feature-mockup → build-from-mockup for the MVP and each backlog item, in solo or council mode, tracked in `docs/pipeline.md`. The `process-guardian` agent audits every gate. |
