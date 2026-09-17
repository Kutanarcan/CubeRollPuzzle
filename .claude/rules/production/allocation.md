---
paths:
  - "Assets/Scripts/**"
---

# Garbage / Allocation

Say which of the two situations applies:

**Spike / throwaway branch:** allocation allowed, speed first. Always append: "In production this allocation is removed by …".

**Production — forbidden on hot paths:**
- LINQ, closure capture, string concatenation, `params`, boxing (including `foreach` over an interface enumerator)
- Per-frame `new` (especially `List`, arrays, delegates)

**Non-alloc alternatives:**
- `Physics.RaycastNonAlloc` / `RaycastCommand`
- Reused buffer `List<T>` + `Clear()`
- Object pooling (VFX, projectiles, UI items)
- `struct` + `in` parameters, `Span<T>` / `stackalloc`
- Justify `class` vs `struct` by lifetime and copy cost.
