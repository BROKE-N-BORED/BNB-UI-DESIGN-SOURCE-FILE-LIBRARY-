# 030 — Toasts and snackbars that respect attention

> Entry 030 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*The quiet confirmation: tell them it worked, then get out of the way.*

**What it is.** A snackbar (Material Design's name for a toast) is a
small, temporary message anchored to the bottom of the screen that
confirms something just happened ("Message deleted", "Photo saved") and
then disappears on its own. It is the lightest-weight feedback surface
there is: below it nothing, above it a banner (persistent, low-severity),
above that a dialog (blocks everything). The rule is to always start at
the least intrusive surface that still informs the user. A snackbar
carries at most one brief action, usually Undo, and there is only ever
one on screen at a time. Further messages queue behind it rather than
stacking.

**Why it feels good.** It closes the loop without stealing focus. The
user did a thing, the app says "done" in past tense ("Draft deleted",
not "Deleting draft…"), and if they made a mistake the Undo is right
there for a few seconds. No modal to dismiss, no flow interrupted, no
decision demanded. The past-tense wording matters: it anchors the user's
model that the action already happened and the snackbar is the receipt,
not a question.

**The numbers.** A snackbar disappears on its own after **4–10 seconds**
(M3 feedback skill doc, citing Material Design 3). The undo window
follows the same rule: at least 4 seconds, up to 10 seconds for
consequential reversals. One snackbar at a time; queue, never stack. A
banner, the next step up, offers at most two actions and must be
dismissible. Snackbars must not be used for errors that block the flow,
for persistent system status, or for marketing.

**Where it fits his apps.** **DUO**: "Message sent" confirmations and
"Draft deleted / Undo" after clearing a chat, instead of a confirm
dialog every time. **MIMIK**: "Clip saved" / "Capture stopped"
confirmations that don't yank focus from the capture. **Qwkhnd**: task
completion and "Moved to Done / Undo" after a quick action. **Pixel
Forge**: "Export finished" and "Preset applied" without a modal.
**GITDATA**: "Sync complete" after a background pull.

**Watch out.** Never put a must-read error in a snackbar. It vanishes on
its own within seconds and a user who looked away misses it; errors that
block the flow get a dialog or an inline message next to the field.
Never stack two snackbars, and never use one for marketing. Android
system Toasts are the wrong tool: they appear outside the app window,
can't carry an action, and aren't reliably announced by screen readers.
Use the in-app snackbar pattern instead. Keep the action label to
"Undo"; "Undo delete" is redundant when the message already says what
was deleted.

## See also

- [001 Micro-interactions](001-micro-interactions.md)
- [003 Calm technology](003-calm-technology.md)
- [033 Forgiving UI](033-forgiving-ui.md)
- [019 Optimistic UI](019-optimistic-ui.md)

## Sources

- Material Design 3 feedback patterns, m3-feedback skill doc, snapshot 2026-06-06 — https://github.com/ichintansoni/skills-master/blob/HEAD/skills/android/design/patterns/m3-feedback/SKILL.md
- Snackbar, Material Design 3 — https://m3.material.io/components/snackbar/overview
