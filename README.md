# BNB UI Design Source File Library

The library every Broke n' Bored app pulls its feel from.

This thread studies real software that is shipping right now: games, apps, websites, phones, tablets, gadgets, anything with an interface worth learning from. What actually works gets written up here as source files any build can pull from.

## Master rules file

`design-rules.md` at the root is the canonical combined doc: Part 1 is the design philosophy, Part 2 is the immutable rules (U1-U39 plus delivery rules D1-D3), Part 3 is the techniques drawer. From 2026-11-13, all UI design rules and material get pulled from this repo, at Joshua's order. The copy in the workspace is a working copy; this repo is the source of truth.

## How to use this library

- Each file under `techniques/` is one research drop: a set of techniques, written up properly.
- Pull what fits the app you are building. Two or three techniques per app is usually the right amount: the ones that fit what the app actually does.
- Every technique carries what it is, why it feels good, the exact numbers (timings, sizes, easing), which apps it fits, and what to watch out for.
- Every file is sourced and dated, so nothing goes stale silently.

## The bar

Every technique has to pass these before it goes in:

1. **The toy test (U34).** A child could pick it up and use it. If the technique needs explaining, it doesn't go in.
2. **It runs on the PC.** 8 GB RAM, no GPU, spinning hard drive. Motion must be cheap: transform and opacity only, no layout thrash, no heavy blur on every frame.
3. **It fits the design rules.** design-rules.md is the source of truth. Nothing here overrides it.
4. **It makes the app feel like itself.** Creativity is wanted, and every app should have a look of its own instead of the same flat thing. Decoration that gives an app its identity is fine. What fails is motion or styling that fights readability or costs frames.

## Contents

- `design-rules.md` (2026-11-13): the master rules file. Philosophy, immutable rules, techniques drawer.
- `techniques/001-modern-ui-design-techniques.md` (2026-11-13): 12 modern techniques. Micro-interactions, spring physics, calm technology, just-in-time GUI, bento grids, neo-skeuomorphism, liquid glass, delight, shape morphing, AI-native patterns, honest loading, progressive disclosure.

## Foundation notes

The three files sent 2026-11-13 were checked against the master before anything went in: the Modern UI file was already file 001, the standalone rules are inside the master doc, and the combined file with the STELLA brief is the pre-removal snapshot (the STELLA part stays out, per Joshua's order 2026-11-13). Nothing was duplicated.

## File format

Each source file carries: what each technique is, why it feels good, the numbers, where it fits across the Broke n' Bored apps, what to watch out for, and its sources.

## Maintenance

Maintained by Arlo from the Maintain BNB UI design library thread. New drops are researched from live software and current sources, then pushed here.
