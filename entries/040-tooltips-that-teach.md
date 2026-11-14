# 040 — Tooltips that teach

> Entry 040 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*The answer appears where the question is, then gets out of the way.*

**What it is.** A tooltip is a brief, user-triggered message that appears when the pointer hovers over a control, or when keyboard focus rests on it, and explains that control in the moment. Material Design 3 splits tooltips into two kinds. A plain tooltip is a short label for an icon-only button or field. A rich tooltip is a small card with a subhead, longer text, and up to two buttons, for definitions or explanations of a feature's value. A tooltip that teaches names the action and its effect in one breath, for example "Search by image" on an unlabeled camera icon. A bad one repeats the label, states the obvious, or hides information the user needs to finish the task. Nielsen Norman Group draws a sharp line here: tips that pop up on their own to announce features are not tooltips at all, since a real tooltip is always triggered by the user.

**Why it feels good.** The user asks by hovering, so the help arrives exactly when curiosity peaks and vanishes when it is done. No tour, no modal, no reading ahead. NN/g frames the hover tooltip as a pull revelation, help triggered by a signal that the user wants it now, and points to Photoshop's hover tooltips, which animate the tool's effect so a new user learns by seeing what the tool does.

**The numbers.** Apple puts a hard cap on tooltip length: a maximum of 60 to 75 characters, starting with a verb, without repeating the control's name, in sentence case. If a control needs more text than that, Apple says the interface design is the problem. Material Design 3 gives the measurements: a plain tooltip container is 24dp high with 8dp padding, placed above its control, 4dp away from a button edge or 8dp from a text baseline. A rich tooltip uses 12dp top padding, 8dp bottom padding, and 16dp side padding, with up to two buttons, and its position adjusts in 8dp increments to stay on screen. On behavior, M3 says transient tooltips disappear 1.5 seconds after the pointer leaves the target region, and only one tooltip shows at a time: triggering a new one immediately closes any open one. Where no number exists, NN/g gives the mechanism instead: a tooltip is microcontent, short text fragments intended to be self-sufficient, so if the text needs more than a line or two it has stopped being a tooltip.

**Where it fits his apps.** Pixel Forge: every icon-only toolbar button gets a verb-first tooltip, so a new user learns the tools by hovering instead of guessing. Reblend: material sliders get tooltips that say what the value does to the render, turning a row of numbers into something learnable. Fyrn: the model list's pull and quantize actions get one-line tooltips explaining what each does before the user commits to a long download. ACR: chart controls and trace filters get tooltips naming the gesture, since the gestures are the part a new user cannot see. Code Forge: the queue and deck icons get tooltips that name the action and its keyboard shortcut, teaching the shortcut at the moment of use.

**Watch out.** Never put essential information in a tooltip. NN/g's example is Amtrak hiding password requirements in a hover tooltip: requirements belong on screen, because a tooltip disappears and forces the user to hold the text in working memory. Instructions, field requirements, and anything destructive belong in visible text or a dialog, never in a tooltip. Support keyboard focus as well as mouse hover, or keyboard users never see the help at all. Be consistent: if only some icons have tooltips, users never learn to trust hovering. Position the tooltip so it never covers the control or the content it describes, and use an arrow when several controls sit close together, or the user cannot tell which element the tip belongs to. And if the explanation needs more than a line or two, reach for a rich tooltip, a help panel, or a coach mark instead.

## See also

- [012 Progressive disclosure](012-progressive-disclosure.md)
- [028 Keyboard-first power patterns](028-keyboard-first-power-patterns.md)
- [031 Empty states and error states done well](031-empty-states-and-error-states-done-well.md)
- [036 Affordances and signifiers](036-affordances-and-signifiers.md)
- [039 Triggered coach marks](039-triggered-coach-marks.md)

## Sources

- Tooltip Guidelines, Nielsen Norman Group, January 27, 2019 (updated January 16, 2024) — https://www.nngroup.com/articles/tooltip-guidelines/
- Tooltips, Material Design 3, accessed November 13, 2026 — https://m3.material.io/components/tooltips
- Tooltips: Guidelines, Material Design 3, accessed November 13, 2026 — https://m3.material.io/components/tooltips/guidelines
- Tooltips: Tokens and specs, Material Design 3, accessed November 13, 2026 — https://m3.material.io/components/tooltips/specs
- Offering help, Apple Human Interface Guidelines, updated November 1, 2026 (via mirror, developer.apple.com would not load) — https://apple-docs.everest.mt/docs/design/human-interface-guidelines/offering-help/
- Onboarding Tutorials vs. Contextual Help, Nielsen Norman Group, February 12, 2023 (updated February 13, 2024) — https://www.nngroup.com/articles/onboarding-tutorials/
