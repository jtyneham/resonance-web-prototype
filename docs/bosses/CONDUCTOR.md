# The Conductor — Production Design

> **Status:** active boss / retained canon

The Conductor represents **order and control**.

## Identity

- floating articulated mechanical conducting hand with baton
- no humanoid body
- ivory, antique-gold, crimson and near-black material language
- rough, grungy semi-pixel rendering
- precise, domineering, economical, metronomic and impatient
- motion grounded in recognizable conducting vocabulary rather than generic baton
  waving

## Performance rules

Attacks must appear physically conducted.

Use musical/conducting language such as:

- preparation / upbeat
- downbeat / ictus
- cues
- cutoffs
- fermatas
- subdivisions
- articulation
- dynamics
- meter and tempo changes

The animation may exaggerate or supernaturalize conducting, but the hand mechanics
must remain intentional.

Successful player hits never flinch, stun or interrupt the authored timeline.

## Damage arc

- ordinary damage reads as disruption of perfect control rather than a conventional
  hurt animation
- low health may introduce restrained tremors, mistimed resets and crimson leakage
- victory direction: arrogant cutoff
- defeat direction: fingers desynchronize before mechanical lockup

## Animation model

Locked:

**whole-character frame-by-frame 2D raster animation**

Every raster frame contains the complete character.

Do not use runtime anatomical assembly, skeletal finger rigs or procedural finger
posing as the production default.

The approved eight-frame, approximately **130 ms wind-up** remains reference canon.

Selected flat effects may remain runtime-driven. The baton-tip flare is the
canonical example.

No dynamic scene lighting, light-dependent highlights or cast shadows are required
for the character to read.

Do not revive the rejected generic HOLD → MICRO-TELL → SNAP formula.

## Production source

The approved visual reference remains canonical for identity. LibreSprite remains
the preferred editable raster source environment pending the Phase 6 pipeline
validation.

Godot integration must not redesign approved Conductor identity or movement merely
because the runtime engine changed.
