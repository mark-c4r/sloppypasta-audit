---
ticket: sloppypasta-audit#2
status: completed
appetite: L
risk_score: 4
project: sloppypasta-audit
updated: 2026-04-01
files:
  - .claude/skills/sloppypasta-audit/SKILL.md
  - docs/scoring-reference.md
  - docs/check-inventory.md
  - docs/scale-anchors/cat1-slop-detection.md
  - docs/scale-anchors/cat2-writing.md
  - docs/scale-anchors/cat3-design.md
  - docs/scale-anchors/cat4-craft.md
  - docs/scale-anchors/cat5-conduct.md
  - docs/scale-anchors/cat6-sovereignty.md
  - docs/scale-anchors/cat7-honesty.md
  - docs/scale-anchors/cat8-economic.md
  - docs/synthesis.md
  - README.md
---

# Sloppypasta Audit V2 — Framework Improvements

## Problem

The 11-product calibration batch (2026-04-01) revealed that the framework's Care-dimension checks (Cats 1-4) produce compressed ranges (stdev 8.7-15.3) while structural checks (Cats 5-6-8) produce wide ranges (stdev 23-27). The Care dimension carries 40% nominal weight but only 22.6% effective influence. The framework claims to measure visible laziness, felt disrespect, hidden betrayal, and delayed traps — but its instruments are sharp only for the latter two.

Additionally: 3/9 audit agents assigned wrong grades, reports don't disclose what was assessed, and two checks have documented bugs (3.2 is non-discriminating, 1.2 punishes newness).

## Verified Assumptions

| Claim | Source | Status |
|-------|--------|--------|
| scoring-reference.md is what skill reads at runtime | SKILL.md:54 | VERIFIED |
| Cat 3 has 6 checks including 3.2 | scoring-reference.md:174 | VERIFIED |
| Cat 2 has 3 checks | scoring-reference.md:128 | VERIFIED |
| Cat 7 has 5 checks | scoring-reference.md:806 | VERIFIED |
| Cat 8 has 3 checks | scoring-reference.md:880 | VERIFIED |
| Python scoring script in SKILL.md | SKILL.md:140-180 | VERIFIED |
| Individual anchor files exist at docs/scale-anchors/ | ls output | VERIFIED |
| 3.2 range is 15 points (55-70%) | batch-analysis.md:91 | VERIFIED |
| 1.2 scores 15% for sloppypasta self-audit | self-audit report | VERIFIED |
| 3/9 agents assigned wrong grades | batch-analysis.md:342 | VERIFIED |

## Shape Decision

Fix the measurement instruments (checks and anchors), not the scoring math. Phase 0 fixes bugs and template. Phase 1 sharpens Care-dimension checks to earn their 40% weight. Phase 2 applies structural changes only if Phase 1 data shows they're still needed. The geometric mean, 5% floor, grade boundaries, and 85% A-threshold are all preserved.

## Acceptance Criteria

- [x] Check 3.2 (Physical Obviousness) removed from framework
- [x] Check 1.2 (Social Authenticity) has pre-community N/A condition
- [x] Every audit report includes an Audit Scope section
- [x] Grade assignment is programmatic (computed from score, not agent judgment)
- [x] Checks scoring < 70% must cite specific evidence in reports
- [x] Check 2.2 split into 2.2a (guides action) + 2.2b (shows authorship)
- [x] Check 7.3 split into 7.3a (AI transparency) + 7.3b (human authorship signal)
- [x] Check 4.1 has maturity-adjusted anchors
- [x] Cat 3 remaining anchors (3.1, 3.3, 3.4, 3.6) have sharper differentiation
- [x] 5.5 anchors include explicit tracking quality taxonomy
- [x] 6.1 anchors include rugpull severity spectrum
- [x] Validation re-scoring of 5 products shows improved Care-dimension discrimination
- [x] scoring-reference.md and individual anchor files are in sync
- [x] 3-check minimum rule changed to 2-check minimum in text (matches existing code)
- [x] check-inventory.md Cat 1/Cat 7 header weights corrected to match scoring-reference.md
- [x] SKILL.md python script updated for new check structure (47 checks)
- [x] Phase 2 decision documented with data (no weight shift — gap is inherent, not a flaw)

## Slices

### Slice 1: Report Template Improvements [downhill]
**Demo:** Run `/sloppypasta-audit` on any product — output includes Audit Scope section, programmatic grade, and specific findings for low-scoring checks.
**Files:** SKILL.md
**Steps:**
1. Add `## Audit Scope` section to report template (after metadata, before Overall). Template includes: surfaces assessed, surfaces via proxy, surfaces not assessed, limitations encountered.
2. Remove grade from report header template. Add instruction: "Always use the python script grade output. Never override." The script already computes the grade (SKILL.md:177) — the fix is preventing agents from writing their own.
3. Add requirement to Phase 4 instructions: any check scoring below 70% must include one specific observation (URL, code pattern, exact text) in the justification.
4. Add to multi-agent scoring agent instructions (SKILL.md ~line 297): "For checks scoring below 70%, include one specific observation in the justification." Otherwise multi-agent mode bypasses the evidence requirement.
**Tests:** Read SKILL.md, verify template includes all 3 additions. Manually verify report format produces correct output.
**Depends on:** nothing

### Slice 2: Check Cleanup — Kill 3.2, Fix 1.2 [downhill]
**Demo:** Cat 3 has 5 checks. New products with no community score N/A on 1.2 instead of 15%.
**Files:** scoring-reference.md, check-inventory.md, scale-anchors/cat1-slop-detection.md, scale-anchors/cat3-design.md, SKILL.md
**Steps:**
0. Fix pre-existing weight conflict in check-inventory.md: Cat 1 header says 15% (should be 10%), Cat 7 header says 10% (should be 15%). Normalize to match scoring-reference.md.
1. Change minimum check rule from "3" to "2" in scoring-reference.md (line 29) and check-inventory.md (line 179). Add: "If a category drops to 1 applicable check, exclude the entire category and redistribute weight." This matches the existing SKILL.md python code (`len(a) >= 2`).
2. Remove 3.2 (Physical Obviousness) from scoring-reference.md. Remove its section entirely. Update Cat 3 header to "5 checks."
3. Remove 3.2 from check-inventory.md.
4. Remove 3.2 from cat3-design.md scale anchor file.
5. Add single sentence to 3.4's 100% anchor: "Interactive elements teach their function through form — controls signal capability through shape, color, and position without relying on convention alone." Do NOT rewrite 3.4's full anchor structure.
6. Add N/A condition to 1.2: `[if product has no discoverable social media presence and no evidence of community engagement → N/A]`. Drop the age requirement — absence of social presence is the actual condition. Add to scoring-reference.md and cat1-slop-detection.md.
7. Update SKILL.md python script: Cat 3 array goes from 6 entries to 5.
8. Update check-inventory.md summary counts.
**Tests:** `grep "### 3.2" docs/scoring-reference.md` returns empty (section header gone). Cat 3 header says 5 checks. Python script runs without error with 5 Cat 3 entries. `grep "Minimum" docs/scoring-reference.md` shows "2" not "3".
**Depends on:** nothing

### Slice 3: Split Check 2.2 — Cat 2 Sharpening [uphill]
**Demo:** Cat 2 has 4 checks. 2.2a and 2.2b have independent scores with distinct justifications.
**Files:** scoring-reference.md, check-inventory.md, scale-anchors/cat2-writing.md, SKILL.md
**Steps:**
1. Write 2.2a "Copy Guides Action" anchor (5 levels: 5/25/50/75/100) focused on: does the text tell you what to do, where you are, what went wrong? Error messages, empty states, labels, CTAs.
   - 5% floor: "No guidance anywhere. Error messages say 'Error.' Empty states are blank. User must guess every action."
   - 100% ceiling: "Every state has specific, actionable copy. Errors explain what went wrong AND what to try. Empty states suggest next steps with specific CTAs. Labels disambiguate without tooltips."
2. Write 2.2b "Copy Shows Authorship" anchor (5 levels) focused on: could this copy only exist in this product? Voice, specificity, personality. Generic "Welcome to [Product]" vs. product-specific language.
   - 5% floor: "All copy is interchangeable template text. 'Welcome to [Product]. Get started today!' Nothing identifies this as a specific product."
   - 100% ceiling: "Copy has a distinctive voice that could not exist in any other product. Specific references, opinions, humor, or domain language that only this team would write."
3. Replace 2.2 in scoring-reference.md with 2.2a and 2.2b.
4. Update cat2-writing.md with new anchors.
5. Update check-inventory.md.
6. Update SKILL.md python script: Cat 2 array goes from 3 entries to 4.
7. Update SKILL.md multi-agent dispatch table (craft-scorer now has 16 checks).
**Tests:** Manually score 2.2a and 2.2b for 5 calibration products (Sparrow, Boris, Claude Code, Coinbase, Twitter). Target: each sub-check should have a wider range than original 2.2's 25 points. Record results.
**Depends on:** nothing (parallel with Slice 2)

### Slice 4: Split Check 7.3 + Maturity Modifier 4.1 [uphill]
**Demo:** Cat 7 has 6 checks. 7.3a scores N/A for non-AI products. 4.1 scores differently for mature vs early products.
**Files:** scoring-reference.md, check-inventory.md, scale-anchors/cat7-honesty.md, scale-anchors/cat4-craft.md, SKILL.md
**Steps:**
1. Write 7.3a "AI Content Transparency" anchor: if AI is used in user-facing content (generated text, AI chatbots, AI summaries, AI recommendations), is it disclosed at point of encounter? **Scope**: measures user-facing AI content only. Backend AI (fraud detection, spam filtering, internal ML) is out of scope. If no user-facing AI content is detected through surface inspection, score N/A. Note this as an acknowledged limitation in the Audit Scope section.
2. Write 7.3b "Human Authorship Signal" anchor: does the content show evidence of human creation? Voice, opinions, personal references, irregular rhythm. Overlaps with Cat 1 but from the honesty dimension — "is this honest about its origins?"
3. Replace 7.3 in scoring-reference.md with 7.3a and 7.3b.
4. Update cat7-honesty.md.
5. Add maturity context to 4.1 anchors in scoring-reference.md and cat4-craft.md: "For products with 1M+ users or $10M+ revenue, the 50% anchor is: core flow works but secondary flows have issues. Billing bugs or data loss in a product at this scale should not score above 50%." Data source: use publicly reported figures (app store download counts, press releases, Crunchbase). If no public figures exist, use early-product anchors. Do not guess.
6. Update check-inventory.md.
7. Update SKILL.md python script: Cat 7 array goes from 5 entries to 6.
**Tests:** Re-score 7.3a and 7.3b for 5 products. 7.3a should be N/A for Sparrow, Vexl (no user-facing AI content). Coinbase may score N/A or low depending on whether customer support chatbots are detectable from the surface. 7.3b should discriminate differently from 7.3a. Re-score 4.1 for AllTrails (should drop from 65% to ~45-50%) and PodNews (should stay ~65%).
**Depends on:** nothing (parallel with Slices 2-3)

### Slice 5: Anchor Refinements — Cat 3, Cat 5, Cat 6 [uphill]
**Demo:** Cat 3 anchors produce wider score ranges. 5.5 anchors name tracking tiers. 6.1 anchors distinguish severity.
**Files:** scoring-reference.md, scale-anchors/cat3-design.md, scale-anchors/cat5-conduct.md, scale-anchors/cat6-sovereignty.md
**Steps:**
1. Rewrite 3.1 (Information Density) anchors: push floor lower ("wall of undifferentiated text" at 5%), push ceiling higher ("layout communicates data hierarchy without labels" at 95%). The middle should describe what separates Sparrow's UTXO interface from Twitter's standard feed.
2. Rewrite 3.3 (Design System Consistency) anchors: floor = "no tokens, pure inline styles, inconsistent spacing" at 5%. Ceiling = "custom design language that could not be mistaken for another product" at 95%.
3. Rewrite 3.4 (Self-Evident UI) anchors: incorporate merged 3.2 concept. Floor = "requires external docs to use basic features." Ceiling = "interface teaches itself through progressive disclosure."
4. Rewrite 3.6 (Accessibility Basics) anchors: sharper distinction between "some ARIA labels" (50%) and "systematic a11y with focus management, screen reader testing, reduced motion" (90%).
5. Add tracking quality taxonomy to 5.5 scale anchors: Infrastructure (70-90%) → First-party analytics (75-90%) → Privacy-respecting third-party (50-65%) → Standard surveillance (20-35%) → Advertising/profiling (5-20%) → Data brokering (5%).
6. Add rugpull severity spectrum to 6.1 anchors: Convenience loss (base score) → Data loss (-10 anchor guidance) → Financial loss (-20) → Identity loss (-15). Baked into anchor descriptions, not separate multipliers.
7. Add "import without matching export" as a named dark pattern in 5.10 anchor text and 6.2 anchor text.
8. Add "acknowledged but dismissed DNT" as explicitly worse than silent DNT ignorance in 5.5e anchors.
**Tests:** Read through all modified anchors. Mentally score 3 products (Sparrow, Coinbase, PodNews) against new anchors — verify the range would be wider than current 30 points for Cat 3.
**Depends on:** Slice 2 (3.2 must be removed before 3.4 gets the merged concept)

### Slice 6: Scoring Script + Sync + Validation [downhill]
**Demo:** Python script matches new 48-check structure. scoring-reference.md and individual files are in sync. 5-product re-scoring shows improved discrimination.
**Files:** SKILL.md, scoring-reference.md (verification only)
**Steps:**
1. Update SKILL.md python scoring script to reflect new check structure:
   - Cat 2: 4 checks [2.1, 2.2a, 2.2b, 2.3]
   - Cat 3: 5 checks [3.1, 3.3, 3.4, 3.5, 3.6]
   - Cat 7: 6 checks [7.1, 7.2, 7.3a, 7.3b, 7.4, 7.5]
   - Total: 47 checks (was 46: -1 from 3.2 removal, +1 from 2.2 split, +1 from 7.3 split)
2. Update SKILL.md multi-agent dispatch table with new check counts per agent.
3. Verify scoring-reference.md and individual scale-anchor files are in sync (diff key sections).
4. Re-score 5 products (Sparrow, PodNews, Coinbase, Fountain, Twitter) on ALL modified checks using new anchors. Use existing batch audit data (docs/audits/). Do not re-fetch products. The goal is anchor discrimination, not absolute accuracy.
5. Compute new discrimination stats: stdev and range for Cats 2, 3, 4, 7.
6. Compare to baseline: Cat 2 stdev was 9.5, Cat 3 was 8.7, Cat 4 was 10.7, Cat 7 was 17.2.
7. Compute new effective influence percentages.
8. Sync synthesis.md check tables and counts for any category that changed (Cat 2: 4 checks, Cat 3: 5 checks, Cat 7: 6 checks).
9. Write results to `docs/calibration/v2-discrimination-analysis.md`.
**Tests:** Python script runs without error. New Cat 2/3 stdev should be >12 (target: comparable to current Cat 1 at 15.3). If not, specific checks need further sharpening.
**Depends on:** Slices 2, 3, 4, 5 (all check changes must be complete)

### Slice 7: Phase 2 Decision + Structural Changes [uphill, conditional]
**Demo:** Weight distribution reflects V2 data. Cat 8 has sustainability sub-check if adopted.
**Files:** scoring-reference.md, scale-anchors/cat8-economic.md, check-inventory.md, SKILL.md, synthesis.md, README.md
**Steps:**
1. Read v2-discrimination-analysis.md from Slice 6.
2. Decision gate (graded response):
   - Care effective influence >= 35% AND Cat 6 rank correlation < 0.95 → No weight changes. Phase 1 fixed it.
   - Care effective influence 30-35% AND Cat 6 rank correlation 0.95-0.98 → Partial shift: Cat 5 to 18%, Cat 6 to 17%.
   - Care effective influence < 30% AND Cat 6 rank correlation > 0.98 → Full Scheme A: Cat 5 to 20%, Cat 6 to 15%.
3. Decision gate for 8.4: if 2+ of the re-scored free products still score >= 90% on Cat 8, add 8.4 sustainability sub-check. If fewer than 2 cluster at 90%+, current 3-check Cat 8 is sufficient.
4. If weight changes adopted: update all weight references in scoring-reference.md, SKILL.md (python script weights dict, weight table, category headers), synthesis.md (dimensions section), README.md (weight table).
5. If 8.4 adopted: write sustainability anchor (5 levels), add to scoring-reference.md and cat8-economic.md, update check inventory, update SKILL.md python script.
6. Re-score 3-5 products to validate no unintended grade flips.
7. Update README.md weight table and check count if weights or counts changed.
8. Document all decisions and data in `docs/calibration/v2-weight-decision.md`.
**Tests:** If weights changed, re-run python script on all 11 calibration products with new weights. No product should flip more than 1 grade. Sparrow should not drop below B. Twitter should stay F.
**Depends on:** Slice 6 (discrimination data needed for decision)

## Existing Patterns
- Check anchors follow 5-level pattern: 5% / 25% / 50% / 75% / 100% with archetype examples
- scoring-reference.md is the consolidated runtime file, individual anchor files are source
- SKILL.md python script uses dict structure: `cat_checks = {1: [...], 2: [...], ...}`
- SKILL.md has multi-agent dispatch table splitting checks across 3 agents

## No-Gos
- Do NOT add new categories (no 9th category for reliability/performance)
- Do NOT change the geometric mean scoring method
- Do NOT change the 5% floor
- Do NOT change the 85% A-grade boundary
- Do NOT add OKR-style counter-metrics to individual checks
- Do NOT increase total check count beyond 48 (current 46 - 1 removal + 2 from splits = 47, + 1 potential 8.4 = max 48)
- Do NOT modify Cat 5's check structure (best-designed category, leave it alone)
- Do NOT change the conditional check system ([if:content], [if:mobile], etc.)
- Phase 2 changes require Phase 1 discrimination data — no weight changes without evidence

## Verification Commands
1. `grep -c "3.2" docs/scoring-reference.md` — should be 0 after Slice 2
2. `grep "Cat 2" docs/scoring-reference.md | head -1` — should show "4 checks" after Slice 3
3. `grep "Cat 3" docs/scoring-reference.md | head -1` — should show "5 checks" after Slice 2
4. `grep "Cat 7" docs/scoring-reference.md | head -1` — should show "6 checks" after Slice 4
5. `python3 -c "..."` with updated script — should run without error on sample data
6. `diff` between scoring-reference.md sections and individual anchor files — should match after Slice 6
