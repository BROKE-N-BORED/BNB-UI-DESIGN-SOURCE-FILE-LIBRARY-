# 009 — Shape morphing and continuity

> Entry 009 — added 2026-11-13 (Drop 1: Modern UI design techniques).

*things that change shape, not screens*

**What it is.** A button expands into a full-screen menu. A card grows into a
detail view. A small control morphs into the thing it controls. The element
keeps its identity through the transition, so the user never loses their
place. The focal point stays put; the shape changes around it.

**Why it feels good.** Screen switches are jarring: everything disappears and
something new appears, and the brain has to re-orient. A morph says "this
thing you were looking at IS the next screen." It reduces the mental effort
of figuring out where one screen ends and another begins, because there was
no switch, only a change of shape.

**Where it fits his apps.** Forge's mode windows (a rail icon expands into its
window). DUO's model picker. STELLA's job picker (pick a job, the picker
becomes the job). Anywhere a small control opens a big surface.

**Watch out.** Morphs need to be fast (under 400 ms) and interruptible. A slow
morph that can't be cancelled is worse than a plain screen switch.

## See also

- [002 Spring physics motion](002-spring-physics-motion.md)
- [001 Micro-interactions](001-micro-interactions.md)
- [007 Liquid Glass and glassmorphism 2.0](007-liquid-glass.md)

## Sources

- Transitions, Material Design 3 — https://m3.material.io/styles/motion/transitions/transition-patterns
- M3 Motion, material-design-3-skill, GitHub — https://github.com/danieldevfull/material-design-3-skill/blob/HEAD/material-design-3/references/motion.md
