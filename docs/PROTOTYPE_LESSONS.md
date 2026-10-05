# Browser Prototype Lessons

This document records what the original browser prototype proved so the Godot
rebuild can preserve useful knowledge without inheriting obsolete implementation.

## Combat

- Exactly five lanes produced a readable, learnable combat field.
- Lane movement and jumping are sufficient to support a strong boss-rush core.
- Low hazards, tall barriers and resonance opportunities need distinct silhouettes.
- Tall barriers should remain unjumpable and should be allowed to block returned
  resonance where the encounter calls for it.
- Boss hits can feel forceful without stunning or interrupting the boss.
- Counterattacks should cross the field extremely quickly while remaining visible.

## Timing

- Audio time must remain the authoritative clock.
- Gameplay must never depend on a render frame occurring at an exact attack time.
- When a frame spans multiple events, all crossed events must resolve in
  chronological order.
- Pause/resume must freeze the encounter coherently rather than allowing music,
  attacks and animation to drift apart.
- Boss animation release moments should be authored against musical time.

## Input

- Touch must be designed as a first-class control method.
- Multitouch is necessary for simultaneous movement/jump interactions.
- Buffered lane movement around landing can improve feel.
- Holding movement should not accidentally create uncontrolled repeated lane
  changes.
- Desktop keyboard and controller input should map to the same abstract actions.

## Portrait presentation

- Portrait combat is a core strength rather than merely a browser constraint.
- Phone readability must be judged at actual gameplay scale.
- Extra desktop width should not alter combat geometry or encounter difficulty.
- Safe areas and control placement need physical-device testing.

## Boss performance

- Bosses are strongest when attacks visibly originate from their performed motion.
- Conductor movement should derive from conducting technique, music and personality.
- Successful player hits should not break the authored boss performance timeline.
- Personality needs to exist in idle, anticipation, attacks, transitions, damage,
  low health, victory and defeat.

## Conductor animation production

- Runtime modular anatomical assembly was rejected as the production approach.
- Independent generated frames caused anatomy, grip, baton and registration drift.
- Complete authored character frames produced a stronger foundation.
- Stable registration and one canonical editable source are important.
- Flat runtime effects such as the baton-tip flare can remain separate from raster
  character art.
- The approved eight-frame ~130 ms wind-up remains reference canon.
- Do not revive the rejected generic HOLD → MICRO-TELL → SNAP formula.

## Art pipeline

- Concept art is not automatically a production asset.
- True transparency, stable silhouette, fixed scale and registration require
  deliberate review.
- Important raster assets need canonical editable sources.
- LibreSprite remains the preferred raster editor pending production validation.
- Review assets both at source scale and at Android gameplay scale.

## Architecture

Preserve the philosophy, not the browser implementation:

- simulation separate from presentation
- renderer is not gameplay truth
- named input actions
- deterministic authored encounter data
- explicit save/settings boundaries
- debug visibility into timing and encounter state
- isolated review scenes for animation and timing where useful

## Rebuild rather than port

The following were appropriate for the prototype but are not production
requirements:

- Vite
- Three.js
- PixiJS experiments
- Web Audio implementation details
- DOM UI
- GitHub Pages deployment
- browser visibility/orientation APIs
- browser-specific automated-test infrastructure
