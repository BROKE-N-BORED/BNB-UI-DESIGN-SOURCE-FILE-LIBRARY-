# 016 — Pie menus

> Entry 016 — added 2026-11-13 (Drop 2: Games, editors, and gadgets).

*flick, don't hunt*

**What it is.** A circular menu that opens at the cursor. You press a key,
flick the mouse in a direction, and release. No aiming at a small row of
text, no reading a list, no travel across the screen. The choice is a
direction, and direction is something your hand learns. Blender has used
pie menus for years. The Sculptools Palette add-on for Blender 4.5 puts a
radial menu in Sculpt Mode: one keypress, flick, click, or tap a number
to switch tools.

**Why it feels good.** A linear menu makes you hunt: read down a list,
find the row, click precisely. A pie menu makes you gesture: up is always
up, left is always left. After a few uses you stop looking at it at all.
Your hand knows the flick. It is the difference between dialing a number
and pointing at a compass.

**The numbers.**
- Blender's own source caps a pie menu at 8 items (PIE_MAX_ITEMS 8), one
  per compass direction: N, NE, E, SE, S, SW, W, NW.
- Sculptools Palette: up to 8 palettes, each with 10 main slots and 3
  sub-slots per slot. One keypress opens it; flick, click, or tap a
  number to pick.

**Where it fits his apps.** Pixel Forge (brush picker at the cursor, right
where you are painting), Reblend (tool picker in the viewport, no trip to
a toolbar), LYNX SHARE (a radial for the eight things you do most while
mixing). Fits any tool with four to eight frequent actions that you
reach for while your eyes are on the work.

**Watch out.** Eight is the ceiling, not a target. Past eight slices the
flick stops being a flick and becomes a hunt again. Every slice needs a
distinct direction, not just a distinct label. And keep a keyboard
alternative (number keys) for people who cannot flick precisely.

## See also

- [023 Focus-first navigation](023-focus-first-navigation.md)
- [024 Clip launcher](024-clip-launcher.md)

## Sources

- Sculptools Palette, Blender Extensions — https://extensions.blender.org/add-ons/sculptools-palette/
- Blender source, interface_intern.h (PIE_MAX_ITEMS 8) — https://projects.blender.org/archive/blender-archive/src/commit/57b5852bc8b8188e73e2ffd7c05aaa3f409c3025/source/blender/editors/interface/interface_intern.h
