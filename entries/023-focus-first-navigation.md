# 023 — Focus-first navigation

> Entry 023 — added 2026-11-13 (Drop 2: Games, editors, and gadgets).

*the highlight is the cursor*

**What it is.** On TV there is no cursor and no touch. A focus highlight
moves between elements with the remote's D-pad, and Select activates the
focused item. That is the whole interaction model, and it is strict:
the focused element must be unmistakable from across the room, so tvOS
scales it up and adds parallax artwork that tilts with the remote, and
Amazon tells Fire TV developers to replace the default browser-style
focus with custom styling. Left and Right wrap within a shelf; Up and
Down keep your column. Focus is never lost: on a screen change it lands
on the most likely next action, and on return it restores the prior
position.

**Why it feels good.** It is navigation you can do without looking at
your hands and without reading a manual. Five buttons, one highlight,
and the highlight is always obvious. It works from ten feet away in a
dark room with other people talking. Any interface that clear at ten
feet is generous at two feet.

**The numbers.**
- tvOS type scale at 1920 by 1080: Body at 29 pt, headlines 38 pt and
  up. Do not port phone type sizes to TV.
- Fire TV: body text at least 14 sp (about 28 px at 1080p).
- Safe areas: Apple wants 60 pt top and bottom, 80 pt sides. Android TV
  wants a 5 percent margin (48 dp left and right, 27 dp top and bottom).
  Fire TV keeps UI out of the outer 5 percent of every edge.
- Autoplay previews: delay of about 2 seconds or more of sustained
  focus, start muted or low-volume, never autoplay on a mere
  focus-pass-through, and provide a setting to disable it entirely.
- Avoid pure white (#FFF): it glows and blooms on many panels. Dark UI
  themes dominate TV because bright full-screen white is fatiguing in
  living rooms.

**Where it fits his apps.** Yahtzee first (arrow-key navigation, a big
obvious focus on the dice and the scorecard, fully playable without a
mouse), LYNX SHARE (keyboard-first pad navigation while mixing), and
every app's keyboard focus ring: it should be unmistakable, not a 1 px
dotted line. A weak focus style (1 px outline, no scale) fails from
across the room, and it fails a tired user at a desk too.

**Watch out.** Never let focus get lost. No focus traps, no diagonal-only
paths, and Back always retreats one level. On a screen change, land
focus on the most likely next action. On return, restore the prior
position. And treat every required keystroke as a design failure: on TV
the answer is voice search, phone handoff, or an activation code on the
phone, never a D-pad keyboard. On Qt, do not trust `outline` for the
ring: in this PySide6 build `outline` renders nothing at all (probed: 0
pixels), so the ring must be a `border` on `:focus`. OLLAMA SYSTEM TEST
v15 found this by probing a ring it had specified and finding it
invisible, which is the entry working as a checklist.

## See also

- [016 Pie menus](016-pie-menus.md)
- [015 Accessibility presets](015-accessibility-presets.md)

## Sources

- TV and 10-Foot Interface Design, UX Encyclopedia, updated 2026-07-22 — https://ux.detroit3d.com/platforms/tv-10-foot.html
- TV navigation, Android Developers (living docs, undated) — https://developer.android.com/training/tv/start/navigation
