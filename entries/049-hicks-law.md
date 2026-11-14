# 049 — Hick's law

> Entry 049 — added 2026-11-13 (Drop 5: Choices, motion, and craft).

*Every extra option charges a little decision time, and the bill grows slower than the menu does.*

**What it is.** Hick's law (or the Hick-Hyman law) says the time it takes to make a decision grows with the number of choices, and it grows logarithmically, not in step with the count. It comes from two choice-reaction experiments in the early 1950s. W. E. Hick's 1952 paper "On the rate of gain of information" (Quarterly Journal of Experimental Psychology) put a subject in front of ten lamps arranged in a circle, each paired with a Morse key under a different finger; a lamp lit at random and the subject pressed the matching key as fast as possible. Reaction time rose with the logarithm of the number of lamps in play. Ray Hyman's 1953 paper "Stimulus information as a determinant of reaction time" (Journal of Experimental Psychology) varied the probabilities of the alternatives and showed the driver is the information in the choice, measured in bits, not the raw count of options. The law is the decision counterpart to Fitts's law (045): Fitts governs how long it takes to reach a target, Hick governs how long it takes to pick one.

**Why it matters.** Decision time is a tax on every screen that asks the user to choose, and the law says the tax is set by information, not by item count. That gives the designer three levers that all work. Cut the options at each step, so fewer bits need deciding. Group options into categories, because people subdivide a collection and eliminate about half the remaining choices at each step rather than weighing every option one by one. Or make one option the obvious pick, by highlighting a recommended choice or a sensible default, so the effective information in the decision collapses. Nielsen Norman Group's point about long menus is the same: combining Hick's law with grouping and chunking makes long menus easy to use, so a long list is not automatically a bad one. Laws of UX adds two more moves: break complex tasks into smaller steps to decrease cognitive load, and use progressive onboarding so new users face few choices at first.

**The key facts.** For n equally probable choices, average reaction time is T = b log2(n + 1), where b is a constant fitted to measured data. Doubling the choices adds a fixed increment of time, it does not double the time. In the general case, where choices are not equally likely, the law is T = bH, where H is the information-theoretic entropy of the decision. Hick's own fit from Experiment I was RT = 0.518 log10(n + 1) seconds, with an estimated rate of gain of information of roughly 5 bits per second. The plus one in the formula is Hick's own detail: during the waiting interval the subject treats "no stimulus yet" as one more possibility. The number of alternatives in Hick's experiment ran from two to ten. The menu model of Cockburn, Gutwin and Greenberg (CHI 2007) splits the task by experience: a novice visually searches, linear in the number of items (T = 0.08n + 0.30 seconds), while an expert decides, logarithmic in the item's probability (T = 0.08H + 0.24 seconds). Going from five menu items to ten adds about 0.4 seconds of search for a novice and about 0.08 seconds of decision for an expert.

**Where it fits his apps.** STELLA: one primary action per screen (ask, or pick a model) instead of a grid of model cards, with the recommended model highlighted so the choice is nearly made. Fyrn: the model list grouped by size or task with the recommended pull first, and advanced pull options behind one "Advanced" step rather than on the first screen. Reblend: material presets as a short list of named looks, with the full slider set one click deeper for the user who wants it. Yahtzee: show only the scoring categories still open, not all thirteen at once, so the decision shrinks as the game goes on. Code Forge: review actions as three choices (approve, fix, skip), not a toolbar of ten. LYNX SHARE: a clip launcher with a small set of scenes visible per bank, so launching a clip is a glance, not a hunt.

**What it gets wrong.** The law models decision time among known, equally likely options, each with a practiced response already mapped to it, which is almost never a real menu. Hick's own Experiment I ran on himself as the subject, after more than 8,000 practice reactions. Real interfaces break all three conditions at once: the options are not known in advance, they are not equally likely, and the user has no dedicated response prepared for each. A first-time user visually searches a menu, and search is linear in the number of items, so citing Hick's law for an unfamiliar nav bar systematically understates the cost of the items added. Practice collapses the slope: after extensive practice on an eight-choice task, the gap in mean reaction time between eight and two alternatives was only 149 milliseconds. Seibel (1963) suggested the linear relation between reaction time and log set size held for two to eight alternatives, not beyond. The popular phrasing "the number and complexity of choices" has no counterpart in Hick or Hyman: their variable is transmitted information among known alternatives, not how complicated the options are. And the law is a model of decision time only. It says nothing about whether people buy, abandon, or enjoy the choice, so it cannot justify cutting options on its own. Cut options to make a decision easier, not because a formula said the count was too high.

## See also

- [045 Fitts's law](045-fitts-law.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [043 Command palette](043-command-palette.md)
- [016 Pie menus](016-pie-menus.md)
- [023 Focus-first navigation](023-focus-first-navigation.md)
- [036 Affordances and signifiers](036-affordances-and-signifiers.md)
- [054 Starter content and templates](054-starter-content-and-templates.md)

## Sources

- Hick's Law: Designing Long Menu Lists (video), Katie Sherwin, Nielsen Norman Group, July 6, 2018 — https://www.nngroup.com/videos/hicks-law-long-menus/
- Hick's law, Wikipedia, accessed 2026-11-13 — https://en.wikipedia.org/wiki/Hick's_law
- Hick's Law, Laws of UX, Jon Yablonski — https://lawsofux.com/hicks-law/
- Two Laws Designers Quote and Misuse, Moc Mallen — https://www.mocmallen.com/blog/fitts-and-hick-misused
