# Resonance — Project Status

> **Date:** 2026-10-05
> **Phase:** 0 — Resonance production reset
> **Engine:** Godot 4.x / GDScript
> **Status:** production seed prepared; account-level repository migration pending

## Current state

The browser prototype has completed its role as pre-production R&D. Its final
checkpoint is preserved in the historical repository on branch
`web-prototype-final`.

A clean Godot production tree has been prepared separately. It intentionally does
not import the old TypeScript, Vite, Three.js, PixiJS, Web Audio, DOM UI or browser
deployment architecture.

## Locked production direction

- Android / Google Play is the primary shipping target.
- Windows / Steam is the secondary shipping target.
- Combat remains five-lane and portrait 9:16.
- Desktop preserves the same combat geometry inside a wider presentation.
- Audio time remains authoritative.
- Timeline events must resolve chronologically across dropped frames.
- Conductor and Dancer are the only active bosses.
- Initial production scope target is six major encounters.
- Conductor remains whole-character frame-by-frame 2D.
- Dancer's production animation pipeline remains open.
- Story fundamentals remain intentionally unresolved.

## Repository migration

Agreed end state:

1. historical browser repository → `jtyneham/resonance-web-prototype`
2. fresh production repository → `jtyneham/resonance`
3. this production seed becomes the starting tree of the new repository

The current GitHub connector can edit repository contents and branches but cannot
rename repositories or create new repositories. Those two account-level actions
remain to be completed before this seed is promoted into its final home.

## Do not implement yet

Do not begin production Conductor integration, final art migration or encounter
content before the Phase 1 game framework and Phase 2 narrative work are complete,
unless the user explicitly changes the production order.

## Next milestone

Complete the repository move, then begin:

**Phase 1 — Game Vision and Full Design Framework**
