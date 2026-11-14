# 065 — Discoverable shortcuts

> Entry 065 — added 2026-11-14 (Drop 6: Structure, comfort, and trust).

*The shortcut nobody finds is a feature nobody has.*

**What it is.** Entry 028 covers the shortcut system itself: the registry, the scopes, the input-field guard. This entry is the teaching layer on top of it, the part that makes users find the shortcuts at all. It has three surfaces. First, the `?` overlay: press `?` and a dialog lists every shortcut, grouped by context. Gmail opens its shortcuts dialog on `?`, and the dialog itself carries an Enable link, so a user who finds the list can switch the feature on from inside it. GitHub opens a dialog listing the shortcuts available for the page you are on. Second, the inline hint: the key shown next to the action wherever the action already appears, in a menu item, a button tooltip, a context menu. Third, the searchable reference: VS Code's Keyboard Shortcuts editor lists every command with and without a binding, searchable by command name or shortcut, and Help > Keyboard Shortcut Reference opens a condensed printable PDF, one per platform. The command palette doubles as a teacher too: run an action from the palette, see its key beside it, press the key next time.

**Why it feels good.** Nobody sits down to memorize a shortcut list, and nobody should have to. The inline hint teaches at the exact moment of intent: the user is already reaching for Archive, and in passing learns E does it. The overlay is the safety net for the curious: one key reveals the whole map, grouped so it scans instead of looming. The palette is the ladder between mouse and keys: the beginner clicks, the intermediate types the action name and sees the key, the expert presses the key directly. Each layer catches the users the layer below missed.

**The numbers.** In Google's studies, 90 percent of people did not know how to use Ctrl/Command+F to find a word in a document or web page, on a sample size of thousands (Dan Russell, Google search anthropologist, speaking to The Atlantic in 2011). A 2025 survey of 853 people found only 6 percent had learned of the keyboard shortcut method by themselves; 28 percent of all respondents said a face-to-face social interaction was how they discovered it, and only a few reported discovering it through computer aids such as tooltips. The lesson is blunt: the interface has to do the teaching, because almost nobody stumbles onto shortcuts alone, and tooltips alone do not do it. Gmail's shortcuts need switching on in Settings, which is why its `?` dialog carries its own Enable link. Where no number exists, the mechanism is the spec: teach in layers, passive hints first, deliberate surfacing second, the overlay as the map.

**Where it fits his apps.** ACR: chart controls and trace filters already carry tooltips (040); add the key to each tooltip, and add a `?` overlay listing the analysis keys, grouped by view. MIMIK: the capture start and stop keys belong in the tooltips on those buttons, so a user learns them the first time they hover. GITDATA: search and filter keys shown beside the search field and in the row actions. Qwkhnd: one key per triage action, printed on the row action itself, so triage teaches itself in the first session. Code Forge: the `?` overlay generated from the registry (028), reachable from a visible keyboard icon as well as the `?` key. Qt fit: the overlay is a plain dialog with a list, cheap on his PC; the focus ring on the overlay's close button must be a `border` on `:focus`, since `outline` renders 0 pixels in this build; and a long overlay must scroll rather than grow past the window.

**Watch out.** Never ship shortcuts without the overlay: undiscoverable shortcuts are dead code with good intentions. Never rely on tooltips alone: the 2025 survey found few people discover shortcuts that way. The overlay must be reachable from a visible affordance, a keyboard icon or a Help menu item, not only from `?`, because the users who need it most do not know `?` exists. Show the user's actual bindings in every hint and in the overlay, not the defaults, the moment remapping exists. Do not try to teach every shortcut at once: the overlay groups by context so a user finds the ten that matter for their workflow. And keep the input-field guard from 028 sacred: a shortcut that fires while the user is typing teaches them the keyboard cannot be trusted, and unteaches everything the hints taught.

## See also

- [028 Keyboard-first power patterns](028-keyboard-first-power-patterns.md)
- [040 Tooltips that teach](040-tooltips-that-teach.md)
- [043 Command palette](043-command-palette.md)
- [039 Triggered coach marks](039-triggered-coach-marks.md)
- [014 Teach by playing](014-teach-by-playing.md)
- [023 Focus-first navigation](023-focus-first-navigation.md)

## Sources

- 90 Percent of People Don't Know What CTRL+F Does on Their Keyboards, The Village Voice, August 20, 2011 (reporting The Atlantic, August 18, 2011, Dan Russell, Google) — https://www.villagevoice.com/90-percent-of-people-dont-know-what-ctrlf-does-on-their-keyboards/
- The Role of Social Interactions in the Interaction Discovery of Keyboard Shortcuts, Proceedings of IHM 2025 (ACM), November 24, 2025 — https://dl.acm.org/doi/10.1145/3765712.3765714
- Keyboard shortcuts for Gmail, Google Support, accessed November 14, 2026 — https://support.google.com/mail/answer/6594
- Keyboard shortcuts, GitHub Docs (Enterprise Server 3.10 docs page), accessed November 14, 2026 — https://docs.github.com/en/enterprise-server@3.10/get-started/accessibility/keyboard-shortcuts
- Keyboard shortcuts for Visual Studio Code, Microsoft, accessed November 14, 2026 — https://code.visualstudio.com/docs/configure/keybindings
- SaaS Keyboard Shortcuts UX (2026), SaaS UI Design, accessed November 14, 2026 — https://www.saasui.design/blog/saas-keyboard-shortcuts-ux-patterns
