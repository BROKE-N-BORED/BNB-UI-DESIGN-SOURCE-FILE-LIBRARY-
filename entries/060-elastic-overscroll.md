# 060 — Elastic overscroll

> Entry 060 — added 2026-11-13 (Drop 5: Choices, motion, and craft).

*Pull past the end and the content stretches, then springs home, so the edge is something you feel instead of something you hit.*

**What it is.** Elastic overscroll is what happens when the user scrolls past the end of a list and the content stretches a little past its limit, then springs back on release, like a rubber band. The stretch resists more the further you pull, and the release is a smooth snap home, not a cut. It is the standard edge behavior on phones: on iOS the bounce is built into the platform, and every browser bounces; Android replaced its old edge glow with a stretch effect in Android 12; mobile browsers bounce by default when a page or scroll area reaches its top or bottom. The same idea works with a mouse wheel or a trackpad on the desktop: the list gives a little at its ends instead of stopping dead.

**Why it feels good.** The edge becomes information instead of a wall. The stretch tells the user there is nothing more in that direction, and the spring back confirms it, all through the fingers, with no label and no sound. A hard stop feels like the app froze or the input died; a stretch feels like the content is a physical thing with give. It also absorbs a fast fling gracefully: instead of slamming to a stop at the last item, the list stretches, bleeds the speed off, and settles. It is a small moment, over in a fraction of a second, and it is the difference between a list that feels alive and one that feels like a spreadsheet.

**The numbers.** The sources give the mechanism, not milliseconds: no opened source states a stretch distance or a bounce timing, so this entry states the mechanism instead of inventing figures. On Android, the change is dated: starting in Android 12 (API level 31), the visual elements stretch and bounce back on a drag, and fling and bounce back on a fling, while Android 11 and earlier showed a glow effect at the boundary. Android's docs give three rules for doing the stretch well: when the user touches the content during a stretch, register the touch as a catch, so the user grabs the stretched content and drives it again; when the user moves their finger back the other way, release the stretch fully before scrolling resumes; and when the user flings during a stretch, fling the edge effect to enhance the stretch. On the web, the CSS overscroll-behavior property names the four boundary behaviors: auto (default, the bounce happens and scrolling can continue into a container behind), chain (scrolling continues behind but the bounce is suppressed), contain (the bounce stays inside the panel and nothing scrolls behind it), and none (no bounce and no chaining).

**Where it fits his apps.** Yahtzee: the scorecard list stretches at its top and bottom, so a flick past the last row answers with a spring instead of a dead stop. Fyrn: the model list, which is long enough that users fling through it. STELLA: the training log, where a fast scroll to the newest entry should settle softly. Pixel Forge: the video strip and the preset lists, both flicked through at speed. Qt gives no overscroll bounce out of the box, so this is a small spring on the scroll offset (entry 002), moving the content with a transform and settling it back, which costs almost nothing on his PC: one animated offset, no layout work, no blur.

**Watch out.** A stretch inside a panel can drag the thing behind it: when a dialog's scroll area hits its edge, the page underneath starts scrolling too, which MDN calls scroll chaining. Contain the overscroll to the panel, so the bounce stays local and the background holds still. Keep chrome fixed and stretch the content only: headers and toolbars that ride the stretch jitter and look broken. Respect reduced motion (entry 041): with reduced motion on, the stretch becomes a plain stop, and the edge is still communicated, just without the spring. Do not stretch far: the resistance must grow with the pull, or the content feels loose and broken instead of springy. And do not use the stretch to trigger an action: a pull that does something (refresh, load more) is a different technique with its own rules, and mixing the two teaches the user that every overscroll might do something unexpected.

## See also

- [001 Micro-interactions](001-micro-interactions.md)
- [002 Spring physics motion](002-spring-physics-motion.md)
- [026 Swipe actions on list rows](026-swipe-actions-on-list-rows.md)
- [041 Reduced motion done right](041-reduced-motion-done-right.md)
- [057 Staggered entrances](057-staggered-entrances.md)
- [059 FLIP layout animations](059-flip-layout-animations.md)

## Sources

- Animate a scroll gesture, Android Developers, accessed 2026-11-13 — https://developer.android.com/develop/ui/views/touch-and-input/gestures/scroll
- overscroll-behavior, MDN Web Docs, accessed 2026-11-13 — https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/overscroll-behavior
- Modifying a "bouncy" viewport effect, part 1, devieffe, Medium, June 9, 2025 (updated December 28, 2025) — https://medium.com/@devieffe/modify-and-prevent-a-bouncy-viewport-effect-d4c0378b55ff
