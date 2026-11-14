# 021 — Glanceable surfaces

> Entry 021 — added 2026-11-13 (Drop 2: Games, editors, and gadgets).

*one fact, no opening the app*

**What it is.** A surface that answers one question without opening the
app: a home screen widget, a lock screen Live Activity, a status chip.
One fact, one number, one action at most. Apple Sports delivers live
scores to the Lock Screen and Apple Watch through Live Activities, and
by February 2026 Apple was expanding that coverage further. Android's
Live Updates do the same for ongoing tasks like navigation, rideshare
tracking, and food delivery. The widget is not a mini-app. It is a
glance.

**Why it feels good.** Roughly 40 percent of mobile interactions are
microsessions under 15 seconds (Nielsen Norman Group). People do not
want to open an app to check one fact; they want the fact where they
already are. A glanceable surface respects that. It also respects
attention: the surface appears for the event, then disappears when the
event ends. Nothing to manage, nothing to close.

**The numbers.**
- About 40 percent of mobile interactions are microsessions under 15
  seconds (Nielsen Norman Group).
- The 5-second test: if a person cannot register the primary metric in
  the time it takes to glance, the layout has failed.
- Apple caps Live Activity visual transitions at 2 seconds, to protect
  battery life.
- Background reloads are budgeted: 40 to 70 refreshes per day on iOS,
  and a 30-minute floor on periodic updates on Android. Show a relative
  timestamp (Updated 12m ago) when data is batched.
- Touch targets: at least 44 by 44 points on iOS, 48 by 48 dp on
  Android. A 2 by 2 card gets a single trigger, not a button matrix.
- Five to nine metrics per card cluster, no more. One display metric,
  a sparkline, a delta badge.
- Distance viewing (docked or ambient mode): drop labels, bump numbers
  to 24 to 32 points.
- iOS enforces a 30 MB memory crash threshold on widgets: vector glyphs
  and system fonts, no uncompressed bitmaps or multi-layer blurs.

**Where it fits his apps.** On a desktop these are tray icons, status
chips, and small always-on windows, not phone widgets. STELLA (a small
training status card: epoch, loss, time left), Code Forge (a run-status
chip), MIMIK (capture status: recording, paused, file size), Fyrn
(model loaded, RAM in use, in the tray).

**Watch out.** One fact, one action at most. The moment a glanceable
surface grows a menu, it has become a mini-app and failed. Stale data
is worse than no data: if the refresh is batched, say when it was last
updated. And respect the refresh budget: polling every second kills the
battery and hammers the drive for a number that changes every minute.

## See also

- [003 Calm technology](003-calm-technology.md)
- [005 Bento grids](005-bento-grids.md)

## Sources

- Widget Design Ideas: 5 UI Patterns for Mobile and SaaS, Fireart, updated 2026-11-13 — https://fireart.studio/blog/ui-ideas-for-designing-widgets/
- Five Interface Moves That Look Ready to Define 2026, DEV, 2026-05-05 — https://dev.to/hng__9dcd454bcbf63005b/five-interface-moves-that-look-ready-to-define-2026-3km
