# 059 — FLIP layout animations

> Entry 059 — added 2026-11-13 (Drop 5: Choices, motion, and craft).

*The layout changes instantly; the eye sees it glide.*

**What it is.** FLIP is a recipe for animating layout changes, coined by Paul Lewis at Google in 2015 and used on the Google I/O 2015 website and the Chrome Dev Summit site. The letters stand for First, Last, Invert, Play. First, record where each element is. Last, apply the layout change instantly (a list reorders, a filter applies, a card expands) and record where each element ended up. Invert, apply a transform that puts each element back where it looked like it was, so visually nothing has moved even though the layout already changed. Play, animate that transform back to zero, and every element glides from its old spot to its new one. The problem it solves is real: when a list reorders, the elements' own properties have not changed, only their positions in the layout, so as Josh Comeau puts it, there is no way to use CSS transitions to animate this change. FLIP creates something to animate (the transform) out of a change that had nothing animatable in it. The trick that makes it cheap is that the per-frame animation touches only transform and opacity, which the compositor moves around without repainting anything.

**Why it feels good.** Without FLIP, a reorder is a teleport: the user was looking at an item, the list reshuffles, and the item is gone from its spot with no trace of where it went. The user has to hunt for it again. With FLIP, the user watches the item travel to its new place, so the reorder tells a story (that item moved up because it was upvoted, this one dropped because it was filtered out) instead of presenting a puzzle. It is also the cheap-motion technique in its purest form: it exists to make layout animation affordable on weak hardware, by doing the expensive measuring once, up front, and keeping the per-frame work to the two cheapest properties there are. On an 8GB no-GPU machine, that is the difference between smooth and stuttering.

**The numbers.** Lewis's core budget is a 100 ms window after the user interacts, inside which all the measuring and inverting must happen unnoticed; past that window the app feels unresponsive. Once the animation is playing, the target is 60 frames per second, and the only properties moving per frame are transform and opacity. Neither source prescribes a play duration, so treat the examples as examples: Lewis's own sample plays at 300 ms with easing cubic-bezier(0, 0, 0.32, 1), and Comeau's list example uses 500 ms. In practice, pick from the Material 3 duration ladder by how far things travel: medium durations of 250 to 400 ms cover most list moves, short durations of 50 to 200 ms cover small nudges, and long durations of 450 to 600 ms are for elements crossing most of the screen. This entry is mechanism-first: the verified numbers are the 100 ms measurement budget and the 60 fps target, and the durations are ladder picks, not rules from the FLIP sources.

**Where it fits his apps.** Fyrn: the model list re-sorts by size or RAM fit, and each row glides to its new place instead of teleporting. STELLA: the training job list re-sorts by status when a run finishes, and the finished job visibly slides to its new position. Yahtzee: dice settle into the kept area after a roll, and scorecard rows shift as categories fill. Reblend: the object list reorders when objects are grouped or renamed. Pixel Forge: strip and layer reordering, where the dragged item and the items making room for it all glide. Code Forge: findings re-sort when a filter or severity changes, so the reviewer sees which issues rose to the top.

**Watch out.** Do not exceed the 100 ms measurement window. If measuring a huge list takes longer, measure only the visible rows and let the rest jump, or the cure is worse than the disease. Do not start a second FLIP while one is still playing: Lewis warns that the precalculation will interrupt the animation in flight, so queue the next change until the current one finishes. Scaling distorts content, so FLIP position and opacity where possible, and separate elements that must scale cleanly rather than stretching text and icons. FLIP only moves things that exist in both states: items entering or leaving need a fade in or out alongside it, since there is no First or Last position to measure for them. With reduced motion on, skip the glide and show the final layout at once (see 041).

**In Qt.** Record each widget's geometry before the change, let the layout settle, then animate. For widgets inside a layout, the honest Qt analog is a pixmap proxy: grab each moving widget as a pixmap, hide the real widgets, animate the pixmaps from old rect to new rect with QPropertyAnimation on geometry, then show the real widgets when the animation ends. For widgets positioned freely, animate geometry directly.

## See also

- [001 Micro-interactions](001-micro-interactions.md)
- [002 Spring physics motion](002-spring-physics-motion.md)
- [009 Shape morphing and continuity](009-shape-morphing-and-continuity.md)
- [027 Drag and drop done right](027-drag-and-drop-done-right.md)
- [041 Reduced motion done right](041-reduced-motion-done-right.md)
- [046 Response-time limits](046-response-time-limits.md)
- [057 Staggered entrances](057-staggered-entrances.md)
- [058 Shared-element transitions](058-shared-element-transitions.md)

## Sources

- FLIP Your Animations, Paul Lewis, Aerotwist, February 2015 (updated May 17, 2022) — https://aerotwist.com/blog/flip-your-animations/
- The FLIP technique for list animations, Josh W. Comeau, last updated February 15, 2016 — https://www.joshwcomeau.com/react/animating-the-unanimatable/
- Easing and duration: Tokens and specs, Material Design 3, accessed 2026-11-13 — https://m3.material.io/styles/motion/easing-and-duration/tokens-specs
