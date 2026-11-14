# 058 — Shared-element transitions

> Entry 058 — added 2026-11-13 (Drop 5: Choices, motion, and craft).

*The thing you tapped becomes the screen you are looking at.*

**What it is.** You tap a card, a list row, an image, or a button, and a new view opens. Instead of a hard cut, one element travels from the old view to the new one: the card grows into the detail page, the search box stretches into the search screen, the button blooms into a sheet. Material Design calls this the container transform, and it is the strongest of its six transition patterns. The shared element is the bounding container of the start view, which changes size and shape into the end view while the contents crossfade inside it. Material's own words: of all transition patterns, this one creates the strongest relationship between elements, and it is also perceived to be the most expressive. The pattern is used with cards, lists, image galleries, search boxes, sheets, FABs, and chips, both between full-screen views and within a single screen. It is related to shape morphing (009), but the difference matters: 009 morphs one control in place, while this carries one element across a view change so the user never loses it.

**Why it feels good.** A hard cut asks the user to reorient: where am I, and what did I just tap? A shared-element transition answers both questions with the motion itself. The tapped thing IS the new screen, so there is no lost moment and no doubt about which card the detail belongs to. Going back reverses the move, and the user watches the detail shrink back into its place in the list, which teaches the app's hierarchy without a single label. The morph is also the app's signature move. It is the one transition users remember and describe to each other, which makes it a cheap way for an app to feel like itself.

**The numbers.** Material Components for Android ships the container transform with an incoming duration of 300 ms and an outgoing duration of 250 ms, so the way back is quicker than the way in, and with standard easing cubic-bezier(0.4, 0, 0.2, 1). The incoming content fades in during the first quarter of the transition (fade thresholds 0.0 to 0.25), and a scrim of 32 percent black dims what sits behind. Material 3's own spec examples run longer when the transition is the expressive moment: a FAB expanding into a sheet uses 400 ms with emphasized easing, and a card expanding to full screen uses 500 ms with emphasized easing. The 300/250 ms defaults are the utility setting; the 400 to 500 ms range is for the hero moment. Either way, the transition sits inside Material's duration ladder (short 50 to 200 ms, medium 250 to 400 ms, long 450 to 600 ms), and duration grows with the area covered and the distance traveled.

**Where it fits his apps.** Fyrn: tap a model row and it grows into the model detail view, with the pull progress and RAM fit inside it. STELLA: a training job card expands into the job view, so the run you tapped is the run you are watching. Reblend: a material swatch expands into the material editor, keeping the color and roughness in view the whole way. Yahtzee: a scorecard row expands into its scoring breakdown, then shrinks back to its place. Pixel Forge: a preset thumbnail grows into the editing canvas. Code Forge: a review finding row expands into the finding detail, with the diff inside the same container that held the summary.

**Watch out.** Only morph elements with a real relationship. If the two views are unrelated destinations, Material's top level pattern (a quick fade out, then fade in) is the honest choice, and a morph would invent a connection that does not exist. The destination content must be ready before the transition ends: a container that arrives in 300 ms and then sits empty while data loads breaks the illusion worse than a plain cut would. Keep the return quicker than the entry, and never morph on every tap, only where the relationship is the point. With reduced motion on, replace the morph with a crossfade or a clean cut (see 041). On his no-GPU hardware, animate one overlay widget (position, size, opacity) rather than repainting the whole screen: a snapshot of the card scaled up is cheap, a full-screen blur behind it is not.

**In Qt.** Grab the start widget as a pixmap, hide the real widget, and animate the pixmap in a floating overlay widget from the start rect to the end rect with QPropertyAnimation on geometry plus a fade of the incoming content. When the animation finishes, show the real destination widget and drop the pixmap.

## See also

- [002 Spring physics motion](002-spring-physics-motion.md)
- [009 Shape morphing and continuity](009-shape-morphing-and-continuity.md)
- [011 Skeleton screens and honest loading](011-skeleton-screens-and-honest-loading.md)
- [017 See it before you commit](017-see-it-before-you-commit.md)
- [041 Reduced motion done right](041-reduced-motion-done-right.md)
- [046 Response-time limits](046-response-time-limits.md)
- [057 Staggered entrances](057-staggered-entrances.md)
- [059 FLIP layout animations](059-flip-layout-animations.md)

## Sources

- Transition patterns, Material Design 3, accessed 2026-11-13 — https://m3.material.io/styles/motion/transitions/transition-patterns
- Motion, Material Components for Android, accessed 2026-11-13 — https://github.com/material-components/material-components-android/blob/master/docs/theming/Motion.md
- Easing and duration: Tokens and specs, Material Design 3, accessed 2026-11-13 — https://m3.material.io/styles/motion/easing-and-duration/tokens-specs
