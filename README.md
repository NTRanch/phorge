# Phorge

Phorge is the Nice Thoughts Ranch game creation pipeline: one deterministic decision pipeline that takes a game from a blank page to a buildable project by walking four axes in order — **language stack → engine → animation type → genre**. A project is not a pile of preferences; it is the path it took through these trees. Every combination the pipeline emits must either name the Torogao layer that implements it or record a TOROGAO-MODEL-GAP — a named, tracked hole — so nothing is ever silently unbuildable. The full axis catalogue lives in [docs/PIPELINE.md](docs/PIPELINE.md); the trees in full, with reading notes, live in [docs/DECISION-TREES.md](docs/DECISION-TREES.md).

A Nice Thoughts Ranch project.

## The four axes, compactly

1. **Language** — a project declares a *stack*, not a language: one primary plus any of embedded scripting, shader, tooling, and a language-agnostic data layer (RON tables with refusing loaders). Rust is the default primary; Lua is the designated mix-in; GDScript is the fast-iteration primary.
2. **Engine** — Torogao is the singular build engine of record. Bevy, Godot 4, and a custom Rust host are the build routes. Unity, Unreal, Ren'Py, RPG Maker, and GameMaker are study targets: clean-room spec sources, never build targets.
3. **Animation** — 2D stills/CG, frame-by-frame sprites and pixel art, 2D puppet rigs (Inochi2D), 3D skeletal rigs with morph targets, cel loops, composites, parallax plates, kinetic UI. Live2D Cubism is studied and read; production builds in Inochi2D. Video is reference only, never shipped.
4. **Genre** — each genre resolves to a production kit (node/story, card, grid, tick sim, rhythm) or to a named exception: a locked-timestep craft title, or pipeline-excluded.

## Master pipeline

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

## Axis 1 — Language tree

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

## Axis 2 — Engine tree

```mermaid
flowchart TD
    A{"Does a Torogao layer<br/>cover this shape?"} -->|Yes| B["Torogao<br/>(build engine of record)"]
    A -->|No| C{"Fast-iteration 2D shape?"}
    C -->|Yes| D["Godot 4"]
    C -->|No| E{"Code-first Rust shape?"}
    E -->|Yes| F["Bevy, or a custom Rust host<br/>when no stock engine fits"]
    E -->|No| G["Record TOROGAO-MODEL-GAP<br/>and stop: the shape is<br/>not buildable yet"]
```

## Axis 3 — Animation tree

```mermaid
flowchart TD
    A{"What does the scene need?"} -->|Dialogue or a still moment| B["2D stills / CG"]
    A -->|A character that moves<br/>and reacts, cheaply| C["2D puppet rig<br/>(Inochi2D)"]
    A -->|Sprites or pixel art| D["Frame-by-frame<br/>(Aseprite lane)"]
    A -->|Full-body performance| E["3D skeletal rig<br/>+ morph targets"]
    A -->|A video clip| F["Reference only:<br/>study it, freeze the motion<br/>to rig/curve data,<br/>never ship the video"]
```

## Axis 4 — Genre tree

```mermaid
flowchart TD
    A{"What is the core verb?"} -->|Read and choose| B["Node / story kit"]
    A -->|Duel with a deck| C["Card kit"]
    A -->|Think on a grid| D["Grid kit<br/>(tactics and puzzle)"]
    A -->|Manage over time| E["Tick sim kit"]
    A -->|Perform to a beat| F["Rhythm kit"]
    A -->|Run and gun| G["Locked-timestep craft title<br/>(exception, not a kit)"]
```

## Status

Draft 0.1 — axes 1–4. Later axes (platform target, art-production route, audio route, determinism class as a stamped field, lane as a content label) are designed seams, not yet drafted.
