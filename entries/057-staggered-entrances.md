# 057 — Staggered entrances

> Entry 057 — added 2026-11-13 (Drop 5: Choices, motion, and craft).

*Many things arrive at once, but the eye reads them one at a time.*

**What it is.** When a screen loads, a list appears, or a panel opens, the elements do not all pop in at the same instant. Each one enters a beat after the previous one, in an order that matches importance, so the whole screen still arrives fast but the eye gets a path to follow. IBM Carbon calls this sequence and stagger: distribute entrances over time instead of introducing everything at once. The stagger is small, tens of milliseconds per item, and the order is deliberate. Carbon sequences content from the most stable to the most important: the shell and navigation first, then headers and written content, then dynamic content like table rows and query results, then the primary action, and animated content such as data visualizations last. The last thing to arrive is what the eye is resting on when the motion stops, so the most important element gets the last beat.

**Why it feels good.** A screen that appears all at once is a wall of information the brain has to sort out in one go. A staggered entrance hands the brain the sorting for free: this is the frame, this is the content, this is the thing to do. Carbon puts it plainly, that staggering helps the user understand the content and orientation, and that staggering table content by 20 ms significantly reduces the cognitive load. The cascade also gives an app a recognizable rhythm. Two apps with the same layout feel different when one pops and the other flows in, and that rhythm is part of what makes an app feel like itself.

**The numbers.** Carbon's worked example staggers table content by 20 ms per item, and says the delay should be adjusted to the number of staggered elements so the total time stays within 500 ms. That total is the hard budget: with 25 rows, the step shrinks to fit, and with a handful of cards, 20 ms each finishes well inside it. Each item's own entrance still needs a duration from the Material 3 ladder: short durations of 50 to 200 ms for small utility elements, medium durations of 250 to 400 ms for cards and larger moves, long durations of 450 to 600 ms only for large expressive transitions. Entrances ease out, never in: Material's emphasized decelerate curve is cubic-bezier(0.05, 0.7, 0.1, 1) and its standard decelerate is cubic-bezier(0, 0, 0, 1). Material's general rule is that duration grows with the area an animation covers and the distance it travels, so a row sliding a few pixels up needs the short end of the ladder, not the long end.

**Where it fits his apps.** STELLA: the training dashboard's bento tiles cascade in on open, shell first, the result card last, so the eye lands on the number that matters. Fyrn: the model list rows stagger in when the app opens or when a pull finishes and the list refreshes. Yahtzee: after a roll, the scorecard rows that changed arrive in order instead of all flashing at once. Reblend: the material preset grid staggers in when a category opens. Pixel Forge: preset thumbnails and layer rows stagger on panel open. Code Forge: review findings cascade in when a review lands, most severe first, so the eye meets the worst issue while the rest settles behind it.

**Watch out.** Never block interaction while the cascade plays. The user should be able to click the first row while the last one is still arriving, or the stagger becomes a loading screen with choreography. Do not stagger on every navigation: first load and big content changes earn it, but a list the user reopens ten times an hour should just appear. Keep the total inside 500 ms even for long lists, by shrinking the step or animating only the visible rows as a group. Use the same motion for elements that mean the same thing (Carbon's rule): if expanding a table row and opening a dropdown both reveal hidden content, they should move the same way, or the motion stops teaching. With reduced motion on, skip the cascade entirely and show the finished screen at once (see 041).

**In Qt.** A QParallelAnimationGroup holds one QPropertyAnimation per item, usually on opacity plus a small vertical offset, with each animation preceded by a QPauseAnimation of its stagger delay. Opacity and position are the cheap properties here, so a 20 ms cascade costs almost nothing on his hardware.

## See also

- [001 Micro-interactions](001-micro-interactions.md)
- [002 Spring physics motion](002-spring-physics-motion.md)
- [009 Shape morphing and continuity](009-shape-morphing-and-continuity.md)
- [011 Skeleton screens and honest loading](011-skeleton-screens-and-honest-loading.md)
- [041 Reduced motion done right](041-reduced-motion-done-right.md)
- [046 Response-time limits](046-response-time-limits.md)
- [058 Shared-element transitions](058-shared-element-transitions.md)
- [059 FLIP layout animations](059-flip-layout-animations.md)

## Sources

- Motion: Choreography, Carbon Design System, accessed 2026-11-13 — https://www.carbondesignsystem.com/building-blocks/foundations/motion/choreography
- Easing and duration: Tokens and specs, Material Design 3, accessed 2026-11-13 — https://m3.material.io/styles/motion/easing-and-duration/tokens-specs
- Motion, Material Components for Android, accessed 2026-11-13 — https://github.com/material-components/material-components-android/blob/master/docs/theming/Motion.md
