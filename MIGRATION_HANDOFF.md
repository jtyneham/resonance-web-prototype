# Resonance — Godot Production Migration Handoff

> **Date:** 2026-10-05  
> **Status:** Repository migration in progress  
> **Authority:** `MASTER_DESIGN.md` remains the canonical project-wide design source.

## Purpose

This file records the controlled transition from the original browser prototype to
the clean Godot production project.

The browser prototype is preserved as R&D. The shipping game is not a port of the
TypeScript / Three.js codebase.

## Preserved prototype checkpoint

Repository before rename:

- `jtyneham/resonance`

Final browser-era checkpoint:

- branch: `web-prototype-final`
- commit: `38b0244189534bee10c7d03e49c2bf7efb1e4825`

The checkpoint preserves the complete browser prototype state immediately after the
production-reset master design was introduced.

## Locked repository strategy

The migration target is:

- old repository → `jtyneham/resonance-web-prototype`
- new production repository → `jtyneham/resonance`

The old repository remains available for:

- historical code
- prototype playtesting
- timing references
- animation labs
- accepted and rejected R&D evidence

The new repository becomes authoritative for all production implementation.

## Two GitHub account-level actions still required

The current ChatGPT GitHub connection can edit repository files and branches but
cannot rename repositories or create new repositories.

Perform these two actions in GitHub:

1. Rename the current repository from `resonance` to
   `resonance-web-prototype`.
2. Create a new empty repository named `resonance` under `jtyneham`.

Recommended new repository settings:

- visibility: use the user's preferred production visibility
- initialize without generated starter code if possible
- default branch: `main`
- no GitHub Pages requirement
- do not copy the browser repository wholesale

Once those two operations exist, ChatGPT / Codex can continue seeding the new
repository.

## Canonical material to migrate into the new production repository

Bring forward deliberately:

1. `MASTER_DESIGN.md`
2. canonical Conductor visual reference
3. canonical Dancer visual reference
4. canonical Broken Resonance Mote reference
5. accepted boss-specific design rules that remain current
6. distilled prototype lessons
7. any original audio/art source later explicitly approved for production reuse

Do not bulk-copy the entire `docs/` tree without review.

## Material that stays archive-only by default

Do not migrate these merely because they exist:

- Vite configuration
- Three.js runtime
- PixiJS experiments
- Web Audio transport implementation
- DOM UI
- GitHub Pages workflow
- browser orientation/fullscreen plumbing
- Playwright browser-specific scenarios
- rejected Conductor modular rigs
- superseded generated-frame experiments
- old implementation handoffs
- deprecated boss-roster/finale concepts

Useful behavioral tests may be rewritten for Godot, but their browser harnesses are
not production dependencies.

## Initial Godot production scaffold

The fresh repository should begin small.

Recommended first commit contents:

```text
resonance/
├── project.godot
├── README.md
├── MASTER_DESIGN.md
├── docs/
│   ├── PROJECT_STATUS.md
│   └── PROTOTYPE_LESSONS.md
├── game/
│   └── main.tscn
└── .gitignore
```

Do not pre-create a large speculative folder hierarchy. Let Phase 3 and Phase 4
establish the real architecture.

## Godot baseline

- engine: Godot 4.x
- initial baseline: Godot 4.7.2 stable
- language: GDScript
- rendering direction: Godot 2D / CanvasItem-based
- primary platform: Android / Google Play
- secondary platform: Windows / Steam
- canonical combat geometry: portrait 9:16
- desktop presentation: same portrait combat field inside a wider presentation

## First production milestone

The first Godot milestone is intentionally not a Conductor art rebuild.

Build an ugly technical combat prototype proving:

- exactly five lanes
- lane movement
- jump
- low and tall hazard behavior
- resonance interaction
- charge
- returned-resonance counterattack
- authoritative audio clock
- dropped-frame-safe chronological event processing
- pause / resume
- touch
- keyboard
- controller
- portrait scaling
- Android hardware run
- Windows desktop run

Only after this core survives the engine transition should production boss assets
be integrated.

## Source-priority reminder

When sources disagree:

1. latest explicit user decision
2. current production `MASTER_DESIGN.md`
3. current accepted specialist design docs
4. current production `PROJECT_STATUS.md`
5. browser prototype as R&D evidence
6. older historical material

Only The Conductor and The Dancer are active boss-development subjects.
