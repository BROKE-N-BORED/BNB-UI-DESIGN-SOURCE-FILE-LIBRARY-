# 071 — Microcopy that earns its place

> Entry 071 — added 2026-11-14 (Drop 6: Structure, comfort, and trust).

*Every word does a job, or it goes.*

**What it is.** Microcopy is the words layer of the interface: button labels, error messages, confirmations, field labels, helper text, the short strings a user reads while doing something. Nielsen Norman Group defines it as copy shorter than three sentences, and gives it three jobs: inform, influence, and interact. A button label is interaction microcopy: it tells the user what will happen if they click. An error message is informational microcopy: it tells them what went wrong and what to do next. NN/g's 3 C's set the priority order, and the order is strict: clarity first, concision second, character last. Character, tone and humor and personality, is welcome, but only after the string is already clear and tight. This entry is about the wording itself, everywhere in the app. Entry 031 covers the empty and error states as screens; entry 040 covers tooltips as a surface. This is the sentence inside each of them.

**Why it feels good.** Users scan, they do not read. A button that says what happens removes a decision: "Create an account" needs no thought, "Get started" needs a guess. An error that says what to do next turns a dead end into a next step: NN/g's example is an Out of stock message that says when the item returns or offers a restock notification, instead of stopping at the failure. And when the words are plain and specific, the product feels competent and honest, which is most of what trust is made of. Character is the last touch: Owala replacing Add to Cart with "Out of stock - notify me" leads with the barrier and offers the fix in one label, and OpenAI announcing "Sora 2 is here" instead of a formal launch line sounds like a person, not a press release. Both work because the clarity was already there.

**The numbers.** In NN/g's 1997 writing study, 81 users across three studies, a site rewritten to be concise scored 58 percent higher in measured usability than the promotional original, scannable scored 47 percent higher, objective scored 27 percent higher, and all three together scored 124 percent higher. The study is old, 1997, so treat the exact percentages as historic and the principle as current. On length: NN/g notes page titles over 60 characters tend to be truncated in search results, and descriptions run to about 160 characters. VA.gov's design system caps button labels at 35 characters, with a 50 character absolute maximum enforced by the component, and never truncates a label. On errors: NN/g puts the number of people worldwide with a color vision deficiency at roughly 350 million, which is why an error must never be signaled by color alone. Where no number exists, the mechanism is the spec: every word must serve a purpose, and a few extra words are fine if they make the string easier to understand.

**Where it fits his apps.** ACR: error messages that name the file and the fix, "Could not read this file. Check it is a text file and try again," and buttons that say what happens, "Analyze this file" instead of "Run." MIMIK: capture errors with a next step, "No camera found. Check the cable, then try again," and a plain confirmation when a clip is saved. GITDATA: sync errors that say what to do, and buttons like "Sync now" instead of "OK." Qwkhnd: confirmations in plain words, "Delete this task?" with buttons "Delete task" and "Keep task," never "Yes" and "No." STELLA and DUO: chat copy that says what the model is doing in plain words while it works. Qt fit: wording costs nothing on his PC, it is the cheapest improvement in the library; long error text in a dialog must scroll rather than clip, and the focus ring on dialog buttons must be a `border` on `:focus`.

**Watch out.** Never blame the user: NN/g bans "invalid," "illegal," and "incorrect" from error copy, because the system failed to accommodate the input, not the other way around. Never hide the fix: an error that only announces failure is half a message. Avoid humor in errors, it goes stale the second time the user sees it. Do not put essential information only in a tooltip (040). Do not let character cost clarity: Disneyworld hiding "no results" behind puns left users unsure whether anything was wrong. Do not flag an error prematurely: NN/g calls an error on an empty field that merely lost focus a hostile pattern. And never write "Submit" or "OK" when the label can say what happens: VA.gov's rule is that a label must let the user predict the result of the click from the label alone.

## See also

- [031 Empty states and error states done well](031-empty-states-and-error-states-done-well.md)
- [040 Tooltips that teach](040-tooltips-that-teach.md)
- [044 Inline validation](044-inline-validation.md)
- [030 Toasts and snackbars that respect attention](030-toasts-and-snackbars-that-respect-attention.md)
- [036 Affordances and signifiers](036-affordances-and-signifiers.md)
- [008 Delight, done right](008-delight-done-right.md)

## Sources

- The 3 C's of Informational Microcopy, Nielsen Norman Group, March 20, 2026 — https://www.nngroup.com/articles/3-cs-microcopy/
- The 3 I's of Microcopy: Inform, Influence, and Interact, Nielsen Norman Group, August 1, 2025 — https://www.nngroup.com/articles/3-is-of-microcopy/
- Error-Message Guidelines, Nielsen Norman Group, May 15, 2023 (updated August 2, 2024) — https://www.nngroup.com/articles/error-message-guidelines/
- Concise, SCANNABLE, and Objective: How to Write for the Web, Nielsen Norman Group, January 2, 1997 — https://www.nngroup.com/articles/concise-scannable-and-objective-how-to-write-for-the-web/
- Button labels, VA.gov Design System, accessed November 14, 2026 — https://design.va.gov/content-style-guide/button-labels
