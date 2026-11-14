# 001 — Micro-interactions

> Entry 001 — added 2026-11-13 (Drop 1: Modern UI design techniques).

*the small moments that make it feel alive*

**What it is.** The tiny response to a tiny action: a button that dips when
pressed, a checkmark that draws itself when a task finishes, a field that shakes
gently when the input is wrong, a toggle that slides home. Each one follows four
parts: Trigger (what the user did), Rules (what happens), Feedback (what the
user sees), Loops and Modes (what changes afterwards).

**Why it feels good.** A button that doesn't respond feels broken. A form that
saves without confirmation feels uncertain. Users don't consciously notice good
micro-interactions; they notice their absence. Research cited across the 2026
roundups puts satisfaction up 15 to 25 percent from micro-interactions alone,
with no change to core functionality.

**The numbers.**
- Micro feedback (press, ripple, hover): 100 to 150 ms.
- Small UI actions: 150 to 250 ms.
- Context changes (a panel opening, a view switching): 250 to 400 ms.
- Ease-out for things entering, ease-in for things leaving, ease-in-out for
  loops. Animate transform and opacity, never layout properties, or the frame
  rate dies.

**The premium patterns, measured.**
- Button press: scale to 0.97 (3 percent smaller) over 150 ms. Smaller than
  2 percent is invisible; bigger than 5 percent looks cartoonish.
- Card hover: lift 4 px, over 200 ms, ease-out. Enough to feel tangible,
  not enough to look like a toy popping off the screen.
- Focus ring: a soft glow at about 10 percent opacity, colored border plus
  ring. Visible enough to show focus, quiet enough not to shout.

**Where it fits his apps.** Everywhere, but especially Forge (chat send,
approval buttons, tool-call status), DUO (relay send, model switch), STELLA
(training start, the moment a run finishes). The finish moment matters most:
a small celebration when a long job completes turns waiting into payoff.

**Watch out.** Every animation needs a purpose. If you can't say why it helps,
remove it. Never animate to cover up slowness; fix the slowness.

## See also

- [002 Spring physics motion](002-spring-physics-motion.md)
- [008 Delight, done right](008-delight-done-right.md)
- [009 Shape morphing and continuity](009-shape-morphing-and-continuity.md)
- [019 Optimistic UI](019-optimistic-ui.md)

## Sources

- Microinteractions in 2026 — https://www.maviklabs.com/blog/microinteractions-2026/
- 14 Best Micro-interaction Examples (2026) — https://www.designstudiouiux.com/blog/micro-interactions-examples/
- UI Micro-Interactions: Premium UX Patterns 2026 — https://rune.codes/hub/tech-trends/ui-micro-interactions-the-details-that-make-apps-feel-premium
