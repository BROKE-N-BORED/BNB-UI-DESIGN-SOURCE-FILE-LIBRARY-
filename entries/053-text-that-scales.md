# 053 — Text that scales

> Entry 053 — added 2026-11-13 (Drop 5: Choices, motion, and craft).

*The user bumps the font size and the interface holds together instead of falling apart.*

**What it is.** Text that scales is an interface built so that when the user turns the text size up, everything grows with it: labels wrap instead of clipping, buttons get taller instead of cutting their words off, rows stack instead of overlapping, and the layout reflows instead of breaking. Every major platform has a version of this. Apple calls it Dynamic Type: the user picks a text size in Settings and every app that uses named text styles (body, headline, caption) rescales to match. Android does the same through the font size setting, with sizes defined in scaled pixels. On the Linux desktop, GNOME has a Large Text toggle in Accessibility settings. The technique is the same everywhere: size text by style or by relative unit, never by fixed pixel, and let containers grow with their content.

**Why it feels good.** The people who need bigger text are the people least able to fight a broken layout. When the interface holds together at double size, the user just reads, and never has to think about the app at all. It also protects the hierarchy: a headline must still outrank body text at the largest size, or the screen becomes unreadable in a different way than it started. Done right, scaling is invisible. The user asked for bigger words and got bigger words, and nothing else changed.

**The numbers.** WCAG success criterion 1.4.4 (Level AA) sets the bar: text must resize to 200 percent without loss of content or functionality, with only captions and images of text exempt. W3C adds that above 200 percent, full-page zoom may work better than text resizing, since extreme text growth can turn sentences into vertical columns of single words. Apple's Dynamic Type scale shows how far real users go: body text runs from 17 pt at the default size to 40 pt at the AX3 accessibility size (past 200 percent) and 53 pt at AX5, a 3.1 times range. Large Title grows less, from 34 pt to 60 pt, because big text needs less growth to stay readable. Apple's minimums are 17 pt default and 11 pt minimum on iOS and iPadOS, and 13 pt default and 10 pt minimum on macOS, and macOS does not support Dynamic Type at all, so a Mac app that wants scaling has to build it itself. Android 14 supports font scaling up to 200 percent, with a nonlinear curve: large text scales more slowly than small text, so headings do not balloon while body text is still catching up. Android sizes text in scaled pixels (sp), and its docs tell developers to test at the 200 percent maximum. On the Linux desktop, Ubuntu documents its Large Text toggle as scaling text by 1.2 times, a single fixed step, with GNOME Tweaks available for larger factors.

**Where it fits his apps.** STELLA: training graphs and model picker labels stay readable when the text is bumped, and the field explanations underneath each control (U20) wrap instead of clipping. Fyrn: model list rows grow with the text, and pull progress keeps its numbers visible at double size. Reblend: panel labels and slider values scale, and the value readouts never truncate. Yahtzee: scorecard numbers and the rules text scale for a player reading across the table. On a small laptop screen, scaling to 200 percent means windows must reflow and scroll, never clip: a panel that fits at default size needs a scrollable region or a stacked layout at large size, not a wider window. In Qt, size labels and buttons from the font, not from fixed pixels, so the layout grows with the text on its own.

**Watch out.** Fixed-height labels are the classic failure: the text grows, the box does not, and the words get cut off. W3C lists exactly this as a failure of 1.4.4 (F69: resizing to 200 percent causes text, images, or controls to be clipped, truncated, or obscured). Fixed pixel font sizes ignore the user's setting entirely, so the app looks unchanged while every other app grows. Capping sizes independently inverts the hierarchy: if the headline caps at 20 pt while body text reaches 24 pt, the screen reads backwards. Do not scale everything equally: Apple advises scaling the content the user came to read aggressively and scaling chrome conservatively or not at all, since nobody bumps the text size to read bigger tab titles. Test at the maximum, not the middle: most scaling bugs only appear at the largest sizes. And never put words in images to dodge the problem: images of text pixelate when scaled, and W3C recommends real text wherever possible.

## See also

- [015 Accessibility presets](015-accessibility-presets.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [041 Reduced motion done right](041-reduced-motion-done-right.md)
- [042 Touch targets you can actually hit](042-touch-targets-you-can-actually-hit.md)
- [052 Design tokens](052-design-tokens.md)

## Sources

- Understanding Success Criterion 1.4.4: Resize text, W3C, WCAG 2.2 — https://www.w3.org/WAI/WCAG22/Understanding/resize-text.html
- Typography, Apple Human Interface Guidelines, via mirror — https://apple-docs.everest.mt/docs/design/human-interface-guidelines/typography/
- Typography, Dynamic Type and UI Text, apple-hig-skills (HIG-derived reference tables), GitHub, accessed 2026-11-13 — https://github.com/yue1123/apple-hig-skills/blob/HEAD/apple-hig/references/foundations/typography.md
- Features and APIs Overview (Non-linear font scaling to 200%), Android Developers, Android 14, 2023 — https://developer.android.com/about/versions/14/features
- Change the size of text on the screen, Ubuntu Help, accessed 2026-11-13 (Japanese localization; the 1.2 times line is in English in the page) — https://help.ubuntu.com/stable/ubuntu-help/a11y-font-size.html.ja
