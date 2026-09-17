---
paths:
  - "Assets/Scripts/**"
---

# Testability

- Check for every new type: "Can this be `new`ed without opening Unity?" If no, the design is wrong.
- Put everything non-deterministic behind an interface: `ITimeProvider`, `IRandomSource`, `IInputSource`, `IClock`.
- EditMode tests by default. PlayMode tests only when the Unity runtime is genuinely required.
- Prefer hand-written fakes over mocks — the fake is also documentation.
- Tests mirror the source layout one to one.
- Every phase ends by naming which test turns green.
