# SLATE SCORING — the Phorge narrowing method, worked on the current slate

Companion to docs/PIPELINE.md (axes 1–11). Purpose: prove the selection axes do their job — take everything the studio has in the works or planned, score it on the full axis set, and produce a shortlist short enough to act on.

## Sources and confidence

- Lane D facts (queue position, study grade, next rung, blockers) are from the programme's queue record, read 2026-11-10.
- Versemend facts are from its completion-programme status file (Contracts 4–5 gated pass; Contract 6 since landed per the coordinator's machine verification, after that file was written).
- Everything else is from studio programme records current to 2026-11-10. Any cell resting on records rather than a same-day verification is marked *(assumed)*. No project state was invented for this scoring; where a fact could not be grounded, the cell says so and the P grade falls back per the Axis 10 evidence rule.

## The slate, scored

Shape = Axes 1–4 compressed (stack · engine · animation · genre). Then Axis 5 Scope / 6 Reuse / 7 Load / 8 Dual / 9 Determinism / 10 Playable-distance / 11 Synergy.

| Title | Shape | 5 | 6 | 7 | 8 | 9 | 10 | 11 |
|---|---|---|---|---|---|---|---|---|
| Desperado | GDScript · Godot 4 · frame sprites · run-and-gun | M | R2 | Art, moderate (eye) | T1 *(assumed — Godot Android export not yet estate-proven)* | D2 | P1 | Y1 |
| Strobe | Rust · Bevy · 3D skeletal + morph · VN / rhythm layer | XL | R3 | Art + Audio, heavy (eye + ear) | T2 (3D Android envelope unmeasured — gap named) | D1 | P2 | Y3 |
| Light Show | Rust · Bevy · puppet + frame *(assumed)* · rhythm / puzzle, SFW | M | R3 | Balanced, moderate | T1 *(assumed — Android is a designed publish channel)* | D1 | P1 *(assumed)* | Y2 |
| MoonDeep | Rust · Bevy · 2D stills · VN *(genre assumed)* | M | R2 | Text/Systems, moderate (art landed: 79 plates, candidate) | T1 *(assumed)* | D1 | P1 | Y1 |
| Roseford | Rust · Torogao *(assumed)* · 2D stills *(assumed)* · RPG | L | R1 (grid/RPG kit is planned, not built) | Text, heavy | T1 *(assumed)* | D1 (potential) | P3 | Y3 |
| Where She Asks to Fall | Rust · Torogao · puppet + stills · VN / session | M | R3 | Audio, heavy (ear) | T1 | D0 | P1 | Y2 |
| Magic Coin | Rust · Torogao shell · stills/composite · puzzle | S→M | R3 | Data, light | T1 (dual-build proof is its named next rung) | D0 | P1 | Y2 |
| Milk Factory | Rust · Torogao shell · 2D stills · management sim | M | R3 | Art, heavy at full roster | T1 | D0 | P1 (data pass) | Y1 |
| Modification App | Rust · Torogao shell (Godot original) · 2D stills · management sim | M | R2 | Systems, moderate | T1 | D0 | P2 (minigames + four open spec-review items) | Y2 |
| Time Stop | Rust · Torogao shell · 2D stills · management sim | S as commissioned (L if full) | R3 | Art, heavy if full | T1 | D0 | P1 demonstrator / P3 full | Y1 |
| Hypnosis Card | Rust · Torogao shell · stills/cards · card battler | M | R3 | Data/Systems, moderate | T1 | D0 | P1 (staged delta) | Y3 |
| Night School | Rust host *(assumed)* · puppet rig · VN / demonstrator | M *(assumed)* | R2 | Art/Animation, moderate (eye) | T2 *(assumed — animation-heavy Android unmeasured)* | D2 | P1 (close-out: gating + wiring note) | Y2 |
| Hands-On Technical Rope | Rust host · frame/GIF · education sim, SFW | S/M | R3 | Balanced, light | T0 (shipped APK) | D0 | P0 — shipped v0.1.0 | Y3 (historical: the Android-route proof every shell consumes) |
| Versemend | Rust + vendored Lua · custom host · kinetic text · RPG-framed learning | L | R3 | Systems/Text, moderate | T0 (APK built per contract) | D0 (byte-identical transcript gates) | P1 per contract (whole programme P2) | Y3 (the Lua mix-in template) |
| Niflheim | Rust · Bevy · frame/stills · RPG | L | R2 | Systems, moderate | T1 (Android library built per rung, per studio records) | D1 (per-rung determinism hashes pinned) | P1 per step (whole P2) | Y2 (split-build programme is itself a production template) |
| Personality Excretion remake (Prima template) | Rust · Torogao · real-time 3D cinematics (per census: no video clips) · trainer/sim | M | R2 | Systems + Art, moderate-heavy | T1 *(assumed)* | D0 (potential — state grammar measured at census) | P2 (study rung next; beyond-metadata dynamics await the native RE rung) | Y3 (Prima corruption template) |
| Uncommissioned Lane D queue (as a class) | mixed | S–L | R1–R3 by family | S5 content dominates: heavy | T1 once a crate lands in the shell pattern | D0 potential in the data-shaped families | P3 (one member P2: the rhythm title, spec done, one spike from its systems crate) | Y2 as a class (value concentrates in two shared rungs, below) |

Per-title grounding notes (only where the table compresses something that matters):

- **Desperado** — a playable slice is public today; P1 scores the *next increment* (Stage 1 art iteration plus the ARM/duel implementation), which is what the slate decision is actually about.
- **Strobe** — the cast fleet is landed and pipeline-complete (R3/Y3), but the game itself is XL, its remaining load is verdict-concentrated on both eye and ear, and its public build is held by an Owner ruling until the smoothing pass lands. It proceeds on its own Owner-gated track; the axes explain why it should not block the rest of the slate.
- **Where She Asks to Fall** — systems crate landed and hash-pinned (D0); the single remaining rung to playable is shell binding. Its schedule risk is not build risk: the session audio masters are ear-gated and still in batch production.
- **Magic Coin** — spec measured, systems and shell landed, production build commissioned; the commissioned first rung is the production content data layer. Lightest load on the board relative to distance.
- **Milk Factory** — P1 covers the commissioned roster expansion, which is data-only. The full art-volume pass behind it (the largest content surface in the queue's front half, per its spec) is a separate, later commission and is *not* smuggled into this score.
- **Modification App** — the four open spec-review items (first-entry route, quick-travel charge, cafe price table, per-level tuning) are named in its commission as items to surface, not silently resolve; they are why it sits at P2 despite a landed shell.
- **Time Stop** — capped at its demonstrator by Owner ruling. The axes score the full version P3/heavy; the ruling, not the score, is what keeps it small. Recorded here so the cap is a decision on the books, not drift.
- **Personality Excretion remake** — Owner-commissioned as the next remake and as the template for Prima's corruption play (desire as the progression engine; the original's defeat arc does not carry over — design doc landed). Intake and metadata census are done; the study rung is next. Its D0 is marked *potential*: the meter/ending grammar is measured, the hash gate exists only once its systems crate does.
- **Uncommissioned Lane D queue** — scored as a class because no member is commissioned. Family reuse runs high for the data-shaped families (Mono, Ren'Py, RPG Maker — census idiom already proven on the commissioned five) and low for the native-walled families (IL2CPP, Unreal, custom). Two shared blockers gate most of the class: the native IL2CPP rung and the rhythm audio-sync spike.

## Applying the method

1. **Gates first.** Nothing on the slate fails the provenance/exclusion gates as scored (excluded source material stays excluded inside the relevant titles; that is a property of how they are built, already enforced upstream of scoring). Hands-On is complete — it leaves the candidate set and stays on the board only as the T0/P0 reference proof.
2. **Sequence by P.** The P1 set: Desperado (next increment), Light Show *(assumed)*, MoonDeep, Where She Asks to Fall, Magic Coin, Milk Factory (data pass), Hypnosis Card (delta), Night School (close-out), Versemend (per contract), Niflheim (per step), Time Stop (demonstrator — capped by ruling, excluded from the pick).
3. **Tie-break by synergy, then by load.** Within P1, verdict-gated load is the constraint: the studio can run several data/systems builds in parallel, but eye and ear verdicts arrive one at a time. That pushes the data-shaped P1s (Magic Coin, Hypnosis Card) ahead of the ear-gated one (Where She Asks to Fall) and the eye-gated ones (Desperado increment, Night School close-out is small enough to ride along), and it defers MoonDeep and Light Show — both fine titles whose next increments consume the same scarce verdict capacity for less portfolio return (Y1/Y2, no kit produced).
4. **Capability rungs outrank consumers.** Two rungs unblock more than any single title: the native IL2CPP rung (unblocks the IL2CPP family, the doll-shop and 3D-touching titles, and beyond-metadata dynamics for the Prima template) and the rhythm audio-sync spike (unblocks the rhythm remake's systems crate, and de-risks the rhythm steps in Hypnosis Card's second stage and Strobe's rhythm layer). Both score Y3 under the method and belong on the shortlist as purchases, not titles.

## The shortlist

In order, with the axis values that put each one here:

1. **Magic Coin — production build.** P1, D0, load Data/light, Y2. The pilot pattern for all Lane D production: if this commission's shape works, four more titles inherit it.
2. **Hypnosis Card — staged delta, then stage 2.** P1, D0, Y3. Builds the card kit, the second genre kit in the build order; its desire-hook delta is already staged as a bounded contract.
3. **Where She Asks to Fall — shell binding.** P1, D0, Y2. First shipped Torogao session game; proves the audio-session pattern in production. Named risk: ear-gated masters land in parallel and set the real ship date.
4. **Night School — close-out.** P1, small. Gating plus the wiring-in note finishes a published title; cheap enough to ride alongside any of the above.
5. **Versemend (next contract) and Niflheim (split-build) — standing cadences, run in parallel.** Both D0/D1, systems-loaded, hash-gated, and neither touches the GPU or the verdict bottleneck. They are the slate's ballast: always advancing, never blocking the picks above.
6. **Milk Factory — roster expansion, data pass only.** P1, D0. The data-shaped half of its commission now; the art-volume half waits for a verdict-capacity slot.

**Capability purchases (ranked with the titles, per the method):** the native IL2CPP rung and the rhythm audio-sync spike — either outranks shortlist items 4–6 if a build slot forces the choice, because each converts a class of P3s into P2s.

## Held by ruling, not by score

- **Strobe public build** — held until the smoothing pass lands (Owner ruling); the verdict walk on its texture pack is parked by the same ruling and resumes from the smoothed artifacts.
- **Desperado next increment** — queued behind the Wan rerun (Owner ruling); its P1 stands when the slot opens.
- **Time Stop** — capped at the demonstrator (Owner ruling).
- **Fall audio masters** — an ear-gated batch already in production; they are Where She Asks to Fall's load, counted there, not a separate candidate.

## Deferred, with the reason on the record

- **Roseford** — P3 but Y3: the studio's first full RPG builds the grid kit and the RPG data idiom that the Lane D RPG family later consumes. It is the first P3 to promote when a commission slot opens; promoting it now would spend the verdict and design capacity the shortlist is conserving. TOROGAO-MODEL-GAP recorded: grid/RPG kit is planned, not built.
- **MoonDeep** — P1/Y1: rises the moment a Bevy content slot matters more than kit production.
- **Light Show (next increment)** — P1 *(assumed)* / Y2: the SFW storefront proof is already substantially retired by its publish routes; further increments are polish until a release slot is the priority.
- **Modification App** — P2: rises when its four spec-review items are ruled on; building the minigames around unruled tuning would bake guesses into a D0 crate.
- **Strobe (full production)** — XL scope, heavy verdict load, and the unmeasured Android 3D envelope keep it on its own Owner-gated track regardless of shortlist mechanics.
- **Uncommissioned Lane D queue** — capability-gated as a class. When a commission slot reaches it, family order by reuse: data-shaped families first (Mono, then Ren'Py/RPG Maker state-vocabulary rungs), native-walled families only behind the IL2CPP rung.
