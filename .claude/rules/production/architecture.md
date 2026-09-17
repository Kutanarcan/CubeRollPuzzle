---
paths:
  - "Assets/Scripts/**"
---

# Architecture

## C# Core, thin Unity shell
Game logic lives in a pure C# layer that does not reference `UnityEngine`, enforced by assembly definitions:

```
Assets/Scripts/
  Core/       (Game.Core.asmdef)           -> NO UnityEngine reference
  Runtime/    (Game.Runtime.asmdef)        -> Core + UnityEngine
  Tests/
    EditMode/ (Game.Tests.EditMode.asmdef) -> Core
    PlayMode/ (Game.Tests.PlayMode.asmdef) -> Runtime
```

Calling a Unity API from Core is a **compile error**.

## MonoBehaviour = dumb adapter
A MonoBehaviour may only:
- Carry serialized data from the Editor (`[SerializeField]`)
- Forward lifecycle events into Core
- Call Unity APIs (Instantiate, Transform, Animator, Audio…)

Forbidden: business-rule `if`s, calculations, state machines, caching logic, data transformation.

- Never do work inside `Update()` — call `ITickable.Tick(float dt)`.
- No singletons. One composition root (`GameInstaller : MonoBehaviour`) with manual wiring.
- No constructors on MonoBehaviours — inject via `Initialize(...)`.

## Design patterns
- Simplest working solution first. Propose a pattern only for a concrete problem: an axis of change, a testing barrier, the third repetition.
- When proposing a pattern, state in one sentence **what it solves**. If you cannot, do not propose it.
- Banned reflexes: singleton for everything, factory with a single implementation, unnecessary observer layers, premature abstract factory.
