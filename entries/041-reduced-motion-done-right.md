# 041 — Reduced motion done right

> Entry 041 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*Respect the user's motion preference by replacing motion, not just deleting it.*

**What it is.** Every major operating system has a setting where a user can ask for less motion, and on the web that setting surfaces as `prefers-reduced-motion`. Honoring it properly means treating the preference as a design brief, not a kill switch. Large zooms, spins, parallax, and multi-directional slides get replaced with instant state changes or gentle opacity fades, while the meaning of the change stays fully visible. The user still sees what happened, they just never have to ride the movement to get there. In a Qt desktop app there is no media query to read, so the same idea lands as a setting in the app (ideally defaulting to the OS reduced-motion flag where the platform exposes one) plus motion designed from the start to avoid the worst triggers.

**Why it feels good.** Motion that the user did not ask for can make people physically ill. WCAG's own explanation says vestibular reactions to non-essential motion include dizziness, nausea, and headaches, and can be severe enough to need bed rest to recover. A person who turns on reduced motion is not asking for a lesser app, they are asking for an app that does not hurt them. When the reduced version is designed with care, it feels calm and direct rather than stripped down, and the full-motion version stays expressive for everyone else. Smashing Magazine's Val Head puts it plainly: we can be expressive and creative with motion while also being responsible and inclusive.

**The numbers.** WCAG 2.3.3 Animation from Interactions (Level AAA) requires that motion animation triggered by an interaction can be disabled, unless the animation is essential to the functionality or the information being conveyed. Two neighboring criteria set the other motion limits: 2.2.2 Pause, Stop, Hide (Level A) requires a pause, stop, or hide control for content that moves, blinks, or scrolls on its own for more than 5 seconds beside other content, and 2.3.1 (Level A) allows no more than 3 flashes in any one second. `prefers-reduced-motion` has been Baseline widely available since January 2020, with two values: `no-preference` and `reduce`. The W3C offers three routes to meet 2.3.3: avoid unnecessary animation, provide a control that turns it off, or honor the reduce-motion feature of the user agent or operating system. The triggers to design around, per the WebKit guidance GotAlt cites: scaling and zooming, spinning, multi-speed or multi-directional movement such as parallax, plane shifting, and horizontal movement in the peripheral field of vision. Color fades, opacity changes, and small changes in scale are unlikely to be problematic (Smashing Magazine).

**Where it fits his apps.** Pixel Forge: canvas zoom and panel slides become instant jumps or quick fades when reduced motion is on, so a zoom to 400 percent never whips across the screen. Reblend: camera orbit and viewport transitions get a static cut option, since a spinning 3D view is exactly the kind of motion that triggers vestibular symptoms. Yahtzee: the dice roll animation becomes an instant result with the final faces shown, keeping the game fully playable with zero tumbling. LYNX SHARE: clip launching and mixer view changes crossfade instead of sliding, and the playhead moves in steps rather than sweeping. ACR: chart redraws and trace scrolling snap to the new state instead of animating through it, so a long trace never scrolls itself past the user.

**Watch out.** Do not blanket-kill every animation with a global off switch: MDN warns that `reduce` does not mean all animations must be removed, and a loading spinner that vanishes leaves the user staring at a frozen-looking app with no idea work is happening. Essential motion stays, it just gets a calmer form. Do not treat `no-preference` as consent to the wildest motion either: it can simply mean the user never found the setting. And remember the preference does nothing by itself: a looping video or auto-advancing carousel keeps playing until your code acts on the setting, so wire the check into scripted and timed motion too, not just transitions. Finally, a visible in-app toggle matters, because many people who need reduced motion do not know the OS setting exists; Smashing Magazine recommends one for any motion-heavy experience.

## See also

- [002 Spring physics motion](002-spring-physics-motion.md)
- [003 Calm technology](003-calm-technology.md)
- [008 Delight, done right](008-delight-done-right.md)
- [009 Shape morphing and continuity](009-shape-morphing-and-continuity.md)
- [015 Accessibility presets](015-accessibility-presets.md)

## Sources

- Understanding Success Criterion 2.3.3: Animation from Interactions, W3C WAI — https://w3c.github.io/wcag/understanding/animation-from-interactions
- Using media queries for accessibility, MDN — https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Media_queries/Using_for_accessibility
- Designing With Reduced Motion For Motion Sensitivities, Smashing Magazine, September 2020 — https://www.smashingmagazine.com/2020/09/design-reduced-motion-sensitivities/
- Animation, motion and prefers-reduced-motion (WCAG 2.2.2 and 2.3.3), GotAlt, October 13, 2026 — https://gotalt.com/guides/animation-and-reduced-motion/
