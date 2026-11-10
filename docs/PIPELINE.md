# PHORGE — game creation pipeline (working title)

Draft 0.1 — 2026-11-10. Axes 1–4: language → engine → animation → genre.

Status tags: **BUILD** = the studio builds in it today · **STUDY** = clean-room reverse-engineering / study target only · **PLANNED** = designed, not yet built.

Popularity notes are storefront-presence judgement (itch.io / DLsite / FANZA / Steam adult catalogue), not measured sales data.

## Axis 1 — Programming language (mixing is a first-class feature)

A Phorge project declares a STACK, not a language: one primary + any of {embedded scripting, shader, tooling, data}. The data layer is language-agnostic by design (RON dynamics tables, refusing loaders) — that is what makes mixing safe.

### Primaries

- **Rust — BUILD.** Studio primary (Torogao, the agent runtime, Bevy titles, the dungeon crawler, the Lua-mastery host). Determinism is strongest here: seeded RNG, fixed-step simulation, replay hashes.
- **GDScript — BUILD.** Godot titles. Fast iteration; pair with Rust via GDExtension when a system goes hot or must be proven.
- **Lua — BUILD** as embedded scripting (a vendored Lua 5.5 inside the Rust host; the studio's editor ecosystem). The designated mix-in language: gameplay scripts, dialogue logic, mod surfaces — sandboxed, hot-swappable, deterministic when RNG is host-provided.
- **C# — STUDY + reference.** Unity titles are the largest studied class (the IL2CPP census lane); one flagship's C# Core stands as reference for its Rust production. Not a build primary.
- **Python — BUILD for tooling only** (asset factory, gates, census scripts); STUDY as Ren'Py's base. Never a shipped-game primary in the studio.
- **C++ — STUDY.** Unreal titles. Reverse-engineering / spec source only.
- **JavaScript / TypeScript — STUDY.** RPG Maker MV/MZ plugin layer; Electron titles. Spec source only.
- **Ruby (RGSS) — STUDY.** RPG Maker VX/Ace titles. Spec source only.
- **Ren'Py script — STUDY** as a primary; its dialogue/scene grammar is a spec input to the node/story kit.

### Mixing patterns (proven in production or designed)

- **Rust host + Lua scripts** — the default mix: proven core, scripted content.
- **Rust + WGSL/GLSL/Slang shaders** — the GPU layer is declared in the stack and portability-tested.
- **GDScript + Rust GDExtension** — prototype in GDScript, promote hot/proven systems to Rust without changing the project.
- **Any primary + Python/Rust tooling** — build-time only; tooling never ships in the game.
- **Reference-language → Rust port** — studied or legacy code is a spec; production is rewritten, never linked.

## Axis 2 — Game engine

- **Torogao — BUILD**, the singular build engine of record under the studio's singular build-engine ruling. Every adopted capability lands as a Torogao layer; Phorge routes projects to Torogao first.
- **Bevy (Rust) — BUILD.** Code-first, deterministic-friendly; Torogao-adjacent.
- **Godot 4 — BUILD.** The fast-iteration 2D route.
- **Custom Rust host — BUILD.** For education / embedded-script shapes no stock engine fits (a Bevy host with vendored Lua).
- **Unity — STUDY.** The dominant commercial engine in this market (especially 3D and Live2D-integrated titles) and the largest reverse-engineering class; census-grade support (the IL2CPP slice), never a build target.
- **Unreal Engine 5 — STUDY.** High-end 3D niche; spec source only.
- **Ren'Py — STUDY.** The visual-novel default worldwide; its project shape is the node/story kit's reference grammar.
- **RPG Maker (MZ/MV/VX Ace) — STUDY.** The DLsite RPG workhorse; spec source for the RPG kit.
- **GameMaker — STUDY.** 2D action titles; spec source only.

## Axis 3 — Animation / presentation type

The cross-medium pipeline covers all of these as one pipeline: neural authoring proposes, motion freezes to deterministic rig/curve data, and video is reference only.

- **2D stills / CG — BUILD.** The visual-novel and trainer backbone; cheapest per scene; the market's highest-volume form (event CG sets).
- **2D frame-by-frame sprites + pixel art — BUILD.** The Aseprite lane; deterministic by construction.
- **2D puppet rig — BUILD.** Inochi2D, with the studio's puppet evaluator of record; Live2D-style motion without the Cubism licence chain.
- **Live2D Cubism — STUDY** (census tooling exists). Extremely popular commercially (standing portraits, touch reaction, scene loops); the studio reads Cubism models and builds in Inochi2D.
- **Spine-style 2D skeletal — PLANNED** as a spec; common in mobile/gacha-shaped titles; the rig/curve model maps onto the puppet lane.
- **3D skeletal + morph targets — BUILD.** Blender/Rigify → glTF; the fleet of record (54-bone rigs, facial morph sets); real-time cinematics instead of video files.
- **Cel / hand-drawn loops — BUILD** as authored loops frozen to curve/frame data; premium accents.
- **GIF / composite — BUILD.** Light loops, storefront media, layered composite scenes.
- **2.5D parallax plates — BUILD.** Layered foreground/midground/background plates for backgrounds and side-scrollers; cheap depth.
- **Video / FMV (including image-to-video) — REFERENCE ONLY** by doctrine; never the shipped determinism path.
- **Kinetic text / UI motion — BUILD.** Dialogue and UI as animation; part of the presentation type, not an afterthought.

## Axis 4 — Genre

Popularity = market weight by storefront presence. Determinism = fit to the pipeline's replay-hash standard.

- **Visual novel / ADV** — Market: dominant genre. Determinism: perfect (node kit).
- **Trainer / raising sim** — Market: top tier (schedule + stat thresholds). Determinism: perfect (node + tick kits).
- **RPG (JRPG / dungeon crawler)** — Market: top tier (the DLsite backbone). Determinism: high when turn-based + seeded (grid kit).
- **Simulation / management SLG** — Market: strong (club/factory economies). Determinism: perfect (tick kit).
- **Action RPG** — Market: strong. Determinism: conditional — fixed timestep, or it leaves the pipeline class.
- **Puzzle** — Market: steady mid-tier (unlock-progression framing). Determinism: perfect (grid kit).
- **Card / dice battler** — Market: niche but rising. Determinism: perfect (card kit).
- **Roguelike / roguelite** — Market: niche, loyal audience. Determinism: high (seeded runs).
- **Rhythm** — Market: niche. Determinism: high (fixed charts).
- **Shooter** — Market: small niche (run-and-gun and shmup-with-unlock-gallery shapes work; the FPS shape does not fit the pipeline). Determinism: conditional — locked-step 2D only.
- **Platformer / run-and-gun** — Market: niche. Determinism: conditional, same locked-step rule.
- **Tactics / SRPG** — Market: small niche. Determinism: perfect (grid kit).
- **Idle / incremental** — Market: quiet, growing (mobile-shaped). Determinism: perfect (tick kit).
- **Sandbox / dress-up 3D** — Market: commercially huge, **PIPELINE-EXCLUDED** (continuous 3D, no replay hash; one-off craft titles only).
- **Fighting** — Market: tiny niche, **PIPELINE-EXCLUDED** for production (frame-data determinism exists, but the animation cost per character breaks the line).

## Draft notes / open seams

- Axes 5+ are not yet drafted. Candidates: platform target (Linux/Android/Windows), art-production route, audio route, determinism class as its own stamped field, and lane (all-ages / adult) as a content label rather than an axis.
- Every (language × engine × animation × genre) combination Phorge emits must name its Torogao layer or record a TOROGAO-MODEL-GAP, per the singular build-engine ruling.
- Genre popularity is judgement, not measurement; a storefront census could replace it with numbers if that gate is wanted.
