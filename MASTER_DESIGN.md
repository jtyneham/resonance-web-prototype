# Resonance — Master Design

> **Status:** WIP / living design document  
> **Version:** 0.1 — 2026-10-04  
> **Role:** Stable project-wide design source of truth

## 1. Purpose and source-of-truth order

Resonance is a compact, difficult, music-driven browser boss-rush built around a
five-lane combat field. The player is a small spark-like entity moving through a
broken musical machine while boss performance, hazards, music and player response
remain tightly synchronized.

Use this document for stable project-wide design decisions. More specialized
documents may define deeper details, while `IMPLEMENTATION_STATUS.md` records the
current implementation checkpoint and `PROTOTYPE_SPEC.md` records the neutral
prototype's concrete scope.

When information conflicts, prefer:

1. the user's latest explicit decision
2. this `MASTER_DESIGN.md`
3. specialist accepted-design documents in `docs/`
4. `IMPLEMENTATION_STATUS.md` for current implementation state
5. `PROTOTYPE_SPEC.md` for prototype-specific defaults
6. older experiments and archived notes

## 2. Product and technical baseline

- Delivery: browser game hosted through GitHub Pages
- Mobile-first, portrait gameplay
- Desktop presents a centered portrait playfield
- Stack: TypeScript, Vite, Three.js, PixiJS where useful, Web Audio
- No conventional engine such as Godot or Unity
- Audio time is authoritative for combat timing
- Five playable lanes
- Touch-first controls with keyboard support
- Pausing, visibility interruption and orientation changes must preserve timing
- Testing uses Vitest and Playwright
- Runtime rendering and authored raster art are separate concerns

## 3. Core combat identity

The player moves between five lanes, jumps low hazards, sidesteps tall barriers,
absorbs compatible resonance opportunities while grounded, stores charge, and
returns that resonance as a very fast boss-specific counterattack.

Core readability rules:

- low hazard: broad, shallow, jumpable or sidesteppable
- tall barrier: upright, unjumpable, sidestep-only, blocks counterattacks
- resonance opportunity: hollow/permeable and absorbable while grounded
- counterattack: extremely fast, boss-specific, clearly separate from the player
- shape carries the primary gameplay meaning; color reinforces it
- boss hits receive strong feedback but do not interrupt boss timing or animation

The combat system should remain difficult but readable. Random or authored
variation must never produce unavoidable combinations.

## 4. Boss-rush structure

The game has no overworld requirement. Encounters are the product.

The Conductor is the first production boss and establishes the production standard
for later bosses such as The Dancer / Prism direction and Silence, subject to the
latest specialist design documents.

Boss identity should come from:

- character design
- animation/performance vocabulary
- music and timing
- attack language
- arena/background treatment
- encounter-specific counterattack presentation

Do not rely on large quantities of dialogue or exposition to make bosses distinct.

## 5. Conductor — locked direction

The Conductor is a floating mechanical hand with a baton, not a humanoid body.

Preserve the accepted:

- ivory, antique-gold, crimson and near-black material language
- rough, chunky semi-pixel treatment
- intentional hand mechanics and recognizable conducting vocabulary
- wrist-core registration logic
- approved Ictus preparation, strike and recovery timing
- approved idle concept as a whole-character hover with restrained secondary motion
- continuous performance: successful player hits do not cause flinch, stun or loss of beat
- separate runtime baton-tip glow/effect rather than baking the effect into every frame

Existing approved Conductor images, labs, timing studies and motion checkpoints are
**reference canon**. They remain the authority for what the rebuilt production art
must preserve unless the user explicitly redesigns something.

## 6. Character animation model

The production character-animation model is:

**whole-character frame-by-frame 2D raster animation**

Do not return to a modular 3D/constructed production rig as the default solution.

Frames may be created with careful production tooling, but each visible frame must
read as authored character art with stable anatomy, silhouette, registration,
materials and prop geometry.

Timing remains controlled by the encounter/audio system rather than by a generic
sprite player's assumptions.

## 7. Production pixel-art pipeline

Resonance adopts a canonical editable pixel-art production pipeline.

For important raster assets:

**brief / concept**
→ **ChatGPT visual exploration or existing approved reference**
→ **user-approved visual direction**
→ **Codex deliberate production translation**
→ **layered LibreSprite source**
→ **runtime PNG / sprite-sheet export**
→ **isolated animation lab**
→ **user visual review**
→ **gameplay integration**

Use image generation primarily for concept exploration and reference creation.
Do not rely on repeated image-generation attempts as the production animation
pipeline for characters that require frame-to-frame consistency.

LibreSprite source files become the canonical editable production source after
creation. Generation scripts may assist initial authoring but must not become a
requirement that overwrites later direct pixel edits.

Suggested source organization:

```text
art-source/
  libresprite/
    conductor/
    player/
    bosses/
```

Runtime exports remain separate from editable sources.

## 8. Conductor production-art migration

The existing Conductor is **not being redesigned**. Its production source is being
rebuilt so future animations can expand from one consistent editable character.

Migration order:

1. preserve all currently approved Conductor references, labs and timing evidence
2. build one canonical layered LibreSprite base pose with fixed canvas, scale,
   wrist-core anchor, palette and true transparency
3. visually compare it against the accepted Conductor identity
4. rebuild the approved Ictus key motion from that canonical source while preserving
   approved motion and timing
5. compare old and rebuilt versions in the existing isolated animation labs
6. only after approval, promote the LibreSprite source as production canon
7. rebuild/extend idle, continuity, Changing Meter phrases and future gestures from
   that same canonical source

Do not delete historical raster attempts merely because a new source becomes
canonical; they document accepted/rejected decisions and timing evidence.

## 9. Runtime effects remain runtime effects

Do not bake everything into character sprites.

Keep suitable effects procedural/runtime-controlled, including:

- baton-tip glow and release flashes
- attack arcs
- barriers and resonance-wave presentation
- particles
- impact flashes
- lane/arena presentation
- screen-space feedback

Character raster art and runtime effects should complement rather than duplicate
each other.

## 10. Player art direction

The selected player direction is the Broken Resonance Mote described in
`docs/PLAYER_VISUAL_DIRECTION.md`.

Its concept is accepted, while exact production sprite resolution, palette balance,
animation frames and source construction remain open. It should eventually use
the same canonical editable LibreSprite discipline as production boss raster art.

## 11. Art-production review rule

A generated concept, isolated PNG or technically valid export is not automatically
a production asset.

Production acceptance requires visual review for:

- silhouette
- anatomy/proportions
- frame-to-frame identity
- palette/material consistency
- registration
- transparency
- animation continuity
- readability at portrait-phone gameplay size
- interaction with runtime effects

Rejected studies remain evidence; do not silently reinterpret them as approvals.

## 12. Handoff — 2026-10-04

This master-design document and the LibreSprite migration direction were introduced
during a short cross-project review from the Rustflower main-hub conversation.

Reason for the change: the Conductor development history repeatedly exposed the
limits of independent generated raster frames—anatomy drift, baton/grip changes,
registration mismatches, matte/alpha problems and inconsistent in-betweens. At the
same time, the project already had strong approved motion timing, isolated review
labs and a whole-character 2D animation direction.

The decision is therefore to **preserve the approved creative/motion work and
replace the fragile production-art foundation underneath it**.

### Handoff to the Resonance Master Design chat

On resume:

1. read this file first
2. read `IMPLEMENTATION_STATUS.md`
3. read `docs/CONDUCTOR_VISUAL_DIRECTION.md`
4. inspect the existing Conductor animation labs and approved references
5. treat the LibreSprite migration as an approved production direction
6. plan the canonical Conductor base-pose reconstruction before adding further
   production Conductor animations
7. do not reinterpret this migration as permission to redesign approved Ictus
   motion or replace the runtime-effects architecture

The next substantial Resonance discussion should continue in the dedicated
Resonance Master Design workflow rather than in the Rustflower project hub.
