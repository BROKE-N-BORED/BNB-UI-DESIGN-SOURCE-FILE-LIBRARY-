# 026 — Swipe actions on list rows

> Entry 026 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*Flick a row to act on it — the gesture is the button.*

**What it is.** Drag a list row sideways and actions reveal themselves
underneath it: archive and delete on one side, pin on the other, iOS
Mail style. A short drag parks the row open; a long flick fires the
primary action with no tap at all.

**Why it feels good.** The most common row actions take one gesture
instead of open-menu-tap-confirm. The row itself is the affordance, and
the armed state before a full swipe means the destructive action never
fires by surprise.

**The numbers.** Two careful reconstructions of iOS Mail behavior agree
on the shape (Apple publishes no hard numbers for this pattern, so these
figures are the reconstructions', not Apple's). Design Lounge's iOS-style
reference build: action buttons 80 px each; drag under 40 px and release
springs back over 360 ms (`cubic-bezier(.32,.72,0,1)`); drag over 40 px
snaps open to −160 px, showing both actions; past the reveal width,
travel damps to 45% (rubber band); crossing 60% of row width arms
commit: the outer action fills to 100% over 200 ms, the inner action
collapses, the icon scales to 1.15, and the row plays a 120 ms 3 px
nudge; release past 60% slides the row off-screen over 360 ms, then
collapses its height over 320 ms after a 200 ms pause. Only one row is
open at a time. Keyboard mirrors the gesture: ArrowLeft/ArrowRight opens,
Escape closes, Tab reaches the revealed buttons. JSBits' design adds the
gesture engine: stay undecided until ~10 px of travel, then lock the
axis once per gesture (|dx| vs |dy|, never re-evaluated mid-gesture); a
flick at 0.5 px/ms counts as intentional even over a short distance; the
commit threshold is 0.6 of row width; animate `translateX` only
(GPU-composited, no layout); deleted items sit in an undo buffer with a
6-second timer before the real DELETE fires.

**Where it fits his apps.** **DUO**: message and chat lists, swipe to
pin, archive, delete. **Qwkhnd**: task rows, swipe to complete or
delete. **GITDATA**: dataset rows, swipe to open or remove. **Data Pack
Builder**: pack list, swipe to duplicate or delete. **MIMIK**: capture
list, swipe to delete or share.

**Watch out.** Swipe must never be the only path to an action. A
VoiceOver or keyboard user cannot swipe, so every action needs a visible
menu or keyboard route too. Never steal vertical scroll: lock the axis
after ~10 px and never re-evaluate it mid-gesture, or the row jitters. A
destructive full-swipe needs the armed state *and* undo. Never fire the
real delete up front. On desktop, also show hover-revealed inline
actions (Design Lounge uses 32 px icon buttons) so mouse users are not
forced to drag. Keep it to two actions per edge; beyond that, hit
targets cramp and discoverability dies.

## See also

- [001 Micro-interactions](001-micro-interactions.md)
- [002 Spring physics motion](002-spring-physics-motion.md)
- [019 Optimistic UI](019-optimistic-ui.md)
- [015 Accessibility presets](015-accessibility-presets.md)

## Sources

- Swipe-to-reveal row actions, Design Lounge, 2026-09-29 — https://www.designlounge.live/p/ios-swipe-row-actions
- Design Swipeable List Items (Swipe Actions), JSBits — https://www.jsbits.com/frontend-design/design-a-swipeable-list
