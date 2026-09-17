# CubeRollPuzzle — Unity / C#

## Communication
- Short, precise, bulleted. No intro sentence, no closing summary.
- Do not dump depth unprompted. If there is more, leave one line: "I can expand on X if you want."
- Never guess — ask.
- Match the user's language; keep technical terms in English.

## Mode
MODE: PROTOTYPE
@.claude/modes/prototype.md

- Only the user changes the two lines above. Never change them, never assume they changed, never infer the mode from the code.
- If the mode line and the import disagree, or either is missing, stop and ask.
- Available modes: `prototype`, `production`.

## Layout
- `Assets/Prototype/` (`Game.Prototype.asmdef`) — disposable, excluded from player builds.
- `Assets/Scripts/` — production.
- The two assemblies never reference each other.
- Code rules live in `.claude/rules/` and load by folder. Before creating the first file in a folder, read the rule files whose `paths` match it.
