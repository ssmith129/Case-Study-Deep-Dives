# Computis Deck — Change Log v17.2 → v18

**Date:** May 15, 2026
**Author:** Sean Smith
**Scope:** Full-deck reflow from v17.2 → v18, two variants

---

## Variants delivered

| File | Spec | Use case |
|---|---|---|
| `computis-deck-v18_FHD-fixed.html` | All 39 slides at exactly 1920×1080 | Single-aspect projection · screen recording · Decktape PDF |
| `computis-deck-v18_FHD-flex.html` | Default 1920×1080 · slide-16 extended to 1920×1200 | Web presentation · per-slide scale-to-fit |

Both files self-contained · zero external dependencies (except Google Fonts) · all 20 source images re-embedded as base64 verbatim from v17.2 · all 39 speaker notes round-tripped intact.

---

## Severity legend

- **P0** — bug fix; previous deck rendered broken or missing data
- **P1** — significant composition improvement; whitespace, scale, or hierarchy
- **P2** — design system tightening; tokens, type, spacing
- **P3** — copy refinement or annotation pass

---

## Cross-deck changes

| Change | Severity | Notes |
|---|---|---|
| Type scale rebuilt for FHD: H1 48, H2 30, body 18 (was 20), stat-display 84, cover-H1 96 | P1 | All slides; body 18 reads better at projection distance than 20 |
| Slide title block consistent: H2 max-width 1400, subtitle max-width 1200, mb 32 | P1 | All content slides |
| `height: calc(100% - 200px)` on col-2 grids so cards fill the canvas vertically | P1 | All multi-column content slides |
| Card stacks use `flex:1` with `justify-content: center` so heights match | P1 | Slides 3, 5, 9, 10, 14b, 19b, 20, 21, 23, 24, 25, 31, 32, 33 |
| Anchor "SEAN SMITH · smithdesign.live" on every content slide; cover keeps triple anchor | P3 | Consistent presence cue; project URL only on cover/closing |
| Page-num corrected from hardcoded "/34" to dynamic count via JS | P0 | Fixed counter mismatch (39 slides, was showing /34) |
| 350ms transition replaced with 280ms ease-out · slide bleed-through eliminated | P2 | Render screenshots no longer capture transition state |
| Inline `transition:none` injected during PDF/screenshot capture | P2 | Render utility script |
| Speaker notes panel: 38vh max height, JetBrains Mono for header, scroll on overflow | P2 | All slides |
| Help overlay: Esc closes, F fullscreens, S toggles notes, ? shows help | P2 | Standardized |
| Print rules: 1 slide/page at 1920×1080 (V1) or per-slide height (V2) | P1 | Both variants |

---

## Per-slide changes

### Section 01 — Context

#### Slide 1 — Cover
- **P1** Cover H1 bumped from 72px → 96px after first-render review; reads as commanding at FHD
- **P1** Rebuilt as 560/1168 split (was 50/50); text column tighter, hero image bigger
- **P3** Subtitle copy preserved; "Includes 2 misses I'd answer for" anchor preserved verbatim
- **P3** Single-line role-line above title at 14px mono uppercase

#### Slide 2 — Section divider 01
- **P1** Ghost numeral "01" at 360px, right-aligned, 4.5% white opacity — quiet anchor
- **P1** H1 at full type-display 72px; section meta at 22px on dark
- **P3** Consistent with all 5 dividers — uniform composition

#### Slide 3 — Context (company / product / users / compliance / team)
- **P1** Rebuilt as 2-col fill-canvas grid (`height: calc(100% - 120px)`)
- **P1** Left column: 3 cards distributed with `justify-content:space-between`
- **P1** Right column: compliance card (flex:2) + team card (flex:1) at matched heights
- **P3** Body sized to 22px in the upper cards for projection readability
- **P3** Compliance disclaimer line moved into the card itself rather than below

#### Slide 4 — CPA day
- **P1** Banner exhibit fills the canvas; caption + source band styled consistently
- **P2** Removed forced 560px max-height on the banner image
- **P3** Source line tightened: "Baseline: CPA shadow sessions, weeks 4–6 · target state validated against beta cohort"

#### Slide 5 — Problem sized
- **P1** Full canvas-fill rebuild: 40/60 grid at `calc(100% - 200px)`
- **P1** Left column hero stats at 24px paragraphs; right card stats at 72px (was 56)
- **P1** Right card: working-hypothesis quote with attribution moved into a divided section
- **P3** Subtitle added: "User pain on one side, business pain on the other — and a single 73% number that became the wedge"

#### Slide 6 — Section divider 02
- **P3** Standardized with divider system

### Section 02 — Research

#### Slide 7 — Voices from the field
- **P1** Exhibit caption gives 4-quote breakdown; banner preserved as-is
- **P3** Synthesis row at bottom anchored at max-width 1400; reads as section closer

#### Slide 8 — Research method
- **P1** Two banner exhibits stacked, each flex:1 — fills canvas instead of 380px caps
- **P3** Captions tightened to mono-uppercase

#### Slide 9 — V1 rejection (0 of 6)
- **P1** Dark card on left fills 60% with full bleed; "0 / 6" big-stat at 84px
- **P1** Right column "What we initially thought" + "What we were wrong about" composition
- **P3** Added "→ Next slide" cue at bottom of right column

#### Slide 9b — Diagnosis
- **P1** Symmetrical to slide 9 — same 60/40 grid composition
- **P1** Big-stat "6 / 6" in teal; stat breakdown grid below
- **P3** Right column composition mirrors slide 9 (intentional)

#### Slide 10 — Joint session move
- **P1** Three quote-cards stacked left (CTO week 7 → Sean week 7 → CTO week 8); synthesis board card right
- **P1** Synthesis board uses 3-pin chip row + dark decision tag
- **P3** Reconstruction note in mono caption

#### Slide 11 — Section divider 03
- **P3** Standardized

### Section 03 — Solution

#### Slide 12 — Three principles
- **P1** 3-column grid; principle-cards at min-height 460 (was 380)
- **P1** Title moved out of card and into `.pc-title` element at 28px
- **P3** Bottom mono band at max-width 1200 anchors the slide

#### Slide 13 → Position 14 — The solution (3-tier confidence system)
- **P1** Renamed function to s14_ to enforce deck position
- **P1** Tier badge grid at fixed 600px height; badges scale to fit width
- **P1** "Three different denominators" disclaimer card at bottom
- **P2** `.tier-badge-grid` rule: align-items stretch; cells centered

#### Slide 13b → Position 15 — Thresholds (P0 BUG FIX)
- **P0** **Bar chart rebuilt as inline SVG** — v17.2 had broken HTML/CSS bars rendering at zero height
- **P0** SVG dimensions: 720×380 viewBox; bars at proportional heights 33%/52%/89%
- **P1** Left column: 4 threshold options with proper card-flat treatment + rejected/adopted pills
- **P1** Right column: chart + footer with `[FABRICATED-PLAUSIBLE]` flag preserved
- **P1** Bottom anchor band: "Thresholds aren't arbitrary"

#### Slide 28 → Position 16 — Rule Builder management
- **P1** 60/40 grid: production capture + 3-block narrative
- **P3** Caption: "Rule Engine · active rules + conflict detection · audit logged"

#### Slide 28b → Position 17 — Merge modal (rule authoring)
- **P1** 60/40 grid with production capture left; conditions/actions/preview narrative right
- **P3** "Paired with previous slide" card at bottom-right

#### Slide 32 → Position 18 — Information architecture
- **P1** 60/40 grid; IA diagram + commentary
- **P3** "IA is the augmentation principle in structure" anchor card

#### Slide 14 → Position 19 — Token foundation
- **P1** Full-bleed exhibit with proper cap framing; kills hard-coded heights

#### Slide 14b → Position 20 — Two regimes (WCAG + IRS)
- **P1** **Ghost watermark killed** (was reading as decoration; semantically meaningless)
- **P1** 50/50 grid; two cards with top-border accents (P2 blue / navy)
- **P1** Tradeoff cards at bottom of each (left-border accent matching)

#### Slide 15 → Position 21 — UI evolution
- **P1** Full-bleed exhibit; kills 560px hard-cap

#### Slide 16-new → Position 22 — Before / After
- **P1** 50/50 grid with two exhibits; 3-pin strip below
- **P3** Captions differentiate (miss-amber dot / teal dot)

#### Slide 16 → Position 23 — Transactions
- **P1** HTML mock with all 14 rows preserved (full mock fidelity)
- **P2** `.tx-table` padding tightened to 7px so 14 rows fit at 1080
- **P1** Right column: 4 pin annotations + sample-size note at bottom
- **V2** Extended to 1200px in flex variant — gives table ~120px breathing room

#### Slide 17 → Position 24 — Audit drawer
- **P1** 62/38 grid; drawer image + 5-category reason taxonomy
- **P3** Tag-category pills used for taxonomy markers

#### Slide 18 → Position 25 — Wallet upload
- **P1** 60/40 grid; problem/redesign/outcome stack on right
- **P3** "Honest note" card preserved at bottom; [ASSUMED] flag intact

### Section 04 — Outcomes

#### Slide 19 → Position 26 — Section divider 04
- **P3** Standardized

#### Slide 19b → Position 27 — Partnership
- **P1** 60/40 grid; dark card left (cadence + venue grid) + 3 artifact cards right
- **P1** `[ASSUMED — PR ref pending]` flag preserved on token artifact

#### Slide 20 → Position 28 — Four numbers
- **P1** 4-up metric grid + comparison table below
- **P3** Table uses 4-column "what it means / what it doesn't prove / source" pattern
- **P3** [ASSUMED] flag inline on onboarding source

#### Slide 21 → Position 29 — Two misses
- **P1** 50/50 grid; two miss-cards with top-border miss-amber
- **P1** Each card: what shipped / what should have shipped / principle that surfaced
- **P3** Honest-miss framing preserved verbatim (staff-level credibility signal)

#### Slide 22 → Position 30 — Section divider 05
- **P3** Standardized

### Section 05 — Appendix (Cuttable backup pack + Year 2 + Closing)

#### Slide 23 → Position 31 — Personas
- **P1** [CUTTABLE] chip in slide-tag (visible badge)
- **P1** 50/50 grid; two persona cards; flex:1 sections (goals / pain / surfaces)

#### Slide 24 → Position 32 — Attribution
- **P1** 40/60 grid; role context + ownership table
- **P3** STRONG/MODERATE strength labels preserved

#### Slide 25 → Position 33 — Counterfactual
- **P1** 50/50 grid; descope (amber) + accelerate (teal) cards

#### Slide 26 → Position 34 — Onboarding method caveats
- **P1** 50/50 grid; method left, caveats right (with honest-framing card)

#### Slide 27 → Position 35 — Competitive
- **P1** Full-bleed exhibit; kills hard-cap

#### Slide 29 → Position 36 — Timeline
- **P1** Full-bleed exhibit on soft background

#### Slide 31 → Position 37 — Three threads
- **P1** 3-column grid using principle-card pattern (consistent with slide 12)

#### Slide 32-year2 → Position 38 — Year 2 thesis
- **P1** 3-column grid; each move-card has "Extends: [principle]" footer
- **P3** Anchor band: "Each move extends a principle the system already enforces"

#### Slide 33 → Position 39 — Closing
- **P1** Centered cover-style layout; 80px H1 over two lines
- **P1** Three principle pills centered + signature block
- **P3** No anchor footer (closing slide is its own anchor)

---

## V2 (FHD-flex) extension rationale

**Only one slide extends beyond 1080:** slide-16 (Transactions, deck position 23) → 1200px.

Reasoning: 14 transaction rows + 4 pin annotations + sample-size note + bottom anchor zone compose without overflow at 1080, but feel cramped. 1200px gives the table ~120px of vertical breathing room without changing horizontal composition.

Other dense candidates considered but kept at 1080:
- **13b Thresholds** — 4-option left list + chart right + anchor band compose adequately at 1080.
- **14b Regimes** — 4-bullet lists + tradeoff cards compose adequately at 1080.
- **19b Partnership** — dark card + 3 artifact cards compose adequately at 1080.

Half-the-deck-at-1400 would look like sprawl, not deliberation. Extension is a feature for the one slide where 1080 forces a real compromise.

**Presentation strategy recommendation:**
- For projection: use V1 (FHD-fixed) — single aspect, no scaling surprises
- For web/browser presentation: use V2 (FHD-flex) — per-slide scale-to-fit
- For PDF export: V1 → Chrome `--print-to-pdf` produces clean 39-page PDF at 1920×1080
- For Decktape per-slide export: V2 → per-slide Decktape calls with correct heights

---

## Build artifacts

- `/home/claude/v18/01_shell_head.html` — CSS shell (tokens + components + nav)
- `/home/claude/v18/slides_*.py` — modular slide builders (6 files)
- `/home/claude/v18/assemble.py` — V1 builder
- `/home/claude/v18/assemble_v2.py` — V2 builder
- `/home/claude/asset_uris.pkl` — base64 image manifest (preserved from v17.2)
- `/home/claude/notes_by_id.pkl` — speaker notes manifest (preserved from v17.2)

## Verification

- All 39 slides render at 1920×1080 (V1) with zero overflow (measured with Playwright at scale 1.0)
- V2 slide-16 renders at 1920×1200 as designed; all other V2 slides at 1920×1080
- All 19 of 20 source images re-embedded verbatim (1 intentionally dropped: the slide-14b regimes ghost watermark, per Creation Decisions Log CD-07 — it read as decoration, not signal)
- All 39 speaker notes round-tripped (HTML-entity-encoded data-notes attributes preserved)
- All preservation flags intact: `[ASSUMED]`, `[DATA NEEDED]`, `[FABRICATED-PLAUSIBLE]`, `[ASSUMED — PR ref pending]`, `[CUTTABLE]`
- Honest miss (Rule Builder v1 failure) prominent on slide 29 (deck position) — staff-level credibility preserved
- Anchor "SEAN SMITH · smithdesign.live" present on every content slide; cover keeps triple anchor `· computis.netlify.app`
- Cover H1 (Computis) at 96px tested as commanding at FHD
