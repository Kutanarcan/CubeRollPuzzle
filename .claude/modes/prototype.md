# Mode: Prototype — Process

## Purpose
Answer one question about the game as fast as possible. The output is **knowledge, not code**. The code is disposable and will be deleted.

Every prototype opens by writing its question into `Assets/Prototype/FINDINGS.md`.

Code rules for this mode: `.claude/rules/prototype.md`.

## Phased progress
- **One phase per answer.** Always, without exception.
- A phase is done when the user can **see or play** its result in the Editor. A phase that cannot be tried on its own is too big — split it.
- **Stop after every phase.** Do not begin the next one until the user says to.
- Slice vertically, not by layer. "Grid renders" is a phase. "All data classes" is not.
- If a phase touches more than two files, or introduces more than one new concept, split it.
- Name the next phase as a headline only. No code, no scaffolding, no placeholder methods for it.

## Phase format
- **Goal:** one sentence
- **Files touched:** list
- **Done when:** what is visible or playable on screen — never a green test

## Tuning
- State the knobs at the end of the phase: which fields to touch, what each one changes.
- **A tuning request is not a new phase.** Change the value or the field, nothing else.
- When a tuned value settles, append it to FINDINGS.md under **Tuning**.

## Answer format
1. What is about to be built (1–2 lines)
2. Code
3. How to try it in the Editor
4. Which fields to tune
5. One line to append to `FINDINGS.md`
6. Next phase: one headline — then stop

## FINDINGS.md
One line per entry, under these headings:
- **Rule:** a mechanic rule that is now settled
- **Tuning:** a value that felt right, with the value
- **Cost:** something that turned out expensive
- **Rejected:** something tried and dropped, and why
- **Shape:** a data shape the code kept converging on

## Exit and Harvest
- Only the user ends prototype mode. When the opening question looks answered, say so once, in one line. Do not repeat it.
- On exit, produce a **Harvest** from FINDINGS.md: settled rules, tuning values, data shapes, rejected paths.
- Prototype code is read as a **spec, never migrated**. Do not copy files, refactor the prototype in place, or open it as a starting point.
- FINDINGS.md is a required input for the first production phase.
