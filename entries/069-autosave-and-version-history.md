# 069 — Autosave and version history

> Entry 069 — added 2026-11-14 (Drop 6: Structure, comfort, and trust).

*Work that saves itself, and can be wound back.*

**What it is.** Two halves of one promise. Autosave means the app
writes your work without being asked: Google Docs has no save button
at all, it syncs every edit to the cloud within seconds, and the only
visible trace is a status line that cycles through Saving, All changes
saved in Drive, and Offline. Figma does the same for design files and
says so plainly: working in the cloud means you do not have to worry
about regularly saving or backing up your files. Version history is
the second half: every saved state kept as a point you can return to.
Google Docs keeps a timeline back to the document's creation, with
named versions you can label ("Before edits", "Final draft"). Figma
cuts a checkpoint every 30 minutes and lets you name versions with a
title and description. VS Code's Timeline view records a full copy of
a file at every save, no git required. Obsidian runs two layers: the
File recovery plugin snapshots notes locally, and Obsidian Sync keeps
a server-side version history. Restoring is usually safe by design:
Figma's restore adds two checkpoints, one saving the state you are
leaving and one for the state you restored, so the current work is
never destroyed by going back. This is distinct from 033: undo reverses
an action inside one session, while version history reaches across
sessions and days, and it rescues work you did not even know was lost
until later.

**Why it feels good.** Saving is a chore the user should never have
to think about, and the fear of losing work is a tax on every edit.
Autosave removes both at once. The visible Saved state is the trust
mechanism: a small line of text that says the work is safe, right
where the user can check it without opening anything. Version history
removes the fear of the edit itself: a bad rewrite, a deleted
paragraph, a wrong turn three days ago, all recoverable, which is
what makes people willing to experiment instead of hoarding cautious
copies named final_v7. Named versions add intent to the timeline: a
timestamp says when, a name says why.

**The numbers.** Figma records a new checkpoint every 30 minutes and
keeps the current version up to date with your changes. On the free
Starter plan and in Drafts, only 30 days of version history are
reachable; a paid plan opens the full history. Figma clips version
titles longer than 25 characters and asks for descriptions under 140
characters to read at a glance. VS Code's local history is on by
default and keeps 50 entries per file, each a full copy of the file,
with a 256 KB file size limit and a 10 second merge window that folds
rapid saves into one entry. Obsidian's File recovery snapshots a note
at least 5 minutes apart and keeps snapshots for 7 days, both
configurable; Sync keeps note versions for 1 month on Standard and 12
months on Plus, and attachment versions for 2 weeks. Google Docs
syncs each edit within seconds, and a deleted document sits in Trash
for 30 days before permanent deletion. Figma stores offline changes
in the browser for up to 30 days, or 7 days in Safari. For contrast,
Word's AutoRecover saves a recovery copy every 10 minutes by default,
which is why a crash in Word can cost minutes of work while a crash
in Docs costs seconds at most.

**Where it fits his apps.** ACR: autosave every analysis run and
its settings as it goes, with a visible "Saved" line in the status
bar, and keep earlier runs as restorable versions so a re-run never
destroys the first result. MIMIK: a capture is autosaved the
moment it ends, and the capture library keeps earlier trims as
versions instead of overwriting. GITDATA: row edits save
immediately with a Saved indicator, and dataset snapshots get names
("before dedupe", "v2 import") so a bad transform is one restore away.
Qwkhnd: task edits and moves save instantly, and deleted tasks
stay recoverable for a stated window instead of vanishing. Code
Forge: a VS Code style Timeline for reviewed files, one entry per
save, capped and stated. In Qt, the Saved state is plain text in the
status bar, never an animation; the history list needs a visible
`border` on `:focus`, since `outline` renders 0 pixels in this build;
and a restore dialog that grows a preview section must scroll.

**Watch out.** Autosave saves mistakes too. In Google Docs a deleted
paragraph is committed the moment you delete it; only the history
saves you, so history is not optional, it is the other half of the
feature. History expires, and it usually expires silently: Figma's
free 30 days, Obsidian's 7 day default, VS Code's 50 entry cap, and
Figma's 30 day offline window all quietly drop old versions, so say
the window out loud in the UI instead of letting the user discover
it after the fact. Google says revisions may occasionally be merged,
so fine-grained history can collapse into coarser versions without
warning. Conflicts need a human decision: when Figma syncs
offline changes that clash with the latest file, it shows a
notification with Review or Dismiss, and it cuts a checkpoint before
and after applying the offline changes. Restoring is not the same
everywhere: Figma's restore is non-destructive, but Obsidian's
Restore replaces the note contents, so offer Copy to a new note as
well as Restore. Deleting history is permanent in every app that
offers it: Docs warns that deleting version history cannot be
undone, Obsidian's Clear history irreversibly deletes all snapshots,
and Figma cannot undo deleting version info. Local history is
per-device: Obsidian snapshots never sync between devices, VS Code
history lives on one machine, and Figma's offline changes live in
one browser's storage, so clearing the cache wipes them. And Docs
only shows version history to people with edit permission, so a
viewer who loses work has no way back at all.

## See also

- [033 Forgiving UI](033-forgiving-ui.md)
- [038 Comparison and diff views](038-comparison-and-diff-views.md)
- [017 See it before you commit](017-see-it-before-you-commit.md)
- [030 Toasts and snackbars that respect attention](030-toasts-and-snackbars-that-respect-attention.md)

## Sources

- Find what's changed in a file, Google Docs Editors Help — https://support.google.com/docs/answer/190843
- Does Google Docs Autosave?, Nerd Techy, 2026-03-19 — https://nerdtechy.com/does-google-docs-autosave (secondary source)
- View a file's version history, Figma Help — https://help.figma.com/hc/en-us/articles/360038006754-View-a-file-s-version-history
- What can I do offline in Figma?, Figma Help — https://help.figma.com/hc/en-us/articles/360040328553-What-can-I-do-offline-in-Figma
- File recovery, Obsidian Help — https://obsidian.md/help/plugins/file-recovery
- Version history, Obsidian Help — https://obsidian.md/help/Obsidian+Sync/Version+history
- User interface (Timeline view, Local file history), Visual Studio Code Docs — https://code.visualstudio.com/docs/editing/getting-started/userinterface
