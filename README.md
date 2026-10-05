# Resonance Web Prototype

> **Status: preserved pre-production prototype / R&D archive**
>
> Active production is moving to a fresh Godot-based `jtyneham/resonance` repository.
> This repository should be renamed to `jtyneham/resonance-web-prototype` during the
> migration. Do not continue production implementation here.

**Five lanes. One spark. Strike the rhythm back.**

This repository contains the original portrait-first browser prototype for
**Resonance**. It proved the game's core five-lane musical combat, touch controls,
audio-authoritative timing, deterministic authored attack handling, counterattack
loop, pause/resume behavior and several early Conductor animation studies.

The prototype is built with TypeScript, Three.js, Vite and Web Audio. Those
technologies are **not** the production stack for the shipping game.

The production game is being rebuilt in **Godot 4.x with GDScript**, targeting
Android / Google Play first and Windows / Steam second. See
`MASTER_DESIGN.md` for the canonical production direction.

## Final prototype checkpoint

The preserved checkpoint is:

- branch: `web-prototype-final`
- commit: `38b0244189534bee10c7d03e49c2bf7efb1e4825`

This branch is the historical reference point for the browser era.

## What remains useful here

Use this repository as reference for:

- five-lane combat behavior
- movement and jump feel
- deterministic chart concepts
- audio-authoritative timing lessons
- chronological dropped-frame-safe event handling
- touch and multitouch lessons
- browser prototype playtests
- Conductor motion/timing studies
- approved visual-reference history
- rejected experiments and production lessons

Do **not** treat browser-specific implementation as production architecture.

## Play the prototype

The existing GitHub Pages build may remain available for historical testing while
the archive repository is retained.

Current deployed path:

https://jtyneham.github.io/resonance/

Repository renaming may affect deployment configuration or URLs. Preserve the
prototype for reference, but do not let its hosting requirements constrain the
Godot production project.

## Run locally

Install Node.js **22.12+** (Node 24 recommended), then:

```sh
npm ci
npm run dev
```

To preview the production browser build:

```sh
npm run build
npm run preview
```

## Automated checks

```sh
npm run check
npm run format:check
npm run test:e2e
```

These checks apply only to the historical browser prototype.

## Canonical production handoff

Read:

1. `MASTER_DESIGN.md`
2. `MIGRATION_HANDOFF.md`
3. accepted specialist design/reference documents only as needed

The old `IMPLEMENTATION_STATUS.md`, `PROTOTYPE_SPEC.md`, browser labs and
TypeScript source describe the prototype era unless a decision is explicitly
promoted into the new Godot production project.

Only **The Conductor** and **The Dancer** are active boss-development subjects.
Older roster/finale ideas must not be silently restored.
