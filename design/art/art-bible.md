# Art Bible: Sudoku Rush

*Status: Complete — All 9 Sections Authored*
*Last Updated: 2026-04-29*

---

## 1. Visual Identity Statement

### The One-Line Visual Rule

> **"The board earns its calm; the effects earn their chaos."**

This is the governing contract for every visual decision in *Sudoku Rush*. The base game state — the grid, the cells, the numbers at rest — is deliberately stripped of ornament. Visual energy is budgeted, not spent freely. The budget is spent entirely on feedback events: placements, combos, technique recognitions, and area clears. A player who has never touched an art bible should be able to derive every visual hierarchy decision from this single sentence.

---

### Supporting Visual Principles

**Principle 1: Neutral Base, Vibrant Events**

The grid and all static cell states (empty, given digit, player-placed digit at rest) render in near-neutral values: dark backgrounds with low-saturation surfaces, white or off-white numerals at full opacity. Color — defined here as any hue with saturation above 20% — is permitted only when attached to an active game event. The moment the event resolves, the board returns to neutral.

> `[IMAGE: Two side-by-side board states — (A) board at rest: monochrome grid, white digits on dark background, zero color; (B) same board mid-area-clear: gold burst radiating from completed box, electric blue technique banner, contrast between the two states illustrates the principle]`

- **Pillar served**: "Every Hit Lands" — a neutral resting state guarantees that the moment color appears, the player's peripheral attention snaps to it. If the board already contains ambient color, the placement event competes rather than pops.
- **Design test**: At any moment when no event is actively animating, take a screenshot. Desaturate it to greyscale. If any element is lost (i.e., depended on hue for meaning rather than value contrast), it has been colored incorrectly. Revert to a neutral value-based treatment.

**Principle 2: Scale Is Score**

The visual magnitude of a feedback event must directly encode its score value, not just its category:
- **Single cell placement**: cell-local pulse (radius: cell-local, duration: 200–300ms)
- **Single-area clear** (one box, row, or column): area-spanning burst (radius: area-spanning, duration: 400–600ms)
- **Multi-area clear** (simultaneous): screen-filling eruption (radius: screen-filling, duration: 800–1200ms with particle tail)

Players should be able to estimate their score delta from the size of the visual reaction before looking at the score counter.

> `[IMAGE: Three-panel sequence showing scale progression — panel 1: small ripple from single digit placement; panel 2: medium burst filling one 3×3 box on row-clear; panel 3: full-screen particle cascade on simultaneous triple-clear. Each panel labeled with approximate score value to make the scale-value link explicit]`

- **Pillar served**: "Depth is Earned, Not Taught" — if scale tracks score, players develop an intuitive feel for high-value moves purely through visual feedback. A triple-clear doesn't need a "+450" callout to feel enormous; the screen tells them.
- **Design test**: If two events of different point value produce feedback of visually similar scale (burst radius within 20% of each other or duration within 100ms), the lower-value event must be reduced, not the higher-value event inflated.

**Principle 3: Technique Banners as Kinetic Punctuation**

When the engine recognizes a technique (Naked Single, Hidden Pair, X-Wing, etc.), a name banner appears at the horizontal center of the screen, positioned in the lower third so it does not occlude the active play area in the upper two-thirds. The banner is large enough to read in a single eye fixation at arm's length on a 6-inch screen (minimum 28sp equivalent, bold weight, 5–8 degrees italic). It persists for 1.5–2 seconds, then fades over 300ms. The font is the same display typeface used for the score — kinetic and confident, not decorative or soft.

> `[IMAGE: Phone screen mockup (375pt width) showing a technique banner — "HIDDEN SINGLE" in bold italic at lower-third position — overlaid on an active board. Dotted overlay shows the 9 bottom-row cells are still visible and untouched by the banner. A second panel shows the same banner incorrectly centered mid-board, obscuring play cells, to illustrate what to avoid]`

- **Pillar served**: "Flow Over Friction" — the banner is designed to be readable in peripheral vision during continued play. It must not demand that the player stop to read it. If a player can naturally ignore a banner and still feel its presence as a reward, it is correctly designed.
- **Design test**: If a technique banner obscures a cell the player would need to tap within its 2-second window of visibility, the banner is too large or incorrectly positioned. Reposition to the lower third and verify against the nine bottom-row cells on the smallest supported screen (375pt width).

---

### What This Means in Practice

- **Digit placement animation**: A placed digit does not appear instantly at full opacity. It scales from 0 to full size over approximately 80–120ms with a subtle overshoot easing (scale to 110%, settle to 100%). This applies to every placement without exception. Instant appearance fails the "Every Hit Lands" test.
- **Grid lines**: Flat, no texture, no gradient, no glow. "Clean" defined operationally: a line is clean if its sole job is to indicate cell boundaries. Line color: white at 10–15% opacity on a dark background.
- **Combo meter at idle**: Static — no pulse, no breathing, no animation. Motion = event only. Exception: a 150ms wake-up animation on first combo activation in a run.
- **Color during quiet moments**: Only the neutral palette and the active cell selection highlight are permitted. Any other color present between events is a Principle 1 violation.
- **Base layer stays still**: If the board feels lifeless between clears, the correct response is to enrich the effect events — not add ambient animation to the base layer. The board's stillness is a feature, not a bug.
- **Typography as a system**: All numeric glyphs use the same typeface family at different weights. Given digits: medium weight, 90% white opacity. Player-placed digits: bold weight, 100% opacity. Pencil marks: light weight, 60% opacity. Weight encodes semantic meaning; no decorative typefaces appear outside technique banners and the game title lockup.

---

## 2. Mood & Atmosphere

### The Emotional Architecture

Before the per-state breakdown, one framing note: *Sudoku Rush* runs on a single session arc. The mood does not reset between puzzles — it accumulates. The player enters cool and quiet, and the session *earns* its heat. Every atmospheric shift must feel like a consequence of player action, not a scheduled event. If the environment intensifies before the player has earned it, the reward is diluted.

The visual arc across a full run moves along two axes simultaneously:

- **Temperature**: cool blue-grey (neutral) at rest → warming toward amber-gold at peak flow → settling to warm embers at results
- **Density**: sparse and open at rest → particle density increasing with combo accumulation → briefly saturating at burst moments → releasing

A player at peak combo who makes three errors should *feel* the environment cool and quiet behind them. This is not punishment — it is honest feedback. The atmosphere is a mirror.

---

### 2.1 Home / Menu Screen (Pre-Run)

**Primary emotion**: Composed readiness. The feeling of a pianist sitting at the bench before the first note — alert, settled, slightly anticipatory. Not relaxed (that implies passive), not tense (that implies fear). Poised.

**Lighting character**: Low contrast. Background fill at cool blue-grey (approximately 210° hue, 8–12% saturation, 18–22% brightness). No glow present. Color temperature slightly cool-leaning. Contrast between UI elements carried entirely by value (light/dark), not by color.

**Atmospheric descriptors**:
- *Quiet* — the absence of particle activity is intentional; the screen has the quality of a held breath
- *Precise* — edges are clean, spacing is generous, nothing overlaps; communicates that the system ahead is ordered and knowable
- *Anticipatory* — subtle slow-drift in the background fill (cycle time 8–12 seconds, imperceptible as motion but alive enough to distinguish from a static screenshot)
- *Uncluttered* — visual weight concentrated at center; screen margins are empty
- *Reserved* — no color has been spent yet; the palette is holding back

**Energy level**: Still. This is the baseline zero of the session arc.

**Visual cues**: No particle activity. Background static or near-static. All UI elements desaturated. Board, if visible, shown neutral — no highlights, no fills, no cell glow.

> `[IMAGE: Reference target — a dark, low-saturation game menu with generous whitespace and near-zero particle activity. Contrast comes purely from value relationships. Think: a music venue before the house lights dim, or a blank sheet of staff paper.]`

---

### 2.2 Puzzle Solving — Low Combo (Early Run, Warming Up)

**Primary emotion**: Focused attention. The specific quality of attention that comes with the first few minutes of reading a book — you are building context, tracking the logic, and nothing has surprised you yet. Deliberate. Not urgent.

**Lighting character**: Background remains cool-neutral. A trace of warmth permitted at the combo meter — a faint amber edge glow (below 15% opacity). No background glow. All contrast value-based, not hue-based.

**Atmospheric descriptors**:
- *Attentive* — the visual environment is leaning forward slightly; not passive like the menu, but not yet engaged like mid-combo
- *Controlled* — every effect is contained and proportionate; a cell fill should feel satisfying but not celebratory
- *Sparse* — particle count is low; individual particles are legible and distinct; density reads as "occasional" not "continuous"
- *Building* — faint suggestion that something is accumulating
- *Clean* — no lingering particle trails; effects resolve quickly and return the screen to neutral

**Energy level**: Measured. The player is active but the environment is not yet responding with full voice.

**Visual cues**: Combo meter shows a faint activation glow (absent on Home). Cell placements produce 1–3 particles max, resolving under 0.4 seconds. Background remains static.

> `[IMAGE: Reference target — a sudoku board with a single recently filled cell showing a small white flash almost fully faded. The rest of the board is neutral. Combo meter shows a dim, first-notch activation. Particle count: near zero.]`

---

### 2.3 Puzzle Solving — Mid Combo (Flow Building, 3–6× Multiplier)

**Primary emotion**: Momentum. The specific sensation of a run where your stride has found its rhythm — you are not yet in the zone, but you can feel the zone approaching. Each step lands a little more confidently than the last.

**Lighting character**: Background begins to show a very low-saturation warm fill — temperature shifts from cool-blue toward a very desaturated amber (approximately 35–40° hue, 15–20% saturation, 15–20% brightness). Combo meter glow becomes visible and continuous. Color temperature now clearly warmer than the Home state.

**Atmospheric descriptors**:
- *Rhythmic* — visual feedback fires in a pattern the player begins to anticipate
- *Accumulating* — particle trails from cell fills do not fully resolve before the next one fires; a faint residue communicates history without obscuring legibility
- *Warm* — color temperature has shifted enough to register as "different from the start" without being saturated
- *Continuous* — something is always slightly moving; the board feels alive between taps
- *Purposeful* — every visual element present is doing work; nothing decorative has been added

**Energy level**: Escalating. This state should feel like it is pulling the player forward, not satisfying them.

**Visual cues**: Background warm fill visible (not present in low combo). Combo meter glow steady and bright. Particle trails have short linger (0.3–0.5 second decay). Absence of any background motion (warmth is ambient, not dynamic) distinguishes this from peak combo.

> `[IMAGE: Reference target — board with 3–4 recently filled cells, each showing a faint decay trail. Background shows a warm but very low-saturation amber ambient. Combo meter at approximately half brightness. Board remains fully readable.]`

---

### 2.4 Puzzle Solving — Peak Combo (Flow State, 7× + Multiplier)

**Primary emotion**: Effortless mastery. The specific quality described in flow literature as the disappearance of the boundary between the player and the task. This is not excitement — excitement is aroused. This is a deep, fast, quiet certainty. The musician who has played this passage five hundred times and no longer has to think about their hands. The speedrunner two minutes into a clean run.

This is the emotional apex of the game session. It must feel earned.

**Lighting character**: Background fill shifts further warm, approaching a low-saturation gold (approximately 42–48° hue, 25–35% saturation, 20–25% brightness). A soft vignette glow at screen edges pulses very slowly with tap rhythm (pulse cycle 0.5–1.0 second, tied to input frequency). The board itself remains high-contrast and fully readable — the warmth lives in the periphery, not the playfield.

**Atmospheric descriptors**:
- *Radiant* — the screen is visibly warmer and brighter than earlier states; warmth as an achieved state
- *Saturated* — color is present for the first time at a level readable without close attention
- *Pulsing* — the background glow has a rhythm synchronized loosely with player input; the environment breathes with the player
- *Immersive* — screen-edge vignette tightens the visual field toward the board; peripheral distractions are suppressed
- *Sovereign* — nothing feels tentative; every effect is confident and fully realized

**Energy level**: Peak. The environment should feel like it is sustaining a plateau, not still climbing. Frenetic energy here would be wrong — peak flow is not chaotic; it is maximally ordered at high speed.

**Visual cues**: Background warm glow unmistakable. Screen-edge pulse present (absent in all lower states). Particle trails brighter with longer decay (up to 0.8 seconds). Combo meter fully bright. The combination of three simultaneous signals (background warmth + edge pulse + bright trails) identifies this state unambiguously.

> `[IMAGE: Reference target — board fully lit with warm gold ambient. Screen edges show faint gold vignette pulsing. Recent cell fills visible as bright-to-faint decay trails. Combo meter fully illuminated. Atmosphere reads as "performance at full capacity" — warm, fast, clean.]`

---

### 2.5 Area Clear Event (Row / Column / Box Completed)

**Primary emotion**: The sharp pleasure of a click. Not a sustained emotion — a punctuation mark, not a sentence. Brief, specific, and unmistakable.

**Lighting character**: A brief expansion of the existing background fill color — the warmth present at the moment of the clear intensifies by 30–40% for 0.2–0.3 seconds, then returns to the current state level. The clear flash inherits the current combo temperature and amplifies it — no new hue introduced.

**Atmospheric descriptors**:
- *Percussive* — visual event has attack and decay, not sustain; it lands and releases
- *Proportionate* — a single-row clear is visually smaller than a box clear; magnitude is variable but vocabulary is consistent
- *Additive* — the flash adds to the existing visual state rather than replacing it
- *Clean* — after decay, the visual environment returns to exactly the state it was in before the clear
- *Legible* — even at peak combo, the clear flash must be distinguishable; the cleared area briefly highlights to confirm *which* area cleared

**Energy level**: Burst within arc. A spike within the current state, not a state unto itself.

**Visual cues**: Cleared cells briefly highlight (cool-white at low combo, warm-gold at peak). Particle burst radiates from cleared area (8–12 particles for a single clear, resolved within 0.5 seconds). Combo meter receives a visible pulse. Nothing persists after 0.6 seconds.

> `[IMAGE: Reference target split panel: (left) single-row clear at low combo — cool white burst from a horizontal row of cells, minimal particle count, board returns to neutral within half a second. (right) single-box clear at peak combo — warm gold burst, slightly larger particle radius, same rapid decay. Both panels emphasize the "before and after" being nearly identical — the event is legible but non-disruptive.]`

---

### 2.6 Multi-Clear Cascade (2+ Areas Cleared Simultaneously)

**Primary emotion**: The involuntary gasp of witnessing something exceptional. This is distinct from the satisfaction of a single clear — a cascade is rare, and the emotional response is more surprised delight than earned pleasure.

This is the one moment where the "Neutral base, vibrant events" principle permits real color and real density.

**Lighting character**: Cascade events are the only moment where the background fill is permitted to reach meaningful saturation (40–55% saturation, still controlled). The temperature during a cascade pushes fully to warm gold regardless of current combo state — a universal override, not state-dependent amplification. Duration: 0.4–0.6 seconds of peak, then a 0.8–1.2 second return curve to the current combo state level.

**Atmospheric descriptors**:
- *Explosive* — visual onset is fast (under 100ms to full brightness); it erupts, not ramps
- *Resonant* — unlike the percussive single-clear, a cascade has a brief sustain before decay; it rings rather than clicks
- *Chromatic* — color saturation reaches its session maximum here; the contrast with the rest of the game's desaturated aesthetic makes it feel extraordinary
- *Earned* — the cascade is visually exceptional because cascades are mechanically rare; the magnitude communicates rarity
- *Resolving* — the decay returns deliberately to the current state; the cascade passes through and clears

**Energy level**: Exceptional spike. Exceeds the normal peak combo arc line briefly, then settles back.

**Visual cues**: Multiple cell-group highlights fire simultaneously. Particle burst 20–35 particles, wider radius, 0.8-second decay. Background fill saturation visibly exceeds any other game state moment. If a technique banner fires after a cascade, the cascade visual must complete its peak before the banner appears.

> `[IMAGE: Reference target — board at mid-combo state showing two simultaneously highlighted areas (one row, one box) with overlapping warm-gold particle bursts. Background fill at its maximum permitted saturation. Board remains readable through the burst. A frame at 0.8 seconds later shows the scene already returning to the mid-combo baseline.]`

---

### 2.7 Technique Recognition (Technique Banner Fires)

**Primary emotion**: The moment of being named. The specific quality of someone saying the exact right word for something you just did — not the achievement itself, but the *recognition* of the method.

**Lighting character**: Technique banners do not alter the background fill or ambient state. All technique recognition lighting is localized to the banner element: bright interior fill (near-white at 90% brightness) against a very dark semi-transparent backing (15–20% brightness, 70–80% opacity). No glow bleeds into the surrounding board area. The surrounding scene continues in its current combo state uninterrupted.

**Atmospheric descriptors**:
- *Declarative* — the banner has the quality of an announcement; bold, italic, compressed, confident
- *Brief* — visible duration 1.2–1.8 seconds; it says its word and exits
- *Peripheral* — lower-third placement ensures readability without demanding attention shift from the board
- *Non-disruptive* — the game does not pause, slow, or dim when a banner fires
- *Precise* — the specific technique name matters; vague labels ("Nice!") would fail this state's emotional target

**Energy level**: Acknowledgment pulse within the current state. The banner does not change energy level; it annotates it.

**Visual cues**: Banner slides in from the left (or fades from bottom-left) at lower-third position. Entry animation fast (0.1–0.15s ease-out), hold still, exit fast fade (0.2s). Large bold-italic text is the only element in the game's visual vocabulary with these properties — the banner is unambiguous.

> `[IMAGE: Reference target — game board at mid-combo state with a technique banner in the lower third reading a fictional technique name (e.g., "NAKED PAIR"). Banner text is bold italic, near-white on a very dark semi-transparent backing. The board above remains fully active. The banner occupies roughly the bottom 12–15% of screen height.]`

---

### 2.8 Puzzle Transition (Brief Bridge Between Puzzles)

**Primary emotion**: The breath between waves. Not relief — the run is not over. Not anticipation — the player is not starting fresh. Awareness that a segment completed, and immediate forward projection.

**Lighting character**: Board clears and background briefly returns toward the neutral cool-blue before the new puzzle fades in. The return toward neutral is fast (0.3–0.5 seconds) and does not fully reach the Home/Menu baseline — the combo state carries through. This is a relative cooling, not a full reset.

**Atmospheric descriptors**:
- *Momentary* — if the player is in flow, they should barely notice it as a state change
- *Continuous* — the visual arc does not restart; the combo meter does not visually reset to zero
- *Clean* — the old puzzle board exits cleanly; no visual debris persists into the new puzzle
- *Bridging* — the brief cool dip marks the join between two pieces of music without silencing either
- *Unsentimental* — no lingering on the cleared puzzle; the visual system already moved on

**Energy level**: Momentary dip then immediate continuation. The arc has a 1–2 second valley before climbing back to the current combo state.

**Visual cues**: Board cells fade out simultaneously (not one at a time). Very brief full-screen desaturation pulse (0.15–0.2 seconds). New puzzle fades in over 0.3–0.4 seconds. Total transition time: 1.0–1.5 seconds. Speed communicates urgency and continuity.

---

### 2.9 End-of-Run / Results Screen (Post-Run Reflection)

**Primary emotion**: The stillness after performance. The musician who has just walked offstage — the intensity does not vanish, it settles. Earned quiet that is categorically different from the pre-run quiet of the menu. The difference must be visible.

**Lighting character**: Background settles at a warm, low-saturation gold that is slightly brighter and warmer than peak-combo state but calmer — embers, not fire. Color temperature: 42–48° hue, 20–28% saturation, 22–28% brightness. No pulsing, no reactivity, just a held warmth. Warmth is calibrated to the session's actual peak: a modest run gets modest warmth, a peak run gets the full settled-gold.

**Atmospheric descriptors**:
- *Settled* — the reactive quality of the in-game environment is gone; the screen has transitioned from an active instrument to a reflective surface
- *Warm* — warmth is ambient and uniform, not directional; it fills the screen evenly; the light source, conceptually, is the run itself
- *Spacious* — the results layout has more whitespace than any in-game state; numbers and labels breathe
- *Legible* — all information at low-energy, high-readability contrast; no particles or glows competing with data
- *Honest* — the visual warmth is calibrated to the run's actual performance ceiling; the screen tells the truth about what just happened

**Energy level**: Contemplative. The lowest active energy level after the menu — but categorically different from the menu's "not yet started" quality. This quiet is earned.

**Visual cues**: Background warm (not cool-neutral like menu). Board, if visible, shown fully completed rather than empty. All particles from the run's final moment fully resolved. Touch targets are soft navigation elements (replay, home, share), not gameplay.

> `[IMAGE: Reference target split panel: (left) menu screen — cool blue-grey, near-zero saturation, sparse layout, unlit combo meter, board blank. (right) results screen — warm amber-gold, low saturation but palpably warm, spacious score layout, no active particles. The contrast between these two "quiet" states should be unmistakable: one is cool and waiting, the other is warm and at rest.]`

---

### Cross-State Continuity Rules

1. **Temperature never jumps.** All background color temperature changes are interpolated, never cut. Minimum transition duration: 0.3 seconds for in-game state changes, 0.5 seconds for screen transitions.

2. **The board is always readable.** At no point does particle density, glow intensity, or background luminance reduce grid legibility. If a mobile device test shows legibility reduction at any state, the effect intensity is reduced — not the contrast of the board.

3. **Effects are always caused.** No visual event fires without a direct player action or mechanical trigger. No random ambient particles, no idle animations on cells, no decorative loops not tied to game state.

4. **Combo loss cools the room.** When a combo breaks (timer expiry or incorrect placement), the background temperature returns toward cool-neutral proportional to the lost combo depth. The cooling is not punishing in tone — it is honest. The warmth was borrowed from performance; when performance stops, the warmth releases.

5. **Each state must be distinguishable from its neighbors.** Low combo and mid combo must look different. Mid combo and peak combo must look different. Test: take a screenshot at any game state — it must be immediately classifiable. If two adjacent state screenshots are indistinguishable, the transitions between them need more range.

---

## 3. Shape Language

### The Central Principle

**"Still shapes hold the puzzle; moving shapes celebrate it."**

Every geometric decision in *Sudoku Rush* falls into one of two states: at-rest geometry (the board, the glyphs, the UI chrome) or in-motion geometry (particles, animations, feedback bursts). At-rest shapes are minimal and subordinate — they disappear into habit so the player can think. In-motion shapes are expressive and momentary — they reward the player's action and then release. If a shape choice does not clearly belong to one state, it does not belong in the game.

---

### 3.1 Grid Shape Design

The 9×9 sudoku grid is the game's primary surface. Its shape language must communicate a single message before any interaction occurs: *"This system is knowable."*

#### Line weight hierarchy

The grid uses exactly three line weights, each encoding a different level of structural authority:

| Level | Structure | Weight | Purpose |
|---|---|---|---|
| 1 | Outer border | Heaviest (3–4px at 1x) | Contains the whole system; grounds the board |
| 2 | 3×3 box boundaries | Medium (2px at 1x) | Reveals the puzzle's meta-structure |
| 3 | Cell boundaries | Lightest (0.75–1px at 1x) | Subdivides without asserting — reads as texture at small sizes |

These three weights must remain perceptually distinct on all target screen sizes. On the smallest supported width (375pt), cell boundaries may approach the rendering minimum — verify at physical device pixel density. Never introduce a fourth line weight; the hierarchy must remain readable without conscious interpretation.

#### Corner treatment

All grid corners — outer border, box boundaries, and cells — use **sharp (0px radius) corners**. Rounded corners on a sudoku grid create ambiguity: softness implies approachability, but it also implies imprecision. The grid is a formal system. Its corners are square. This also provides the maximum contrast surface against which circular particle effects will later read.

The *only* exception: the active cell highlight (see §3.6) may use a very subtle inner radius (1–2px) to soften selection without adding color — enough to read as "selected" rather than "drawn," not enough to read as "soft."

#### Box vs. cell visual treatment

Box boundaries carry slightly more visual weight than cells but remain below the outer border. In addition to line weight, the 3×3 box structure may be reinforced through a near-imperceptible fill tint — the same value, shifted by 2–3% luminance against the base neutral. This creates a quilted surface that reads as a single coherent board, not 81 separate cells.

Under flow states (warming amber-gold base temperature), the box tint contrast may increase proportionally — the board's hidden structure becomes more visible as the player's mastery grows.

**Pillar alignment**: Clean by Default (reduces visual noise), Depth is Earned, Not Taught (the 3×3 structure clarifies at performance, not onboarding).

> `[IMAGE: Grid at three zoom levels — full board, single box, single cell — annotated with line weights and fill tint percentages]`

---

### 3.2 Number Glyph Style

Number glyphs are the game's content. They are not decoration. Every glyph state communicates a semantic meaning, and those meanings must be distinguishable without relying on color alone.

#### Typeface personality

The typeface must read as **geometric and monolinear** — strokes of consistent weight, constructed from circles and straight lines, not drawn from calligraphic tradition. Think of the geometric sans-serif genre rather than humanist sans-serifs. Humanist letterforms carry warmth and personality; geometric forms carry system-precision.

Specific requirements:
- **Moderate x-height** — not extreme (very low = editorial; very high = childlike)
- **Tabular figures** — all digits occupy the same horizontal advance so they visually anchor within cells without shifting
- **No decorative terminals** — cuts should be horizontal or angled mechanically, never calligraphic
- **Numerals evaluated solely on 1–9** — Latin character quality is irrelevant to this game

#### Glyph state vocabulary

Each semantic state uses shape properties — weight, scale, opacity, and treatment — not color.

| State | Weight | Scale | Opacity | Treatment |
|---|---|---|---|---|
| Given digit (pre-filled) | Bold / Heavy | 100% | 85–90% | No decoration; anchored, immovable |
| Player-placed digit | Regular / Medium | 100% | 100% | Clean; the freshest mark on the board |
| Pencil mark | Light / Thin | 44–50% cell height | 60–70% | Small, grouped, subordinate to main digits |
| Active input (pending) | Medium | 105–108% | 100% | Subtle scale-up; "being typed" feeling |

Given digits use a heavier weight to communicate immutability — they are the puzzle's skeleton, not the player's contribution. The weight difference must be visible at a glance without feeling like two different typefaces.

Pencil marks occupy a 3×3 micro-grid within each cell (positions 1–9), echoing the macro-grid's geometry: same corner treatment (sharp), same implicit structure.

> `[IMAGE: Single cell shown in all four states — given, player-placed, pencil-marked (3 marks), active input — annotated with scale and weight differences]`

#### Glyph as event anchor

When a digit is placed, the glyph participates in the placement pulse (§3.5). The glyph does not move — it lands and holds. The effect radiates from the glyph's bounding box. This keeps the content legible through the event and reinforces the **Every Hit Lands** pillar: the digit is the hit, not a byproduct of it.

---

### 3.3 Input Pad Design

The number input pad is a 3×3 arrangement of digit buttons (1–9) — a direct mirror of the sudoku 3×3 box structure. This geometric relationship is intentional and must be preserved.

#### The echo principle

The input pad's grid must visually echo the game board's box grid at a smaller scale. Same corner treatment (sharp). Same line weight hierarchy (compressed to two levels: outer border, cell boundary). Same proportional internal spacing.

**What the pad must not do**: It must not look like a numpad, a calculator, or a keyboard. Those are input devices with affordances built around cursor movement and data entry. The pad is a performance control surface — closer in spirit to a drum pad than a keyboard. Its geometry should suggest a spatial layout (digits occupy positions, like cells) rather than a sequential layout (digits occupy a queue).

#### Size and touch target

On a 375pt screen, the pad must provide minimum 44×44pt touch targets per button, per Apple HIG. At the standard 9-button layout, this means the pad occupies approximately 132–148pt of width. The pad should be visually grounded toward the bottom third of the screen.

Padding within each pad cell should be generous — the digit reads as floating in space, not squeezed into a container. The container is subordinate to the number.

#### State contrast with the board

At rest, the input pad uses the same near-neutral base palette as the board but may use a slightly warmer or lighter neutral to separate it as a distinct zone — control surface vs. playing field. Under active events, the pad may receive a much-attenuated echo of the board's hue shift (10–15% of the board's saturation gain) — enough to feel like they are in the same performance, not enough to distract from the board.

> `[IMAGE: Input pad annotated — touch target boundaries, internal proportions, comparison to single 3×3 box from the main board]`

**Pillar alignment**: Flow Over Friction (removal of interface unfamiliarity), Every Hit Lands (the pad is a performance instrument, not a form).

---

### 3.4 UI Component Shape Grammar

Combo meter, timer, and score display are information displays — not gameplay surfaces. Their shape grammar must clearly signal this distinction.

#### The separation rule

Board elements use **contained geometry** — shapes that imply enclosure, system, and field. UI chrome elements use **open or linear geometry** — shapes that imply measurement, readout, or progress.

| Component | Shape grammar | Rationale |
|---|---|---|
| Combo meter | Horizontal fill bar, rounded cap ends only | Linear motion communicates accumulation; rounded caps soften the HUD layer |
| Timer | Numeric readout only; no decorative border | The number is the information — any enclosing shape competes with it |
| Score display | Numeric readout; wide tracking (letter-spacing) | Wide tracking slows reading speed — score is glanced, not read fast |
| Technique banner | Full-width rectangular strip, sharp corners | Echoes the board's formal geometry; the banner is a system announcement, not decoration |

The technique banner deliberately borrows the board's formal corner treatment (sharp). It should feel like the game's system issuing a notation — an official mark on the session.

UI chrome uses the same typeface family as digit glyphs but at heavier weights and sizes that place them clearly outside the grid's typographic scale. A player must never mistake a score digit for a cell digit.

> `[IMAGE: Full-screen composition showing board + chrome — annotated to show which shapes use "contained" vs. "open" grammar]`

**Pillar alignment**: Clean by Default (clear semantic separation between information and gameplay), Flow Over Friction (chrome reads without conscious attention).

---

### 3.5 Particle and Effect Shape Vocabulary

Particle effects are the only expressive domain in *Sudoku Rush*. Their shape vocabulary is scaled precisely to the event's score value.

#### Base shape vocabulary

All particle forms derive from two primitive categories:

1. **Circular soft forms** — blurred or feathered discs, halos, and ring pulses. Convey energy, warmth, and diffusion. Primary particle type.
2. **Hard-edged geometric fragments** — thin diamond slivers, squares, and elongated rectangles. Convey precision and impact. Secondary accents within larger events.

**No organic shapes** (blobs, irregular forms, brush strokes) — the visual world is constructed from clean geometry.

**No trailing streaks as primary shapes** — streaks imply motion path. Sudoku cells do not move. Effects radiate, pulse, and dissipate; they do not travel across the board.

#### The three event scales

**Scale 1 — Digit placement pulse (small)**

Triggered: Single correct digit placed.

Shape vocabulary: A tight circular ring pulse expanding from the cell center, fading as it reaches the cell boundary. 1–3 small hard-edged fragments ejected radially, dissipating within the cell's immediate neighbors. Duration: 200–300ms.

The effect must not leave the visual neighborhood of the placed cell.

> `[IMAGE: Cell-level pulse diagram — ring radius at 0ms, 100ms, 200ms; fragment ejection vectors]`

**Scale 2 — Area clear (medium)**

Triggered: Completion of a row, column, or 3×3 box.

Shape vocabulary: A sweep or flash along the completed line or box boundary — a linear highlight that traces the cleared structure's shape. Circular halos pulse at the intersecting corners. 6–12 hard-edged fragments scattered within the cleared region's bounding box. Duration: 400–500ms.

The linear sweep echoes the grid's own line geometry — the effect reads as the grid briefly illuminating its own structure. This teaches the grid's anatomy through celebration.

> `[IMAGE: Row clear sweep — line trace animation, corner halo positions, fragment scatter zone]`

**Scale 3 — Multi-clear cascade (exceptional)**

Triggered: Multiple simultaneous clears.

Shape vocabulary: Layered rings expanding outward from the cascade's origin cell — multiple concentric pulses at staggered delays (100ms apart). A screen-edge vignette pulse that momentarily brightens the frame border. Larger hard-edged fragments reaching up to 40–60% of board width. Duration: 600–900ms.

At this scale, effects may briefly overlap cell boundaries. The board's structure becomes a stage, not just a field.

> `[IMAGE: Cascade event — concentric ring timing diagram; fragment reach zones mapped to board; vignette pulse annotated]`

#### Directionality

All effects radiate outward from the triggering event. Effects never move toward the player's hand position on screen — this prevents visual conflicts with the input pad and natural thumb positioning on mobile.

#### Shape and color interaction

Effect color scales with the game's current mood temperature. A cascade during high-flow amber-gold produces a warm gold-tinted burst. The same event in a cool opening session produces a cooler, more restrained pulse. Shape vocabulary is the constant; color is the variable.

**Pillar alignment**: Every Hit Lands (each event has a distinct, sized visual response), Clean by Default (effects are momentary and dissipate completely — they never accumulate visual noise).

---

### 3.6 Shape Hierarchy and Selection States

The player must always know three things without reading anything: where they are on the board, what is placed, and what is still open. Shape hierarchy — not color — is the primary tool.

#### The resting hierarchy (no color active)

From most visually prominent to least:

1. **Active cell** — selected; inner radius treatment + luminance lift. No color.
2. **Player-placed digits** — 100% opacity, regular weight. The player's active contribution.
3. **Box fill tint** — the quilted surface tint (§3.1) as a mild structural cue.
4. **Given digits** — heavier weight but 85–90% opacity, signaling background structure.
5. **Cell boundary lines** — texture-weight; present but not demanding.
6. **Pencil marks** — smallest, lightest, most subordinate.

#### Making the active cell feel selected without color

The active cell solution uses three simultaneous cues below the threshold of a color event:

- **Inner radius** (1–2px): creates a visible distinction from the sharp-cornered unselected state
- **Luminance lift** (2–4%): separates the cell from its neighbors without introducing saturation
- **Scale treatment**: the in-cell glyph at 105% gives a feeling of the digit being "held" or "ready"

Together these three sub-threshold cues produce a clear selection state. Any single cue alone would be ambiguous; the three together are unambiguous without triggering the visual weight of a color event.

> `[IMAGE: Side-by-side grid showing: unselected cell, active cell (no digit), active cell with player digit pending — annotated with inner radius, luminance delta, and scale values]`

**Pillar alignment**: Flow Over Friction (instant orientation), Clean by Default (selection is clear without visual noise), Depth is Earned, Not Taught (the hierarchy is intuitive — players discover rules through visual weight, not tutorials).

---

### Shape Language Summary

| Decision | Value | Pillar |
|---|---|---|
| Central principle | Still shapes hold the puzzle; moving shapes celebrate it | All four |
| Grid corner treatment | Sharp (0px radius) everywhere | Clean by Default |
| Line weight levels | Exactly three (outer, box, cell) | Clean by Default |
| Active cell selection | Inner radius + luminance lift + glyph scale | Flow Over Friction |
| Typeface personality | Geometric monolinear, tabular figures | Clean by Default, Every Hit Lands |
| Input pad echo | Mirrors 3×3 box geometry exactly | Flow Over Friction |
| Effect scale 1 | Tight ring + 1–3 fragments, cell-contained | Every Hit Lands |
| Effect scale 2 | Line sweep + corner halos + 6–12 fragments | Every Hit Lands |
| Effect scale 3 | Concentric rings + screen vignette + far fragments | Every Hit Lands |
| Organic shapes in effects | Prohibited | Clean by Default |
| Trailing streaks | Prohibited | Clean by Default |
| UI chrome geometry | Open/linear (contrast with contained board geometry) | Clean by Default, Flow Over Friction |

---

## 4. Color System

### Primary Palette

The board's visual language rests on six named colors. Each exists to answer a specific player question — not to decorate.

> `[IMAGE: Swatch strip showing all six colors in order, labeled with role names and hex values, on a dark near-neutral background matching the board rest state.]`

**Base-00 — Board Night**
HSB: 213°, 12%, 14% | Hex: `#1E2229`
The resting board background. This is the visual anchor against which all other colors are measured. It reads as "neutral" — neither warm nor cold, neither active nor dead. At rest, it asks nothing of the player. All contrast ratios for digit legibility are calculated against this value as the darkest background case. It does not shift with combo state; it is permanent.

**Base-01 — Cell Surface**
HSB: 215°, 10%, 20% | Hex: `#2D333D`
The fill of individual cells at rest. Slightly lighter than Board Night to give cells visible separation without a hard border. Given digits live on this surface. The gap between Base-00 and Base-01 (roughly 6% luminosity delta) is the thinnest grid separation the design can sustain while still reading cleanly at 375px screen width. Do not compress this gap.

**Text-Primary — Chalk**
HSB: 210°, 6%, 92% | Hex: `#E8EAEC`
Given digits and all locked board numbers. Near-white with a faint cool bias — pure white on Base-01 reads as sterile and slightly aggressive on OLED panels. The 6% saturation toward cool removes that harshness while maintaining contrast ratio of approximately 11:1 against Base-01 — well above WCAG AA. This value must not warm with combo state. Digit legibility is a hard requirement, not an aesthetic preference.

**Text-Secondary — Fog**
HSB: 210°, 8%, 55% | Hex: `#828C96`
Player-entered candidates (pencil marks) and secondary UI labels. Contrast against Base-01 is approximately 4.8:1 — just above WCAG AA minimum. Candidates are information the player holds in working memory, not instruction from the board. They should be present but not competing with confirmed digits.

**Signal-Gold — Clear**
HSB: 44°, 88%, 96% | Hex: `#F5C70A`
Area clear confirmation. At 88% saturation, it exceeds the normal game-state saturation ceiling — this is permitted because area clears are discrete events (200–400ms flash), not sustained states. Gold is semantically unambiguous in score-attack games: it means "you scored something significant." Reserved exclusively for area clear events. No other game element may use this hue range (35–50° at saturation above 60%).

**Signal-Blue — Technique**
HSB: 200°, 90%, 95% | Hex: `#0ADAF5`
Technique banners (naked pair, hidden triple, etc.). Electric cyan-blue. This is the "recognition" color — it tells the player "the game saw what you just did and named it." Its hue sits 160° away from Signal-Gold on the wheel, providing maximum separation. Reserved exclusively for technique identification banners.

> `[IMAGE: Color wheel diagram showing Signal-Gold and Signal-Blue at opposite positions, with the warm combo arc (35–55° hue band) and cool technique anchor annotated.]`

---

### Semantic Color Vocabulary

Color in this game is a grammar, not a decoration. Each element of the grammar has one owner. Semantic overlap causes confusion; confusion breaks flow.

| Color / Range | Owner | Meaning | Reserved? |
|---|---|---|---|
| Near-neutral (0–15% sat) | Board at rest | "Nothing is happening — read the board" | Yes — no effects in this range |
| Warm amber arc (35–55°, 15–55% sat) | Combo state and background temperature | "You are in a scoring run — maintain it" | Yes — no UI chrome in this hue range |
| Signal-Gold (44°, 88%+ sat) | Area clear flash | "You cleared a row/column/box" | Yes — strictly clear events only |
| Signal-Blue (200°, 88%+ sat) | Technique banner | "You executed a named technique" | Yes — strictly technique identification |
| Difficulty accent (see §4.3) | Combo meter and difficulty framing | "This is the tier you are playing" | Scoped — only active during a session at that tier |
| Cascade red-orange (18–25°, 40–55% sat) | High-combo cascade overlay | "You have reached peak flow — this is the maximum" | Yes — saturation ceiling; nothing may exceed it |
| Pure white or 0° neutral | Error / warning states (future) | Reserved — do not use casually | Not yet assigned |

**Three production rules that enforce this grammar:**

1. **Saturation gating**: Normal board state operates below 15% saturation. Effect colors (Signal-Gold, Signal-Blue) only exist during their trigger window. No persistent UI element may sit above 20% saturation.

2. **Temperature ownership**: The 35–55° warm arc belongs to the game's scoring momentum system. No UI button, icon, or label may use amber or gold at rest. When the player sees warmth, they should feel it as score pressure — never as decoration.

3. **Cool = Information, Warm = Momentum**: Signal-Blue lives in the cool zone not by coincidence but by function. Information the game gives you (technique names, labels) is cool. Momentum you are generating is warm. Players internalize this grammar within a session without being told.

---

### Difficulty Tier Accent Palettes

Each difficulty tier carries a single accent identity. The accent drives the combo meter's color climb and frames the session. Tiers must be visually distinct from each other and from the two reserved signal colors.

The combo meter climb follows a consistent logic across all tiers: the accent starts desaturated and dim at low combo, reaches full saturation at mid combo, then bleeds toward the cascade arc at peak. Peak flow looks the same across tiers because the experience of peak flow is universal.

> `[IMAGE: Four horizontal strips, one per tier, each showing the combo meter color ramp from rest (leftmost, desaturated) through mid (saturated accent) to peak (cascade approach). Labeled with tier name and key hex values at five stops.]`

**Easy — Jade**
- Primary accent: HSB 158°, 55%, 72% | Hex: `#53B888`
- Meaning: Fresh, approachable, verdant. Green reads as "safe to proceed" and aligns with entry-level confidence.
- Combo ramp:
  - 1× (rest): `#435549` — near-neutral; barely tinted
  - 2–3× (building): `#578C71` — unmistakably green, readable
  - 4–6× (mid): `#53B888` — full accent, vivid jade
  - 7×+ (peak): `#47CC6E` — shifts slightly yellow-green, begins approaching cascade warm-shift
- Beyond the combo meter: Faint jade tint on Easy difficulty card; session borders on results screen carry the accent at 25% opacity.

**Medium — Cobalt**
- Primary accent: HSB 218°, 72%, 82% | Hex: `#3D7BD6`
- Meaning: Confident, structured, analytical. Blue communicates "you know what you're doing."
- Combo ramp:
  - 1× (rest): `#3E4653` — near-neutral; barely distinguishable from board
  - 2–3× (building): `#537DAA` — clearly blue, measured
  - 4–6× (mid): `#3D7BD6` — full cobalt
  - 7×+ (peak): `#3347E6` — deepens toward electric violet, signals escalation
- Separation note: Medium-Cobalt (218°) sits 18° away from Signal-Blue (200°). Mitigate by ensuring technique banners appear at the top of screen, spatially separated from the combo meter. Hue separation + spatial separation together prevent confusion.

**Hard — Amber**
- Primary accent: HSB 32°, 85%, 90% | Hex: `#E8820D`
- Meaning: Pressure, precision, heat. Orange-amber is the color of a deadline. Operates below 35° so it does not collide with Signal-Gold area clears.
- Combo ramp:
  - 1× (rest): `#4A3D2D` — near-neutral, brown-tinted
  - 2–3× (building): `#B37340` — visible amber, contained energy
  - 4–6× (mid): `#E8820D` — full amber, unmistakable urgency
  - 7×+ (peak): `#F25C0A` — burns into orange-red, cascade approach
- Separation note: Hard-Amber (32°) and Signal-Gold (44°) are 12° apart. Disambiguation: Signal-Gold only fires for 200–400ms as a flash; Hard-Amber is sustained. Signal-Gold must always be brighter (value 96%) than Hard-Amber (value 90%) at equivalent saturation to maintain luminance separation.

**Expert — Crimson Violet**
- Primary accent: HSB 290°, 70%, 75% | Hex: `#8A2DB8`
- Meaning: Mastery, intensity, the edge of control. Red-violet carries the urgency of red but the depth of purple, signaling something beyond ordinary difficulty.
- Combo ramp:
  - 1× (rest): `#362040` — near-neutral, barely violet
  - 2–3× (building): `#6B3680` — clearly purple, focused
  - 4–6× (mid): `#8A2DB8` — full crimson-violet, commanding
  - 7×+ (peak): `#CC1FA3` — hot magenta-purple, feels dangerous; cascade is imminent
- Separation: Expert-Violet (290°) has over 90° of hue separation from every other tier accent and from both signal colors — the clearest tier from a colorblind-safety standpoint.
- Beyond the combo meter: On the Expert difficulty card, a very faint violet vignette at screen edges signals "this is different territory."

> `[IMAGE: Four difficulty cards side-by-side showing the selection screen treatment — tinted card face, session-border color, and a small combo meter preview showing the color ramp from 1× to 7×.]`

---

### Colorblind Safety

This game uses color as a primary communication channel. Color alone cannot be the only carrier for any signal.

> `[IMAGE: Simulation grid showing all four tier accents and both signal colors as they appear under deuteranopia, protanopia, and tritanopia filters. Highlight pairs that become perceptually identical.]`

**Deuteranopia (red-green, ~8% of males)**

| Risk | Pair at risk | Backup cue |
|---|---|---|
| Easy-Jade vs. Hard-Amber | Both shift toward similar yellow-brown | Tier is always labeled in text (EASY / HARD word mark on combo meter frame) |
| Signal-Gold vs. Hard-Amber | Area clear flash and active Hard combo could be indistinguishable | Area clear adds a radial outward pulse animation + dedicated audio trigger. Animation is the primary signal |
| Easy-Jade peak vs. board rest | Green-to-yellow shift may read close to warm board background | Peak combo also triggers particle density increase — particle count is the backup cue |

**Protanopia (red weakness, overlaps deuteranopia in risk profile)**

| Risk | Pair at risk | Backup cue |
|---|---|---|
| Hard-Amber peak vs. cascade | Orange-red and warm tones desaturate toward yellow-grey | Cascade adds full-screen vignette pulse — spatial scale change is unmissable |
| Expert-Violet peak vs. Expert mid | Magenta can shift toward yellow-grey, collapsing the ramp | Combo meter fill level (bar quantity) is independent of color — always visible |
| Signal-Blue | Unaffected — cyan-blue is preserved in protanopia | N/A |

**Tritanopia (blue-yellow, very rare)**

| Risk | Pair at risk | Backup cue |
|---|---|---|
| Signal-Gold vs. neutral background | Yellow shifts to pink-red on now-greenish background | Radial pulse animation + audio are primary signals — same coverage as deuteranopia |
| Signal-Blue vs. Easy-Jade | Both shift toward similar green tones | Technique banners carry icon shape + text label — color is mood, text is meaning |
| Medium-Cobalt vs. Easy-Jade | Both may appear as similar mid-green | Text word mark on combo meter frame is primary tier identifier |

**Universal backup cues — required at launch, not optional:**

1. All tier identifiers: Text word mark (EASY / MEDIUM / HARD / EXPERT) on the combo meter frame
2. Area clear event: Radial cell-outward pulse animation + dedicated audio trigger
3. Technique banners: Icon shape + text label (Signal-Blue is mood; text is communication)
4. Combo level: Bar fill quantity (always legible independent of color)
5. Cascade state: Full-screen vignette pulse animation (unmissable regardless of hue)

---

### Dark/Light Theme Support

The game was designed for dark-on-OLED. A light theme, if offered as an accessibility option, requires exactly seven token substitutions — not a full retheme.

**Governing Principle**: Semantic colors (Signal-Gold, Signal-Blue, cascade arc, difficulty accents) must preserve their hue identity in both themes. Hue is identity; value and saturation are adaptable.

> `[IMAGE: Side-by-side comparison of a single game board cell in dark theme vs. light theme variant, showing both digit legibility and a combo state effect overlay.]`

**Seven token substitutions for light theme:**

| Token | Dark Theme | Light Theme | Reason |
|---|---|---|---|
| Board Night | `#1E2229` (14% brightness) | `#EDF0F2` (94% brightness) | Full inversion — light paper background. Hue preserved. |
| Cell Surface | `#2D333D` (20% brightness) | `#DCE2EA` (88% brightness) | Slightly darker than background to maintain cell separation |
| Text-Primary (Chalk) | `#E8EAEC` (92% brightness) | `#1F2733` (15% brightness) | Near-black with cool bias — same cool character, opposite luminosity |
| Text-Secondary (Fog) | `#828C96` (55% brightness) | `#606E7A` (42% brightness) | Darkened to maintain 4.5:1 on light background |
| Signal-Gold | `#F5C70A` (96% value) | `#CCA408` (80% value) | Gold on white is invisible at full value — drop to 80%. Hue and saturation preserved. |
| Signal-Blue | `#0ADAF5` (95% value) | `#199FBA` (65% value) | Cyan on white needs value reduction. Hue preserved. |
| Combo background arc | Warms from dark cool to amber | Cools from light neutral to warm cream | Direction reverses — the screen warms toward cream rather than brightening from dark. Amber hue (35–50°) preserved. |

**Values that never change:** All difficulty accent hues, Signal-Gold hue (44°), Signal-Blue hue (200°), cascade saturation ceiling (55%), all combo ramp hue progressions. Minimum viable light theme = exactly these seven substitutions.

---

### What This Means in Practice

- **Digits must always pass contrast independently of combo state.** Verify Text-Primary (`#E8EAEC`) against the warmest background state (cascade peak, approximately HSB 48°, 55%, 22%) before declaring implementation complete. Target minimum ratio: 4.5:1. If ratios fall below 4:1 during the cascade effect, darken the cascade peak background floor to HSB 48°, 45%, 18%.

- **No UI chrome in the warm hue band.** Buttons, icons, labels, and navigation elements must not use any hue between 25° and 55° at saturation above 15%. This range is semantically owned by the scoring momentum system. If a UI element resembles the combo warm-up arc, it will mislead the player about game state.

- **Difficulty tiers are established once, not throughout.** The accent palette appears during difficulty selection, on the combo meter frame, and on the results screen. It does not invade the board grid, digit colors, or event signals.

- **Area clear gold has a duration budget.** The flash window is 200–400ms — this is a semantic contract, not a style guideline. If gold persists longer, players will interpret it as a sustained state rather than a discrete reward signal. Implement with an explicit animation curve that returns to below 15% saturation within 400ms. The radial pulse animation may run to 600ms; the color component must complete within 400ms.

- **The cascade saturation ceiling (55%) is the system maximum.** If any element during a session ever exceeds 55% saturation, the cascade loses its identity as "the peak." Treat 55% as a hard ceiling in asset authoring. Any effect that approaches this ceiling requires explicit sign-off before shipping.

- **Colorblind backup cues are day-1 requirements, not a post-launch patch.** The five universal backup cues (text labels, radial animation, icon shape, fill quantity, vignette animation) must be implemented simultaneously with the color system. Color-only implementation is an incomplete implementation.

---

## 5. Character Design Direction

### 5.1 The Absence of Characters as a Design Decision

Sudoku Rush has no characters. This is not a scope reduction — it is a pillar decision.

In games with avatar characters, the player watches someone succeed. In Sudoku Rush, there is no proxy self. The player *is* the reasoning. When a technique fires and Signal-Gold floods a column, that response belongs directly to the player's deduction — no character animation mediates the satisfaction. This fulfills pillar (1) **Every Hit Lands** in its most literal sense: the board responds to the player's mind, not to a character's gesture.

The absence of figurative imagery also enforces pillar (4) **Clean by Default**. No mascots, no avatar portraits, no idle animations competing for attention during board states. Visual complexity is reserved as currency for payoff moments. When the board is calm, it is purely calm.

**Production rule:** No figurative illustration, character art, avatar sprites, or anthropomorphized elements may appear anywhere in the game — not on loading screens, not on achievement badges, not in tutorial panels. Abstraction only.

---

### 5.2 App Icon and Brand Identity

The app icon must compress the game's entire visual identity into a 1024 × 1024 px canvas. It communicates to a potential player in approximately 400ms on a store shelf.

**Visual direction:** A single bold digit — the numeral **9** — rendered in the display weight of the geometric monolinear typeface (see §5.3), centered on a Board Night (`#1E2229`) field. The numeral is set in Signal-Gold (`#F5C70A`) and scaled to fill approximately 68% of the canvas height. No border radius on the outer icon shape (follow platform masking conventions — iOS rounds externally, Android provides the mask layer; the source art remains square and sharp). No grid lines. No secondary elements.

The icon communicates: precision, confidence, a single point of focus. The gold digit on near-black reads at 16 × 16 px (notification badge size) and at full resolution on a store page.

**Splash screen:** Board Night field, centered gold "9" identical to icon, fades to board state. Duration 1.2 seconds maximum. No animation beyond the fade.

**Notification icon:** White silhouette of the "9" numeral on transparent background, for system-level notification rendering (follows Android / iOS monochrome notification icon specifications).

**Forbidden on the icon:** Multiple digits, grid overlays, gradients on the background field, glow halos, drop shadows, any secondary color from the difficulty tier palette.

---

### 5.3 Typographic Personality as Character

Because Sudoku Rush has no characters, its numbers *are* its characters. The digit set is the cast.

The geometric monolinear typeface family carries the game's emotional register in two weights:

**Body weight (board digits):** Calm, neutral, legible. Uniform stroke width communicates fairness — no digit feels more or less important than another before the player acts. Emotionally: composed, present, waiting.

**Display weight (technique banners, score callouts, combo counter):** The same geometric skeleton, but with increased stroke weight and tighter horizontal spacing. At scale, display-weight digits feel declarative — they do not ask, they announce. A "5×" combo counter in display weight is not ornamentation; it is the board asserting what just happened.

**Rule:** All in-board numerals use body weight. All event-driven callouts (technique banners, score popups, combo counter) use display weight. No italic, no oblique, no mixed weights within a single UI element. The typeface should be a single geometric sans-serif family that provides both weights — specific family selection deferred to typography review, but must have tabular figures and a minimum of four weight variants (Regular, Medium, SemiBold, Bold).

---

### 5.4 Effect Personality

Effects are the game's most expressive visual layer — they substitute for the expressiveness that characters would otherwise provide.

**Personality archetype: Sharp-electric with soft release.** The leading edge of any effect is angular and fast — hard-edged fragments, straight-cut shards, tight radial bursts (consistent with the 0px corner radius of the board's shape vocabulary from §3). These sharp forms communicate precision: a technique was *executed*, not stumbled into.

The trailing edge softens. After the hard burst, residual particles are circular and slow, drifting off-board as the board returns to calm. This soft organic tail provides the emotional exhale after the sharp inhale.

**Rule:** No effect may be purely soft (bubbly, rounded, flowing) — that register belongs to games with different pillars. No effect may be purely chaotic (random scatter, no directionality) — effects must have a legible origin point and a legible direction that matches the triggering geometry (row clear = horizontal; column clear = vertical; box clear = centripetal). Effects are sharp first, soft second, always directional.

---

## 6. Environment Design Language

### Reframing: The Screen IS the Environment

*Sudoku Rush* has no world, no levels, no location. The environment is the game
screen itself: the board, the surrounding field, and the full-screen context that
holds the session. Every decision in this section governs how those surfaces are
treated and how they support the mood arc defined in Section 2.

---

### 6.1 Background Design Language

The background is the field behind the board. It is not decoration — it is the
game's atmospheric temperature gauge made visible.

**Surface treatment**

The background uses a single layer with two components at all times:

1. **Fill layer**: A flat color fill at the base dark value (Board Night, `#1E2229`
   by default). No texture. No noise pattern. No gradient. The fill is the
   anchor — it should feel as neutral as possible so that temperature shifts are
   unambiguous.

2. **Temperature overlay**: A second pass — rendered as a very large radial gradient
   originating at screen center, clipping to the full screen bounds — that applies
   the combo-state warmth described in Section 2. This overlay has opacity of 0%
   at idle and scales up to approximately 65–75% opacity at peak combo. The overlay
   color follows the warm amber arc (35–55° hue band); the fill layer beneath it is
   always cool-neutral. The overlay alone carries all temperature information.

   Implementation note: render the temperature overlay as a full-screen quad in
   URP with Additive or Screen blend mode. Drive its opacity and hue from a single
   `_ComboHeat` float property (0.0 = idle, 1.0 = peak) passed from the combo
   state manager. Never compute this inside the background material itself — the
   property must be addressable from gameplay code.

**Texture policy**

The background is flat. No procedural noise, no tile texture, no vignette pattern.
The only acceptable non-flat element is the temperature overlay described above.
Rationale: any ambient texture competes with the particle effects for the player's
peripheral attention. The background's job is to recede.

**Board edge relationship**

The board does not cast a shadow on the background, nor does it float above it.
The board edge is a hard contrast edge — the board's outer border (Section 3.1,
level-1 line weight) reads against the background at the maximum value contrast
the background affords. There is no vignette, halo, drop shadow, or inner glow
at the board perimeter. The board is embedded in the field, not floating above it.

Background never bleeds visible color into the board surface. The board's color
system is self-contained. If the temperature overlay is bright enough to visually
tint the board, the overlay opacity ceiling must be lowered until the board surface
reads independently.

---

### 6.2 Screen Architecture

The screen is divided into four functional zones. Proportions are expressed in
logical points at the 375pt reference width; scale proportionally to wider
breakpoints.

| Zone | Vertical span | Content | Boundary type |
|---|---|---|---|
| **HUD zone** | Top 13–15% of screen | Score display, timer, combo meter | Implied — no drawn line |
| **Board zone** | Middle 52–56% of screen | The 9×9 grid | Hard edge — the board's outer border |
| **Input pad zone** | Lower 24–26% of screen | 3×3 number pad | Implied — no drawn line |
| **Margin zones** | Remaining height | Bottom safe-area buffer; top notch buffer | Structural — safe-area controlled |

**Total: 375pt width example**

At 375pt × 812pt (iPhone SE 3 / standard non-dynamic-island):
- Safe area top: ~44pt consumed by status bar
- HUD zone: 44–106pt (62pt, ~8 rows at 8pt grid)
- Board zone: 106–510pt (404pt; board is square, ~370–380pt with 12–16pt horizontal padding each side)
- Input pad zone: 510–680pt (170pt; pad is ~132–148pt tall plus margins)
- Bottom safe-area buffer: 680–812pt (132pt; home indicator and breathing room)

**Zone boundaries are implied, not drawn.** No lines, dividers, or rule elements
separate zones. Separation is achieved through spatial grouping and value contrast.
The board's outer border is the only structural edge on screen.

**Horizontal margins**

The board is centered horizontally with a minimum 12pt margin on each side at
375pt width. The input pad is also centered. The HUD elements are aligned to the
board's left and right edges — the board's width is the layout column. Nothing
extends past the board width in the HUD zone.

---

### 6.3 Non-Board Visual Surfaces

Each screen context has a concrete visual treatment consistent with the Section 2
mood specification.

**Home / Menu screen**

Background fill: Board Night (`#1E2229`). Temperature overlay: 0% opacity —
completely absent. No particles. The board, if shown in preview, renders with
all cells empty and zero event activity. The visual result is the coolest,
quietest state in the entire game. Any element on this screen that introduces
warmth, glow, or saturation above 15% is an implementation error.

Specific treatment: the title wordmark and difficulty selection cards are the only
elements with meaningful visual weight. The rest of the screen is negative space.
Difficulty cards use the tier accent colors at 25% opacity on their card surface
(see Section 4, difficulty accent palettes) — enough to identify which tier is
which without introducing warmth into the global background.

**Results screen**

Background fill: Board Night. Temperature overlay: 30–45% opacity, set to the
warmth level that reflects the session's actual peak — driven by the peak combo
value from the completed run, not a fixed value. A run that peaked at 3× gets
an overlay near 25% opacity; a run that peaked at 7×+ gets the full 45%.

No active particles. The results screen is not a celebration loop — it is a
record. All particle systems from the final area clear have fully resolved before
the results screen fades in. The warmth is ambient and static (no pulse, no
breathing). Results content — score, technique list, personal best delta — is
laid out in the board zone and HUD zone footprint with generous vertical spacing.

**Puzzle transition (board-to-board bridge)**

This is not a discrete screen; it is a 1.0–1.5 second crossfade within the game
session. Visual treatment:

- Board cells fade out simultaneously (not one-by-one): fade duration 0.3 seconds.
- Temperature overlay dips 15–20% toward neutral during the fade — a perceptible
  but non-jarring relative cooling. It does not return to 0%. The combo state is
  continuous; only the board content transitions.
- New puzzle fades in over 0.3–0.4 seconds. Cells appear at correct opacity
  simultaneously.
- Background returns to the current combo level immediately when the new board
  is visible.

Total visual gap between old board-gone and new board-visible: do not exceed
0.2 seconds of empty board state. The screen should never feel blank.

---

### 6.4 Depth Language

*Sudoku Rush* is architecturally flat. There is no z-depth, no parallax, no blur-
based depth separation, and no shadow casting between layers.

**The layering vocabulary — composited, not z-ordered**

The game uses three composited layers, all on the same conceptual z-plane:

1. **Background layer** — fill + temperature overlay. Always behind everything.
2. **Board layer** — grid, cells, digits. Always above background.
3. **Effect layer** — particles, technique banners, combo meter effects. Always
   above board.

"Closer" is encoded by opacity and scale in animation only — never as a permanent
spatial relationship. When a technique banner appears, it does not feel like it is
floating in front of the board; it reads as a declared overlay, a flat annotation
on the session.

**No drop shadows.** Board, HUD elements, and input pad cast no shadows on the
background or on each other. The board is embedded in the field, not hovering
above it. A drop shadow would imply a physical world that this game does not have.

**Semi-transparency as layer signaling**

The one permitted depth cue is the technique banner's backing: a very dark semi-
transparent strip (70–80% opacity, HSB 0°, 0%, 10–15% brightness) behind the
banner text. This does not create a sense of a floating pane — it creates a readable
contrast surface for the text. The opacity is set to the minimum needed for the text
to pass 4.5:1 contrast against any game-state background, and no higher.

---

### 6.5 Safe Area and Device Context

**Universal rule**: The background fill and temperature overlay extend to the full
screen bounds including behind the status bar, notch, Dynamic Island, and home
indicator. Background color fills edge-to-edge and corner-to-corner — clipping to
the device's physical screen shape if rounded corners are present.

**Content never extends into the unsafe zones.** The HUD zone, board zone, and
input pad zone are all positioned within the safe area insets reported by the
operating system. No digit, button, combo meter element, or technique banner may
overlap an unsafe area.

**iOS safe area implementation (Unity 6 / URP)**

Use `Screen.safeArea` to retrieve the safe inset rectangle at runtime. Apply the
inset as padding to the canvas root. The background RectTransform remains at full
screen bounds (`Stretch All`, with offset 0,0,0,0); the content canvas root
constrains to `Screen.safeArea`.

Safe insets by device context:

| Device class | Top inset | Bottom inset | Notes |
|---|---|---|---|
| Standard iPhone (no notch, home button) | 20pt | 0pt | Status bar only |
| Notched iPhone (iPhone X–14) | 44pt | 34pt | Notch + home indicator |
| Dynamic Island iPhone (iPhone 14 Pro+) | 59pt | 34pt | Dynamic Island + home indicator |
| iPad (no home button) | 24pt | 20pt | Landscape values differ; verify at runtime |

These values are provided for design mockup reference. Always use `Screen.safeArea`
at runtime — never hard-code inset values.

**Android cutout rules**

Use `Screen.safeArea` on Android as well (Unity propagates the API on Android 9+).
For Android devices with punch-hole cameras in the top-right corner: the safe area
inset only protects the left-right center column where the cutout appears. HUD
elements must not be pushed against the screen edge corners — maintain a minimum
12pt mechanical margin from all screen edges regardless of safe area, treating the
safe area as a floor, not a precise wall.

**Background fill behind unsafe areas**

The background fills behind the status bar on iOS and the Android status bar.
The color the system shows in the status bar area is the background fill color.
On dark background (Board Night, `#1E2229`), this reads as a near-black status bar
which is consistent with the game's identity. In Unity, set the application's
`UIViewControllerBasedStatusBarAppearance` to respect the screen fill and set
`statusBarStyle` to light content.

The home indicator area on iOS receives the full background fill treatment — no
special dark band, no white strip. The home indicator itself is rendered by the
OS at a color that contrasts its background; ensure the background color at the
bottom of screen provides sufficient contrast for the indicator to remain visible.
Board Night (`#1E2229`) at the home indicator position satisfies this requirement
without modification.

**Landscape orientation**

The game targets portrait orientation only. Landscape is not a supported layout.
Lock the app to portrait in both the iOS Info.plist and the Android Manifest.
No environment design work is required for landscape.

---

## 7. UI/HUD Visual Direction

### 7.1 HUD Composition and Visual Hierarchy

The screen divides into three fixed zones. On a 375pt-wide reference screen (iPhone SE 3 / standard non-dynamic-island at 812pt tall), the proportions are:

**Top Strip — 15% of screen height (approx. 122pt)**
Left slot: score readout. Right slot: run timer. Both flush to their respective edges with 16pt horizontal margin, vertically centered in the strip. No background panel, no card surface — the readouts float directly against the board's implied extension. The strip is not separated from the board by a visible rule or fill; only spatial distance creates the boundary.

**Board Zone — 65% of screen height (approx. 528pt)**
The board is a square, centered horizontally with 12pt horizontal gutter on each side (351pt wide on a 375pt screen). It sits 8pt below the top strip's baseline and 8pt above the bottom zone. The board does not fill to the edges; that 12pt margin is load-bearing whitespace — it prevents the grid from reading as a raw data table and gives VFX particles a brief travel region before exiting screen.

**Bottom Zone — 20% of screen height (approx. 162pt)**
Top of zone: combo meter (horizontal fill bar, full width minus 32pt gutter, 12pt tall with rounded caps). Below it: the digit input pad (1–9 plus erase), arranged in a 3×3+1 grid. Input pad occupies the remaining vertical space, with cells sized to approximately 52pt touch targets.

**Hierarchy when all elements are simultaneously active:** The technique banner (lower third, overlaid across board and bottom zone boundary) is the highest-priority read — it is the largest single text element on screen and appears only on an event, so transience itself commands attention. Below that: score (top-left, large) reads before timer (top-right, smaller). Combo meter reads before digit pad because it is positioned above the pad and closer to the board. This is a top-left-to-bottom-right Z-path with the technique banner as an interrupt that hijacks the eye momentarily then releases.

---

### 7.2 Diegetic vs. Screen-Space

All HUD is screen-space. This is the correct choice for two reasons specific to this game:

First, the board is the diegetic world and must remain uncontaminated. Any in-world data display (a number shown on the grid itself, a glow attached to a cell as a persistent readout) would collapse the visual separation between game-state information and UI information. When a digit appears in a cell, the player must read it as game content, not metadata. Screen-space HUD enforces this distinction by material contrast: the board is flat, static, and gridded; the HUD is typographic, positioned outside the grid boundary, and animated in characteristic screen-space ways (counter increments, bar fills, fade transitions).

Second, the game's core mechanic is a spatial grid that the player must read continuously. Any diegetic overlay would occlude logical relationships between cells that the player is actively tracking. The screen-space HUD lives in zones the player's attention does not need during solving.

**Visual convention that signals "information, not content":** All HUD elements use the primary typeface at weights heavier than board digits (see §7.3). Score and timer use tabular monospaced numeral alignment — digits do not shift left or right as values change, which is a typographic behavior that reads as "readout" rather than "game event." The combo meter's horizontal fill bar has no analog in the board's visual vocabulary (the board has only square cells and thin lines), so it reads unambiguously as UI chrome.

---

### 7.3 Typography Hierarchy

Reference screen: 375pt wide. All sizes in typographic points (pt), which map 1:1 to Unity's UI units at the reference DPI.

| Element | Weight | Size | Tracking | Notes |
|---|---|---|---|---|
| Score | Bold (700) | 28pt | +80 | Tabular figures; monospaced numeral advancement |
| Combo multiplier label (e.g. "4×") | Black (900) | 36pt | +40 | Largest persistent HUD numeral |
| Run timer | Medium (500) | 22pt | +60 | Intentionally smaller than score — pressure, not reward |
| Technique banner | Bold Italic (700i) | 32pt | +20 | Largest element on screen when active |
| Digit input pad numerals | Regular (400) | 26pt | 0 | Lighter weight — must not compete with combo multiplier |
| Score popup (floating "+NNN") | SemiBold (600) | 18pt | +40 | Short lifespan; legible at small size over board |

Optical spacing note: The score and timer share the top strip. Size difference alone (28pt vs 22pt) is insufficient to communicate hierarchy at a glance — weight reinforces it. The timer uses Medium rather than Bold so that at a glance the eye reads score first, then timer, not both simultaneously.

The combo multiplier is the largest persistent numeral. It does not compete with the technique banner because the two never demand attention simultaneously — the multiplier is always visible, while the banner is a brief interrupt.

---

### 7.4 Iconography Style

**Style:** Flat, outlined, 2px stroke at 1x (scales proportionally). No fills except state-active tints. No decorative shadows or bevels — the board's grid already supplies all rectilinear geometry; icons must not add visual noise that reads as additional grid structure.

**Construction grid:** 20×20pt artboard, 2pt minimum stroke, 2pt corner radius on rounded elements. Icons never touch the artboard edge — 2pt safety margin on all sides, so effective drawing area is 16×16pt.

**Icon set:**
- Settings: standard gear, simplified to 6 teeth (not 8) for cleaner silhouette at small size
- Navigation back: left-pointing chevron, not an arrow with a shaft — the shaft reads as a play button at small size
- Erase/delete: backspace symbol (rectangle with left notch cut), consistent with platform conventions
- Difficulty tier identifiers: filled circle scaled to 8pt — one circle per tier (Easy: 1, Medium: 2, Hard: 3, Expert: 4), using the tier's accent color. No star or medal imagery, which carries cultural reward connotations that conflict with "Clean by Default"

**Color states:** Default: foreground color at 60% opacity. Active/pressed: foreground at 100% opacity. Disabled: foreground at 30% opacity. Opacity-only modulation — no separate icon color per state, zero additional color tokens.

---

### 7.5 UI Animation Feel

**Score counter:** Increments in a fast number roll over 400ms, easing out (cubic ease-out curve). Each digit position ticks independently — a score jump of +1,500 should visually cascade from the ones digit upward, not jump atomically. This is subtle but reinforces "Every Hit Lands" by making each point feel counted.

**Combo meter fill:** Fills smoothly on correct placement (spring ease, 200ms, slight overshoot of 4pt then settle). Decays in real time as a continuous drain at a constant rate — no stepping, no visual ticking. The decay animation is uninterrupted until an input event occurs. During high combo states (above 6×), the fill bar takes on the tier accent color with a low-amplitude pulse (scale: 1.0 to 1.03 and back, 800ms period) — the HUD "feeling alive" per "effects earn their chaos."

**Technique banner entrance:** Translate-in from 8pt below final position over 150ms (ease-out), hold for 1.5–2.0 seconds, translate-out upward 16pt and fade over 200ms. The upward exit mirrors the physical intuition of the score "going up." No bounce on entry — the emphasis is on readability, not playfulness.

**Timer:** Never animates normally. In the final 30 seconds of a run, the timer weight jumps from Medium to Bold and pulses (scale 1.0 to 1.04, 600ms period). This is the only moment the timer demands attention.

**Wrong-input feedback:** Screen vignette dims to a 20% black overlay over 80ms, clears over 200ms. No shake. Shake on mobile touch is a physical conflict — the player's hand may still be touching the screen. Vignette achieves the same negative signal without the collision.

**HUD state transitions (e.g., puzzle complete to next puzzle):** Score carry-over: score readout holds for 400ms then re-increments with any puzzle-completion bonus (same roll animation). Combo meter: briefly flashes white fill (full width, 150ms) to signal the carry, then immediately resumes at the current combo level.

**Reduce Motion variants (Accessibility):**
When the OS Reduce Motion setting is active (iOS) or Disable Animations is set (Android), apply these substitutions: technique banner — cross-fade instead of slide (150ms fade-in, 150ms fade-out); combo meter — instant fill with no overshoot easing; area-clear burst — single-frame flash at 30% opacity rather than expanding particles; score counter — instant value jump rather than rolling animation; screen vignette on wrong input — single-frame flash rather than fade curve. All motion-reduced variants must still produce a legible feedback signal — the signal is preserved, the motion is reduced.

---

### 7.6 Navigation and Overlay Screens

**Modal surface:** All modals (pause, settings, run-end summary) use a floating panel centered on screen. Panel dimensions: 311pt wide × variable height, 16pt corner radius, background token `surface-overlay` (dark theme: `#1A1A2E` at 96% opacity; light theme: `#F5F5F5` at 96% opacity). Not frosted glass — frosted glass reads as device-level UI on iOS and would compete with the game's own visual language.

**Board dimming:** When a modal opens, the board and bottom zone dim behind a full-screen scrim: `#000000` at 48% opacity. The scrim does not blur — blur at 48% opacity causes visual muddiness on the near-neutral board background.

**Transition in:** Modal panel slides up from off-screen-bottom over 280ms, cubic ease-out. Scrim fades in simultaneously over 200ms. The panel arrives slightly after the scrim reaches half-opacity — the scrim clears the background before the panel enters, so the panel always reads against a dimmed background rather than the live board.

**Transition out:** Reverse sequence — panel slides down while scrim fades. Duration: 200ms (faster out than in; closing should feel snappy, not ceremonial).

**Run-end summary:** Full-screen panel filling the screen with 16pt margin on all sides. Score, peak combo, technique count, and personal best delta are the four primary data points. Personal best delta uses the tier accent color when a PB is set; uses the foreground color at 60% opacity when not — the player reads immediately whether the run was a PB without decoding a symbol.

**Settings and pause share one modal design.** The visual language must not make pause feel like a significant interruption — "Flow Over Friction" applies to modal design too. No dramatic full-screen cover for pause; a clean panel that can be dismissed with one tap, tapping anywhere on the scrim.

---

## 8. Asset Standards

### 8.1 File Format Preferences

**UI Sprites:** PNG is the required format for all UI sprites. The minimal, flat aesthetic — hard-edged cells, clean numerals, thin grid lines — has no gradient complexity that benefits from vector formats at runtime. SVG is acceptable only as a source file for path-based UI elements (e.g., combo meter arc or cell border masks) that are exported to PNG before import.

**Particle Textures:** PNG with premultiplied alpha. Soft circular glow forms must be authored at their full radius without hard cutoffs — the alpha fade is the shape. Geometric fragment shapes (hard-edged shards, ring slices) should have clean alpha boundaries with no anti-aliasing bleed on the opaque edge. Do not use JPG for any particle texture.

**Fonts:** OTF preferred over TTF for all type families. OTF provides better hinting at small sizes, which matters for the numeric readability pillar. Fonts must be imported into Unity as TextMeshPro font assets with SDF (Signed Distance Field) rendering enabled — non-negotiable for maintaining crispness at the variable display densities of iOS and Android devices.

**App Icon Variants:** Source as a single 1024×1024 PNG (sRGB, no transparency). All platform-required size variants are generated from this master by the Unity build pipeline or the platform submission tool, not authored separately.

---

### 8.2 Naming Convention

All assets follow: `[category]_[name]_[variant]_[size].[ext]`

| Category prefix | Example |
|---|---|
| `ui_` | `ui_cell_selected_normal.png`, `ui_btn_primary_active.png` |
| `vfx_` | `vfx_clear_row_burst_medium.png`, `vfx_hit_pulse_loop_small.png` |
| `font_` | `font_body_regular.otf`, `font_display_bold.otf` |
| `icon_` | `icon_app_master_1024.png` |
| `bg_` | `bg_board_dark_tile.png` |

Variant tokens must be drawn from a controlled list: `idle`, `selected`, `active`, `disabled`, `error`, `loop`, `burst`, `fade`. Do not invent new variant names without updating this list. Size tokens: `small`, `medium`, `large` (pixel dimensions documented per asset category in §8.3).

---

### 8.3 Texture Resolution Tiers

Given the flat, minimal style, resolution budgets are deliberately conservative. More pixels do not improve this aesthetic — precision of edge and clarity of shape do.

| Asset Category | Base Resolution | Notes |
|---|---|---|
| UI cell sprites (9×9 grid tile, selector) | 64×64 px | Scaled by Unity's UI system; SDF handles sub-pixel rendering |
| UI icon glyphs (technique banner icons, settings) | 128×128 px | |
| UI full-screen panels / backgrounds | 512×512 px, tiled or stretched | Keep textures tileable where possible |
| Particle: soft glow / circular forms | 64×64 px | Gaussian falloff — no detail is lost at this size |
| Particle: geometric fragments | 128×128 px | Hard-edge detail justifies the higher resolution |
| App icon master | 1024×1024 px | Platform export scales down from this |

Maximum justified texture size: 512×512 px for any single asset. Nothing in this game's visual language requires a 1K sprite texture. Any request to author a 1024×1024 UI or VFX texture should be treated as a scope question, not a technical one.

**Technical constraint:** All source textures must be power-of-two dimensions. Non-power-of-two textures disable GPU texture compression on mobile and increase memory usage significantly.

---

### 8.4 Sprite Atlas Strategy

Pack atlases by render context, not by visual category. Atlases that span render passes waste batch calls.

| Atlas | Contents |
|---|---|
| `ui-core` | Combo meter chrome, timer display, score elements, difficulty cards, input pad |
| `board-elements` | Cell highlight states, selection ring, grid line textures (if rasterized) |
| `vfx-particles` | All particle sprites: soft discs, ring pulses, hard-edged fragments, halo forms |
| `technique-banners` | Banner backing slice, icon shapes (if rasterized) |

**Unity 6 Sprite Atlas settings:**
- Packing algorithm: Tight (reduces atlas waste for non-rectangular sprites)
- Allow Rotation: Off (rotation can misalign nine-slice sprites)
- Padding: 4px — prevents UV color bleed between sprites at compressed mip levels
- Maximum atlas size: **2048×2048** — 4096 atlases are unsafe for low-end Android targets (a single 4096×4096 ASTC 4×4 atlas consumes ~8 MB of GPU memory)

Include in Build: yes for `ui-core` and `board-elements`; use Addressables for `vfx-particles` and `technique-banners` (load only during active gameplay, unload during menus).

> **Note for engine integration:** Unity 6 with UI Toolkit manages its own internal atlas and may not consume SpriteAtlas assets the same way a Canvas Renderer does. Confirm the batching path with the engine-programmer before finalizing the art pipeline for UI Toolkit assets.

---

### 8.5 Typography Sourcing and Licensing

The typeface must meet all of the following: geometric monolinear construction, tabular figures (fixed-width numerals), at minimum four weights (Regular, Medium, SemiBold, Bold), and full licensing for commercial mobile distribution on iOS and Android. Desktop embedding rights are not required.

License requirement: the selected typeface must permit embedding in a compiled mobile application distributed commercially. Google Fonts OFL (SIL Open Font License) satisfies this. Commercial font services requiring per-app or per-seat licensing are permissible only if the license explicitly covers compiled mobile app distribution at the expected install volume.

If the preferred typeface is unavailable, fallback candidates (OFL-licensed): DM Sans, Nunito, Outfit. Numeric readability must be verified against the established HSB color system at 24pt equivalent on a 390px-wide display before accepting any fallback.

Do not use system fonts (SF Pro, Roboto) as the primary typeface. System fonts are acceptable only for legal/compliance text that must match OS conventions.

**TextMeshPro Font Asset setup:**
- Atlas resolution: **1024×512** — the character set is narrow (digits 1–9, plus Latin for technique names and labels)
- Sampling point size: 60–72pt for best SDF edge quality at large display sizes
- Atlas populate mode: **Static** — the character set is fully known at build time; Dynamic mode causes GPU texture uploads mid-session
- Character set: define explicitly as `0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz :/.,!-` — do not use Unicode range mode
- Generate a separate Font Asset for each weight variant (the art bible §3.2 uses four distinct weights: Regular, Medium, Bold, Light for pencil marks)

> **Flag:** If a variable font is selected, Unity's TMP Font Asset Creator does not support variable font axes. Each weight must be exported as a discrete static font file. Confirm with the font license that discrete-weight exports are permitted.

---

### 8.6 Motion and Animation Format

**UI Animations:** Code-driven via DOTween or Unity's Animation component, not sprite sheets. The visual language — number pops, cell selection scale, technique banner slide — consists of simple transform, alpha, and scale curves. Define all UI animation curves in a single `UIAnimationConfig` ScriptableObject so timings are tunable without code changes. This also makes Reduce Motion variants (§7.5) implementable as a config swap.

**Area Clear and Hit VFX — Particle System decision:**
The art direction specifies the built-in Particle System (Shuriken) rather than VFX Graph.

*Context:* In Unity 6, the built-in Particle System is deprecated in favor of VFX Graph, meaning no new feature development. However, VFX Graph requires compute shader support (OpenGL ES 3.1+ / Vulkan), which is not guaranteed across the full low-end Android target market. Using VFX Graph as the primary effect tool introduces a real device compatibility risk for this audience.

*Decision:* Retain the built-in Particle System for all particle effects. It remains fully functional in Unity 6 LTS — "deprecated" means no new feature investment, not removal. This decision should be reviewed if the minimum supported Android spec rises post-launch or VFX Graph's mobile compute requirements change.

Particle count hard ceiling per simultaneous emission: **50 particles total across all active systems** (enforced in code). Individual event limits: Scale 1 (digit placement) = 1–3 particles; Scale 2 (area clear) = 6–12; Scale 3 (cascade) = 20–35.

**Particle material requirements (URP):** Soft particles (depth intersection fading) require a depth prepass — disable for all particle materials in this 2D game. Particle materials must use the URP/Particles/Unlit shader or a URP-compatible Shader Graph; built-in pipeline particle shaders will render pink/error in URP. Additive blending is permitted for ring pulses and halos; alpha-blend with premultiplied alpha is preferred for soft disc particles.

**Combo Meter and Score Popup Transitions:** Code-driven animation only. The combo meter's color shift through the accent palette is a shader-level HSB lerp, not a frame animation — drive it from a `_ComboHeat` float matching the background system (§6.1).

Sprite sheets are prohibited for animation in this project. Every case where sprite-sheet animation might be considered should be re-evaluated as either a particle system (bursts and ambient effects) or a code-driven tween (UI state transitions).

---

### 8.7 Technical Constraints Summary

| Constraint | Value | Rationale |
|---|---|---|
| Texture compression (iOS) | ASTC 4×4 or 6×6 | Supported on all A8+ chips (iPhone 6+) |
| Texture compression (Android) | ASTC primary, ETC2 fallback | Set per-platform in Texture Importer overrides |
| Max sprite atlas size | 2048×2048 | Safe ceiling for low-end Android GPU |
| Total texture memory target | Under 64 MB at runtime | Conservative for a 2D UI game |
| Max unique materials | 8–12 | Each unique material generates its own draw call group |
| Draw call budget (estimated usage) | 27–49 of 100 | SRP Batcher handles same-shader batching automatically |
| Mip maps | Off for all 2D/UI textures | Not needed; adds 33% to texture memory |
| Initial download size | Under 50 MB compressed | Critical for App Store / Google Play conversion rate |
| Shader variant stripping | Enable `Strip Unused Shader Variants` in URP Asset | Prevents 5–20 MB shader bundle bloat |

> **Verify against Unity 6.3 reference docs:** The `Strip Unused Shader Variants` setting location may have shifted in URP 17.x (shipping with Unity 6.3). Confirm in `Edit > Project Settings > Graphics > URP Global Settings` and the URP Asset's Advanced section before relying on automatic stripping.

---

## 9. Reference Direction

This section is a field guide, not a mood board. For each reference: what to extract, what to deliberately leave behind, and why the distinction matters for Sudoku Rush's specific visual identity.

---

### 9.1 Monument Valley (ustwo games, 2014) — Geometric Silence as Visual Language

**Extract:** The way Monument Valley treats negative space as an active design element, not an absence of content. Every screen has a clear figure/ground relationship — the focal object sits against a field that recedes without texture or noise. Geometry is precise; edges are exact; no surface is decorated beyond its structural role.

**Apply to Sudoku Rush:** The board in its neutral state should read with the same quality of deliberate emptiness. Cell surfaces are not blank by default — they are calm by design. The grid lines exist to define space, not to add visual interest. This is the perceptual foundation that makes event-state color register as a true contrast shift.

**Avoid:** Monument Valley's isometric depth, soft pastel palette, and architectural whimsy. Sudoku Rush is flat, dark-background, and sharp-cornered throughout. Any hint of dimensionality in the board surface violates the screen-space flatness principle.

---

### 9.2 Downwell (Ojiro Fumoto, 2015) — High-Contrast Palette Restraint with Punctuation Color

**Extract:** Downwell's default palette is near-monochromatic (black, white, one red). When the player activates a color palette unlock, the contrast shift is immediately legible because the base was so stripped down. The single accent color does enormous emotional work precisely because it is surrounded by nothing.

**Apply to Sudoku Rush:** This is the mechanical model for the Signal-Gold and Signal-Blue usage rule. Board Night (`#1E2229`) and Cell Surface (`#2D333D`) are the "Downwell black." Signal-Gold exists to function like a single red pixel against a white field — it earns its impact through surrounding restraint. Any addition of a third simultaneous event color risks collapsing this contrast.

**Avoid:** Downwell's chunky pixel art, its violence-genre energy, and its vertical-scroll layout language. The aesthetic code to borrow is purely the palette discipline — not the pixel resolution, not the character, not the feel of danger.

---

### 9.3 Reigns (Nerial, 2016) — Typography as the Entire Visual Event

**Extract:** Reigns places large, readable text at mid-screen as the primary feedback mechanism. The text treatments — weight, position, timing — carry full emotional load without illustration support. Text is the event, not a label on an event.

**Apply to Sudoku Rush:** The technique banner system (X-WING, NAKED PAIR, HIDDEN SINGLE) follows this model directly. The banner IS the reward, not a caption on a particle burst. This means the technique name must be large enough to feel like an announcement, held on screen long enough to be read and savored, then dismissed cleanly. Reference Reigns' card-reveal text timing specifically: the moment before text resolves, the hold, the fade.

**Avoid:** Reigns' gothic, desaturated, medieval card aesthetic. The typeface, color, and texture language there is entirely the wrong register. Borrow only the compositional principle — centered, large, temporary text events — not the visual tone.

---

### 9.4 Mobile Score-Attack Genre (Kairosoft / SUPERSTAR lineage) — Score Popup Hierarchy

**Extract:** The best mobile score-attack games establish a visual hierarchy for score feedback: a small number for small events, a larger styled number for area bonuses, a full-width styled treatment for rare events. Players learn to read the magnitude of their action from the popup typography size and weight alone, before reading the actual number.

**Apply to Sudoku Rush:** The score popup system must operate on at least three distinct visual scales: (1) small `+NNN` in Chalk for a single-cell hit; (2) mid-sized styled `+NNN × MULTIPLIER` in Signal-Gold for area clears; (3) large full-panel typographic event for multi-clears and peak-combo milestones. The size ratio between levels 1 and 3 should be approximately 4:1.

**Avoid:** The chaotic layering common in mobile gacha games, where four or five popup types fire simultaneously and overlap. Sudoku Rush enforces a queue: only one popup tier is legible at a time. Simultaneous events stack vertically, not on top of each other.

---

### 9.5 Prune (Joel McDonald, 2015) — Particle Motion as Emotional Register, Not Spectacle

**Extract:** Prune uses sparse particle motion — a few slow-moving dots, a clean sweep arc — to suggest organic responsiveness without volume or noise. The motion communicates aliveness without demanding attention. There is a specific quality of restraint in how the particles know when to stop.

**Apply to Sudoku Rush:** This is the reference for cell-hit particles in the neutral-to-low-combo state. Early-combo feedback should feel like Prune: a small sharp release of energy, a quick dissolve. The escalation from "Prune-quiet" to "full-chaos cascade" is the visual arc of the combo system. If the small-hit particles already look like a celebration, the full-board cascade has nowhere to escalate to.

**Avoid:** Prune's organic, botanical, slow-dissolve aesthetic at higher intensity levels. As combo escalates, the Sudoku Rush particle language becomes harder and faster (electric leading edges, sharp geometry). Prune is the bottom of the scale, not the model for the whole range.
