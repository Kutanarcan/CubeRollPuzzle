---
paths:
  - "Assets/Prototype/**"
---

# Prototype Code Rules

These rules apply to every file under `Assets/Prototype/`, in any mode. Production rules never apply here.

## Allowed and expected
- Logic in `Update()`, singletons, public fields, `GameObject.Find`, LINQ.
- Hard-coded values and magic numbers — except for anything that affects feel.
- One 400-line MonoBehaviour.

## Required
- Before writing code, two lines: what is about to be built.
- Every value that affects feel is a `[SerializeField]` with a sane default. No `const`, no literal.
- **Playable floor:** stable frame rate on the target device, no visible hitch, input feels immediate. Nothing beyond that.

## Forbidden
- Proposing architecture, patterns, refactors or abstractions.
- Writing tests.
- Saying "we should do this properly later".
- Fixing a design smell on sight. Log it in FINDINGS.md and move on.
- asmdef splits, Core/Runtime separation, interfaces for non-determinism, size limits, SOLID checks, allocation rules, benchmarks, profiling.
