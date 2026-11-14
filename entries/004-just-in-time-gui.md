# 004 — Just-in-time GUI

> Entry 004 — added 2026-11-13 (Drop 1: Modern UI design techniques).

*invisible until the moment it matters*

**What it is.** The interface is invisible by default and surfaces only when
context demands it, then disappears when its purpose is served. Coined by
Andrew Sims (Signal Path). Related to calm technology, but stricter: zero
inventory. No unused features sitting in the interface; show what's needed,
discard the rest.

**Why it feels good.** The screen never shows you something you don't need
right now. Every control you see is relevant to this exact moment. That is
the toy bar, enforced by the system instead of by willpower.

**The calm test.** Before adding any visible UI, ask: can this be done without
a screen at all? Can it be a quiet indicator instead of a control? Can it
appear only when the user is in the situation where it matters?

**Where it fits his apps.** Forge's approval flow (the approval appears when a
tool needs it, not before). STELLA's settings (they don't exist on screen at
all until the backend can't decide something itself). ACR's controls (the
learning rate lives in its own window, behind the menu, not on the main
screen). This is U35 and U36 from the rules, as a named technique.

**Watch out.** Context has to be accurate. A just-in-time UI that guesses the
context wrong hides the thing the user needs. When in doubt, the menu bar is
the fallback: everything is still reachable, just not on screen.

## See also

- [003 Calm technology](003-calm-technology.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [013 Diegetic UI](013-diegetic-ui.md)

## Sources

- Just-in-Time GUI Expert (skill) — https://github.com/diegosouzapw/awesome-omni-skill/blob/HEAD/skills/design/jit-gui-expert/SKILL.md
- Just-in-Time Interfaces, Andrew Sims, Signal Path, April 2, 2025 — https://signalpath.substack.com/p/just-in-time-interfaces
