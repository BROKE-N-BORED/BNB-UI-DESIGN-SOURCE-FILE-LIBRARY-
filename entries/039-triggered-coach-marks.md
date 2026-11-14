# 039 — Triggered coach marks

> Entry 039 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*One hint, on one control, at the exact moment the user needs it.*

**What it is.** A coach mark is a small overlay, usually a dimmed layer with a cutout, an arrow, and a few words, that points at one control and explains it. A triggered coach mark appears only when the user's behavior says the hint is useful right now: the first time they open a panel, reach a feature, or hit a state where the control matters. It never appears before that moment, and it never arrives as part of a front-loaded tour. Nielsen Norman Group calls this a pull revelation: help content triggered by a signal that the user would benefit from that information at that moment. The opposite is a push revelation, a tutorial shown at launch or at a random point, which interrupts, gets skipped, and is quickly forgotten. Figma does the triggered version well: a tip about a text change appears only once the user has added a text box, when the information is immediately usable.

**Why it feels good.** The user is already looking at the control and already doing the task, so the hint lands in context and asks for no memorization. NN/g puts it plainly: presenting hints one by one, at the right moment, makes instructions much easier to understand and learn, and it teaches the user at which point in the workflow the feature applies. It also respects the paradox of the active user: people launch an app to do a task, not to study the interface. A triggered mark meets them inside the task instead of lecturing them before it.

**The numbers.** Short-term memory fades in about 20 seconds, per NN/g, which is why a hint shown at launch is gone before the user reaches the control it describes. Apple's Human Interface Guidelines put hard bounds on the same idea for tips: keep a tip to one or two sentences, and if a feature needs more than three actions it is too complicated for a tip. Apple also advises setting a display cadence when an app has more than one tip, for example once every 24 hours, so tips never pile up. On effectiveness, the honest picture is thin: a study (Noriega et al., published by Springer in 2020) ran a between-subject test with four tasks, one group with overlays and one without, and found a tendency toward lower completion times with overlays, but the sample was too small to confirm the result statistically. Treat the benefit as plausible, not proven.

**Where it fits his apps.** Pixel Forge: the first time the user opens the layers panel, one mark points at the blend mode control and says what it does, then never shows again. Reblend: the first time a material is selected, a mark points at the roughness slider, the one control that changes the look most. Code Forge: when the first review issue appears, a mark points at the fix button, so the user learns the core loop at the moment it matters. ACR: on the first trace run, a mark points at the chart scrubber, since scrubbing is the gesture that makes the trace readable.

**Watch out.** Never chain marks into a tour. NN/g warns that a series of tips overloads working memory and makes the app look complicated and daunting, which alone can send a new user hunting for a simpler alternative. One mark per moment, spaced out. Make the mark look like an annotation, not part of the interface: NN/g recommends a different font from the main UI, ideally one with a handwritten feel, so users never try to click the hint itself. Skip the obvious: never mark a standard control, since a gear icon already means Settings. Always make the mark easy to dismiss and easy to recall, for example through a Help menu entry that replays the marks, because the user who dismissed one in a hurry will want it back later. And never trigger on a guess about intent: Clippy failed because its pattern matching was often wrong and its interruptions were intrusive, the exact failure this technique exists to avoid.

## See also

- [004 Just-in-time GUI](004-just-in-time-gui.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [014 Teach by playing](014-teach-by-playing.md)
- [020 Setup checklist](020-setup-checklist.md)
- [040 Tooltips that teach](040-tooltips-that-teach.md)

## Sources

- Instructional Overlays and Coach Marks for Mobile Apps, Nielsen Norman Group, February 16, 2014 (updated April 24, 2020) — https://www.nngroup.com/articles/mobile-instructional-overlay/
- Onboarding Tutorials vs. Contextual Help, Nielsen Norman Group, February 12, 2023 (updated February 13, 2024) — https://www.nngroup.com/articles/onboarding-tutorials/
- Offering help, Apple Human Interface Guidelines, updated November 1, 2026 (tips guidance added September 12, 2023; via mirror, developer.apple.com would not load) — https://apple-docs.everest.mt/docs/design/human-interface-guidelines/offering-help/
- Effectiveness of Coach Marks or Instructional Overlay in Smartphone Apps Interfaces, Noriega et al., Advances in Ergonomics in Design, Springer, 2020 — https://www.springerprofessional.de/en/effectiveness-of-coach-marks-or-instructional-overlay-in-smartph/16768770
