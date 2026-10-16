---
name: feature-mockup-variants
description: Use when the user wants 2 or 3 alternative mockups of one feature (or the MVP) to compare before choosing - "give me 3 mockups of X", "two design options for X", "mock up X a few different ways". Writes 2-3 distinct .md + .html variant pairs plus a comparison page, all following /feature-mockup's rules, then stops for the user to pick one. The picked variant becomes the normal mockup pair that /build-from-mockup builds. Not for implementation.
---

# Feature mockup variants

Same job, rules and gate as [`feature-mockup`](../feature-mockup/SKILL.md); read it first and
follow every rule (profile, data reality, three frames, design system, verify). The
difference: you produce **N variants** (N = 2 or 3; default 3 unless the user says 2) so the
user can compare directions, then you promote the chosen one to the single canonical pair.

## 1. Understand once

Do `feature-mockup` steps 0–1 a single time. Data reality, the diff table and the shell
placement are shared by every variant; variants differ in design, never in what data exists.

## 2. Pick N genuinely different directions

Before drawing, write one line per variant naming its **direction** and the trade-off it makes
(e.g. A "table-first, dense", B "card list, scannable on mobile", C "wizard, one step per
screen"). Two variants that differ only in colour or spacing count as one; replace it.
Each must still fit the profile's shell, design system and data.

## 3. Write the variant pairs

For each variant `a`, `b`, `c`:

- `YYYY-MM-DD-<feature>-<letter>.md` and `.html`, built exactly as `feature-mockup` steps 2–3,
  with `Status: Variant`, the direction line, and its own Open questions.
- Shared sections (Data reality, States that do not differ) may link to variant `a` instead of
  repeating.

Then write `YYYY-MM-DD-<feature>-variants.md`: the shared intent and data summary, a
comparison table (`criterion | A | B | C`: core-flow clicks, mobile fit, new components,
build cost, risk), a thumbnail screenshot of each variant's desktop and mobile portrait frame,
and your recommendation with one sentence of reasoning.

## 4. Verify

`feature-mockup` step 4 for every variant HTML. Add one README row per variant, status
**variant**.

## 5. Hand back and choose

Report the comparison page path, the directions, the findings that apply to all variants, and
your recommendation. Wait. The user may pick one, ask to merge ideas ("A's layout with C's
filters"), or request changes to a variant; edit those files in place.

When the user picks a variant:

1. Copy it to the canonical pair `YYYY-MM-DD-<feature>.md` / `.html`, add
   `Chosen from: <feature>-variants.md (variant <letter>)` to the header, `Status: Proposed`.
2. Set the other variants and the comparison page to `Status: Not chosen` (keep them; they
   record why), and update the README rows.
3. From here iterate as `feature-mockup` step 5. Approval sets the canonical pair to
   `Approved`, which is what `build-from-mockup` reads.
