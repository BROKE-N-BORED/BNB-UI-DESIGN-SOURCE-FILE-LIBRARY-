# 047 — Live presence and named cursors

> Entry 047 — added 2026-11-13 (Drop 4: Seeing, learning, and responding).

*You can see who else is here, and where their attention is.*

**What it is.** Presence is each person's temporary state, shared with everyone else in the same document or room: where their cursor is, what they have selected, whether they are typing. Each cursor carries a name and a color, so you can tell at a glance who is doing what, and usually a row of avatars shows who is in the room at all. Figma built its whole product on this idea: everyone editing the same document at once, changes synced over a WebSocket connection, each document handled by its own server process. Liveblocks defines presence the same way in its documentation: temporary per-user state, held apart from the document itself.

**Why it feels good.** It turns a lonely document into a shared room. You stop asking whether anyone is there, and you stop overwriting each other, because you can see the other person's cursor heading for the same paragraph you are about to edit. It builds trust too: the work is visibly happening, live, instead of arriving as a surprise in the next sync. Figma's founders note that designers feared exactly this at first ("hovering art directors" and design by committee), and that the bet paid off because it removed the whole export, sync, and email-copies dance.

**The numbers.** The sources give no latency figures for presence, so this entry claims none: the figures below are mechanisms, not measurements. A cursor in presence is an x/y coordinate pair, or null when the cursor is off screen (Liveblocks). Presence is temporary state, not document data: it is shared while you are connected and gone when you leave. Figma's sync rule is last-writer-wins per property: its servers track the latest value for each property on each object, so two people changing different properties never conflict, and when two people change the same property on the same object the document ends up with the last value that reached the server. Changes are applied immediately on your screen instead of waiting for the server to acknowledge them, so the app feels responsive; incoming changes that conflict with your unacknowledged ones are discarded, so the screen never flickers between two values. Undo in multiplayer is genuinely confusing, and Figma's guiding principle is that if you undo a lot, copy something, and redo back to the present, the document should not change.

**Where it fits his apps.** Most of his apps are solo, so this is a narrow technique, and it earns its place only where people already share a session. Yahtzee: online rooms are already planned, and a presence strip showing who is at the table, whose turn it is, and who just left beats a bare player count. LYNX SHARE: in a shared session, a colored marker on the clip someone else is touching stops two people fighting over the same fader. Pixel Forge: if a shared canvas mode ever arrives, named cursors over the canvas are the natural form; until then this entry is a pattern to know, not a feature to build.

**Watch out.** Presence without a shared task is noise, so do not add it to a solo app. Presence is temporary: never save it, never build history on it. Give people a way to go quiet, since being watched while you work is not everyone's idea of fun. Keep each person's color stable across the session and distinct from everyone else's, or the cursors stop meaning anything. A cursor that flickers or lags is worse than none at all. And presence needs a connection: his apps are local-first, so this only earns its place where a session already exists, like a Yahtzee room.

## See also

- [019 Optimistic UI](019-optimistic-ui.md)
- [021 Glanceable surfaces](021-glanceable-surfaces.md)
- [033 Forgiving UI](033-forgiving-ui.md)
- [030 Toasts and snackbars that respect attention](030-toasts-and-snackbars-that-respect-attention.md)

## Sources

- How Figma's multiplayer technology works, Evan Wallace, Figma Engineering blog (archived copy, no date on the archived page) — https://www.madebyevan.com/figma/how-figmas-multiplayer-technology-works/
- Using presence, Liveblocks tutorial (no date on page) — https://liveblocks.io/docs/tutorial/react/getting-started/presence
