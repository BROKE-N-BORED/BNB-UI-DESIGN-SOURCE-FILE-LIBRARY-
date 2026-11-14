# 032 — Self-hiding chrome

> Entry 032 — added 2026-11-13 (Drop 3: Input, feedback, and forgiveness).

*The controls get out of the way while you watch, and come back the instant you move.*

**What it is.** Interface chrome that fades out after a short idle
period and returns on any input or state change. Video players do it
with their control bars; games do it with their HUDs; fullscreen
canvases do it with their toolbars. The mechanism is a timer plus an
activity state, not a mode the user picks.

**Why it feels good.** The content becomes the whole screen. The
controls are one mouse-move away, never a hunt through a menu. And
because they return on *any* activity, the user never has to remember
how to summon them.

**The numbers.** Video.js models it as a single `userActive` true/false
state on the player: any mouse event resets a 2-second inactivity
timeout, and when the timeout fires, the control bar fades out over a
1.5-second opacity transition. To keep rapid mouse movement cheap,
mousemove only sets a flag that a 250 ms interval polls, instead of
resetting the timer on every event. In fullscreen the cursor hides the
same way (`cursor: none` when inactive). On touch devices there is no
mousemove, so a tap toggles visibility and the idle delay is longer. The
earlier approach, fading on mouseout with a 2-second CSS delay, failed
in fullscreen because the mouse can never leave the player area. In
games the same idea is driven by state, not a timer: in Ghost of
Tsushima the HUD disappears during exploration and reappears in combat,
and The Last of Us Part II runs HUD-off during traversal and dialogue,
HUD-on during combat, with the stated goal of encouraging the player "to
look into the game world, not at UI."

**Where it fits his apps.** **Pixel Forge**: fullscreen preview and
canvas view: toolbars fade while viewing, return on mouse move.
**Reblend**: 3D viewport chrome that gets out of the way while orbiting
a model. **MIMIK**: capture preview with controls that fade during
playback. **Yahtzee**: fullscreen game view where the score chrome fades
between turns and returns on hover.

**Watch out.** Never hide something the user needs to act on: recording
state, health, an unsaved change. Those return on *state change*, not
just on input. The fade must be opacity-only (cheap on his hardware);
never animate layout. Always provide a non-mouse way back: any key
press or tap. Do not hide in the middle of an interaction the user
started, like a slider drag. Keep the idle window short (2 seconds for
video is the established shape) so the screen does not feel dead.

## See also

- [003 Calm technology](003-calm-technology.md)
- [004 Just-in-time GUI](004-just-in-time-gui.md)
- [013 Diegetic UI](013-diegetic-ui.md)
- [021 Glanceable surfaces](021-glanceable-surfaces.md)

## Sources

- Hiding and Showing Video Player Controls, Video.js Blog — https://legacy.videojs.org/blog/hiding-and-showing-video-player-controls/
- U4 — Game UI/UX, HUD, Menus, and Information/Feedback Design, gamestack, GitHub — https://github.com/rondorkerin/gamestack/blob/HEAD/docs/research/round1-universal/U4-ui-ux-and-feedback.md
