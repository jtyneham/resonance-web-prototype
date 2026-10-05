# Resonance — Master Game Design

> **Status:** WIP / production reset source of truth  
> **Version:** 1.0 — 2026-10-05  
> **Current workstream:** Phase 0 — Resonance 2.0 production restructure  
> **Role:** Canonical project-wide design and production roadmap

---

## 1. Purpose and source-of-truth order

Resonance is being restructured from a browser-first prototype into a deliberately
planned, engine-based commercial game project.

The existing TypeScript / Vite / Three.js browser build remains valuable as
**prototype R&D**. It proved core combat ideas, timing principles, controls,
readability rules and several boss-performance concepts. It is no longer the
production target and must not dictate the new implementation merely because code
already exists.

When information conflicts, prefer:

1. the user's latest explicit decision
2. this `MASTER_DESIGN.md`
3. specialist accepted-design documents that have not been superseded
4. current production-project status documents once the Godot project exists
5. the existing browser implementation as prototype evidence
6. older experiments, historical handoffs and rejected alternatives

The browser-era `README.md`, `IMPLEMENTATION_STATUS.md`,
`PROTOTYPE_SPEC.md`, laboratory pages and TypeScript source describe the legacy
prototype unless explicitly promoted into the new production architecture.

Never silently restore superseded boss-roster, finale, rigging, animation or
technical decisions.

---

## 2. Product definition

Resonance is a compact, difficult, music-driven **boss-rush action game** inspired
mechanically by the lane-based musical fights of Everhood, without an overworld or
RPG layer.

The player controls the **Broken Resonance Mote** through a sequence of authored
boss encounters inside a broken musical machine or music-box-like world.

The defining fantasy is:

> Survive a piece of music that a boss is physically performing at you, understand
> its rhythm and choreography, absorb compatible resonance, and strike that
> resonance back without ever breaking the musical performance.

The game is not a collection of ordinary fights with music playing underneath.
Music, boss acting, attacks, camera, effects and player response are one authored
performance.

### Locked core identity

- boss rush; no conventional overworld
- five perspective lanes
- deterministic, authored and learnable combat
- music-driven timing
- touch-first mobile play
- strong desktop/controller support
- bosses physically perform the encounter
- readable difficulty rather than random difficulty
- character personality expressed primarily through motion, music and attack
  choreography
- compact scope with high encounter quality rather than a large content map

---

## 3. Resonance 2.0 — locked production decisions

### 3.1 Engine

The production game will be built in **Godot 4.x using GDScript**.

Initial production baseline:

- Godot **4.7.2 stable** at the time of this reset
- GDScript as the default gameplay language
- Godot 2D / CanvasItem-based rendering for the combat playfield
- Godot audio, animation, particles, shaders and platform export systems
- engine upgrades are deliberate project decisions, not automatic migrations

The old Three.js / Web Audio architecture is not ported line-by-line.

What survives is the proven design philosophy:

- authoritative audio time
- renderer-independent gameplay truth
- chronological resolution of crossed timeline events
- five-lane movement
- deterministic authored charts
- explicit pause/resume behavior
- platform-independent input actions
- tests and isolated review scenes where useful

### 3.2 Target platforms

**Primary shipping target**

- Android
- Google Play Store release is an intended production target
- touch is a first-class control method, not a desktop scheme adapted at the end

**Secondary shipping target**

- Windows PC
- Steam is an intended production target
- keyboard and controller are first-class desktop inputs

**Later / optional targets**

- Steam Deck / Linux
- macOS
- other storefronts

Do not let optional platforms delay the primary Android + Windows production path.

### 3.3 Orientation and playfield

The canonical combat geometry remains **portrait 9:16**.

On Android:

- gameplay is portrait-first
- touch controls live around the lower playfield / safe-area-aware UI
- landscape gameplay is not a separate combat layout

On widescreen desktop:

- the same portrait combat field remains authoritative
- surrounding horizontal space may show atmospheric scenery, UI or restrained
  presentation
- extra width must not change lane spacing, attack timing, dodge distance or chart
  difficulty
- touch controls are hidden and replaced by keyboard/controller affordances

One encounter chart therefore plays identically across mobile and desktop.

### 3.4 Launch-scope target

The initial full-game production target is:

- **six major boss encounters**
- Conductor and Dancer are the only currently active production bosses
- four additional encounter slots remain unnamed / incubator-only until explicitly
  promoted
- no older roster name becomes active merely because it appears in historical files

This six-boss target is a production scope, not permission to design four bosses
prematurely. It may be reforecast after the Conductor vertical slice if real
production cost proves materially different from estimates.

Initial pacing target:

- approximately 4–8 minutes of successful performance per major encounter
- roughly 30–50 minutes for a clean boss-rush clear
- approximately 1.5–3 hours for a first successful clear depending on retries and
  difficulty

These are planning targets rather than promises and must be validated through
production playtests.

### 3.5 Repository reset strategy

The existing repository is treated as the **web-prototype / research archive**.

The intended production migration is:

1. preserve the current repository and its history
2. mark a final browser-prototype checkpoint before destructive restructuring
3. create a clean Godot production repository or clean production root
4. bring forward only approved design references, art sources, audio sources and
   lessons that the new game actually needs
5. do not drag browser-specific build infrastructure, experimental labs or obsolete
   renderer code into the production architecture by default

Repository strategy is now locked:

- preserve the current repository as the historical browser prototype
- preserve a final `web-prototype-final` branch before migration
- rename the current repository to `resonance-web-prototype`
- keep the prototype deployable for historical/reference testing where practical
- create a fresh `jtyneham/resonance` repository for Godot production
- migrate only approved canon, production references and distilled prototype lessons

The repository rename and creation are account-level migration operations and must
not destroy the preserved prototype history.

---

## 4. Design pillars

Every substantial feature should strengthen at least one pillar and should not
undermine the others.

### Pillar A — The boss performs the music

Boss animation is not decoration layered over an attack chart.

The boss should appear to:

- conduct
- dance
- strike
- cue
- gesture
- recoil
- repeat
- accelerate
- freeze
- deform
- or otherwise physically perform musical events

Attack release should visually belong to the boss's performed phrase.

### Pillar B — Music is gameplay structure

Music determines:

- anticipation
- attack release
- phrase boundaries
- transitions
- tempo and meter changes
- counterattack openings
- boss acting
- major visual accents

The encounter should still make musical sense when studied as an authored timeline
without relying on random event generation.

### Pillar C — Difficult but readable

A player should lose because they misread or mistimed something learnable, not
because the game produced an unfair combination.

Threat language must be consistent.

### Pillar D — Character through performance

Every boss needs personality in:

- idle
- anticipation
- normal attacks
- major attacks
- transitions
- damage state
- low health
- victory
- defeat

Avoid generic floating, pulsing and shaking when articulated acting can communicate
the moment.

### Pillar E — Compact, high-density boss rush

No filler exploration layer is required to justify the fights.

Time outside combat should support:

- anticipation
- narrative
- recovery
- progression
- settings
- replay

rather than become a separate RPG.

---

## 5. Core combat

The Broken Resonance Mote moves across exactly five lanes.

Primary verbs:

- move left
- move right
- jump
- absorb compatible resonance automatically or through the final approved rule
- store charge
- fire a boss-specific returned-resonance counterattack
- pause / resume

The precise absorption input rule remains subject to production prototype review;
the browser prototype's automatic-grounded absorption is useful evidence but is not
automatically permanent.

### Core hazard language

**Low hazard**

- broad and shallow
- jumpable
- may also be sidestepped when spacing permits

**Tall barrier**

- upright
- unjumpable
- must be sidestepped
- blocks returned-resonance shots where appropriate

**Resonance opportunity**

- visually permeable / hollow
- compatible with absorption
- behavior must be unmistakably different from damaging hazards

**Counterattack**

- fired from the Mote
- extremely fast
- visible enough to read its path and collision
- presentation changes by boss
- successful hits never stop the boss's authored timeline

Shape carries the primary meaning. Color reinforces it.

---

## 6. Authoritative musical time

This is a non-negotiable architectural principle carried forward from the prototype.

**Audio time is authoritative.**

The visual frame rate must never become the source of truth for encounter timing.

Conceptual flow:

```text
Audio playback
      ↓
SongClock
      ↓
Tempo / meter map
      ↓
Encounter timeline cursor
      ↓
Chronological event resolution
      ↓
Combat simulation + boss performance + camera + VFX
```

### Dropped-frame rule

If one rendered frame observes song time at 12.418 seconds and the next observes
12.471 seconds, every authored event crossed between those times must resolve in
chronological order.

No attack, collision, cue or transition may depend on the renderer producing a
frame at the exact event timestamp.

### Musical authoring units

Encounter content should be authored primarily in musical positions:

- section
- measure
- beat
- subdivision / tick

A tempo and meter map converts those authored positions into playback time.

Tempo changes, meter changes and rubato-like authored transitions must therefore be
representable without hand-editing large quantities of absolute seconds.

---

## 7. Encounter authoring model

Boss encounters should be **data-driven performances**, not long scripts full of
hard-coded waits.

Each encounter definition should eventually describe tracks such as:

- music / section structure
- tempo and meter
- boss performance cues
- attack spawn / warning / impact
- counterattack windows
- camera accents
- arena changes
- VFX
- state transitions
- narrative beats where applicable

Conceptual example:

```text
Measure 12, beat 1
BossGesture: IctusPreparation

Measure 12, beat 2
BossGesture: IctusRelease
Attack: LaneStrike
Lane: 3

Measure 12, beat 3
CameraAccent: ShortImpact
BatonFlare: Release
```

The exact serialization format is not yet locked.

Preferred Godot direction:

- custom `Resource` types for encounter definitions
- reusable event resources
- a tempo / meter map asset
- development-time validation of impossible or contradictory combinations
- later consideration of a dedicated Resonance encounter-editor tool inside Godot

Do not build a custom editor before the first technical encounter prototype proves
the underlying data model.

---

## 8. Core Godot architecture

Exact node names remain implementation details, but responsibility boundaries are
part of the design.

Conceptual structure:

```text
Application
├── Session / progression
├── Save service
├── Settings
├── Input router
├── Audio service
│
├── Encounter runtime
│   ├── SongClock
│   ├── TempoMap
│   ├── TimelineScheduler
│   ├── CombatSimulation
│   ├── PlayerController
│   ├── BossController
│   ├── AttackController
│   ├── CameraDirector
│   └── EffectsDirector
│
└── UI
```

### Architecture rules

- simulation state is separate from presentation state
- renderer nodes do not own gameplay truth
- physical inputs map to named game actions in one place
- timeline events are deterministic and inspectable
- save data contains serializable game state, not scene-tree objects
- debug tools can expose current beat, section, lane state and pending events
- encounter content is reusable across Android and desktop builds
- no boss gets permission to bypass the central timing model for convenience

---

## 9. Player — Broken Resonance Mote

The selected player identity remains the **Broken Resonance Mote**.

Preserve the accepted concept:

- compact asymmetrical graphite shell / damaged tuning chamber
- warm luminous fissure or core
- short mismatched tuning-fork-like prongs
- limited detached fragments
- worn dark material and restrained aged-ivory edging
- no face or eyes
- no humanoid anatomy
- no conventional floating music-note silhouette

Its production sprite scale, exact palette, animation count and construction can be
revisited for Godot production.

Player readability has priority over decorative detail.

Core player states eventually require clear acting for:

- grounded idle
- lateral move
- jump
- landing
- absorption
- charged
- counterattack
- damage
- defeat / recovery where applicable

---

## 10. Boss framework

Every boss must be radically distinct in:

- silhouette
- palette
- arena
- movement grammar
- music
- attack choreography
- counterattack presentation
- damage behavior
- low-health behavior
- victory
- defeat

The shared five-lane rules are a common language, not a reason for bosses to feel
structurally identical.

### Active production roster

Only these bosses are active:

1. **The Conductor**
2. **The Dancer**

All other concepts remain inactive until explicitly promoted.

---

## 11. The Conductor — retained canon

The Conductor represents order and control.

Preserve:

- floating articulated mechanical conducting hand
- baton
- ivory, antique-gold, crimson and near-black material language
- rough, grungy semi-pixel treatment
- precise, domineering, economical and impatient personality
- recognizable conducting vocabulary as the foundation of movement
- attacks appearing physically conducted rather than merely spawned
- uninterrupted performance when struck
- damage expressed as disruption of perfect control rather than ordinary flinch
- low-health deterioration through restrained tremors, mistimed resets and
  crimson leakage
- arrogant cutoff as victory language
- finger desynchronization / mechanical lockup as defeat direction

### Conductor animation

The accepted production animation model remains:

**whole-character frame-by-frame 2D raster animation**

Every visible raster frame contains the complete character.

Do not use:

- runtime anatomical assembly
- skeletal finger rigs as the production default
- procedural finger posing
- dynamic scene lighting required to make the sprite read
- light-dependent highlights or cast shadows as part of the character solution

Selected flat effects may remain separate runtime elements.

The baton-tip flare is the canonical example.

The approved eight-frame, approximately **130 ms wind-up** remains reference canon
unless the user explicitly changes it.

Do not revive the rejected generic
`HOLD → MICRO-TELL → SNAP...` formula.

Conductor motion must derive from:

- conducting
- the music
- order / control
- impatience
- increasing difficulty maintaining perfect execution

### Production source

The current approved Conductor references remain reference canon.

LibreSprite remains the intended editable source environment for deliberate
frame-by-frame raster production, but the Godot reset allows the asset pipeline to
be reevaluated before large-scale animation production.

Do not redesign the accepted Conductor simply because the runtime engine changes.

---

## 12. The Dancer — retained canon and open pipeline

The Dancer represents performance and choreography.

Preserve:

- broken music-box ballerina / automaton identity
- graceful, expressive, uncanny and increasingly unstable performance
- midnight blue, cold porcelain and electric violet palette
- restrained antique-gold / bronze mechanical joints and trim
- established porcelain and mechanical anatomy
- ornamentation, ribbons and celestial motifs
- grungy semi-pixel treatment
- ballet phrases, elongated arcs, mechanical repetitions, sudden freezes,
  overextended joints and ribbon / skirt follow-through
- **Spiral Cascade** as a recurring signature attack
- **Broken Coda** as an active major-special proposal
- progressive corruption of controlled choreography under damage

### Dancer animation pipeline

The production pipeline is **not locked**.

Older layered-rig instructions are historical proposals, not current canon.

The engine reset is an opportunity to evaluate:

- whole-character frame-by-frame animation
- carefully layered 2D animation
- hybrid approaches

The choice must serve the Dancer's visual identity and animation quality rather
than forcing her into the Conductor's technical solution.

---

## 13. Character and effects art direction

The broad character language remains:

- rough, grungy semi-pixel rendering
- chunky visible pixel edges
- dithered / worn texture where appropriate
- strong silhouettes
- deep dark fields
- handmade surface imperfection supported by precise timing

Bosses do not share palettes or anatomy merely to look like one asset set.

### Character production principle

Important character art should have a canonical editable source.

Concept / exploration is not automatically production art.

Preferred pipeline:

```text
brief
→ visual exploration / approved reference
→ production reconstruction
→ canonical editable source
→ animation authoring
→ export
→ Godot import
→ isolated review scene
→ phone-size review
→ encounter integration
```

LibreSprite is the preferred raster-animation editor unless a later test proves a
better production method for a specific asset class.

### Runtime effects

Suitable effects should remain engine-driven rather than baked into every sprite:

- baton-tip glow
- attack arcs
- resonance waves
- barriers
- impact flashes
- particles
- trails
- arena accents
- screen-space feedback

Effects must not obscure gameplay silhouettes or telegraphs.

---

## 14. Music and audio production

Every boss encounter requires original music designed with gameplay in mind.

Music production and encounter authoring are one workflow.

For each encounter, define:

- composition
- tempo map
- meter map
- sections / phrases
- major accents
- boss-performance relationships
- attack relationships
- counterattack opportunities
- transition points
- ending behavior

Where useful, stems may be exported for:

- adaptive layering
- low-health changes
- transitions
- effects ducking
- clean looping / section handling

Do not assume stems are required for every track.

### Audio synchronization

The Godot production implementation must use the engine's audio playback timing
facilities and compensate for presentation / output timing as needed.

Bluetooth latency cannot be assumed away. Calibration and latency strategy are a
production design problem and must be tested on real Android hardware.

---

## 15. Input strategy

### Android

Primary input:

- touch

Requirements:

- comfortable two-thumb operation
- simultaneous / multitouch actions
- safe-area-aware control placement
- strong feedback without visual clutter
- no requirement to look away from the playfield to operate controls

### Desktop

Primary inputs:

- keyboard
- controller

The action layer should expose named actions such as:

- move_left
- move_right
- jump
- resonate
- pause
- confirm
- cancel

Device-specific bindings must never leak into combat logic.

---

## 16. UI, accessibility and settings

Required production surfaces include:

- title
- continue / new game where appropriate
- options
- pause
- encounter intro
- defeat / retry
- victory / result
- progression / boss selection where unlocked
- credits

Initial accessibility/settings targets:

- master / music / SFX volume
- reduced motion
- haptics toggle
- screen-shake intensity
- input rebinding on desktop where practical
- readable telegraph mode / contrast support to be explored
- boss HP visibility option may remain off by default, with an option to show it
- latency / timing calibration to be investigated during technical prototyping

Accessibility may alter presentation, but must not silently change authored combat
timing unless an explicit assist mode is designed.

---

## 17. Game structure and progression

The game has no conventional overworld.

The high-level loop is:

```text
Game shell
→ encounter introduction
→ boss performance
→ victory / defeat
→ short transition / narrative consequence
→ next encounter or retry
```

The exact narrative transitions remain open.

### Progression goals

The finished game should support:

- first-play linear progression
- immediate retry after failure
- saved completion state
- later replay of cleared bosses
- final completion state
- post-clear boss-rush / replay structure to be designed

Do not add stat grinding merely to create progression.

Player mastery should be the dominant form of progression unless a later explicit
decision adds another system.

---

## 18. Narrative and world canon — intentionally open

The broad setting is established:

- a broken musical machine / music-box-like world
- the Broken Resonance Mote travelling through it
- bosses embodying distinct modes of musical performance / control
- conflict expressed through sound, rhythm and machinery

The following are **not yet canonical**:

- what the machine originally was
- who or what built it
- why it broke
- why the Mote exists
- the Mote's ultimate purpose
- the exact nature of the bosses
- whether defeating a boss destroys, restores, frees or transforms it
- the final antagonist or final encounter identity
- the ending
- the exact amount of explicit dialogue or exposition

Do not restore older finale or roster concepts to fill these gaps.

Narrative is a dedicated production phase before the full roster is locked.

---

## 19. Production roadmap

### Phase 0 — Resonance 2.0 production reset

**Current phase.**

Goals:

- choose engine
- choose programming language
- define primary platforms
- define playfield/orientation policy
- define launch-scope target
- define repository migration strategy
- rewrite canonical project plan

Status after this document:

- engine: locked
- language: locked
- Android target: locked
- Windows / Steam target: locked
- portrait combat geometry: locked
- six-boss launch-scope target: locked
- repository migration direction: locked
- final web-prototype checkpoint branch: created
- old-repo target name: `resonance-web-prototype`
- new production-repo target name: `resonance`
- account-level rename / new-repository creation: pending

Exit criterion:

A clean production repository can be created without needing to rediscover the
project's fundamental technical direction.

### Phase 1 — Game vision and full design framework

Deliverables:

- concise game vision
- pillar validation
- exact core loop
- failure / retry rules
- completion rules
- first-clear and clean-run pacing targets
- progression structure
- launch-scope confirmation

Exit criterion:

A new contributor can explain what the complete game is without reading prototype
history.

### Phase 2 — Narrative and world bible

Deliverables:

- machine origin / purpose
- break event
- Mote identity and goal
- boss narrative function
- progression logic
- ending
- story-delivery method
- tone rules

Exit criterion:

Every encounter has a reason to exist in the sequence without requiring an
overworld.

### Phase 3 — Godot technical combat prototype

Use placeholder art and a test track.

Implement:

- five lanes
- movement
- jump
- hazard collision
- resonance interaction
- charge
- counterattack
- authoritative SongClock
- timeline scheduler
- pause / resume
- touch
- keyboard
- controller
- portrait scaling

Exit criterion:

The old core combat has been proven in Godot on both a real Android device and
Windows desktop.

### Phase 4 — Core production architecture

Deliverables:

- stable Godot project structure
- input action layer
- encounter-resource model
- tempo / meter map
- deterministic scheduler
- save/settings foundation
- debug timing tools
- automated test strategy
- export presets

Exit criterion:

New encounter content can be added without rewriting core systems.

### Phase 5 — Encounter authoring pipeline

Deliverables:

- data-driven attack/event format
- validation rules
- boss-performance tracks
- camera / VFX tracks
- authoring preview tools
- timing inspection
- chart iteration workflow

Exit criterion:

A designer can author and iterate a musical phrase without hard-coding scene waits.

### Phase 6 — Production art and audio pipeline

Deliverables:

- LibreSprite conventions
- export/import conventions
- anchor / scale rules
- Godot sprite-animation conventions
- effects boundaries
- audio source / master / stem rules
- performance budgets
- naming and asset manifest rules

Exit criterion:

One approved character animation and one finished musical phrase travel from source
asset to final Godot playback without ad hoc cleanup.

### Phase 7 — Conductor vertical slice

Produce the first commercially representative encounter.

Includes:

- final visual direction in-engine
- production Conductor animation
- full music
- authored chart
- arena
- attacks
- counterattack
- damage / low-health acting
- victory
- defeat
- UI
- touch
- keyboard/controller
- haptics
- save result
- retry
- Android and Windows builds

Exit criterion:

The Conductor encounter is strong enough to define the quality bar and estimate the
true production cost of the remaining game.

At this gate, reforecast the six-boss scope before promoting more bosses.

### Phase 8 — Permanent game shell

Build:

- title
- save flow
- progression
- options
- accessibility
- encounter transitions
- replay structure
- credits foundation
- production UI language

Exit criterion:

A player can move through the game structure without developer-only screens.

### Phase 9 — Dancer production

Finalize her animation methodology and produce the complete Dancer encounter using
the proven pipeline.

Exit criterion:

Dancer is production-complete and demonstrates that the architecture supports a
boss with radically different movement grammar.

### Phase 10 — Remaining encounter production

Promote incubator concepts one at a time until the approved launch roster is
complete.

Do not conceptually treat all four remaining scope slots as active development.

### Phase 11 — Whole-game integration

Perform:

- difficulty curve pass
- music pacing pass
- narrative continuity pass
- transition pass
- save / completion pass
- replay pass
- device-wide readability pass

### Phase 12 — Platform production and release

Android:

- physical device matrix
- performance / thermal profiling
- audio latency testing
- haptics
- safe areas
- signed release build
- Google Play AAB
- internal / closed testing
- store assets

Windows / Steam:

- keyboard/controller verification
- multiple resolutions
- fullscreen/windowed behavior
- Windows x86_64 export
- Steam build/depot preparation
- store assets
- optional Steamworks features only when explicitly approved

### Phase 13 — Final QA and launch

Required gates:

- no known unavoidable chart combination
- pause/resume preserves timeline integrity
- dropped frames do not skip authored events
- input remains reliable on target devices
- safe areas and portrait scaling work across supported Android ratios
- boss animation and effects remain readable on phone
- clean install / save / update paths tested
- release builds verified outside the editor
- full game can be completed from a fresh save

---

## 20. Legacy prototype salvage rules

The browser prototype is valuable, but it is not a dependency.

### Preserve conceptually

- five-lane geometry
- core movement and jump feel as a reference
- deterministic attack philosophy
- renderer-independent combat principles
- audio-authoritative timing
- chronological event catch-up
- touch lessons
- Conductor timing studies
- approved visual references
- Broken Resonance Mote direction
- readability findings
- automated-test cases that describe real game behavior

### Rebuild for Godot

- audio transport
- renderer
- UI
- scene lifecycle
- input plumbing
- save/settings
- asset loading
- platform exports
- pause / focus handling
- encounter authoring implementation

### Do not carry forward by default

- Vite
- Three.js
- PixiJS experiments
- Web Audio implementation details
- DOM UI
- GitHub Pages constraints
- browser orientation APIs
- laboratory code that exists only to inspect rejected techniques
- obsolete modular Conductor rigs

Historical evidence may remain archived even when its implementation is discarded.

---

## 21. Development workflow

### Design

This project chat is the creative / design hub.

Use it for:

- master design
- boss concepts
- narrative
- attack choreography
- animation acting
- music relationships
- art direction
- implementation planning

### Production implementation

Codex may work directly against the production Godot repository for:

- project scaffolding
- GDScript
- scenes/resources
- tooling
- tests
- export configuration
- asset integration

Codex prompts should identify:

- intended outcome
- approved references
- constraints
- files/systems allowed to change
- acceptance criteria

### Game Studio skills

ChatGPT's Game Studio skills may assist with:

- general game-planning methodology
- sprite QA
- UI reasoning
- playtest discipline

They are browser-oriented and are **not** the technical authority for the Godot
production project.

The Resonance design documents and current Godot production repository take
priority.

---

## 22. Review and acceptance rules

Nothing becomes production canon merely because it exists.

### Design acceptance

A proposal is not approved until the user explicitly approves it or it is written
into the canonical design under an explicit decision.

### Art acceptance

Review at:

- source resolution
- gameplay scale
- Android portrait scale
- representative effects density

Check:

- silhouette
- anatomy
- palette
- frame consistency
- registration
- transparency
- readability
- personality
- musical timing

### Gameplay acceptance

A mechanic must be judged by:

- readability
- learnability
- input comfort
- timing consistency
- cross-platform parity
- interaction with real music

### Technical acceptance

A feature is not finished because it works once in the editor.

Where relevant verify:

- automated tests
- release build
- Android hardware
- Windows build
- pause/resume
- frame drops
- save/reload
- different aspect ratios
- input devices

---

## 23. Current canonical state — 2026-10-05

### Approved

- Resonance is being rebuilt as a Godot production game
- Godot 4.x / GDScript is the production direction
- Android / Google Play is the primary shipping target
- Windows / Steam is the secondary shipping target
- five-lane musical boss-rush combat remains the core
- portrait 9:16 remains the canonical combat geometry
- desktop preserves that geometry inside a wider presentation
- authoritative audio time remains mandatory
- the existing browser build becomes prototype R&D
- initial full-game target is six major boss encounters
- only Conductor and Dancer are active bosses
- Broken Resonance Mote remains the player direction
- Conductor remains whole-character frame-by-frame 2D
- approved Conductor wind-up reference remains approximately 130 ms / eight frames
- Dancer's animation pipeline remains open
- story fundamentals remain deliberately unresolved

### Not yet approved / still open

- exact story
- exact ending
- identities of the four inactive launch-scope encounter slots
- monetization / pricing
- exact save UX
- exact boss-select / postgame structure
- exact latency-calibration UX
- exact Godot encounter-resource schema
- exact automated-test framework
- Dancer animation pipeline
- exact long-term hosting/deployment policy for the preserved web prototype after
  the repository rename

---

## 24. Immediate handoff

Resume from this file, not from the browser prototype's old implementation
handoffs.

Next production action:

**complete the two remaining account-level repository operations: rename the
prototype repository to `resonance-web-prototype`, create the new
`jtyneham/resonance` repository, then promote the prepared Godot production seed
into the new repository.**

Do not resume the old Conductor LibreSprite migration as the automatic next task.
It remains useful art-production work, but the project-wide Godot foundation now
comes first.

The first Godot milestone is an intentionally ugly technical five-lane combat
prototype that proves authoritative musical timing, movement, jumping, resonance
interaction and counterattack behavior on Android and Windows before production
boss assets are integrated.
