# Resonance — Prototype Lessons

> **Source:** original TypeScript / Three.js / Web Audio browser prototype  
> **Purpose:** preserve validated lessons for the Godot production rebuild without
> treating browser implementation details as production dependencies.

## 1. What the prototype successfully proved

The prototype established that Resonance's central combat premise is viable:

- exactly five perspective lanes
- portrait-first presentation
- discrete lateral lane movement
- jump as a second defensive axis
- low versus tall hazard distinction
- absorbable resonance opportunities
- stored charge and returned-resonance counterattack
- difficult authored patterns that can still be deterministic and learnable
- boss performance synchronized to a musical timeline
- touch and keyboard control of the same underlying combat rules

These are design findings, not reasons to port browser code.

## 2. Audio must remain authoritative

The strongest technical lesson is that encounter truth cannot depend on rendered
frames.

The prototype's audio-authoritative transport and chronological event handling
should survive conceptually.

Production rule:

- read authoritative song time
- determine which authored timeline events were crossed since the previous update
- resolve every crossed event in chronological order
- render the resulting state

A dropped frame must not skip:

- attack releases
- telegraphs
- collisions
- phase changes
- boss cues
- counterattack windows

In Godot, rebuild this around Godot audio timing rather than reproducing the Web
Audio transport implementation.

## 3. Simulation and rendering should remain separated

The browser prototype benefited from keeping combat logic independent from Three.js.

Preserve that principle:

- combat owns truth
- encounter data owns authored events
- the renderer presents the state
- animation does not decide whether an attack happened
- VFX does not own collision logic

This is especially important when one encounter must behave identically on Android
and Windows.

## 4. Five-lane movement is a useful hard constraint

Exactly five lanes provide:

- immediate spatial readability
- compact touch controls
- authored rhythm-pattern clarity
- enough lateral decision-making without turning the game into free movement
- a strong connection to Everhood's lane-fight inspiration without copying charts

Do not casually increase lane count or replace lanes with free horizontal movement.

## 5. Jump should stay compact and readable

Prototype iteration showed that jump feel matters heavily to rhythm readability.

Useful principles:

- jump duration should not remove the player from meaningful control for too long
- the airborne state must be visually obvious
- lane-change rules while airborne must be deterministic
- buffered late movement can improve responsiveness
- holding a direction should not accidentally produce repeated moves unless
  deliberately designed

Exact values should be retuned in Godot rather than copied numerically.

## 6. Threat categories need shape-first readability

Color alone should never carry gameplay meaning.

The successful conceptual language is:

- low hazard: broad / shallow
- tall barrier: upright / blocking
- resonance opportunity: hollow / permeable / absorbable
- returned resonance: fast, player-originating and visually distinct

Production art may radically improve these forms, but their gameplay grammar should
remain immediately distinguishable at phone size.

## 7. Automatic absorption is useful evidence, not locked law

The browser prototype tested grounded automatic absorption.

Advantages observed conceptually:

- reduced touch-button overload
- lets the player focus on movement and timing
- reinforces resonance as something received rather than manually grabbed

However, the production game should re-evaluate the exact absorption rule during
the Godot technical prototype.

Do not preserve automatic absorption only because it exists in browser code.

## 8. Touch must be designed as a native control scheme

The prototype validated multitouch as essential.

Production implications:

- movement and jump/resonate must coexist under simultaneous touch
- controls need safe-area-aware placement
- visual controls must not steal attention from telegraphs
- touch targets must be comfortable on real phones
- Android hardware testing matters more than desktop emulation

Do not design desktop input first and retrofit touch later.

## 9. Pause and interruption need timeline integrity

Browser visibility/orientation work exposed an important general rule:

When gameplay is interrupted, music and encounter time must remain coherent.

Godot production must explicitly define:

- pause
- resume
- app backgrounding
- Android lifecycle interruption
- focus loss
- audio-device changes where relevant

The encounter must never resume with audio and combat on different timelines.

## 10. Bluetooth and output latency are real design problems

Timing judgments can be affected by output latency.

Production should investigate:

- device output latency
- wired versus Bluetooth behavior
- whether calibration is necessary
- whether visual timing should reference predicted presentation time
- how much leniency belongs in collision windows

Do not assume that a musically correct internal timeline automatically feels correct
through every audio device.

## 11. Boss hits should not stop the performance

The prototype and accepted design direction support a strong identity rule:

A successful player counterattack may produce strong feedback, but the boss does
not:

- flinch out of the phrase
- pause the chart
- lose the beat
- enter conventional hit-stun

Damage state should be expressed inside the ongoing performance.

This is particularly important to The Conductor.

## 12. Conductor animation lessons

Several animation experiments were useful specifically because they failed.

### Keep

- whole-character authored raster frames
- stable registration
- stable silhouette
- intentional conducting mechanics
- approved Ictus motion/timing reference
- separate baton-tip runtime effect
- isolated animation review scenes
- phone-scale review

### Avoid as production defaults

- runtime anatomical assembly
- modular finger rigging
- procedural fingers
- independent AI-generated frames with drifting anatomy
- baked effects that should track separately
- accepting technically valid exports without visual review

The main failure mode was consistency rather than lack of visual ideas.

## 13. Generated concept art is not production art

The prototype era repeatedly demonstrated the difference between:

- a compelling concept image
- a consistent animation-ready production asset

Production assets require:

- stable proportions
- fixed registration
- transparent edges
- predictable anchors
- repeatable palette
- editable source
- reliable frame-to-frame construction

Image generation remains useful for ideation and reference, but not as an automatic
replacement for deliberate sprite production.

## 14. Isolated labs were valuable

Small isolated review scenes helped separate questions such as:

- does the motion work?
- does the character remain consistent?
- does the baton effect track correctly?
- does the phrase loop cleanly?
- is the timing readable?

Carry this principle into Godot.

Use dedicated review scenes/tools where useful, but do not let them become a second
game architecture.

## 15. Authored chart data should not live as scattered waits

The browser prototype proved authored attacks, but the production game needs a more
explicit encounter-authoring model.

Godot should move toward:

- tempo/meter map
- musical positions
- reusable event resources
- explicit boss-performance cues
- attack events
- camera/VFX events
- validation

Avoid long procedural scripts made from chained timers and delays.

## 16. Desktop should not change combat geometry

The portrait combat field is a gameplay constraint, not merely a mobile layout.

On desktop:

- keep the same five-lane geometry
- keep the same travel distances
- keep the same chart
- use extra horizontal space for atmosphere or secondary presentation

This protects cross-platform fairness and reduces duplicated encounter tuning.

## 17. Tests should describe behavior, not the old stack

The browser project built useful regression coverage around:

- lane movement
- jump interaction
- absorption
- collision ordering
- full winning routes
- pause/resume
- touch combinations
- defeat/retry
- layout boundaries

Do not port Playwright/Vitest infrastructure merely for continuity.

Instead, rewrite the valuable behavioral invariants for Godot using the most
appropriate production testing strategy.

## 18. The prototype should remain runnable

The old build remains useful as a historical reference for:

- feel
- timing
- control comparisons
- visual evolution
- implementation archaeology when a solved problem resurfaces

That is why it is preserved separately rather than deleted or placed inside the
production repository.

## 19. Production takeaway

The browser prototype succeeded at its job.

It does not need to become the final game.

The Godot rebuild should preserve the **validated constraints and lessons**, while
being free to replace every browser-specific implementation needed to ship a
coherent Android and Windows game.
