# PHORGE — game creation pipeline (working title)
Draft 0.2 — 2026-11-10. Axes 1–4 choose a build's shape (language → engine → animation → genre). Axes 5–11, added on the Owner's steering, score and sequence the slate: they exist to narrow down games the studio already has in the works or planned, and every class is defined broadly enough to score a game nobody has thought of yet.
Status tags: BUILD = estate builds in it today · STUDY = clean-room RE / study target only · PLANNED = designed, not yet built.
Popularity notes are storefront-presence judgement (itch / DLsite / FANZA / Steam adult), not measured sales data.

## Axis 1 — Programming language (mixing is a first-class feature)
A Phorge project declares a STACK, not a language: one primary + any of {embedded scripting, shader, tooling, data}.
The data layer is language-agnostic by design (RON dynamics tables, refusing loaders) — that is what makes mixing safe.

Primaries:
- Rust — BUILD. Estate primary (Torogao, phlow, light-show/Bevy, Niflheim, Versemend host). Determinism strongest here: seeded RNG, fixed-step, replay hashes.
- GDScript — BUILD. Godot titles (Desperado line, Modapp). Fast iteration; pair with Rust via GDExtension when a system goes hot or must be proven.
- Lua — BUILD as embedded scripting (Versemend: vendored Lua 5.5 inside the Rust host; diver/rose ecosystem). The estate's designated mix-in language: gameplay scripts, dialogue logic, mod surfaces — sandboxed, hot-swappable, deterministic when RNG is host-provided.
- C# — STUDY + reference. Unity titles are the largest studied class (IL2CPP census lane); Strobe's C# Core stands as reference for the Rust production. Not a build primary.
- Python — BUILD for tooling only (asset factory, gates, census scripts); STUDY as Ren'Py's base. Never a shipped-game primary in the estate.
- C++ — STUDY. Unreal titles (NTR Idol class). RE/spec source only.
- JavaScript/TypeScript — STUDY. RPG Maker MV/MZ plugin layer; Electron titles. Spec source only.
- Ruby (RGSS) — STUDY. RPG Maker VX/Ace titles. Spec source only.
- Ren'Py script — STUDY as a primary; its dialogue/scene grammar is a spec input to the node/story kit.

Mixing patterns (estate-proven or designed):
- Rust host + Lua scripts (Versemend pattern) — the default mix: proven core, scripted content.
- Rust + WGSL/GLSL/Slang shaders (Bevy / light-show pattern) — GPU layer declared in the stack, portability-tested.
- GDScript + Rust GDExtension — prototype in GDScript, promote hot/proven systems to Rust without changing the project.
- Any primary + Python/Rust tooling — build-time only; tooling never ships in the game.
- Reference-language → Rust port (C# Core pattern) — studied or legacy code is a spec; production is rewritten, never linked.

## Axis 2 — Game engine
- Torogao — BUILD, the singular build engine of record. Every adopted capability lands as a Torogao layer; Phorge routes projects to Torogao first.
- Bevy (Rust) — BUILD. light-show, Niflheim; Torogao-adjacent, code-first, deterministic-friendly.
- Godot 4 — BUILD. Desperado, Modapp. The fast-iteration 2D route.
- Custom Rust host — BUILD. Versemend (Bevy + vendored Lua); for education/embedded-script shapes no stock engine fits.
- Unity — STUDY. The dominant NSFW commercial engine (esp. 3D and Live2D-integrated titles) and the largest RE class; census-grade support (IL2CPP slice), never a build target.
- Unreal Engine 5 — STUDY. High-end 3D NSFW niche; RE/spec only (Seahawk lane).
- Ren'Py — STUDY. The NSFW visual-novel default worldwide; its project shape is the node/story kit's reference grammar.
- RPG Maker (MZ/MV/VX Ace) — STUDY. The DLsite RPG workhorse; spec source for the RPG kit.
- GameMaker — STUDY. 2D action titles; spec source only.

## Axis 3 — Animation / presentation type
Cross-medium pipeline goal covers all of these as one pipeline: neural authoring proposes, motion freezes to deterministic rig/curve data, video is reference only.
- 2D stills / CG — BUILD. VN and trainer backbone; cheapest per scene; NSFW's highest-volume form (event CG sets).
- 2D frame-by-frame sprites + pixel art — BUILD. Aseprite lane; Desperado, jam titles; deterministic by construction.
- 2D puppet rig — BUILD. Inochi2D + lumen puppet evaluator of record; Live2D-style motion without the Cubism licence chain.
- Live2D Cubism — STUDY (census tooling exists: census_cubism_model). Extremely popular in commercial NSFW (standing portraits, touch reaction, H-scene loops); estate reads models, builds in Inochi2D.
- Spine-style 2D skeletal — PLANNED as a spec; common in mobile/gacha-shaped NSFW; rig/curve model maps onto the puppet lane.
- 3D skeletal + morph targets — BUILD. Blender/Rigify → glTF; Torogao/Strobe fleet of record (54 bones, Fac_ morphs); real-time cinematics (SLATE-style) instead of video files.
- Cel / hand-drawn loops — BUILD as authored loops frozen to curve/frame data; premium VN/action accents.
- GIF / composite — BUILD. Light loops, README/storefront media, layered composite scenes.
- 2.5D parallax plates — BUILD. Layered fg/mid/back plates for VN backgrounds and side-scrollers; cheap depth.
- Video / FMV (incl. img2video) — REFERENCE ONLY by doctrine; never the shipped determinism path.
- Kinetic text / UI motion — BUILD. Dialogue and UI as animation (kinetic-ui lane); part of the presentation type, not an afterthought.

## Axis 4 — Genre
Popularity column = NSFW market weight (storefront presence); Determinism = fit to the pipeline's replay-hash standard.
- Visual novel / ADV — NSFW: dominant genre. Determinism: perfect (node kit). Estate: Strobe, Prima design, most Lane D studies. SFW: yes.
- Trainer / raising sim — NSFW: top tier (schedule + stat thresholds). Determinism: perfect (node + tick kits). Estate: Prima template, trainer studies.
- RPG (JRPG / dungeon crawler) — NSFW: top tier (the DLsite backbone). Determinism: high when turn-based + seeded (grid kit). Estate: Niflheim, Versemend (RPG-framed learning), Lane D RPG studies. SFW: yes.
- Simulation / management SLG — NSFW: strong (club/factory/brothel economies). Determinism: perfect (tick kit). Estate: Milk Factory, Fall.
- Action RPG — NSFW: strong. Determinism: conditional — fixed timestep or it leaves the pipeline class. Estate: Lane D studies.
- Puzzle — NSFW: steady mid-tier (unlock-progression framing). Determinism: perfect (grid kit). Estate: Magic Coin, light-show (SFW).
- Card / dice battler — NSFW: niche but rising. Determinism: perfect (card kit). Estate: Hypnosis Card.
- Roguelike / roguelite — NSFW: niche, loyal audience. Determinism: high (seeded runs). Estate: Niflheim (SFW), Lane D studies.
- Rhythm — NSFW: niche. Determinism: high (fixed charts). Estate: Strobe's rhythm layer.
- Shooter — NSFW: small niche (run-and-gun and shmup-with-unlock-gallery shapes work; FPS does not fit the pipeline). Determinism: conditional — locked-step 2D only. Estate: Desperado (2D run-and-gun, SFW) is the template shape.
- Platformer / run-and-gun — NSFW: niche. Determinism: conditional, same locked-step rule. Estate: Desperado.
- Tactics / SRPG — NSFW: small niche. Determinism: perfect (grid kit). Estate: planned shape only.
- Idle / incremental — NSFW: quiet, growing (mobile-shaped). Determinism: perfect (tick kit). Estate: none yet.
- Sandbox / dress-up 3D — NSFW: commercially huge, PIPELINE-EXCLUDED (continuous 3D, no replay hash; one-off craft titles only).
- Fighting — NSFW: tiny niche, PIPELINE-EXCLUDED for production (frame-data determinism exists but the animation cost per character breaks the line).

## Axis 5 — Scope class (how big the finished thing is)
Score the contented size, never the shell: a landed shell with no content pass is S until its content lands. Scope is the denominator for every later axis — a heavy load at S is a weekend, at XL a season.
- S (slice) — one loop, one content set. Jam titles, demonstrators, landed shells.
- M (short) — one loop fully contented, or a small set of loops over one cast / content set.
- L (full) — several systems or a full campaign / roster; multiple content sets.
- XL (flagship) — multi-region or large-roster, staged over multiple production passes.
Estate evidence: Hands-On shipped at S/M; Niflheim is L by design (17 floors); Strobe is XL (ten-heroine cast, staged progression ladders).

## Axis 6 — Asset-pipeline reuse (what the estate already owns that this title consumes)
- R3 (native) — an existing estate pipeline carries the title end to end; the work is content through it. Lane D shells on landed kits; cast-fleet derivatives.
- R2 (high) — the pipeline exists; the title adds content and at most minor stages. MoonDeep's plates through the stills pipeline.
- R1 (partial) — some stages exist; at least one pipeline stage must be built or proven for this title.
- R0 (greenfield) — the title needs a pipeline the estate does not have. Commissioning it commissions the pipeline too, and the score must say so.
Honesty rule: a reuse claim names the pipeline it reuses. "We have art" is not a pipeline.

## Axis 7 — Content-production load (where the hours and the verdicts sit)
Two fields: dominant load class + grade (light / moderate / heavy).
- Text — writing volume dominates (VN and RPG dialogue).
- Art — stills, sprites, or model work dominates. If the Owner's eye is the gate, say so: verdict-gated art is schedule, not just labour.
- Audio — voice, music, or mastering dominates; the Owner's ear is the gate where masters ship.
- Data/systems — data tables, tuning, state vocabularies. The cheapest load class: generatable, diffable, hash-gated, delegatable.
- Balanced — no single class dominates.
Estate evidence: the Surrender-derived session game is audio-heavy and ear-gated; Milk Factory's full roster is art-heavy at production volume (18 girls × 15 parts × up to 3 sets, plus 20 battle portraits, per its measured spec); Magic Coin's production pass is data-shaped and light.

## Axis 8 — Dual-target cost (Linux + Android)
Standing law: every shipped title ships on both. The axis prices the marginal cost; it never asks whether.
- T0 (proven) — this crate/engine shape already dual-builds in the estate: the shell pattern with its separate Android crate; Hands-On's shipped APK is the reference proof.
- T1 (standard) — the shell pattern applies unchanged; no exotic input, memory, or render needs.
- T2 (elevated) — per-platform work is expected: touch-first input, large memory footprint, GPU-heavy presentation, platform audio latency.
- T3 (blocked) — a named platform capability gap stops the Android half today; the gap is recorded and the title scores as a study until it clears.
Named gap, honestly held: the Android performance envelope for 3D cast-fleet titles is unmeasured — fleet titles score T2 with the gap named, not T3, because no blocker is proven either. A title that cannot dual-target at all is a tool or a study, never a slate candidate.

## Axis 9 — Determinism / testability class (stamped on every project)
- D0 (exact) — state + finite choices + seeded RNG + data tables; a full playthrough is replay-hashable and the gate is hash equality. Lane D systems crates; the Lua host's byte-identical transcript gate.
- D1 (engine) — fixed-step simulation; state-level replay hashes hold, presentation is free. Bevy/Godot titles run locked-step.
- D2 (sampled) — deterministic core, non-deterministic presentation (puppet, particle, physics dressing); gates cover core state exactly and presentation statistically.
- D3 (exempt) — tools and studies; no shipped determinism claim.
The class decides how much of the gate battery is automated, which decides who can build it: D0/D1 work delegates to gated build lanes; D2 work keeps a human verdict in the loop.

## Axis 10 — Time-to-playable (distance to a slice a person can judge)
- P0 — playable today (shipped, or a running shell).
- P1 — one rung away: shell binding, a content pass on landed systems, a close-out.
- P2 — one system plus its content: spec in hand, crate or kit not yet built.
- P3 — design or earlier, or blocked on a capability rung or an Owner gate. A P1 behind an unclaimed Owner gate is P3 until the gate clears, and the gate is named in the score.
Evidence basis: spec maturity (measured > specced > designed > premise) is recorded with the P grade. A P grade without its evidence basis is a guess and scores P3.

## Axis 11 — Slate synergy (what building this builds for the others)
- Y3 (template) — the build produces a kit, pipeline, or pattern other titles consume. The first card-kit title; the Prima corruption template.
- Y2 (proof) — retires a named risk shared by several titles: a storefront route, a sync spike, a dual-build proof.
- Y1 (consumer) — uses what exists; adds content and polish only.
- Y0 (orphan) — nothing else consumes the work. Allowed, but chosen knowingly.
Synergy is the portfolio axis: it is why a P2 template can outrank a P1 orphan.

## How the axes narrow (selection method)
Axes 1–4 describe; axes 5–11 decide. Order of application:
1. Gates before scores. Provenance/exclusion checks and the dual-target law are fail-closed and are never traded against a score.
2. Sequence by P, lowest first.
3. Break ties by synergy, then by load: data/systems load before verdict-gated load, because Owner verdicts are the scarcest schedule resource in the studio.
4. A capability rung that unblocks several titles scores as a title with Y3 and outranks any single consumer of it.
The worked example — the current slate scored on all eleven axes, with the shortlist this method produces — lives in SLATE-SCORING.md.

## Draft notes / open seams
- Draft 0.1 candidates resolved: platform target folds into Axis 8 (under the dual-target law platform is a cost, not a free choice); determinism class is promoted to Axis 9 as its own stamped field; art and audio production routes fold into Axes 6–7 (reuse and load) rather than standing alone; lane (SFW/NSFW) stays a content label carried on every record, not an axis — it describes audience and handling, never producibility.
- Considered and rejected as axes: monetisation (no studio title is monetised under the standing ruling, so a revenue axis would be fiction today; revisit if that ruling changes); novelty/prestige (unmeasurable — Axis 11 captures the real portfolio value); storefront-first / platform exclusivity (contradicts the dual-target law); licence and provenance risk (a fail-closed gate applied before scoring, not a gradient to trade off); engine-native fit (already decided by Axes 1–2; scoring it again double-counts).
- Every (language × engine × animation × genre) combination Phorge emits must name its Torogao layer or record a TOROGAO-MODEL-GAP.
- Genre popularity is judgement, not measurement; a storefront census could replace it with numbers if the Owner wants that gate.
