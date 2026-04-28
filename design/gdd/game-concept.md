# Game Concept: Sudoku Rush

*Created: 2026-04-28*
*Status: Draft*

---

## Elevator Pitch

> A clean, ad-free sudoku where every correct fill is a satisfying hit event,
> chaining placements builds a score multiplier, and clearing rows, columns, and
> boxes triggers explosive visual bursts. Play a 10–15 minute run across
> back-to-back puzzles — technique names flash up as you use them, the combo
> never fully dies, and the board rewards mastery like a score-attack arcade game.

---

## Core Identity

| Aspect | Detail |
| ---- | ---- |
| **Genre** | Puzzle / Score-Attack Arcade |
| **Platform** | Mobile (iOS / Android) |
| **Target Audience** | Mid-core mobile puzzle players who want more energy from sudoku |
| **Player Count** | Single-player |
| **Session Length** | 10–15 minutes (run-based) |
| **Monetization** | Premium, ad-free (to be confirmed) |
| **Estimated Scope** | Medium (3–4 months, solo) |
| **Comparable Titles** | Tetris Effect, NYT Mini Crossword, sudoku.coach |

---

## Core Fantasy

You are in a flow state where the puzzle flows through you. Numbers land with
satisfying weight, combos stack across puzzle after puzzle, technique names
flash up like achievement banners, and the board erupts with clears. You are
not just solving sudoku — you are performing it. Every run is a chance to hit
a higher peak multiplier, chain a longer sequence, and watch your personal best
fall.

---

## Unique Hook

Like classic sudoku (clean, no ads, pure logic), AND ALSO a live combo-scoring
system that makes technique mastery feel like shredding a guitar solo. Rows,
columns, and boxes cleared trigger visual explosions. Technique names appear in
real time as you use them. A decay-based multiplier rewards sustained flow and
carries across back-to-back puzzles in a timed run.

---

## Player Experience Analysis (MDA Framework)

### Target Aesthetics (What the player FEELS)

| Aesthetic | Priority | How We Deliver It |
| ---- | ---- | ---- |
| **Sensation** (sensory pleasure) | 1 | Particle bursts on area clears, screen pulse on each hit, escalating audio feedback, combo meter animations |
| **Challenge** (obstacle course, mastery) | 2 | Technique depth, difficulty tiers, personal best pressure, combo optimization decisions |
| **Discovery** (exploration, secrets) | 3 | Technique glossary fills in as new techniques are used; players discover the scoring system depth organically |
| **Fantasy** (make-believe, role-playing) | N/A | Not a narrative or world-building game |
| **Narrative** (drama, story arc) | N/A | No story layer |
| **Fellowship** (social connection) | N/A | Solo experience; optional future leaderboard as light social layer |
| **Expression** (self-expression, creativity) | N/A | Not a creative tool |
| **Submission** (relaxation, comfort zone) | N/A | The game actively builds energy, not calm |

### Key Dynamics (Emergent player behaviors)

- Players will optimize the *order* of number placements to maximize combo chain
  and trigger multi-area clears in a single move
- Players will start recognizing and hunting for advanced techniques (X-Wing,
  Hidden Pair) because they offer score multipliers, not just progression
- Players will replay runs specifically to beat their peak combo multiplier, not
  just their total score
- Players will develop a "feeling" for when their combo is about to decay and
  consciously accelerate their pace

### Core Mechanics (Systems we build)

1. **Sudoku puzzle engine** — valid puzzle generation across 4 difficulty tiers;
   input validation; correct/wrong detection
2. **Hit event system** — every correct placement fires a visual pulse + sound hit;
   area clear detection (row, column, 3×3 box) with escalating visual burst
3. **Decay-based combo multiplier** — multiplier increases with consecutive correct
   placements; decreases gradually over time; wrong placements cost multiplier
   levels (not a full reset); multiplier carries across puzzle transitions in a run
4. **Technique detection and labeling** — identifies which solving technique
   the player just used (Naked Single, Hidden Single, Naked Pair, Hidden Pair,
   Pointing Pair, X-Wing, etc.); displays technique name with bonus score popup
5. **Run system** — 10–15 minute timed run; puzzles chain immediately on completion;
   score accumulates across all puzzles; end-of-run summary with personal best delta

---

## Player Motivation Profile

### Primary Psychological Needs Served

| Need | How This Game Satisfies It | Strength |
| ---- | ---- | ---- |
| **Autonomy** (freedom, meaningful choice) | Player chooses placement order — the scoring system rewards *how* you play, not just *that* you finish; no forced tutorial path | Core |
| **Competence** (mastery, skill growth) | Technique names teach you what you just did; score shows measurable improvement; difficulty tiers provide a clear skill ladder; personal best gives objective proof of growth | Core |
| **Relatedness** (connection, belonging) | Personal best comparisons connect the player to their own history; optional leaderboard creates light community presence | Supporting |

### Player Type Appeal (Bartle Taxonomy)

- [x] **Achievers** (goal completion, collection, progression) — High scores, personal bests, technique glossary completion, difficulty tier unlocks
- [x] **Explorers** (discovery, understanding systems) — Discovering new techniques, understanding combo optimization, finding multi-clear setups
- [ ] **Socializers** — Minimal; leaderboard is a future layer, not a core feature
- [x] **Killers/Competitors** — Personal best pressure; future: optional online leaderboard

### Flow State Design

- **Onboarding curve**: First run uses Easy puzzles. Combo system is visible
  immediately but not explained — the first area clear teaches it by feel. No
  tutorial popups; technique names appear in-context as they happen.
- **Difficulty scaling**: Runs can be set to a fixed difficulty tier or progressive
  (puzzles get harder mid-run as the player proves competence). Personal best
  separates by difficulty tier.
- **Feedback clarity**: Combo meter is always visible. Technique names appear on
  use. Score popups show contribution of each event. End-of-run breakdown shows
  technique usage, peak combo, and PB delta.
- **Recovery from failure**: Combo never fully resets — it decays. Wrong placements
  cost levels, not the run. There is no "game over" mid-puzzle; the run ends only
  when the 10–15 minute timer expires.

---

## Core Loop

### Moment-to-Moment (30 seconds)

Player taps a cell, selects a number. If correct:
- Visual pulse + hit sound fires
- Combo meter extends (or holds at current level if warm)
- If a row, column, or 3×3 box is completed: explosion burst + score popup
- If a technique is detected: technique name label floats up with bonus score
- Multiple areas cleared by a single placement: "MULTI-CLEAR!" cascade

If wrong:
- Brief negative feedback (screen dims, sound cue)
- Combo multiplier drops by one level (does not reset to 1×)

**Strategic tension**: Do I place the easy Naked Single now (low score but keeps
combo hot) or spend extra seconds finding the X-Wing (5× bonus but combo decays)?

### Short-Term (5–15 minutes)

A single puzzle within the run. The player builds toward area clears — placing
numbers in sequences that chain 2–3 clears at once. The "one more chain" loop:
almost triggered a triple clear, see it again on the next puzzle. Combos from
late in the previous puzzle carry into the opening moves of the next.

### Session-Level (10–15 minute run)

- Run begins: difficulty selected (or progressive mode)
- Puzzles chain automatically on completion — no pause between
- Combo carries across transitions; completing a puzzle awards a brief multiplier
  spike before the next loads
- Run ends when the timer hits 0 (mid-puzzle play is counted but not forced to finish)
- End screen: total score, peak combo, techniques used, puzzles completed, personal
  best comparison

### Long-Term Progression

- **Difficulty tiers**: Easy → Medium → Hard → Expert — each requiring mastery of
  higher-level techniques to score competitively
- **Technique glossary**: Fills in as new techniques are used for the first time —
  collectable knowledge, not a tutorial
- **Personal bests**: Tracked per difficulty tier and per run length (10 min / 15 min)
- **Achievement milestones**: First X-Wing, first 10× combo, first triple-clear, etc.

### Retention Hooks

- **Mastery**: "I peaked at 8× — I know I can hold it longer"
- **Curiosity**: "What score does an X-Wing in a triple-clear actually give me?"
- **Investment**: Personal best records that the player actively wants to protect
  and break
- **Daily pull**: Daily challenge puzzle (V1.5) — same puzzle for all players that day

---

## Game Pillars

### Pillar 1: Every Hit Lands

Every correct placement is a satisfying event, not a neutral data entry. The
board gives immediate, physical feedback on every move.

*Design test*: If a feature makes placing a number feel like clicking a form
field, cut it or add feedback until it doesn't.

### Pillar 2: Depth is Earned, Not Taught

The game rewards players who learn technique naturally — by doing, not by
reading tutorials. Technique names appear when you use them; the glossary fills
in as you play. No popup explains what a Naked Pair is before you've found one.

*Design test*: If we're debating a tutorial popup vs. showing the technique name
in-context when it happens, this pillar says show-don't-tell wins.

### Pillar 3: Flow Over Friction

The combo never dies completely. The run never pauses between puzzles.
Mistakes cost but don't punish. The game wants you to stay in motion.

*Design test*: If a feature would make a player close the app in frustration,
soften it. If it slows momentum without adding strategic depth, cut it.

### Pillar 4: Clean by Default

No ads, no paywalls, no dark patterns. The UI exists to make the game feel
good, not to upsell. The base board is deliberately stark and clean — all the
visual energy lives in the effect layers.

*Design test*: If a UI element primarily serves monetization over player
experience, it doesn't belong in this game.

### Anti-Pillars (What This Game Is NOT)

- **NOT a story game**: Narrative arcs would pace-break the score-attack flow. No
  story mode, no characters, no plot.
- **NOT powered by items or power-ups**: External help breaks the technique mastery
  fantasy. Score is earned with logic alone, not consumables.
- **NOT multiplayer**: Out of scope for a first game; real-time competition also
  clashes with flow-state design.
- **NOT a clock-race puzzle**: The whole puzzle is not timed. Only the *combo* feels
  time pressure. A global countdown timer would destroy Pillar 3.

---

## Inspiration and References

| Reference | What We Take From It | What We Do Differently | Why It Matters |
| ---- | ---- | ---- | ---- |
| **Tetris Effect** | Sensory feedback layered on a classic puzzle; the "flow state" as explicit design goal | Score-attack focus over meditative mode; technique naming as real-time feedback | Proves puzzle + sensation = massive crossover audience |
| **NYT Mini Crossword** | Daily short sessions, personal best loop, millions of daily active users | Run-based (not one daily puzzle); score-attack over time-attack | Validates short-session daily habit for logic puzzles on mobile |
| **sudoku.coach** | Technique awareness in sudoku drives engagement; naming techniques mid-solve works | Native mobile-first; game-feel layer (combos, scores) not just coaching | Proves the audience wants to *understand* their technique, not just finish |
| **Threes!** | Clean puzzle + combo feel = mobile hit; "one more" loop via score pressure | Sudoku logic layer replaces spatial reasoning; combos are score multipliers not merges | Validates clean score-attack puzzle design on mobile |

**Non-game inspirations**: Guitar Hero / Rock Band (technique name banners,
streak visualization); speedrun culture (personal best as primary motivation);
jazz improvisation (mastery feels like flow, not calculation).

---

## Target Player Profile

| Attribute | Detail |
| ---- | ---- |
| **Age range** | 20–40 |
| **Gaming experience** | Mid-core — plays mobile games daily, occasionally plays PC/console |
| **Time availability** | 10–20 minute sessions on commute, lunch break, or before bed |
| **Platform preference** | Mobile-primary |
| **Current games they play** | NYT Mini Crossword, Threes!, Duolingo (streaks), sudoku apps |
| **What they're looking for** | A sudoku that has *energy* — they've played standard sudoku but want more satisfaction from each solve |
| **What would turn them away** | Forced ads, paywalls mid-game, punishing difficulty spikes, slow UI feedback |

---

## Visual Identity Anchor

**Direction: Minimal Canvas, Maximum Impact**

The base board is deliberately stark and clean — white or near-white background,
thin grid lines, high-contrast numerals. The art burden lives entirely in the
*effect layers*: particle bursts, number animations, technique banners, and combo
meter visuals.

**One-line visual rule**: *The board earns its calm; the effects earn their chaos.*

**Supporting visual principles:**

1. **Neutral base, vibrant events** — Grid and cell backgrounds are near-neutral.
   Color appears only when something happens: gold for area clears, electric blue
   for technique banners, orange-red cascade for high combo states.
   *Design test*: If color is visible during a quiet moment (no active event), reduce it.

2. **Scale communicates value** — Bigger explosions = more score. A single-area
   clear is a small pulse; a triple-clear is a full-screen burst. Players read the
   value of their move from the size of the reaction.
   *Design test*: If two events of different score value produce visually similar
   feedback, differentiate the scale.

3. **Technique banners feel like Guitar Hero streaks** — Name labels appear at
   mid-screen for 1.5–2 seconds, large enough to read at a glance, then fade. Font
   is bold, slightly italicized — kinetic, not formal.
   *Design test*: If a technique banner would interrupt the player's reading of the
   board, reduce duration or reposition to edge.

**Color philosophy**: Neutral grid + a single accent palette per difficulty tier
(e.g., blue tones for Medium, amber for Hard, deep red-violet for Expert). The
combo meter transitions through the accent palette as it climbs.

*This section is the seed of the art bible — confirm with `/art-bible` before
asset production begins.*

---

## Technical Considerations

| Consideration | Assessment |
| ---- | ---- |
| **Recommended Engine** | Unity — strongest mobile toolchain (iOS/Android), large particle/UI asset store, mature build pipeline |
| **Key Technical Challenges** | (1) Accurate technique detection algorithm for advanced moves (X-Wing, Swordfish); (2) Combo timing calibration for mobile touch speed; (3) Sudoku puzzle generation that guarantees unique solutions at all difficulty levels |
| **Art Style** | Clean 2D minimal base + dynamic particle effect layer |
| **Art Pipeline Complexity** | Low-Medium — no illustrated characters; effort concentrated on particle FX, UI animations, and sound design |
| **Audio Needs** | Music-heavy / adaptive — rhythm game-style soundtrack that responds to combo state; satisfying SFX per event type |
| **Networking** | None (local-only for MVP and V1.0); optional online leaderboard in V1.5+ |
| **Content Volume** | Infinite puzzles (procedural); 4 difficulty tiers; ~12 technique types; ~6–8 UI screens |
| **Procedural Systems** | Sudoku puzzle generator — must produce valid, uniquely-solvable puzzles at each difficulty tier |

---

## Risks and Open Questions

### Design Risks

- **Combo timing vs. mobile touch speed**: Decay timing that feels fair on touch
  input requires careful calibration — too fast frustrates, too slow makes the combo
  feel meaningless. Requires early playtesting.
- **Score system balance**: Multiplier values and area-clear bonuses need iteration
  to feel rewarding without being trivially gamed or broken at high difficulty.
- **Audience mismatch**: Traditional sudoku players may find the energy jarring;
  the game must hook score-attack players who don't currently play sudoku.

### Technical Risks

- **Technique detection complexity**: Accurately detecting and labeling which solving
  technique the player used (especially X-Wing, Swordfish, Naked/Hidden Triples)
  requires a sophisticated solver-state analyzer. This is the highest scope risk for
  a first project — may require limiting to simpler techniques for V1.0.
- **Puzzle generator correctness**: A bad generator that produces unsolvable or
  multi-solution puzzles would break the core game. Requires thorough testing.

### Market Risks

- **App Store discoverability**: First-time developer on a crowded platform — requires
  strong ASO strategy and community seeding.
- **Saturated genre**: Sudoku.com has massive install base; differentiation must be
  immediately legible from screenshots and first session.

### Scope Risks

- **Technique detection algorithm** could expand to consume the entire development
  timeline. Mitigation: ship V1.0 with only 4–6 simple techniques; add advanced
  detection post-launch.
- **Sound design and music** are critical to the "arcade feel" but easily
  underestimated in scope for a solo dev.

### Open Questions

- **Combo decay rate**: What is the right time window before the multiplier starts
  dropping? This needs a playtest prototype to answer.
- **Puzzle chaining transition**: Does the combo feel good carrying across puzzles,
  or does the transition feel abrupt? Needs prototype validation.
- **Technique detection scope for MVP**: Which techniques can be reliably detected
  with reasonable engineering effort? Needs technical spike before committing.

---

## MVP Definition

**Core hypothesis**: Players find the combo-scoring sudoku loop engaging enough
to replay a run and try to beat their personal best score.

**Required for MVP**:
1. Valid sudoku puzzle generation (Easy + Medium difficulty, unique solutions)
2. Correct/wrong input detection with immediate visual + audio hit feedback
3. Area clear detection (row, column, 3×3 box) with visual burst + score popup
4. Decay-based combo multiplier (visible meter, decays over ~5–8 seconds, costs
   levels on wrong input — never resets to 0)
5. Technique detection for 2–3 most common types: Naked Single, Hidden Single
6. Technique name popup on detection with bonus score
7. 10-minute run timer with automatic puzzle chaining on completion
8. End-of-run score summary with local personal best tracking

**Explicitly NOT in MVP** (defer to later):
- Advanced technique detection (Naked/Hidden Pair, X-Wing, Swordfish)
- Online leaderboard
- Daily challenge puzzle
- Technique glossary UI
- Hard / Expert difficulty tiers
- Progressive difficulty within a run
- Polished music and adaptive audio

### Scope Tiers

| Tier | Content | Features | Timeline |
| ---- | ---- | ---- | ---- |
| **MVP** | Easy + Medium puzzles (infinite, procedural) | Core loop: hit events, area clears, decay combo, 2–3 techniques, 10-min run, local PB | Months 1–2 |
| **Vertical Slice** | + Hard difficulty | + 6–8 technique types, technique banners polished, all difficulty tiers | Month 2–3 |
| **Alpha** | + Expert difficulty | + Full run mode, sound design, combo meter polish, settings screen | Month 3 |
| **Full Vision** | Complete content | + Daily challenge, technique glossary, online leaderboard, advanced techniques, adaptive music | Month 4+ |

---

## Next Steps

- [ ] Run `/setup-engine` — configure Unity and populate version-aware reference docs
- [ ] Run `/art-bible` — establish visual identity before writing any GDDs (gates asset
      production and shapes rendering/VFX architecture decisions)
- [ ] Run `/design-review design/gdd/game-concept.md` — validate concept completeness
      before going downstream
- [ ] Run `/map-systems` — decompose the concept into individual systems with
      dependencies and priorities
- [ ] Run `/design-system` for each system identified — author per-system GDDs
- [ ] Run `/create-architecture` — produce the master architecture blueprint and
      Required ADR list
- [ ] Run `/architecture-decision (×N)` — record key technical decisions per ADR list
- [ ] Run `/gate-check` — validate readiness before committing to production
- [ ] Run `/prototype combo-loop` — validate the combo timing and area-clear feel
      before full implementation
- [ ] Run `/playtest-report` after prototype to validate the core hypothesis
- [ ] Run `/sprint-plan new` — plan the first sprint once prototype is validated
