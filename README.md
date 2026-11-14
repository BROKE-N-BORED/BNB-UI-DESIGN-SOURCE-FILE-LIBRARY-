# BNB UI Design Source File Library

The library every Broke n' Bored app pulls its feel from.

This thread studies real software that is shipping right now: games, apps, websites, phones, tablets, gadgets, anything with an interface worth learning from. What actually works gets written up here as source files any build can pull from.

## How to use this library

- Each file is one research drop: a set of techniques, written up properly.
- Pull what fits the app you are building. Two or three techniques per app is usually the right amount: the ones that fit what the app actually does.
- Every technique carries what it is, why it feels good, the exact numbers (timings, sizes, easing), which apps it fits, and what to watch out for.
- Every file is sourced and dated, so nothing goes stale silently.

## The bar

Every technique has to pass these before it goes in:

1. **The toy test (U34).** A child could pick it up and use it. If the technique needs explaining, it doesn't go in.
2. **It runs on the PC.** 8 GB RAM, no GPU, spinning hard drive. Motion must be cheap: transform and opacity only, no layout thrash, no heavy blur on every frame.
3. **It fits the design rules.** design-rules.md is the source of truth. Nothing here overrides it.
4. **It earns its place.** It helps the user understand, feel, or enjoy something. Delight and personality count. Creativity is wanted, and every app should have a look of its own instead of the same flat thing.

## Contents

- `techniques/001-modern-ui-design-techniques.md` (2026-11-13): 12 modern techniques. Micro-interactions, spring physics, calm technology, just-in-time GUI, bento grids, neo-skeuomorphism, liquid glass, delight, shape morphing, AI-native patterns, honest loading, progressive disclosure.

## File format

Each source file carries: what each technique is, why it feels good, the numbers, where it fits across the Broke n' Bored apps, what to watch out for, and its sources.

## Maintenance

Maintained by Arlo from the Maintain BNB UI design library thread. New drops are researched from live software and current sources, then pushed here.
