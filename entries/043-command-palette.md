# 043 — Command palette

> Entry 043 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*Every command in the app, one keystroke and a few letters away.*

**What it is.** A command palette is a small search bar that floats over the app and lists every command the app can run. Press one shortcut (Ctrl+Shift+P in VS Code, Cmd+K or Ctrl+K in Linear and Raycast), type a few letters of what you want, and run the match with Enter. You never have to remember where a command lives in the menus or what its shortcut is; you only have to remember its name, roughly. Typing filters the list as you go, and fuzzy matching means a few letters typed in order are enough, even if you skip letters or miss the exact wording. This is different from entry 028: shortcuts reward memory, the palette rewards guessing. A beginner and a power user type the same thing and get the same result.

**Why it feels good.** It turns the whole app into something you can ask for. Menus hide features behind nesting; the palette puts every feature one search away, so features you forgot existed get found again. It also teaches shortcuts for free: Raycast shows each action's shortcut on the right of its row, so the thing you look up three times becomes the thing you press without thinking. And it keeps your hands on the keyboard, which matters in apps where the work itself is typing. Linear calls Cmd+K the most important shortcut to remember: if you want to do something but are not sure how, search the command menu.

**The numbers.** The sources give no timing study, so here is the mechanism instead. Opening costs one chord (Ctrl+Shift+P, or Cmd/Ctrl+K), and every command is reachable from that chord plus a few letters, with no menu depth to climb. Raycast's action search filters in real time with fuzzy matching, so partial input narrows the list as you type. Raycast ranks results by frecency (frequency plus recency): commands you use often rise, a pinned favorite always appears at the top of search, and the ranking can be reset if a command lands too high or too low. VS Code's palette covers editor commands, file opening, symbol search, and a file outline in one window, and typing `?` lists every command the palette can run.

**Where it fits his apps.** Code Forge: run a review, apply a fix, open a file, or toggle a view by typing its name instead of hunting menus. Pixel Forge: reach any tool, filter, or canvas command ("resize", "flip", "export") without leaving the keyboard. Fyrn: switch models, pull a model, or open settings by typing the model name or the action. ACR: jump to a trace view, run an analysis, or export results from one box. Qwkhnd: triage by typing ("snooze", "done", "move to today") instead of dragging cards through columns.

**Watch out.** A palette is only as good as its command names: vague or jargon-heavy names cannot be searched, so name commands the way a user would ask for them. Do not let the palette become the only way to reach a feature; menus and buttons still teach beginners what exists, and a child opening the app for the first time will not guess Ctrl+K. Keep the list short and ordered (favorites and frequent commands first), and show each command's shortcut beside it so the palette teaches as it serves. On a no-GPU machine this is cheap: it is a text filter over a list, with no animation budget needed.

## See also

- [028 Keyboard-first power patterns](028-keyboard-first-power-patterns.md)
- [029 Search-as-you-type done well](029-search-as-you-type-done-well.md)
- [023 Focus-first navigation](023-focus-first-navigation.md)
- [014 Teach by playing](014-teach-by-playing.md)
- [004 Just-in-time GUI](004-just-in-time-gui.md)

## Sources

- User interface, Visual Studio Code Docs, accessed 2026-11-13 — https://code.visualstudio.com/docs/editing/getting-started/userinterface
- Action Panel, Raycast Manual, updated 2026-08-20 — https://manual.raycast.com/action-panel
- Tips for joining your team on Linear, Linear Docs, accessed 2026-11-13 — https://linear.app/docs/joining-your-team-on-linear
