# 022 — Per-context profiles

> Entry 022 — added 2026-11-13 (Drop 2: Games, editors, and gadgets).

*settings follow the job*

**What it is.** The settings change themselves when the job changes. On
the Steam Deck, the Quick Menu Performance tab has a "Use per-game
profile" toggle. Turn it on, and every setting you configure (FPS cap,
power limit, refresh rate, GPU clock) saves to that specific game.
Switch from Cyberpunk 2077 to Stardew Valley and each loads its own
profile automatically, with no manual adjustment. You tune once, for
ten minutes, in the first session, and it stays set.

**Why it feels good.** Global settings force a compromise: one setup
that is wrong for half of what you do. Per-context profiles remove the
compromise and remove the remembering. The user never has to think
"did I switch the settings back?" The app already did it. The setting
follows the work, not the other way around.

**The numbers.**
- SteamOS 3.7.x, verified April 2026. The toggle lives in Quick Menu,
  Performance tab: "Use per-game profile."
- FPS cap 30 or 40. Locking to 30 FPS instead of running uncapped
  typically cuts active power draw by 30 to 50 percent.
- Power limit math on the LCD model (40 Wh battery): 10 W average is
  about 4 hours, 7 W about 5.7 hours, 5 W about 8 hours.
- Tune once: about 10 minutes in the first session with a new game,
  then it stays set unless a patch changes performance.

**Where it fits his apps.** Fyrn (a profile per model: context size,
threads, RAM cap; load the model and the settings follow), STELLA (a
profile per training job), Reblend (a profile per scene type: sculpt,
render, animate), Code Forge (a profile per project: model, budget,
tools). Any app where the right settings depend on what is open.

**Watch out.** The profile must load automatically and silently. If the
user has to remember to switch it, it is just settings with extra
steps. And always show which profile is active in one glance: a small
label, not a mystery. A user who does not know a profile switched will
blame the app when the behaviour changes.

## See also

- [015 Accessibility presets](015-accessibility-presets.md)
- [004 Just-in-time GUI](004-just-in-time-gui.md)

## Sources

- Steam Deck Battery Life Guide, Switchblade Gaming, verified April 2026 — https://www.switchbladegaming.com/game-settings/steam-deck-battery-life-guide/
- How to Optimize Steam Deck's Performance in Games, Guiding Tech, January 25, 2024 — https://www.guidingtech.com/optimize-steam-deck-performance/
