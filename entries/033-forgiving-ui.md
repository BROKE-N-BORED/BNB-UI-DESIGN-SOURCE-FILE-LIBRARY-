# 033 — Forgiving UI

> Entry 033 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*Nothing you do by accident is final — every action has a way back.*

**What it is.** Reversibility as a system, not a single feature: a
multi-level undo stack for edits, a timed undo window for sends and
deletes, toast-based undo for quick reversals, soft delete (trash) and
version history as safety nets, and confirmation dialogs reserved
strictly for the truly irreversible. The rule is forgiveness over
permission: let the action happen, then offer the way back, instead of
interrogating the user beforehand.

**Why it feels good.** Users explore boldly when mistakes are cheap. A
recovered mistake produces relief, which builds trust; an unrecoverable
one produces frustration and defensive, hesitant use. And every routine
confirmation dialog trains people to click without reading, so the
dialogs that matter get ignored too.

**The numbers.** Gmail's Undo Send is the canonical timed undo: promoted
from Gmail Labs to a formal setting in June 2015; desktop users choose
a 5, 10, 20, or 30-second window, with 5 seconds the default. The undo
is real because the message is *held*, not sent. During the window
nothing has left yet, and undo returns the message to a draft. The
notification sits bottom-left: "Message sent" with Undo and View
message. The forgiveness framework behind it rests on three pillars:
reversibility (return to exactly the prior state), safety nets (trash,
version history, auto-save), and graceful failure (clear, actionable
error states). Undo comes in four shapes: multi-level stack (Photoshop,
Figma), single undo, timed undo (5–30 s), and confirmable undo. When a
confirmation dialog *is* warranted, it must restate the action in the
user's terms ("Delete 'Q4 Budget Report.xlsx'?"), name the consequence
and the recovery ("moved to trash, restore within 30 days"), use
action-oriented buttons ("Delete File" / "Keep File", never Yes/No),
and never default to the destructive action.

**Where it fits his apps.** **Pixel Forge**: multi-level undo for edits
is the expected standard in a creative tool. **Reblend**: undo for
transforms and material changes. **Data Pack Builder**: undo pack edits;
soft-delete packs to a trash instead of destroying them. **DUO**:
undo-send on messages, the Gmail pattern with a 5-second window.
**Qwkhnd**: undo for task deletes. **GITDATA**: undo row edits, version
history for datasets.

**Watch out.** Timed undo is a delay, not a recall. After the window
closes the action is final, and the interface must say so. Do not call
a compensating action "Undo" if the original effect cannot be erased.
Use "Send correction" or "Request refund" instead. Irreversible actions
still need a real confirmation (type-to-confirm for account deletion).
And do not stack undo on top of a confirmation dialog for the same
action. Pick one; both together is friction with no extra safety.

## See also

- [019 Optimistic UI](019-optimistic-ui.md)
- [017 See it before you commit](017-see-it-before-you-commit.md)
- [012 Progressive disclosure](012-progressive-disclosure.md)
- [030 Toasts and snackbars that respect attention](030-toasts-and-snackbars-that-respect-attention.md)

## Sources

- Defensive Design — Gmail Undo Send, Human Standards — https://www.humanstandards.org/examples/defensive-design/defensive-design-gmail-undo/
- UX Forgiveness: Undo, Confirm & Error Recovery, Credit Union Web Solutions — https://creditunionwebsolutions.com/ux-design/the-forgiveness-principle-in-ux-design-a-practical-framework-for-designing-undo-confirmation-and-error-recovery-patterns-users-can-trust/
- Designing human-agent interaction, datarekha — https://datarekha.com/agentic-ai/agentic-ux/
