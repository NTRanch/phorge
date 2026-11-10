# Phorge decision trees

The five trees a Phorge project walks, in pipeline order. Each tree is a contract: answer the questions honestly, take the branch, and accept what the terminal node obliges. A terminal node is one of three kinds — a **kit** (a production template with a pure core, data tables, and a deterministic smoke test), a **record** (a TOROGAO-MODEL-GAP: a named, tracked hole that blocks the project until the missing capability lands as a Torogao layer), or an **exception** (a craft title built outside the kit system under a locked timestep).

## 1. The master pipeline

```mermaid
flowchart TD
    A["Start: a game idea"] --> B{"Axis 1: Language stack<br/>primary + mix-ins + data layer"}
    B --> C{"Axis 2: Engine<br/>which build route?"}
    C --> D{"Axis 3: Animation type<br/>how does it move?"}
    D --> E{"Axis 4: Genre<br/>which kit does the core verb imply?"}
    E --> F{"Determinism gate:<br/>is a full playthrough replay-hashable?"}
    F -->|Yes| G{"Does a Torogao layer<br/>implement this combination?"}
    F -->|No| H["Locked-timestep craft title<br/>(exception, not a kit)"]
    G -->|Yes| I["Buildable project:<br/>named Torogao layer"]
    G -->|No| J["Record TOROGAO-MODEL-GAP<br/>named, tracked, blocking"]
```

**How to read it.** The axes run in a fixed order because each one constrains the next: the language stack bounds what engines are reachable, the engine bounds the animation routes, and the genre is read last because the same genre lands in different kits depending on the choices above it. The determinism gate is the pipeline's quality bar — if a full playthrough cannot be replayed from a seed and hashed byte-identical, the project is not a pipeline project. It may still be built, but as a craft title: one-off, locked-timestep, with its extra gates named up front. The final question is the honesty gate: a combination nobody has implemented yet does not get hand-waved into the plan. It becomes a TOROGAO-MODEL-GAP record, and the project waits on the layer, not on hope.

## 2. Language

```mermaid
flowchart TD
    A{"Need maximum determinism<br/>or a custom engine?"} -->|Yes| B["Rust primary"]
    A -->|No| C{"Need the fastest 2D iteration?"}
    C -->|Yes| D["GDScript primary<br/>(promote hot systems to Rust<br/>via GDExtension)"]
    C -->|No| E{"Studying an existing title<br/>(Unity / Unreal / Ren'Py / RPG Maker)?"}
    E -->|Yes| F["Spec only:<br/>production rewritten in Rust,<br/>never linked"]
    E -->|No| B
    B --> G{"Need embedded scripting,<br/>dialogue logic, or a mod surface?"}
    D --> G
    G -->|Yes| H["Add the Lua mix-in<br/>(host-provided RNG,<br/>sandboxed)"]
    G -->|No| I["Primary only"]
    H --> J["Stack declared:<br/>primary + mix-ins + RON data layer"]
    I --> J
```

**How to read it.** The tree chooses a *stack*, never a single language. Rust is the default terminal because determinism is cheapest there; GDScript is chosen for iteration speed, with the standing obligation that hot or proof-critical systems get promoted into Rust through GDExtension rather than rewritten wholesale. The study branch is the clean-room rule in tree form: a studied title's language produces a specification, and the production code is written fresh in Rust — studied code is never linked, copied, or shipped. The Lua question is asked of every stack, because mixing is a first-class feature: Lua carries gameplay scripts, dialogue logic, and mod surfaces, sandboxed, with all randomness supplied by the host so scripted content stays replay-deterministic. Every path ends at the same obligation: the declared stack, including its language-agnostic RON data layer — the layer that makes the mixing safe.

## 3. Engine

```mermaid
flowchart TD
    A{"Does a Torogao layer<br/>cover this shape?"} -->|Yes| B["Torogao<br/>(build engine of record)"]
    A -->|No| C{"Fast-iteration 2D shape?"}
    C -->|Yes| D["Godot 4"]
    C -->|No| E{"Code-first Rust shape?"}
    E -->|Yes| F["Bevy, or a custom Rust host<br/>when no stock engine fits"]
    E -->|No| G["Record TOROGAO-MODEL-GAP<br/>and stop: the shape is<br/>not buildable yet"]
```

**How to read it.** Torogao is asked first, always: it is the singular build engine of record, and every capability the studio adopts lands there as a layer. Godot and Bevy are not rivals to that rule — they are the proven build routes for shapes Torogao does not yet express, and work done in them feeds back as layer specifications. Unity, Unreal, Ren'Py, RPG Maker, and GameMaker never appear as terminals in this tree at all: they are study targets, read for specifications, and a project that "needs Unity" is really a project whose shape needs naming. If no route fits, the terminal is a record, not a compromise: a TOROGAO-MODEL-GAP is filed and the project stops, honestly, until the layer exists.

## 4. Animation

```mermaid
flowchart TD
    A{"What does the scene need?"} -->|Dialogue or a still moment| B["2D stills / CG"]
    A -->|A character that moves<br/>and reacts, cheaply| C["2D puppet rig<br/>(Inochi2D)"]
    A -->|Sprites or pixel art| D["Frame-by-frame<br/>(Aseprite lane)"]
    A -->|Full-body performance| E["3D skeletal rig<br/>+ morph targets"]
    A -->|A video clip| F["Reference only:<br/>study it, freeze the motion<br/>to rig/curve data,<br/>never ship the video"]
```

**How to read it.** The question is asked per scene type, not per game — one title routinely takes several branches. Stills are the cheapest honest answer for dialogue and carry the visual-novel backbone. The puppet branch is the studio's Live2D-shaped answer: Live2D Cubism models are studied and censused, but production builds in Inochi2D to keep the licence chain out of shipped games. The 3D branch obliges the full rig discipline (skeleton plus facial morph targets, exported as glTF) and buys real-time cinematics instead of video files. The video branch is a doctrine terminal: video — generated, captured, or studied — is reference. Its motion gets frozen into deterministic rig/curve data, and the clip itself is never the shipped artifact, because a clip cannot be replay-hashed, re-gated, or re-rendered.

## 5. Genre

```mermaid
flowchart TD
    A{"What is the core verb?"} -->|Read and choose| B["Node / story kit"]
    A -->|Duel with a deck| C["Card kit"]
    A -->|Think on a grid| D["Grid kit<br/>(tactics and puzzle)"]
    A -->|Manage over time| E["Tick sim kit"]
    A -->|Perform to a beat| F["Rhythm kit"]
    A -->|Run and gun| G["Locked-timestep craft title<br/>(exception, not a kit)"]
```

**How to read it.** Genres are marketing labels; kits are machinery. The tree therefore asks for the *core verb* — the thing the player does most — and routes to the kit that verb implies: the node/story kit (visual novels, trainers, branching adventure), the card kit (deckbuilders and duels), the grid kit (tactics, puzzles, grid crawlers), the tick sim kit (management and incremental games, balanced by fast-forward simulation), and the rhythm kit (fixed charts, scoring as a pure function of input timing). Each kit terminal obliges the kit's full shape: a pure deterministic core, content as data tables with refusing loaders, and a headless playthrough smoke test. The run-and-gun branch is the honest exception: real-time action leaves the kit system and ships as a locked-timestep craft title, with fixed-step physics as its entry fee. Genres with no branch — sandbox 3D, fighting — are pipeline-excluded, not forgotten: the full genre catalogue, with market weight and determinism fit per genre, is in [PIPELINE.md](PIPELINE.md).
