# 042 — Touch targets you can actually hit

> Entry 042 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*Make every clickable thing big enough to hit on the first try, with a shaky hand or a trackpad.*

**What it is.** A touch target is the whole area that responds to a click or tap, not just the visible icon or label inside it. A 16 pixel trash icon inside a 48 pixel padded button has a 16 pixel icon and a 48 pixel target, and only the second number decides whether someone can hit it. This technique is the discipline of sizing every control's hit area to a real minimum and giving neighbors enough clear space that a miss lands on empty background instead of the wrong button. It matters on desktop just as much as on phones: WCAG's criterion covers every pointer, mouse and trackpad included, and people with tremors or limited fine motor control miss small targets with a mouse too.

**Why it feels good.** Missing a small button is a tiny failure that happens dozens of times a day, and each one costs a second of attention and a little trust in the app. Hitting the wrong button next to it is worse, especially when the wrong button deletes something. Generous targets make an app feel forgiving and fast: the hand does not have to slow down to be precise, and the eye does not have to hunt for a 12 pixel speck. Fitts's law, from Paul Fitts's 1954 research, says the time to reach a target depends on its size and its distance, so bigger and closer both make every action quicker. The fix is usually free: padding grows the hit area without changing the look at all.

**The numbers.** WCAG 2.2 Success Criterion 2.5.8 Target Size (Minimum), Level AA, requires targets for pointer inputs to be at least 24 by 24 CSS pixels, with five exceptions (spacing, equivalent, inline, user agent control, essential). The spacing exception works by a 24 CSS pixel diameter circle centered on each undersized target: it passes only if that circle intersects no other target and no other undersized target's circle. The W3C's own example: 20 by 20 pixel buttons with a 4 pixel gap between them pass, the same buttons with no gap fail. The stricter 2.5.5 Target Size (Enhanced), Level AAA, asks for 44 by 44 CSS pixels. Apple lists a default control size of 44 by 44 points on iOS and iPadOS, with a 28 by 28 point minimum. Material Design 3 says to consider touch targets of at least 48 by 48dp and pointer targets of at least 44 by 44dp; Android's guidance adds that a 48 by 48dp target is about 9mm on screen, that targets should be separated by 8dp of space or more, and that the recommended size for touchscreen objects is 7 to 10mm. Treat 24 as the floor everywhere, 44 as the working standard, and 48 as the comfortable target.

**Where it fits his apps.** Pixel Forge: toolbar and palette icons keep their small artwork but get padded hit areas, and the color swatch grid gets real spacing so a click never lands on the neighboring swatch. LYNX SHARE: clip pads and mixer controls are large by nature, but the small mute, solo, and delete buttons beside them are the classic miss-and-hit-the-wrong-one case. Yahtzee: dice and scorecard cells are the whole game, so each die and each score row needs a full, generous hit area rather than a tight box around the pips. MIMIK: capture start and stop sit next to each other and do opposite things, so both need size and separation. Qwkhnd: triage actions (done, snooze, delete) are tapped in rapid succession, so each row action needs a full-height target with clear gaps between neighbors.

**Watch out.** Padding counts toward the target and margin does not, because margin sits outside the clickable element, so grow targets with padding or an explicit minimum size, never with margin. Rounded corners can quietly fail the test: a round button 24 pixels across cannot hold a solid 24 by 24 square inside it, so it still counts as undersized. Do not lean on the spacing exception as a design strategy: the W3C warns that very small targets with no neighbors can technically pass while still being hard to activate, and it encourages meeting the 24 pixel size anyway. And size is only half the problem: a correctly sized button still gets missed if the layout shifts under the pointer, so pair this with stable layouts.

## See also

- [015 Accessibility presets](015-accessibility-presets.md)
- [016 Pie menus](016-pie-menus.md)
- [023 Focus-first navigation](023-focus-first-navigation.md)
- [027 Drag and drop done right](027-drag-and-drop-done-right.md)
- [036 Affordances and signifiers](036-affordances-and-signifiers.md)
- [045 Fitts's law](045-fitts-law.md)

## Sources

- Understanding Success Criterion 2.5.8: Target Size (Minimum), W3C WAI — https://w3c.github.io/wcag/understanding/target-size-minimum
- Touch target size, Android Accessibility Help, Google — https://support.google.com/accessibility/android/answer/7101858
- Tap Target Size Guidelines: WCAG 2.2, Apple and Material Compared, ProCurveUX, November 9, 2026 — https://www.procurveux.com/blog/tap-target-size-guidelines (Apple HIG and Material Design 3 figures via this comparison; developer.apple.com would not load)
