---
paths:
  - "Assets/Scripts/**"
---

# Code Shape

## Size & layout
- If a class exceeds 150 lines, split it and state why.
- If a method exceeds 30 lines or 3 levels of nesting, extract.
- One public type per file; the file is named after the type.
- Folders group by domain concept, never by technical kind. `Enums/`, `Interfaces/`, `Structs/`, `Managers/`, `Helpers/`, `Misc/` are not concepts.
- Every folder holds at least two files. A single-file folder is a label — move the file up.
- Folder depth stops at 2 under an assembly root. Deeper means the assembly should be split.
- Namespaces stay at the asmdef root namespace and do not mirror folders.
- Before adding a file, name the concept it belongs to. If you cannot, the type is in the wrong assembly.

## SOLID — practical checks
- **SRP:** If describing the class requires "and", it is two classes.
- **OCP:** A `switch (enumType)` is a polymorphism candidate — but only if it will actually grow.
- **LSP:** Overriding to throw `NotImplementedException` means the hierarchy is wrong.
- **ISP:** An interface with 5+ members is suspect.
- **DIP:** Core never looks at Runtime (asmdef already prevents it).
