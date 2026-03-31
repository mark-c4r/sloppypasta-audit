# Sloppypasta Audit — 7-Slice Implementation PRDs

**Parent plan**: `tidy-stargazing-steele.md`
**Repo**: `~/Coding/sloppypasta-audit/`
**Ships as**: Self-contained Claude Code skill + public open-source framework
**Parallelization**: V2 and V3 are independent (can run simultaneously). V4 depends on V1+V2+V3. V5 depends on V4. V6 depends on V5. V7 depends on all.

```
V1 ──────┐
          ├──→ V4 ──→ V5 ──→ V6 ──→ V7
V2 ──────┤
V3 ──────┘
```

---
---

## SLICE V1: CHECK INVENTORY

### 1. Objective

Produce the DEFINITIVE numbered check list for the Sloppypasta Audit V1. This is the single source of truth that every subsequent slice references. It resolves all overlaps identified by expert reviewers, restores 3 checks that were lost between V1 and V2 of the framework design, adds conditional activation tags to checks that only apply to certain product types, and filters the full ~59-check V3 inventory down to the ~39 HIGH-measurability checks that ship in V1.

This matters because every downstream artifact — scale anchors, detection references, the skill itself, the framework document — must reference a stable, numbered, non-contradictory check list. If this list has overlaps, gaps, or ambiguities, they propagate into every other slice.

### 2. Inputs

Read these files before starting:

- **Plan file**: `/Users/profile_1/.claude/plans/tidy-stargazing-steele.md`
  - Lines 110-135: "FINAL V1 SCOPE" — the expert-consensus check set with category counts
  - Lines 884-999: "COMPLETE CHECK INVENTORY (V3 Final)" — the full 59-check inventory with measurability ratings
  - Lines 1189-1243: "EXPERT REVIEW FINDINGS" — the 5 overlap clusters to resolve and 3 checks to restore
  - Lines 845-881: Conditional check activation rules and app-specific checks
  - Lines 1019-1035: Behavioral tells that integrate into existing checks (not new checks)

- **Existing synthesis**: `/Users/profile_1/Coding/sloppypasta-audit/docs/synthesis.md`
  - Lines 1-8: The axioms — keep these as philosophical anchors
  - Lines 22-108: The old V1 category structure (8 categories, 47 checks) — this is what gets replaced

### 3. Deliverables

**One file**: `/Users/profile_1/Coding/sloppypasta-audit/docs/check-inventory.md`

Contents:
- Title: "Sloppypasta Audit — V1 Check Inventory"
- Version note: "This is the definitive V1 check list. All scale anchors, detection references, and the audit skill reference this document."
- 8 category sections, each containing:
  - Category number, name, and tagline (e.g., `Cat 1: Slop Detection — "Can you smell the AI?"`)
  - V1 weight for the category
  - Table with columns: `#`, `Check`, `Measurability`, `Condition`, `Notes`
  - Only HIGH measurability checks (this is the V1 filter)
- A summary table at the bottom: category, check count, weight
- A "Conditional Activation" reference section explaining the tag system
- A "Deferred to V2" section listing the MEDIUM/LOW checks that were explicitly excluded and why

### 4. Steps

**Step 1: Resolve the 5 overlap clusters.**

Apply each resolution from the expert review (plan lines 1230-1236):

| Overlap | Resolution |
|---------|------------|
| 1.2 (Visual monoculture) overlaps 3.1 (Visual distinctiveness) | Drop 1.2 from Cat 1. Visual assessment lives in Cat 3 only. Cat 1 stays text-focused. 3.1 absorbs the visual monoculture markers (Inter font, purple gradients, card grids). |
| 4.5 (Aerodynamic) overlaps 4.2 (Half not half-assed) | Merge 4.5 into 4.2. They measure the same construct: deliberate restraint in feature set. 4.2's description expands to include "nothing extraneous, can identify what was deliberately left out." |
| 1.4 (Bot engagement) + 1.5 (Dead internet) + 7.6 (Earned audiences) | Consolidate into one check: "1.4 Social authenticity" in Cat 1. Measures: are engagement metrics real? Are followers human? Is community genuine vs manufactured? Covers bot detection, dead internet signals, and audience legitimacy in one check. Remove 1.5 from Cat 1 and 7.6 from Cat 7. |
| 6.7 (Information asymmetry) overlaps 5.5 (Surveillance) | Remove 6.7. The concept (product knows more about you than you know about it) is already captured by the 5.5 privacy composite's tracker counting and shadow profiling sub-checks. |
| 8.5 (Curation rewarded) — LOW-MED measurability | Add `[if:social]` conditional tag. This check is nearly always N/A for non-social products, and even for social products the measurability is weak. |

**Step 2: Restore 3 lost V1 checks.**

These existed in the original V1 (synthesis.md) but were dropped during the V2/V3 restructuring. The expert reviewers flagged them as meaningful:

| Original ID | Check | Restore To | V1 Number | Notes |
|-------------|-------|------------|-----------|-------|
| CI-5 | Provenance traceable — signed, timestamped, attributed | Cat 6 (Sovereignty) | 6.X (assign next available) | Cryptographic provenance is a sovereignty signal, not a slop signal. Add condition `[if:content]`. |
| CC-2 | Iteration visible — changelogs, hard decisions documented | Cat 4 (Craft) | 4.X (assign next available) | Ship-ugly-iterate-publicly requires visible iteration. HIGH measurability: check for changelog, release notes, visible commit history. |
| VH-4 | Dialogue, not broadcast — can you talk back? | Cat 7 (Honesty) | 7.X (assign next available) | Measures whether there is a feedback channel: reply mechanism, issue tracker, public discussion. `[if:content]` conditional. HIGH measurability. |

**Step 3: Add conditional tags.**

Apply these tags to the checks identified in the expert review and plan:

| Check | Tag | Rationale |
|-------|-----|-----------|
| 5.6 (RSS or equivalent) | `[if:content]` | Static tools, protocols, CLI apps have no content feed. |
| 6.9 (Algorithm transparency) | `[if:feed/social]` | Only applies to products with algorithmic feeds. |
| 8.5 (Curation rewarded) | `[if:social]` | Per overlap resolution above. |
| 2.4 (No throat-clearing) | `[if:content]` | Products with no editorial content (pure tools) should not be penalized. |
| 5.5f (Minimal permissions) | `[if:mobile]` | Already tagged in plan. |
| 5.5g (Telemetry opt-in) | `[if:mobile]` | Already tagged in plan. |
| 5.5h (No background data collection) | `[if:mobile]` | Already tagged in plan. |
| 6.12-6.17 | Various `[if:mobile]`, `[if:identity]`, `[if:messaging/social]`, `[if:payments]` | Already tagged in plan. Keep as-is. |

**Step 4: Filter to HIGH measurability only.**

The V1 scope ships only HIGH-measurability checks. Walk through each category and include only checks rated HIGH. The target count per category (from the expert consensus):

| Cat | Target Count | Notes |
|-----|-------------|-------|
| 1 Slop Detection | 3 | 1.1 (text smell), 1.4 (social authenticity — merged), plus one more if available |
| 2 Writing | 3 | 2.1 (economy — promoted with banned-word frequency), 2.2 (copy as interface), 2.4 (throat-clearing) |
| 3 Design | 6 | 3.2, 3.3, 3.6, 3.7, 3.8, 3.9. Drop 3.1 and 3.4 (both MEDIUM). 3.5 moved to Cat 5. |
| 4 Craft | 3 | 4.1 (opinionated), 4.3 (shipped ready), 4.7 (show me the code). 4.2 merged from 4.5. 4.4 is HIGH — include if count allows. Restored CC-2 (iteration visible) also HIGH. |
| 5 Conduct | 10 | 5.1-5.5, 5.6[if:content], 5.7, 5.9, 5.10, plus 3.5 (dark patterns, moved here) |
| 6 Sovereignty | 7+ | 6.1-6.4, 6.6, 6.10, 6.11 + conditionals. Restored CI-5 (provenance). |
| 7 Honesty | 4 | 7.1-7.3, 7.7. Restored VH-4 (dialogue). |
| 8 Economic | 3 | 8.1, 8.2, 8.4 |

Note: The expert consensus says "~39 + conditionals." The exact count will emerge from applying the filter. Do not force the count — let it land naturally after the overlap resolutions and restorations.

**Step 5: Assign final V1 numbers.**

Renumber all checks sequentially within each category. The numbering scheme is `{category}.{sequential}` (e.g., 1.1, 1.2, 1.3; 2.1, 2.2, 2.3). Include a mapping table from V3 numbers to V1 numbers for traceability.

**Step 6: Write the 5.5 privacy composite specification.**

Check 5.5 is a composite of 8 sub-checks that compute a single score:

| Sub-check | Condition | What it measures |
|-----------|-----------|-----------------|
| 5.5a | Universal | Cookie count (zero ideal, first-party session OK, third-party = bad) |
| 5.5b | Universal | Third-party tracker count (network inspector, zero = ideal) |
| 5.5c | Universal | Analytics philosophy (none > self-hosted privacy > hosted privacy > GA > GA+multi) |
| 5.5d | Universal | Cookie consent quality (no banner needed = best > reject-all prominent > accept-all dark pattern) |
| 5.5e | Universal | Do-not-track / DNT respect |
| 5.5f | `[if:mobile]` | Minimal permissions (only what's needed) |
| 5.5g | `[if:mobile]` | Telemetry opt-in (not opt-out) |
| 5.5h | `[if:mobile]` | No background data collection |

The composite 5.5 score = geometric mean of applicable sub-checks. Document this.

**Step 7: Write the weight table.**

Category weights from the plan (set from philosophy, not optimized):

| Category | Weight |
|----------|--------|
| 1 Slop Detection | 15% |
| 2 Writing | 10% |
| 3 Design | 10% |
| 4 Craft | 10% |
| 5 Conduct | 15% |
| 6 Sovereignty | 20% |
| 7 Honesty | 10% |
| 8 Economic | 10% |

Note: These weights differ from the old V1 synthesis.md weights because the category structure changed. Sovereignty + Conduct together = 35% (the structural dimension). Slop Detection + Writing + Design = 35% (the craft dimension). Honesty + Craft + Economic = 30% (the character dimension). This follows the "set from philosophy" directive: structural sovereignty weighs most, craft matters, character closes the gap.

**Step 8: Write the deferred-to-V2 section.**

List every check from the V3 inventory that did NOT make the V1 cut, with its measurability rating and a one-line reason:

- 1.3 Mid-curve convergence (MEDIUM) — needs reference examples to score repeatably
- 2.3 Proof of thought (MEDIUM) — requires deep reading, not surface check
- 2.5 Distinctive voice (MEDIUM) — subjective, needs multi-agent consensus
- 2.6 Writing shows study (LOW-MED) — too judgment-dependent for V1
- 3.1 Visual distinctiveness (MEDIUM) — absorbed visual monoculture markers, rest is subjective
- 3.4 Intentional hierarchy (MEDIUM) — needs trained eye, not binary
- 4.1 Opinionated software (MEDIUM) — borderline; include if strong anchor written
- 4.2 Half not half-assed (MEDIUM) — borderline; same
- 4.4 Orphaned features (HIGH) — include in V1 if under count target
- 4.5 Aerodynamic — merged into 4.2
- 4.6 Build for decades (MEDIUM) — dependency audit requires builder mode
- 5.8 Resilience to takedown (MEDIUM) — hard to test externally
- 6.5 Namespace independence (MEDIUM) — jargon, hard to score
- 6.8 Economic privacy (MEDIUM) — borderline; may upgrade
- 6.9 Algorithm transparency (MED-HIGH, conditional) — keep if conditional tagging works
- 7.4 Marketing as enthusiasm (MEDIUM) — judgment call
- 7.5 Honest about limitations (MEDIUM) — vague
- 7.6 Earned audiences — merged into 1.4
- 8.3 Creator value flows through (MEDIUM) — hard to verify externally
- 8.5 Curation rewarded (LOW-MED, conditional) — nearly always N/A

**Step 9: Final review.**

Before finishing, verify:
1. No check appears in two categories
2. Every check has a measurability rating of HIGH
3. Every conditional tag has its activation condition documented
4. The 5.5 composite sub-checks are fully specified
5. The weight table sums to 100%
6. The deferred list accounts for every V3 check not in the V1 list
7. Total V1 check count is in the 35-42 range (the expert consensus target of "~39 + conditionals")

### 5. Acceptance Criteria

- [x] File exists at `/Users/profile_1/Coding/sloppypasta-audit/docs/check-inventory.md`
- [x] All 5 overlap clusters are resolved (no duplicate concepts across categories)
- [x] 3 restored checks (provenance, iteration visible, dialogue) are present with category assignments
- [x] Every check has a `Condition` column entry (either `Universal` or a specific tag)
- [x] Only HIGH-measurability checks are in the V1 list
- [x] Check count is 35-42 (excluding conditional-only checks)
- [x] Weight table sums to 100%
- [x] Deferred-to-V2 section lists every excluded check with reason
- [x] V3-to-V1 number mapping table is present
- [x] 5.5 composite sub-check specification is complete

### 6. Dependencies

None. This is the first slice. It depends only on the plan file.

### 7. Estimated Time

30-45 minutes.

---
---

## SLICE V2: SCALE ANCHORS

### 1. Objective

Write behavioral scoring anchors for every V1 check at 5 levels: 0%, 25%, 50%, 75%, 100%. These anchors are what make the audit repeatable — two different auditors reading the same anchors should score the same product within 10 points. Without them, every score is subjective opinion.

The Product Scientist's methodology applies: behavioral descriptions first, product examples second. Anchor from extremes inward — define 0% and 100% first (these are the easiest to describe), then 50% (the midpoint), then 25% and 75% (the in-betweens).

### 2. Inputs

- **V1 check inventory**: `/Users/profile_1/Coding/sloppypasta-audit/docs/check-inventory.md` (produced by V1)
- **Plan file**: `/Users/profile_1/.claude/plans/tidy-stargazing-steele.md`
  - Lines 1059-1067: Phase 2 scale anchor methodology (0% = hostile, 25% = bad, 50% = mediocre, 75% = good, 100% = ideal)
  - Lines 1019-1035: Behavioral tells that should appear as scoring examples in specific anchors (3.7, 3.9, 4.3, 4.7)
  - Lines 1103-1184: Detection reference lists (visual markers, text markers, behavioral tells, tool fingerprints) — use these as concrete examples in anchors
- **Existing synthesis axioms**: `/Users/profile_1/Coding/sloppypasta-audit/docs/synthesis.md` lines 1-18

### 3. Deliverables

**8 files**, one per category, at `/Users/profile_1/Coding/sloppypasta-audit/docs/scale-anchors/`:

| File | Contents |
|------|----------|
| `cat1-slop-detection.md` | Anchors for all Cat 1 V1 checks |
| `cat2-writing.md` | Anchors for all Cat 2 V1 checks |
| `cat3-design.md` | Anchors for all Cat 3 V1 checks |
| `cat4-craft.md` | Anchors for all Cat 4 V1 checks |
| `cat5-conduct.md` | Anchors for all Cat 5 V1 checks |
| `cat6-sovereignty.md` | Anchors for all Cat 6 V1 checks |
| `cat7-honesty.md` | Anchors for all Cat 7 V1 checks |
| `cat8-economic.md` | Anchors for all Cat 8 V1 checks |

Each file follows this structure:

```markdown
# Cat N: [Name] — Scale Anchors

Reference: check-inventory.md

## N.1 [Check Name]

**What it measures**: [One sentence]

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0%  | [Actively hostile behavior. Reserved for worst case.] | [Real product at this level] |
| 25%  | [Bad but not hostile. Present but inadequate.] | [Real product at this level] |
| 50%  | [Mediocre. Meets minimum but nothing more.] | [Real product at this level] |
| 75%  | [Good. Clear effort, minor gaps.] | [Real product at this level] |
| 100% | [Ideal. Best known implementation.] | [Real product at this level] |

**Scoring notes**: [Any special instructions for the auditor — what to look at, where to check, edge cases]

---

## N.2 [Check Name]
[same format]
```

### 4. Steps

**Step 1: Create the directory.**

```
mkdir -p ~/Coding/sloppypasta-audit/docs/scale-anchors/
```

**Step 2: Write anchors using the extremes-inward method.**

For each check in the V1 inventory, write anchors in this order:
1. Write the **0%** anchor first — what does actively hostile look like?
2. Write the **100%** anchor — what is the ideal?
3. Write the **50%** anchor — what is the midpoint between hostile and ideal?
4. Write the **25%** anchor — worse than mediocre but not hostile
5. Write the **75%** anchor — better than mediocre but not ideal

**Step 3: Use real product examples where possible.**

The plan and user conversations provide these calibration reference points:

| Product | Expected Range | Use As Example For |
|---------|---------------|-------------------|
| Instagram | 0% access gates (fuck-you login wall) | 5.1 at 0%, 5.4 at 0-10% (infinite scroll, dopamine), 6.3 at 10% (phone/gov ID) |
| Twitter/X | F range (20-30% overall) | Various low scores across honesty, conduct, sovereignty |
| ppq.ai | 100% pay-per-service | 8.2 at 100%, 8.1 at 95-100% |
| Boris | B range (65-75% overall) | Good craft, good sovereignty, honest |
| Basecamp | Good craft, honest business model | 4.1 at 85-90% (opinionated), 7.1 at 90%+ (business model visible), 2.2 at 85%+ (copy as interface) |
| Signal | Good privacy, not Bitcoin-native | 5.5 at 90%+, 6.3 at 70% (phone number required) |
| ChatGPT | Mixed — good craft, bad sovereignty | 4.3 at 80%+ (shipped ready), 6.1 at 15% (rugpull risk), 6.4 at 5% (platform) |
| Nostr clients (Damus, Primal, etc.) | Protocol-native, variable craft | 6.4 at 95-100% (protocol), variable on craft and conduct |

**Step 4: Write specific behavioral tells into the anchors for checks 3.7, 3.9, 4.3, and 4.7.**

Per plan lines 1019-1035, these behavioral tells are scoring examples, not new checks:

- **3.7 Self-evident UI**: dead-end empty states ("No items found" with no CTA) = 25% or below
- **3.9 Accessibility basics**: broken focus states (outline-none with no replacement) = 25% or below
- **4.3 Shipped ready**: spinner trap (no optimistic UI), brutal error handling ("Something went wrong"), placeholder data in production = 25% or below
- **4.7 Show me the code**: console.log("here") in production, inline styles mixed with Tailwind = 25% or below

**Step 5: Write the 5.5 composite anchors.**

The 5.5 privacy composite has 8 sub-checks. Write anchors for each sub-check individually, then add a note explaining the composite scoring:

> "5.5 composite score = geometric mean of applicable sub-check scores. For web-only products, sub-checks 5.5f, 5.5g, 5.5h are N/A and excluded. The composite score uses the 5% floor (minimum score is 5, not 0) to prevent a single privacy failure from zeroing the entire category."

**Step 6: Apply the 5% floor note globally.**

Add a note at the top of each file:

> "Scoring floor: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension."

**Step 7: Review each file for slop.**

Before finishing each file, re-read it and check:
- Are the behavioral descriptions specific enough that two auditors would agree?
- Are there any weasel words, throat-clearing, or filler?
- Does every sentence earn its place?
- Do the 5 levels actually differentiate (or do 25% and 50% sound the same)?

### 5. Acceptance Criteria

- [x] 8 files exist in `/Users/profile_1/Coding/sloppypasta-audit/docs/scale-anchors/`
- [x] Every V1 check has exactly 5 anchor levels (0/25/50/75/100)
- [x] Behavioral descriptions come before product examples in every anchor
- [x] 0% and 100% are written first and are clearly extreme (hostile vs ideal)
- [x] 50% is genuinely the midpoint, not just "average"
- [x] Real product examples are used wherever the plan provides them
- [x] Behavioral tells from plan lines 1019-1035 appear in checks 3.4, 3.6, 4.1, 4.3 (V1 numbers)
- [x] 5.5 composite sub-checks each have individual anchors
- [x] 5% floor note appears at the top of each file
- [x] No slop in the writing itself — no weasel words, filler, or throat-clearing

### 6. Dependencies

- **V1 (Check Inventory)** must be complete. V2 needs the definitive numbered check list.

### 7. Estimated Time

2-3 hours. This is the most labor-intensive slice. 8 files, each with 3-7 checks, each check with 5 levels plus scoring notes.

---
---

## SLICE V3: DETECTION REFERENCE

### 1. Objective

Package the detection markers from the brainstorm sessions into self-contained reference documents. These are the "cheat sheets" that the audit skill will load when scoring Cat 1 (Slop Detection), Cat 3 (Design), Cat 5 (Conduct), and Cat 6 (Sovereignty) checks. They must be usable without the brainstorm context — a fresh Claude Code session reading only these files should be able to detect slop markers.

### 2. Inputs

- **Plan file**: `/Users/profile_1/.claude/plans/tidy-stargazing-steele.md`
  - Lines 1103-1184: "AUTOMATED DETECTION REFERENCE" — the complete lists:
    - 49 banned words
    - 38 banned phrases
    - 16 banned openers
    - Punctuation thresholds (em-dashes, exclamation marks, Rule of Three, uniform sentence length, hedging seesaw)
    - Model-specific first words (ChatGPT, Claude, Grok, Gemini, DeepSeek)
    - Visual slop markers (CSS/layout: purple gradients, Inter font, card grids, hero patterns, rounded corners, dark+neon, gradient text)
    - Gemini additions (Shadcn/UI defaults, Bento Box grids, glassmorphism, Lucide icons, whitespace homogeneity, hidden scroll)
    - Writing slop additions (Bold Prefix bullets, Zoom Out openings, symmetrical paragraphs, Conclusion headers, Title Case abuse)
    - Behavioral/interaction tells (dead-end empty states, spinner trap, brutal errors, broken focus, window resize break)
    - Tool fingerprints (v0/Lovable, Cursor/Bolt.new)

- **V1 check inventory**: `/Users/profile_1/Coding/sloppypasta-audit/docs/check-inventory.md` (produced by V1)
  - Needed to cross-reference which checks each detection marker supports

### 3. Deliverables

**3 files** at `/Users/profile_1/Coding/sloppypasta-audit/docs/reference/`:

| File | Contents | Supports Checks |
|------|----------|-----------------|
| `slop-text-markers.md` | All text-based slop detection: banned words, phrases, openers, punctuation thresholds, structural patterns, model fingerprints | 1.1 (LLM smell), 2.1 (economy of words), 2.4 (throat-clearing) |
| `slop-visual-markers.md` | All visual/UI slop detection: CSS markers, layout patterns, behavioral tells, tool fingerprints | 1.2/3.1 (visual monoculture/distinctiveness), 3.6 (design consistency), 3.8 (modals), 4.3 (shipped ready) |
| `sovereignty-checks.md` | Sovereignty verification procedures: how to test rugpull resistance, exit cost, identity sovereignty, protocol vs platform, self-hosting, payment privacy | 6.1-6.17 (all sovereignty checks) |

### 4. Steps

**Step 1: Create the directory.**

```
mkdir -p ~/Coding/sloppypasta-audit/docs/reference/
```

**Step 2: Write `slop-text-markers.md`.**

Structure:

```markdown
# Text Slop Detection Reference

Self-contained reference for detecting AI-generated text in products.
Used by checks: 1.1, 2.1, 2.4

## Banned Vocabulary (49 words)

Score: Count occurrences per 1,000 words of product text. Frequency-based, not binary.
- 0 per 1k words = clean
- 1-2 per 1k words = minor tells
- 3-5 per 1k words = likely AI-generated
- 6+ per 1k words = almost certainly unedited AI output

[Full alphabetized list of 49 words from plan line 1122]

## Banned Phrases (38 phrases)

Score: Presence of 2+ phrases in any single page = significant AI tell.

[Full list from plan line 1124]

## Banned Openers (16 openers)

Score: Any product text (landing page, about page, docs, error messages, blog) opening with these = AI tell.

[Full list from plan line 1126]

## Punctuation Thresholds

| Marker | Threshold | Significance |
|--------|-----------|-------------|
| Em dashes | >1 per 500 words | Single most cited AI marker |
| Exclamation marks | >1 per 1,000 words | Over-enthusiasm tell |
| Rule of Three | Lists of exactly 3 items | AI defaults to 3-item lists |
| Uniform sentence length | 3+ consecutive same-length sentences | Human writing varies naturally |
| Hedging seesaw | "On one hand... on the other..." without taking a position | AI avoids commitment |

## Structural Patterns

- **"Bold Prefix:" Bullet List**: Every bullet formatted as **Bold Summary Phrase:** followed by one explanatory sentence. THE #1 formatting tell.
- **"Zoom Out" Opening**: Over-contextualizing macro-trends instead of getting to the point.
- **Symmetrical Paragraphs**: Every paragraph exactly 3-4 sentences. Human writing is chunky.
- **"Conclusion" Header**: Literal `## Conclusion` or `## Final Thoughts` header.
- **"Crucially"/"Importantly" Crutches**: Fake transition words masking non-sequiturs.
- **Title Case Abuse**: Capitalizing concepts for false authority.

## Model-Specific First Words

| Model | Common First Words |
|-------|--------------------|
| ChatGPT | as, yes, sure, here, in, to, creating, certainly |
| Claude | in, from, this, how, yes, according, based |
| Grok | step, introduction, yes, creating |
| Gemini | my, creating, while, here |
| DeepSeek | based, yes, step, comprehensive |

## How to Use This Reference

1. Sample text from 3+ product surfaces (landing page, error messages, docs, onboarding, about page)
2. Count banned vocabulary per 1,000 words
3. Check for banned phrases (2+ = significant)
4. Check first sentences for banned openers
5. Measure punctuation densities against thresholds
6. Check for structural patterns (Bold Prefix lists, symmetrical paragraphs)
7. Score: density and variety of markers determines the 1.1 score per the scale anchors
```

**Step 3: Write `slop-visual-markers.md`.**

Structure:

```markdown
# Visual Slop Detection Reference

Self-contained reference for detecting AI-generated visual design in products.
Used by checks: 3.X (design checks), 4.3 (shipped ready), 4.7 (show me the code)

## CSS/Layout Markers

Indicators that visual design was AI-generated without human refinement:

### Color
- Purple/indigo accent colors (`bg-indigo-*`, `#5E6AD2`-family) — Tailwind default infection
- Dark base (#0A0A0A) + neon accent — the "Linear aesthetic"
- Gradient text headlines (blue-to-purple)

### Typography
- Inter, Roboto, or generic system font as the ONLY font — no serif/sans pairing
- No typographic hierarchy beyond size changes

### Layout
- 3-column feature grid with centered icons — the SaaS template
- Hero: centered text + gradient + CTA button — same hierarchy everywhere
- `grid-cols-1 md:grid-cols-3` for everything (Bento Box default)
- No asymmetric or creative layouts anywhere

### Decoration
- Uniform rounded corners on all elements
- Subtle shadows at 0.1 opacity on all cards
- Gratuitous glassmorphism (`backdrop-blur-md bg-white/10`) on non-overlapping elements
- Unedited Lucide/Heroicon (2px stroke-width) next to every menu item

### Spacing
- Uniform `p-4`/`gap-4` everywhere — no optical grouping
- No tight header-paragraph coupling vs loose section spacing

## Component Framework Tells

- **Shadcn/UI Default**: slate-900 buttons, `rounded-md` everywhere, zero token customization. "The new Bootstrap."
- **v0/Lovable**: Sterile layouts. Placeholder data: "John Doe", "Jane Smith", dashboard metrics "+20.1% from last month." Generic bar charts.
- **Cursor/Bolt.new**: `console.log("here")` in production. Inline `style={{ marginTop: '10px' }}` mixed into Tailwind codebase.

## Behavioral/Interaction Tells

These are how AI-generated products BEHAVE, beyond appearance:

- **Dead-End Empty State**: "No items found." — no illustration, no empathy, no CTA
- **Spinner Trap**: Every button click → loading spinner → server round-trip. No optimistic UI.
- **Brutal Error Handling**: Generic "Something went wrong" toasts, no context, no retry
- **Broken Focus States**: `focus:outline-none` without `focus-visible:ring` replacement
- **Window Resize Break**: THE most reliable single marker. Drag browser to ~800px tablet width. Squashed columns, overlapping text = AI built for 375px and 1440px only.
- **Hidden Scroll**: `scrollbar-hide` with zero visual affordance that content is scrollable

## Quick Check: Single Most Reliable Markers

- **Text**: The "Bold Prefix:" list structure
- **Visual**: The Window Resize Test (drag browser width slowly)

## How to Use This Reference

1. Visit the product in a browser
2. Check CSS: font-family, primary colors, border-radius values, shadow values
3. Count purple/indigo color instances
4. Check layout: is it a 3-column grid? Is the hero centered-text + gradient + CTA?
5. Test at 800px viewport width (tablet) — does it break?
6. Check empty states, error states, loading states
7. Score: density of markers determines the design check scores per scale anchors
```

**Step 4: Write `sovereignty-checks.md`.**

Structure:

```markdown
# Sovereignty Verification Reference

Self-contained reference for testing product sovereignty and privacy.
Used by checks: 6.1-6.17 (all sovereignty checks), 5.5 (privacy composite)

## Rugpull Resistance (6.1)

Test: Can the operator unilaterally...
- Lock you out of your account?
- Change terms of service retroactively?
- Seize or freeze your assets/data?
- Shut down the service with no migration path?

Method: Read ToS. Check for "we may terminate at any time" clauses. Check for asset custody model.

## Exit Cost (6.2)

Test: Can you leave with everything?
- Is there an export function?
- What formats does it export? (Standard = JSON, CSV, markdown. Proprietary = bad.)
- Can you export your social graph?
- How long does export take? (Instant = good. "Request and wait 30 days" = bad.)

Method: Actually try to export. Time it. Check formats.

## Identity Sovereignty (6.3)

Scale (score directly from this):
- 100%: Keypair-based identity (Nostr nsec/npub, Bitcoin keys)
- 75%: Minimal account (username only, no email required)
- 50%: Email required, no verification
- 35%: Email + verification required
- 20%: Phone number required
- 5%: Government ID required (always lowest — never higher regardless of other factors)

Method: Go through signup flow. Note every piece of identity information required.

## Protocol vs Platform (6.4)

Test: What happens if this company disappears tomorrow?
- 100%: Open protocol — any client can connect (Nostr, Bitcoin, email, RSS)
- 75%: Open-source with federated instances (Mastodon, Matrix)
- 50%: Open-source but single-instance dominance
- 25%: Proprietary with documented API
- 5%: Proprietary, closed, single point of failure

Method: Check architecture docs. Is there a protocol spec? Multiple clients?

## Self-Hostable (6.6)

Test: Can you run your own instance?
- Check: Docker/install instructions available?
- Check: License allows self-hosting?
- Check: Documentation for self-hosting exists and is maintained?
- Fallback: Is source code at least readable/auditable?

## Privacy Payment (6.10)

Test: Can you pay without revealing identity?
- 100%: Lightning/ecash/Monero accepted — no identity linkage
- 75%: Bitcoin on-chain accepted (pseudonymous but traceable)
- 50%: Crypto accepted but requires account with email
- 25%: Credit card only but no unnecessary data collection
- 5%: Credit card + full identity verification + data sharing with third parties

## Source Availability (6.11)

Scale:
- 100%: FOSS with active development (commits, issues, PRs)
- 75%: Source-available with restrictive license (BSL, SSPL)
- 50%: Partial source (core open, proprietary additions)
- 25%: Proprietary but free to use
- 5%: Proprietary, paid, closed

## Conditional Sovereignty Checks

### Distribution Independence (6.12) [if:mobile]
- 100%: Sideloadable APK + F-Droid
- 75%: App Store + sideload option
- 50%: App Store only but no lock-in features
- 5%: App Store only, uses platform-locked APIs

### Play Services Independence (6.13) [if:mobile]
- 100%: Works fully on GrapheneOS/CalyxOS
- 50%: Core features work, push notifications don't
- 5%: Requires Google Play Services, won't launch without

### Key Management (6.15) [if:identity]
- 100%: NIP-07/NIP-46 external signing (keys never touch the app)
- 75%: App holds key with export/backup option
- 50%: App holds key, no export
- 5%: Custodial (platform holds your keys)

### Custodial vs Non-Custodial (6.17) [if:payments]
- 100%: Non-custodial (you hold keys, you sign transactions)
- 50%: Custodial with withdrawal (like an exchange)
- 5%: Fully custodial, no withdrawal to self-custody

## How to Use This Reference

1. For each applicable sovereignty check, follow the test procedure
2. Score using the scales provided (they map directly to the scale anchors)
3. For conditional checks, first determine if the condition applies
4. If a condition does not apply, mark the check N/A (excluded from geomean)
5. If a condition applies and the check scores poorly, it penalizes the score
```

**Step 5: Cross-reference against V1 inventory.**

After writing all 3 files, verify that every V1 check that relies on detection markers has a corresponding section in one of these reference docs. Specifically:

| Check | Must Be Covered In |
|-------|--------------------|
| 1.1 LLM smell | slop-text-markers.md |
| 2.1 Economy of words | slop-text-markers.md (banned word frequency) |
| 2.4 No throat-clearing | slop-text-markers.md (banned openers) |
| 3.X Design checks | slop-visual-markers.md |
| 4.3 Shipped ready | slop-visual-markers.md (behavioral tells) |
| 4.7 Show me the code | slop-visual-markers.md (tool fingerprints) |
| 5.5 Privacy composite | sovereignty-checks.md |
| 6.1-6.17 Sovereignty | sovereignty-checks.md |

### 5. Acceptance Criteria

- [x] 3 files exist in `/Users/profile_1/Coding/sloppypasta-audit/docs/reference/`
- [x] `slop-text-markers.md` contains: 49 banned words (alphabetized), 38 phrases, 16 openers, punctuation thresholds with numeric values, structural patterns, model-specific first words, scoring methodology
- [x] `slop-visual-markers.md` contains: CSS/layout markers organized by type (color, typography, layout, decoration, spacing), component framework tells, behavioral/interaction tells, quick-check markers
- [x] `sovereignty-checks.md` contains: test procedures for every Cat 6 check, scoring scales that map to scale anchors, conditional check activation rules
- [x] Each file has a "How to Use This Reference" section
- [x] Each file lists which checks it supports
- [x] All content is self-contained — no references to "the brainstorm" or "the plan" or external context
- [x] Banned word frequency is per-1000-words (relative), not binary presence
- [x] No slop in the writing itself

### 6. Dependencies

- **V1 (Check Inventory)** must be complete. V3 needs the definitive check numbers to cross-reference.
- V3 is independent of V2 (Scale Anchors). They can run in parallel.

### 7. Estimated Time

45-60 minutes. The content already exists in the plan — this slice is mostly organization and packaging, not original creation.

---
---

## SLICE V4: SKILL + SCORING

### 1. Objective

Build the working Claude Code skill that runs the Sloppypasta Audit. A user invokes it with a product URL or name, and it walks through every V1 check, scores each 0-100, computes category geometric means, computes the weighted overall geometric mean, assigns a letter grade, and outputs a markdown scorecard with category breakdowns and improvement suggestions.

This is the core deliverable of the entire project. Everything else (inventory, anchors, references, calibration, docs) exists to make this skill produce accurate, repeatable, useful scores.

### 2. Inputs

- **V1 check inventory**: `/Users/profile_1/Coding/sloppypasta-audit/docs/check-inventory.md` (from V1)
- **Scale anchors**: `/Users/profile_1/Coding/sloppypasta-audit/docs/scale-anchors/*.md` (8 files from V2)
- **Detection references**: `/Users/profile_1/Coding/sloppypasta-audit/docs/reference/*.md` (3 files from V3)
- **Plan file**: `/Users/profile_1/.claude/plans/tidy-stargazing-steele.md`
  - Lines 1006-1016: Scoring methodology (geomean, 5% floor, conditional N/A handling, grade scale)
  - Lines 110-135: V1 scope — single-agent execution, markdown output, 3-5 improvement suggestions
  - Lines 1193-1195: 5% floor, 3-agent minimum for subjective (V2 only — V1 is single-agent)

### 3. Deliverables

**One file**: `/Users/profile_1/Coding/sloppypasta-audit/.claude/skills/sloppypasta-audit/SKILL.md`

This file IS the skill. When Claude Code loads it, it becomes the audit agent. The file must contain:

1. YAML frontmatter with skill metadata (name, description, allowed-tools)
2. Complete audit workflow instructions
3. Scoring formula with the 5% floor
4. Output template (markdown scorecard)
5. References to the scale-anchor and detection-reference files (by path, so the skill can read them)
6. Tone/voice instructions (wise sage, not teenage dunker)

### 4. Steps

**Step 1: Create the directory structure.**

```
mkdir -p ~/Coding/sloppypasta-audit/.claude/skills/sloppypasta-audit/
```

**Step 2: Write the SKILL.md frontmatter.**

```yaml
---
name: sloppypasta-audit
description: >
  Run the Sloppypasta Audit on a product. Scores craft, sovereignty, honesty,
  and AI slop detection across 8 categories. Outputs a graded markdown scorecard
  with improvement suggestions. Use when the user says /sloppypasta-audit or
  asks to audit a product.
allowed-tools: Bash(curl *), Read, Grep, Glob, WebFetch, WebSearch, Write
---
```

**Step 3: Write the audit workflow.**

The skill body should contain these sections:

**Section A: Product Gathering**

```markdown
## Phase 1: Gather Product Information

1. Accept input: URL, product name, or both
2. If URL provided, use WebFetch to load:
   - Landing page / home page
   - About page (if exists)
   - Pricing page (if exists)
   - Documentation / help (if exists)
   - Terms of service (if exists)
3. If product name only, use WebSearch to find the product, then fetch as above
4. Determine product type: web app, mobile app, desktop app, CLI tool, protocol/library
5. Determine applicable conditional tags based on product features:
   - [if:content] — does the product have editorial/content features?
   - [if:social] — does the product have community/social features?
   - [if:mobile] — is there a mobile app?
   - [if:identity] — does the product manage user identity?
   - [if:payments] — does the product handle money?
   - [if:feed/social] — does the product have an algorithmic feed?
6. Note which conditional checks activate and which are N/A
```

**Section B: Scoring Instructions**

```markdown
## Phase 2: Score Each Check

Read the following reference files before scoring:
- Scale anchors: `~/Coding/sloppypasta-audit/docs/scale-anchors/cat{N}-*.md`
- Text markers: `~/Coding/sloppypasta-audit/docs/reference/slop-text-markers.md`
- Visual markers: `~/Coding/sloppypasta-audit/docs/reference/slop-visual-markers.md`
- Sovereignty checks: `~/Coding/sloppypasta-audit/docs/reference/sovereignty-checks.md`

For each V1 check:
1. Read the scale anchor for that check
2. Compare the product against the behavioral descriptions at each level
3. Assign a score from 5 to 100 (5% floor — never assign 0)
4. Record a one-sentence justification for the score
5. If the check has a conditional tag and the condition does not apply, mark N/A

Score ALL checks in ALL categories before computing any aggregates. Do not skip categories.
```

**Section C: Scoring Formula**

```markdown
## Phase 3: Compute Scores

### Category Score (Geometric Mean)

For each category, compute the geometric mean of all applicable (non-N/A) check scores:

category_score = (check1 * check2 * ... * checkN) ^ (1/N)

Where N = number of applicable checks (N/A checks excluded).

If a category has fewer than 3 applicable checks after N/A exclusions, 
exclude the entire category and redistribute its weight proportionally 
to remaining categories.

### 5% Floor

Before computing the geometric mean, apply the floor:
- Any check score below 5 is set to 5
- This prevents a single zero from catastrophically collapsing the geomean

### Overall Score (Weighted Geometric Mean)

overall = cat1^w1 * cat2^w2 * ... * cat8^w8

Where weights are:
| Category | Weight |
|----------|--------|
| 1 Slop Detection | 0.15 |
| 2 Writing | 0.10 |
| 3 Design | 0.10 |
| 4 Craft | 0.10 |
| 5 Conduct | 0.15 |
| 6 Sovereignty | 0.20 |
| 7 Honesty | 0.10 |
| 8 Economic | 0.10 |

If any category is excluded (fewer than 3 applicable checks), redistribute 
its weight proportionally. Example: if Cat 8 (0.10) is excluded, multiply 
each remaining weight by 1/(1-0.10) = 1/0.90.

### Grade Assignment

| Grade | Score Range |
|-------|------------|
| A | 85-100 |
| B | 70-84 |
| C | 55-69 |
| D | 40-54 |
| F | 0-39 |

Note: Grade boundaries may be adjusted after calibration (V5).
```

**Section D: Output Template**

```markdown
## Phase 4: Generate Report

Output a markdown file with this structure:

# Sloppypasta Audit: [Product Name]

**Date**: [YYYY-MM-DD]
**Product URL**: [URL]
**Product Type**: [web app / mobile app / CLI / protocol / etc.]
**Audit Mode**: External
**Applicable Conditions**: [list of activated conditional tags]

---

## Overall Score: [XX]% — Grade [A/B/C/D/F]

[One paragraph summary of the product's strengths and weaknesses. 
Wise sage tone — acknowledge what's done well before identifying gaps. 
No shaming. Frame weaknesses as improvement opportunities.]

---

## Category Breakdown

### Cat 1: Slop Detection — [XX]% (weight: 15%)

| Check | Score | Justification |
|-------|-------|---------------|
| 1.1 [name] | XX% | [one sentence] |
| 1.2 [name] | XX% | [one sentence] |
| ... | | |

[Repeat for all 8 categories]

---

## Score Details

| Category | Score | Weight | Checks Applied |
|----------|-------|--------|----------------|
| 1 Slop Detection | XX% | 15% | N/N |
| 2 Writing | XX% | 10% | N/N |
| ... | | | |
| **Overall** | **XX%** | | |

---

## Priority Improvements

[3-5 specific, actionable improvements sorted by expected impact on overall score.
Each improvement should:
- Name the specific check it addresses
- Describe the current state (what was observed)
- Describe the target state (what 75% looks like for this check)
- Estimate the score impact ("improving this from 25% to 75% would raise your 
  Category X score by approximately Y points")]

---

## Methodology

This audit uses the Sloppypasta Framework V1 — [N] checks across 8 categories, 
scored with geometric means. Lower scores drag disproportionately. 
Full methodology: docs/synthesis.md

Applicable checks: [X] of [Y] total (conditional checks: [Z] activated, [W] N/A)
```

**Section E: Tone and Voice**

```markdown
## Voice Guidelines

- **Wise sage, not teenage dunker**: Celebrate what's done well. Frame weaknesses as paths to improvement.
- **Specific, not vague**: "Your error messages use generic 'Something went wrong' text (4.3: 25%)" not "error handling could be better."
- **No slop in the audit itself**: The report must pass its own Cat 2 (Writing) checks. No weasel words, no throat-clearing, no filler.
- **Calibrated praise**: Don't say "great" for 50%. 50% means mediocre. 75% is good. 85%+ deserves praise.
- **Improvement-focused**: The report exists to help builders improve, not to shame them. Every low score should connect to a specific improvement suggestion.
```

**Step 4: Add a usage example to the skill.**

At the top of the skill body (after frontmatter), include:

```markdown
# Sloppypasta Audit

Run a scored product audit for craft, sovereignty, honesty, and AI slop detection.

## Usage

Invoke: `/sloppypasta-audit [URL or product name]`

Example: `/sloppypasta-audit https://boris.bar`
Example: `/sloppypasta-audit ppq.ai`
Example: `/sloppypasta-audit Twitter`
```

**Step 5: Verify the skill is self-contained.**

The skill file must reference all needed files by path. A fresh Claude Code session with no prior context must be able to:
1. Read the SKILL.md
2. Follow the instructions to read scale anchors and detection references
3. Run the audit without asking "what checks should I use?"

Check that every file path referenced in the skill actually exists (or will exist after V1-V3 complete).

### 5. Acceptance Criteria

- [ ] File exists at `/Users/profile_1/Coding/sloppypasta-audit/.claude/skills/sloppypasta-audit/SKILL.md`
- [ ] YAML frontmatter includes: name, description, allowed-tools
- [ ] Skill accepts URL or product name as input
- [ ] Skill instructs reading of scale-anchor files and detection-reference files by path
- [ ] Scoring formula correctly implements: 5% floor, per-check scoring, geometric mean per category, weighted geometric mean overall
- [ ] N/A handling is specified (exclude from geomean, redistribute weight if < 3 active checks in category)
- [ ] Grade boundaries are defined (A: 85-100, B: 70-84, C: 55-69, D: 40-54, F: 0-39)
- [ ] Output template produces: overall score + grade, category breakdown with per-check scores and justifications, priority improvement suggestions (3-5)
- [ ] Tone instructions specify "wise sage" voice
- [ ] Skill is self-contained — no references to external skills, plan files, or brainstorm context
- [ ] Weight table sums to 1.00

### 6. Dependencies

- **V1 (Check Inventory)**: needed for the check list the skill walks through
- **V2 (Scale Anchors)**: needed for scoring references
- **V3 (Detection Reference)**: needed for slop detection procedures

All three must be complete before V4 can be finalized. However, the skill structure (frontmatter, workflow, scoring formula, output template) can be drafted in parallel — only the specific check references need V1-V3.

### 7. Estimated Time

1.5-2 hours for the full SKILL.md. If V1-V3 are already done, the check references are mechanical — the hard work is the scoring formula, output template, and tone calibration.

---
---

## SLICE V5: CALIBRATION

### 1. Objective

Validate the audit skill by running it on two products with known expected outcomes:

1. **Boris** (https://boris.bar or equivalent) — expected B range (65-75%). Good craft, honest, sovereignty-aligned, some rough edges.
2. **Twitter/X** (https://x.com) — expected F range (20-30%). Platform thinking, attention extraction, sovereignty hostile, some craft visible.

If the scores match intuitive expectations (within ~10 points of the expected range), the skill is calibrated. If scores are absurd (Boris gets an F, or Twitter gets a B), identify which checks, weights, or anchors caused the distortion and adjust.

This is NOT optimization. The plan explicitly says "set weights from philosophy, validate with calibration." We are checking directionality (Boris > Twitter across most categories) and range (scores land in plausible zones), not tuning weights to hit exact numbers.

### 2. Inputs

- **The working skill**: `/Users/profile_1/Coding/sloppypasta-audit/.claude/skills/sloppypasta-audit/SKILL.md` (from V4)
- **Scale anchors**: `/Users/profile_1/Coding/sloppypasta-audit/docs/scale-anchors/*.md` (from V2)
- **Detection references**: `/Users/profile_1/Coding/sloppypasta-audit/docs/reference/*.md` (from V3)
- **Check inventory**: `/Users/profile_1/Coding/sloppypasta-audit/docs/check-inventory.md` (from V1)

### 3. Deliverables

**3 files**:

| File | Contents |
|------|----------|
| `/Users/profile_1/Coding/sloppypasta-audit/docs/calibration/boris-audit.md` | Complete audit report for Boris |
| `/Users/profile_1/Coding/sloppypasta-audit/docs/calibration/twitter-audit.md` | Complete audit report for Twitter/X |
| `/Users/profile_1/Coding/sloppypasta-audit/docs/calibration/calibration-notes.md` | Analysis of results: expected vs actual scores, which checks/weights caused issues, adjustments made |

### 4. Steps

**Step 1: Create the calibration directory.**

```
mkdir -p ~/Coding/sloppypasta-audit/docs/calibration/
```

**Step 2: Run the audit on Boris.**

Invoke the skill as designed. If Boris has a public URL, use it. If not, use WebSearch to find the product and gather information. Run through every check, score it, compute the geomean, generate the full report.

Expected ranges per category for Boris:
- Cat 1 (Slop Detection): 70-85% — Boris is a human-built product, text should be clean
- Cat 2 (Writing): 65-80% — likely has personality, may have rough spots
- Cat 3 (Design): 60-75% — functional, may not be polished
- Cat 4 (Craft): 70-85% — opinionated, shipped ready, source available
- Cat 5 (Conduct): 75-90% — unlikely to have dark patterns or surveillance
- Cat 6 (Sovereignty): 80-95% — Bitcoin/Nostr native, protocol-based
- Cat 7 (Honesty): 75-90% — transparent builder, honest marketing
- Cat 8 (Economic): 70-85% — likely V4V or pay-per-service

If the overall score lands 65-75% (B range), the calibration passes for Boris.

**Step 3: Run the audit on Twitter/X.**

Same process. Expected ranges per category:
- Cat 1 (Slop Detection): 30-50% — some AI integration, marketing copy likely sloppy
- Cat 2 (Writing): 40-60% — some craft visible in UI copy, marketing is hype-driven
- Cat 3 (Design): 50-70% — professional design team, but attention-harvesting layout
- Cat 4 (Craft): 40-60% — feature bloat, but core product works
- Cat 5 (Conduct): 10-25% — infinite scroll, attention harvesting, surveillance, nag notifications, difficult to leave
- Cat 6 (Sovereignty): 5-15% — platform, not protocol. Rugpull possible. Gov ID for verification. Proprietary.
- Cat 7 (Honesty): 20-40% — business model partially visible (ads), marketing exaggeration, AI integration disclosed inconsistently
- Cat 8 (Economic): 15-30% — ad-driven, attention extraction, creator monetization exists but platform-controlled

If the overall score lands 20-30% (F range), the calibration passes for Twitter.

**Step 4: Analyze the results.**

Write `calibration-notes.md` with this structure:

```markdown
# Calibration Analysis

## Directionality Check

| Category | Boris | Twitter/X | Boris > Twitter? | Expected? |
|----------|-------|-----------|-----------------|-----------|
| 1 Slop Detection | XX% | XX% | Yes/No | Yes |
| 2 Writing | XX% | XX% | Yes/No | Yes |
| ... | | | | |
| Overall | XX% | XX% | Yes/No | Yes |

Boris should score higher than Twitter on EVERY category except possibly Cat 3 (Design) 
where Twitter has a professional design team.

## Range Check

| Product | Expected Range | Actual Score | In Range? |
|---------|---------------|-------------|-----------|
| Boris | 65-75% (B) | XX% | Yes/No |
| Twitter/X | 20-30% (F) | XX% | Yes/No |

## Anomalies

[List any checks where the score was surprising — either too high or too low 
compared to intuitive expectation. For each anomaly:]

### [Check X.Y: Name]
- **Expected**: [XX%]
- **Actual**: [XX%]
- **Cause**: [Why the anchor/description led to this score]
- **Adjustment**: [What to change — rewrite anchor? Adjust weight? Reclassify measurability?]

## Adjustments Made

[List any changes to anchors, weights, or check descriptions made as a result 
of calibration. Be specific: "Changed Cat 5 weight from 0.15 to 0.12 because..."
Or: "Rewrote 5.4 anchor at 50% because the original description was too lenient."]

## Grade Boundary Validation

[After seeing two real scores, do the grade boundaries make sense?
If Boris = 72% (B) and Twitter = 25% (F), the B/C and D/F boundaries are validated.
If both products land in unexpected grades, consider adjusting boundaries.]

## Confidence Assessment

- Directionality: PASS / FAIL
- Range accuracy: PASS / FAIL  
- Ready to ship: YES / NO (with conditions)
```

**Step 5: Make adjustments if needed.**

If calibration reveals problems:

1. **Score too high for Twitter**: Check if any category is inflating. Common cause: Cat 3 (Design) or Cat 4 (Craft) scored too generously because the scale anchors describe professional-but-hostile products at 75% instead of 50%.

2. **Score too low for Boris**: Check if conditional checks are penalizing unfairly. Common cause: a check that should be N/A for Boris is activating and scoring low.

3. **Weights distorting**: If one category is dominating the overall score, the weight may be too high. But do NOT change weights to hit a target number — only change them if the philosophical justification is wrong.

4. **Anchor ambiguity**: If two products that should score differently on a check both score the same, the anchor at that level needs more specific behavioral descriptions.

For each adjustment: update the source file (scale anchor, check inventory, or SKILL.md), document the change in calibration-notes.md, and re-run the affected computation.

**Step 6: Re-run if adjustments were made.**

If any anchors or weights changed, re-run both audits with the updated references. The second run should produce scores closer to expectations. Document both runs in the calibration notes.

### 5. Acceptance Criteria

- [ ] Complete audit report for Boris exists at `docs/calibration/boris-audit.md`
- [ ] Complete audit report for Twitter/X exists at `docs/calibration/twitter-audit.md`
- [ ] Both reports follow the output template from V4 (all sections present)
- [ ] Calibration notes exist at `docs/calibration/calibration-notes.md`
- [ ] Directionality check: Boris scores higher than Twitter on at least 7 of 8 categories
- [ ] Range check: Boris overall score is 60-80% (B-C range). Twitter overall is 15-35% (F range).
- [ ] Every anomaly is documented with cause and adjustment
- [ ] Any adjustments to anchors/weights/checks are documented and applied to source files
- [ ] Grade boundaries are validated or adjusted based on real data
- [ ] Calibration notes include a "Ready to ship" verdict

### 6. Dependencies

- **V4 (Skill + Scoring)** must be complete. V5 runs the skill.

### 7. Estimated Time

1-1.5 hours. Each audit run takes 20-30 minutes. Analysis and adjustments take 30-45 minutes. If adjustments require re-runs, add another 30 minutes.

---
---

## SLICE V6: FRAMEWORK DOCUMENT

### 1. Objective

Rewrite `/Users/profile_1/Coding/sloppypasta-audit/docs/synthesis.md` as the public-facing framework document. This is NOT the plan, NOT the brainstorm, NOT the shaping doc. It is the clean, published document that anyone on the internet reads to understand what the Sloppypasta Audit is, why it exists, how it works, and how to run it.

Every word earns its place. This document must pass the framework's own Cat 2 (Writing) checks: economy of words, copy as interface design, no throat-clearing, no weasel words. It should also pass Cat 1 (Slop Detection) — no banned words, no Bold Prefix bullet lists, no symmetrical paragraphs.

The axioms from the existing synthesis.md (lines 1-18) were well-written by the user. Preserve their voice and sharpness. Build the rest of the document to that standard.

### 2. Inputs

- **Existing synthesis**: `/Users/profile_1/Coding/sloppypasta-audit/docs/synthesis.md` — the axioms (lines 1-18) are keepers. The rest gets replaced.
- **V1 check inventory**: `/Users/profile_1/Coding/sloppypasta-audit/docs/check-inventory.md` (from V1) — the definitive check list
- **Calibration results**: `/Users/profile_1/Coding/sloppypasta-audit/docs/calibration/calibration-notes.md` (from V5) — validated weights and grade boundaries
- **Scale anchors**: `/Users/profile_1/Coding/sloppypasta-audit/docs/scale-anchors/*.md` (from V2) — summarize, don't duplicate
- **Detection references**: `/Users/profile_1/Coding/sloppypasta-audit/docs/reference/*.md` (from V3) — reference, don't inline
- **Plan file**: `/Users/profile_1/.claude/plans/tidy-stargazing-steele.md`
  - Lines 1-28: Frame section — the problem statement and outcome
  - Lines 600-603: Key principles (lean measurable, not maximalist, wise sage)

### 3. Deliverables

**One file**: `/Users/profile_1/Coding/sloppypasta-audit/docs/synthesis.md` (overwrites existing)

Contents — in this exact order:

1. **Opening** (2-3 sentences max): What is this? Why does it exist? Keep the existing opening paragraph — it is strong.

2. **Axioms** (8 items): Keep from existing synthesis.md. These are the philosophical foundation. They were written by the user and are the voice standard for the entire document.

3. **How It Works** (short): Geometric mean scoring, 8 categories, 0-100 per check, category geomeans, weighted overall. The math in plain language. Include the actual formula. Explain why geometric (multiplicative punishment for low scores — can't compensate for structural failures with nice fonts).

4. **Categories**: For each of the 8 categories:
   - Name and tagline
   - 2-3 sentences explaining what this category measures and why
   - Table of V1 checks (number, name, one-line description)
   - Weight and what it means
   - Do NOT include scale anchors here — reference the scale-anchors docs

5. **Scoring Methodology**: The math. Grade boundaries. The 5% floor and why. Conditional check handling. Weight table with philosophical justification for each weight. "Weights are set from philosophy and validated by calibration, not optimized to produce desired results."

6. **How to Run the Audit**: Step-by-step. As a Claude Code skill: install the repo, invoke `/sloppypasta-audit [URL]`. As a manual process: gather product info, score each check against scale anchors, compute geomeans, assign grade.

7. **How to Interpret Results**: What each grade means (not just the label — the character of a product at each level). The improvement path: where to focus effort for maximum score improvement. The geometric mean insight: one terrible category drags everything.

8. **Calibration**: Brief note that the framework was calibrated on 2 products (Boris and Twitter/X) and the results matched expectations. This builds credibility without over-explaining.

9. **Limitations**: What this framework does NOT measure. Company politics, regulatory history, founder character. Products only. External audit mode only (V1). MEDIUM/LOW checks deferred to V2.

10. **Contributing**: How to contribute. Run the audit on a product and publish the results. File issues on the GitHub repo. Propose new checks or improved anchors.

### 4. Steps

**Step 1: Read the existing synthesis.md in full.**

Identify what to keep (axioms, opening paragraph, scoring explanation) and what to replace (old category structure, old weight table, old check list).

**Step 2: Write the opening.**

Keep the existing opening paragraph verbatim or near-verbatim:

> "Two things broke the internet: no native money, and no taste. The first gave us surveillance advertising and subscription traps. The second gave us sloppypasta — AI-generated content nobody cared enough to stand behind. This framework checks both dimensions."

This is the voice. Match it throughout.

**Step 3: Keep the axioms section.**

The 8 axioms from the existing synthesis.md (lines 8-18) are the user's own writing. They set the philosophical standard. Keep them exactly as written.

**Step 4: Write the "How It Works" section.**

Short. 4-6 sentences plus the formula. No throat-clearing.

```
Each check scores 0-100. Category score is the geometric mean of its checks. 
Overall score is the weighted geometric mean of category scores. Low scores 
drag disproportionately — you can't compensate for a structural failure with 
nice fonts. Grade boundaries: A (85-100), B (70-84), C (55-69), D (40-54), F (0-39).
```

Include the actual formulas from the existing synthesis.md (lines 119-130) — they are well-written.

**Step 5: Write the category sections.**

For each of the 8 categories, write:
- A tagline (already exists in the plan for each category)
- 2-3 sentences of philosophy (what this measures and why it matters)
- A clean table of V1 checks from the check inventory

Do NOT copy-paste the plan text. Rewrite to match the axiom voice. Every sentence earns its place.

**Step 6: Write the scoring methodology.**

Include:
- Weight table with philosophical justification
- 5% floor explanation
- Conditional check handling
- N/A redistribution rule
- Example computation (optional but helpful)

**Step 7: Write "How to Run" and "How to Interpret."**

"How to Run" — three paths:
1. As a Claude Code skill (primary)
2. As a manual audit using the framework docs
3. As a community accountability tool (run on any public product, publish results)

"How to Interpret" — what each grade means in practice. Not just labels — the feel of a product at each level.

**Step 8: Write limitations and contributing sections.**

Keep them short. 3-5 bullet points each. No defensiveness — just honest scope boundaries.

**Step 9: Self-audit the document.**

Before finishing, check against the framework's own standards:

| Check | Pass? |
|-------|-------|
| 2.1 Economy of words — no filler? | |
| 2.2 Copy as interface — every heading, every table header, every label designed? | |
| 2.4 No throat-clearing — does every section open with insight, not preamble? | |
| 1.1 LLM smell — no banned words, no Bold Prefix lists, no symmetrical paragraphs? | |

If any check fails, rewrite that section. The framework must pass its own test.

**Step 10: Verify completeness.**

- All 8 categories are described with their V1 checks
- Weight table is present and matches calibrated values (from V5)
- Grade boundaries are present (adjusted from V5 if needed)
- The document is standalone — readable without the plan, the anchors, or the references
- File paths to scale anchors and detection references are mentioned for deeper reading

### 5. Acceptance Criteria

- [ ] File exists at `/Users/profile_1/Coding/sloppypasta-audit/docs/synthesis.md` (replacing the old version)
- [ ] Opening paragraph preserved or closely adapted from original
- [ ] 8 axioms preserved from original
- [ ] All 8 categories described with V1 check tables
- [ ] Scoring methodology complete (formula, weights, floor, conditionals, grades)
- [ ] "How to Run" section with Claude Code skill instructions
- [ ] "How to Interpret" section with grade meanings
- [ ] Limitations section present
- [ ] Contributing section present
- [ ] Self-audit passes: no banned words, no throat-clearing, no filler, no Bold Prefix lists
- [ ] Word count is reasonable (2,000-4,000 words — comprehensive but not bloated)
- [ ] Document reads as one voice throughout (matching the axiom tone)
- [ ] Weight table matches V5 calibration results

### 6. Dependencies

- **V5 (Calibration)** must be complete. V6 needs validated weights, grade boundaries, and calibration results to reference.
- V6 also references V1 (check inventory) and can reference V2/V3 docs by path.

### 7. Estimated Time

1-1.5 hours. The content exists — this is a writing craft exercise. The hard part is voice consistency and self-audit.

---
---

## SLICE V7: SHIP

### 1. Objective

Package the repo for public release. Create the README, add the MIT license, clean the directory structure, commit everything, push to GitHub, and draft a Nostr announcement post. After this slice, the Sloppypasta Audit is live and usable by anyone.

### 2. Inputs

- **Everything from V1-V6**: The complete repo at `~/Coding/sloppypasta-audit/`
- **Plan file**: For the project description and philosophy
- **Existing git history**: 3 commits on main branch (the rejected V1 framework iterations)

### 3. Deliverables

| File | Contents |
|------|----------|
| `/Users/profile_1/Coding/sloppypasta-audit/README.md` | Project README for GitHub |
| `/Users/profile_1/Coding/sloppypasta-audit/LICENSE` | MIT license |
| `/Users/profile_1/Coding/sloppypasta-audit/docs/nostr-announcement.md` | Draft Nostr announcement post |
| Clean directory structure | No orphaned files, no .DS_Store, proper .gitignore |
| Git commits | All V1-V7 work committed |
| GitHub push | Repo pushed to GitHub (public) |

### 4. Steps

**Step 1: Create `.gitignore`.**

```
.DS_Store
*.swp
*.swo
.claude/
```

Note: `.claude/` is in gitignore because the skill will live in the user's own `.claude/skills/` directory — it is not installed from the repo. The repo provides the skill file; users copy it to their setup. Alternatively, if the skill should be installable from the repo, keep `.claude/` OUT of gitignore and include it. Decide based on the user's intended distribution: since the plan says "self-contained Claude Code skill" and the repo IS the skill package, keep `.claude/skills/sloppypasta-audit/SKILL.md` in the repo and only gitignore `.claude/` at the user level.

Revised approach: Do NOT gitignore the `.claude/skills/` directory. The SKILL.md is a deliverable.

```
.DS_Store
*.swp
*.swo
```

**Step 2: Write `README.md`.**

Structure:

```markdown
# The Sloppypasta Audit

A framework for evaluating whether digital products are built with care or 
shipped as AI-generated slop. Measures craft, sovereignty, honesty, and 
economic alignment across 8 categories.

Built for the Bitcoin/Nostr community. Useful for anyone who gives a damn.

## What It Measures

| Category | Weight | Question |
|----------|--------|----------|
| Slop Detection | 15% | Can you smell the AI? |
| Writing | 10% | Does the text show a thinking human? |
| Design | 10% | Does the look show care? |
| Craft | 10% | Less is more? |
| Conduct | 15% | How does it behave? |
| Sovereignty | 20% | Can they rugpull you? |
| Honesty | 10% | Does it tell you the truth? |
| Economic | 10% | Who captures the value? |

## How to Use

### As a Claude Code Skill

1. Copy `.claude/skills/sloppypasta-audit/` to your `~/.claude/skills/` directory
2. Copy `docs/` to `~/Coding/sloppypasta-audit/docs/` (the skill reads reference files from here)
3. Invoke: `/sloppypasta-audit [URL or product name]`

### As a Manual Audit

1. Read `docs/synthesis.md` for the full framework
2. Score each check using the scale anchors in `docs/scale-anchors/`
3. Compute geometric means per the scoring methodology
4. Assign a grade

### As a Community Tool

Run the audit on any public product and publish the results. Link back to this repo.

## Scoring

Geometric mean, not arithmetic. Low scores drag disproportionately. You can't 
compensate for a structural failure with nice fonts.

- **A** (85-100): Sovereign, crafted, honest.
- **B** (70-84): Solid. Gaps fixable with intention.
- **C** (55-69): Some care visible. Structural problems.
- **D** (40-54): Platform thinking. Attention extraction.
- **F** (0-39): Surveillance product, sloppypasta factory, or both.

## Repository Structure

```
sloppypasta-audit/
├── .claude/skills/sloppypasta-audit/
│   └── SKILL.md              # The Claude Code skill
├── docs/
│   ├── synthesis.md           # Full framework document
│   ├── check-inventory.md     # V1 check list (39 checks)
│   ├── scale-anchors/         # Scoring anchors (0-100) per check
│   │   ├── cat1-slop-detection.md
│   │   ├── cat2-writing.md
│   │   ├── ...
│   │   └── cat8-economic.md
│   ├── reference/             # Detection reference docs
│   │   ├── slop-text-markers.md
│   │   ├── slop-visual-markers.md
│   │   └── sovereignty-checks.md
│   └── calibration/           # Calibration run results
│       ├── boris-audit.md
│       ├── twitter-audit.md
│       └── calibration-notes.md
├── README.md
└── LICENSE
```

## Philosophy

Read the axioms in `docs/synthesis.md`. Short version: digital content has 
zero cost to copy, protocols can't de-platform you, payments can't be faked, 
and the best products ship less. This framework operationalizes those beliefs.

## Contributing

- Run the audit on a product and publish the results
- File issues for checks that produce inconsistent scores
- Propose improved scale anchors with real product examples
- Submit calibration runs on new products

## License

MIT
```

**Step 3: Create `LICENSE`.**

Standard MIT license text with the current year and the user's name/handle.

**Step 4: Write the Nostr announcement draft.**

Create `/Users/profile_1/Coding/sloppypasta-audit/docs/nostr-announcement.md`:

```markdown
# Nostr Announcement Draft

[For publishing as a Nostr note. Keep under 280 characters for the short 
version. Expand for NIP-23 long-form if desired.]

## Short Version (Nostr note)

Shipped the Sloppypasta Audit — an open-source framework for scoring whether 
products are built with care or shipped as AI slop. 8 categories, geometric 
mean scoring, scale anchors for every check. Run it on anything. 

Built as a Claude Code skill. Repo: [GitHub URL]

cc @gigi #sloppypasta #bitcoin #nostr #sovereignty

## Long Version (NIP-23 or blog)

[2-3 paragraphs covering:]
- What: open-source product audit framework, 8 categories, ~39 checks
- Why: no structured way to evaluate product quality in the Bitcoin/Nostr space
- How: Claude Code skill, geometric mean scoring, calibrated on 2 products
- Philosophy: sovereignty + craft. Both necessary, neither sufficient.
- Call to action: run it on products you use, publish the results, help improve the anchors
```

**Step 5: Clean the directory.**

- Remove any `.DS_Store` files: `find ~/Coding/sloppypasta-audit -name '.DS_Store' -delete`
- Verify `docs/framework-overview.html` — decide whether to keep it or remove it. If it reflects the old V1 framework (47 checks, different categories), remove it. If updated, keep it.
  - Decision: Remove it. The V1 HTML is outdated. If an HTML version is wanted, it can be rebuilt from the new synthesis.md in V2 of the project.
- Verify no temp files, no editor backups, no `.swp` files

**Step 6: Stage and commit.**

Create a single commit (or logical commits per slice if preferred) with all V1-V7 work:

```
git add -A
git commit -m "v1: sloppypasta audit framework — 39 checks, 8 categories, scored skill

Complete V1 framework including:
- Check inventory (39 HIGH-measurability checks across 8 categories)
- Scale anchors (0/25/50/75/100 behavioral descriptions per check)
- Detection reference docs (text markers, visual markers, sovereignty checks)
- Claude Code skill (single-agent audit with geometric mean scoring)
- Calibration runs (Boris, Twitter/X)
- Framework document (public-facing synthesis)
- MIT license

Co-Authored-By: Claude <noreply@anthropic.com>"
```

**Step 7: Push to GitHub.**

If the repo does not have a remote yet:
```
gh repo create sloppypasta-audit --public --source=. --push
```

If it already has a remote:
```
git push origin main
```

Verify: `gh repo view --web` opens the repo page.

**Step 8: Final verification.**

After pushing, verify:
- README renders correctly on GitHub
- Directory structure is clean
- All docs are accessible
- SKILL.md is present in the repo
- LICENSE is present

### 5. Acceptance Criteria

- [ ] `README.md` exists at repo root with: project description, usage instructions (3 modes), scoring summary, directory structure, philosophy, contributing, license
- [ ] `LICENSE` exists with MIT license text
- [ ] `.gitignore` exists and excludes .DS_Store
- [ ] `docs/nostr-announcement.md` exists with short and long versions
- [ ] No `.DS_Store` files in the repo
- [ ] `docs/framework-overview.html` removed (outdated V1 HTML)
- [ ] All work committed to git
- [ ] Repo pushed to GitHub as public repository
- [ ] README renders correctly on GitHub (verify after push)
- [ ] No slop in README or announcement copy

### 6. Dependencies

- **All previous slices (V1-V6)** must be complete. V7 packages everything.

### 7. Estimated Time

30-45 minutes. Mostly writing (README, announcement) and git operations.

---
---

## PARALLELIZATION SUMMARY

```
Timeline (sequential dependencies shown):

Week 1, Session 1:
  V1 (Check Inventory)         ████  30-45 min
  
Week 1, Session 2 (parallel):
  V2 (Scale Anchors)           ████████████  2-3 hr
  V3 (Detection Reference)     ██████  45-60 min
  
Week 1, Session 3:
  V4 (Skill + Scoring)         ████████  1.5-2 hr
  
Week 2, Session 1:
  V5 (Calibration)             ██████  1-1.5 hr
  
Week 2, Session 2:
  V6 (Framework Doc)           ██████  1-1.5 hr
  
Week 2, Session 3:
  V7 (Ship)                    ████  30-45 min

Total estimated: 8-10 hours across 5-6 sessions
```

V2 and V3 are fully independent and should be run in parallel (or dispatched as parallel agents). All other slices are sequential.

The critical path is: V1 → V2 → V4 → V5 → V6 → V7 (V3 is off the critical path since it runs parallel to V2 and takes less time).

---

## CROSS-SLICE FILE DEPENDENCY MAP

| File | Created By | Read By |
|------|-----------|---------|
| `docs/check-inventory.md` | V1 | V2, V3, V4, V5, V6 |
| `docs/scale-anchors/*.md` (8 files) | V2 | V4, V5, V6 |
| `docs/reference/slop-text-markers.md` | V3 | V4, V5 |
| `docs/reference/slop-visual-markers.md` | V3 | V4, V5 |
| `docs/reference/sovereignty-checks.md` | V3 | V4, V5 |
| `.claude/skills/sloppypasta-audit/SKILL.md` | V4 | V5, V7 |
| `docs/calibration/*.md` (3 files) | V5 | V6 |
| `docs/synthesis.md` | V6 | V7 |
| `README.md` | V7 | — |
| `LICENSE` | V7 | — |
| `docs/nostr-announcement.md` | V7 | — |
