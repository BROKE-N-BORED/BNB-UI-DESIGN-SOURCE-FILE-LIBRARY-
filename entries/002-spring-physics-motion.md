# 002 — Spring physics motion

> Entry 002 — added 2026-11-13 (Drop 1: Modern UI design techniques).

*things that feel like they have weight*

**What it is.** Motion driven by a simulated spring instead of a fixed timer.
A spring has stiffness (how fast it moves) and damping (how fast the bounce
settles). When you flick a card, it overshoots slightly and settles, the way
a real object would. The key property: a spring is velocity-aware. A fast
fling settles fast; a calm tap settles slow. The animation energy matches the
gesture energy automatically.

**Why it feels good.** Our brains have a lifetime of handling physical objects.
A ball bounces smaller and smaller until it stops. A rubber band snaps and
overshoots. Spring motion matches that expectation, so it reads as real.
Fixed easing curves feel mechanical by comparison, and CSS-style easing can't
overshoot at all, which is exactly the part that feels tactile.

**The numbers.**
- A snappy toggle: stiffness around 500, damping around 30. Quick movement,
  slight overshoot, fast settle.
- Springs are for motion the USER causes: taps, drags, swipes, pull-to-refresh.
  For things that happen on their own (a loading fade), plain easing is better.
- Feed the release velocity into the spring. A spring that restarts from zero
  when you let go of a drag feels disconnected from your hand.
- Transitions must be interruptible: if the user grabs something mid-flight,
  it retargets smoothly instead of finishing the old animation first.

**The earned rule (from Material 3 Expressive).** Expressive spring motion is
earned, not defaulted to. Springs belong on content and interactive surfaces
that reward attention: sheets sliding up, a button expanding into a menu,
hero reveals. Standard motion belongs on chrome and utility controls. Two
schemes coexist; don't spring everything.

**Where it fits his apps.** Reblend (dragging objects, panels), Pixel Forge
(strip reordering, canvas tools), Yahtzee (dice, cards), Forge's deck and
palette. Anywhere the user grabs something and lets go.

**In Qt.** `QEasingCurve::OutBack` gives the overshoot; `OutElastic` gives the
bounce. For true velocity-aware springs, write a small spring animator that
integrates stiffness and damping per frame.

## See also

- [001 Micro-interactions](001-micro-interactions.md)
- [009 Shape morphing and continuity](009-shape-morphing-and-continuity.md)
- [008 Delight, done right](008-delight-done-right.md)

## Sources

- Understanding Spring Animations in SwiftUI — https://www.createwithswift.com/understanding-spring-animations-in-swiftui/
- Material 3 Expressive (skill) — https://github.com/ichintansoni/skills-master/blob/HEAD/skills/android/design/technologies/m3-expressive/SKILL.md
- Material Design Expressive: The Future of UI/UX in 2026 — https://zignuts.com/blog/google-material-design-expressive
