# 044 — Inline validation

> Entry 044 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*Tell the user a field is wrong while they are still looking at it.*

**What it is.** Inline validation checks a form field as the user finishes it and shows the result right next to the field, in the moment, instead of waiting for Submit and dumping every error at once. The classic shape: the user tabs out of a field, and a green check or short red message appears beside it. The timing is the whole technique. Validate after the user leaves the field (on blur), not while they are still typing, and never before they have started. Password rules are the exception: a strength meter updating as you type helps, because the user cannot guess the rules. This is distinct from entry 031, which covers error and empty states broadly; this entry is only about field-level timing and placement.

**Why it feels good.** A form that waits until Submit to complain makes the user re-read the whole form to find what went wrong, then guess, resubmit, and guess again. Wroblewski calls this pogosticking: nobody can know beforehand which username is available, so they guess, submit, find it taken, and repeat. Inline validation turns the form into a conversation: each answer gets a response while the question is still fresh, so mistakes get fixed where they happen and the user never holds an error message in memory while hunting for its field. NN/g puts it plainly: fix errors immediately, without searching or returning to a field you thought was completed correctly.

**The numbers.** Wroblewski and the usability firm Etre tested 22 people on six versions of a registration form in 2009. The best inline version, against a submit-only control: 22% higher success rates, 22% fewer errors made, 31% higher satisfaction ratings, 42% faster completion times, and 47% fewer eye fixations. Timing mattered inside the technique: validating after the user left a field finished the first half of the form 7 to 10 seconds faster than validating while typing or before and while typing, and the before-and-while version also produced more errors and lower satisfaction. Validation landed better where answers were hard: only 30% to 50% of participants even noticed messages on easy fields (name, email), while 80% to 100% noticed them on username and password. NN/g adds a tripwire: the same error 3 or more times in one attempt means the design, not the user, is at fault.

**Where it fits his apps.** Fyrn: check a model name or download URL the moment the field loses focus, before a long pull starts and fails. Data Pack Builder: validate output paths, counts, and format choices per field, so a bad pack is caught before the build runs. STELLA: flag an out-of-range learning rate or a missing dataset path while the settings are still on screen. MIMIK: confirm the save folder exists and the filename is legal the moment the field loses focus, before the first capture runs. DUO: check an API key field on blur, so a bad key is caught before the first chat call.

**Watch out.** Never validate before the user has had a chance to type: participants in the study hated red errors appearing on empty fields ("Well of course it is! I haven't even started!"). Keep messages persistent next to the field, not fading and not hidden inside it; fading messages were missed by hunt-and-peck typists watching their fingers, and in-field messages performed no better than messages beside the field. Skip success checkmarks on trivial fields: users were confused by a green check on their own name ("Are you telling me I entered a valid name or my name correctly?"). Reserve checkmarks for fields where the answer is genuinely uncertain. Keep the error text next to the field with an icon, not only color, so it reads for colorblind users too.

## See also

- [031 Empty states and error states done well](031-empty-states-and-error-states-done-well.md)
- [033 Forgiving UI](033-forgiving-ui.md)
- [034 Conversational repair](034-conversational-repair.md)
- [030 Toasts and snackbars that respect attention](030-toasts-and-snackbars-that-respect-attention.md)
- [036 Affordances and signifiers](036-affordances-and-signifiers.md)

## Sources

- Inline Validation in Web Forms, A List Apart, 2009 — https://alistapart.com/article/inline-validation-in-web-forms
- 10 Design Guidelines for Reporting Errors in Forms, Nielsen Norman Group, published 2019-02-03, updated 2024-12-12 — https://www.nngroup.com/articles/errors-forms-design-guidelines/
