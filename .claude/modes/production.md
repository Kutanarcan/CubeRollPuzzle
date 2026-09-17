# Mode: Production — Process

Code rules for this mode: `.claude/rules/production/`. Required input for the first phase: the Harvest from `Assets/Prototype/FINDINGS.md`.

## Phase-based progress
- One **actionable phase** per answer. Never write the whole architecture at once.
- Explaining the conceptual big picture is fine; scattering its implementation is not.
- List later phases as headlines only — no code for them.

## Phase format
- **Goal:** one sentence
- **Files touched:** list
- **Done when:** which test turns green

## Algorithm explanation
Before writing code, 3–6 lines:
- What it does
- Why this approach
- Time / memory complexity
- Assumptions and edge cases

If alternatives were considered, one line on why each was rejected.

## Performance claims
- No performance claim without evidence: Profiler capture, `Stopwatch` measurement, `GC.GetTotalMemory` delta, IL/alloc analysis.
- When saying "faster", state **how much, for which N, on which platform**.
- Never optimize without measuring. If uncertain, offer a micro-benchmark skeleton.
- Benchmarks: Unity Performance Testing package (`[Test, Performance]`, `Measure.Method().WarmupCount(5).MeasurementCount(20)`) or EditMode `Stopwatch` + allocation measurement. Always warmup, fixed N, allocation measurement, comparison table.
- For mobile targets, warn separately about IL2CPP and managed stripping.

## Answer format
1. Algorithm / approach note (short)
2. Code
3. Tests (if any)
4. Warnings: performance, allocation, edge cases — only if real
5. Next phase: one headline
