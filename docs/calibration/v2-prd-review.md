# V2 Framework Improvements PRD — Adversarial Review

**Date**: 2026-03-31
**Reviewer**: Opus 4.6 (adversarial review)
**PRD**: `docs/plans/2026-04-01-v2-framework-improvements.md`
**Inputs reviewed**: PRD (7 slices), improvement-plan.md, scoring-reference.md, SKILL.md, check-inventory.md, synthesis.md, scale-anchors/cat3-design.md

---

## Overall Assessment: REVISE

The PRD is well-structured with clear acceptance criteria, correct dependency ordering, and a sound philosophy (fix instruments, not math). However, it has **one pre-existing data conflict** it will propagate, **two specification gaps** that will force the builder to improvise, and **one structural problem** with the 3-check minimum rule that the PRD acknowledges but does not resolve. These should be fixed before building starts. Nothing requires rethinking the approach.

---

## Pre-Existing Data Conflict (Fix Before ANY Slices)

**check-inventory.md has weight conflicts within itself.** The category headers say Cat 1 = 15% (line 13) and Cat 7 = 10% (line 122), but the summary table at lines 148-158 says Cat 1 = 10% and Cat 7 = 15%. The summary table matches scoring-reference.md (lines 20, 26) and SKILL.md's python script weights dict (line 156). The category headers are wrong.

This is not caused by the PRD, but every slice that touches check-inventory.md will propagate it unless the builder notices and fixes it. The PRD's files lists for Slices 2, 3, and 4 all include check-inventory.md but none of their steps say "fix the weight conflict in Cat 1/Cat 7 headers."

**Recommendation**: Add a step to Slice 1 (or a new Slice 0): normalize check-inventory.md weights to match scoring-reference.md before making any other changes. This is a 2-minute fix that prevents a confusing diff.

---

## Per-Slice Findings

| Slice | Issue | Severity | Recommendation |
|-------|-------|----------|----------------|
| 1 | Report template changes are in SKILL.md only, but the multi-agent dispatch table (SKILL.md line 285) sends craft-scorer, conduct-scorer, and structure-scorer raw reference slices. The Audit Scope section and evidence-below-70% requirement need to be in the **orchestrator instructions**, not just the report template. Agents returning raw scores won't include evidence unless told to. | Medium | Add "for checks below 70%, include one specific observation" to the agent output instructions (SKILL.md ~line 297). Otherwise multi-agent mode bypasses the improvement. |
| 1 | Grade assignment change says "make the python script output the grade and inject it into the report." The python script already outputs a grade (SKILL.md line 177). The real problem is that the report template lets the agent write the grade independently. Step 2 should say: "Remove the grade from the report header template. Add instruction: always use the python script grade, never override." | Low | Clarify the step. The python script change is already done; the template change is the real work. |
| 2 | "Merge 3.2's best concept into 3.4" is vague. 3.4 already has a full 5-level anchor set measuring self-evident UI (navigation, undo, empty states, error recovery). Adding "affordance quality beyond convention" from 3.2 at the 75-100% level risks making 3.4 measure two different things: edge-state handling AND physical affordance quality. These are different skills. | High | See detailed answer in Q1 below. Either restrict the merge to a single sentence in 3.4's 100% anchor ("controls teach their function through form, not convention") or acknowledge that 3.4 absorbs 3.2 fully and rewrite 3.4 anchors to cover both dimensions. The PRD should specify which. |
| 2 | Step 6 says "Cat 1 is a 2-check sentinel by design" and should be exempt from the 3-check minimum. But scoring-reference.md line 29 states "Minimum 3 applicable checks per category. Below 3 -> exclude category, redistribute weight." And check-inventory.md line 179 repeats: "Minimum 3 active checks per category required." The SKILL.md python script uses `len(a) >= 2` (line 168), which already allows 2-check categories. The text rule and the code rule disagree. | High | The PRD must decide: (a) change the text rule in scoring-reference.md and check-inventory.md to say "Minimum 2" to match the code, or (b) keep the text at 3 and add an explicit Cat 1 exemption. Either way, this needs to be specified, not left for the builder to guess. The improvement-plan.md (lines 46-48) discusses this but does not resolve it. |
| 2 | Test says `grep -c "3.2" docs/scoring-reference.md` should return 0. But scoring-reference.md contains a V3-to-V1 mapping table (if present elsewhere or in check-inventory.md lines 200-201) where "3.2" appears as a historical reference. The grep test will fail unless historical references are also updated or the test is scoped to non-historical sections. | Low | Use a more specific grep: `grep "### 3.2" docs/scoring-reference.md` (matches the section header only). Or accept that historical mapping references to 3.2 will remain. |
| 2 | check-inventory.md is listed as a modified file, but `docs/check-inventory.md` is currently listed as a source in PRD line 11. The PRD says to "Update check-inventory.md summary counts" but the check-inventory.md summary table (lines 148-158) also includes the dimension breakdown (lines 160-163). If Slice 7 changes weights, the dimension breakdown percentages need updating too. | Low | Note in Slice 7 that check-inventory.md's dimension breakdown must be updated if weights change. |
| 3 | The 2.2 split creates 2.2a and 2.2b, but the multi-agent dispatch table says craft-scorer handles "Cat 1-4 (15 checks)." After the split, Cat 2 goes from 3 to 4 checks, making craft-scorer responsible for 16 checks. Step 7 acknowledges this. Good. No issue. | None | Already handled. |
| 3 | Anchor writing for 2.2a and 2.2b has no worked examples. Steps 1-2 say "Write anchor" with a brief focus description but no prototype anchor text. The builder must improvise 10 anchor levels (5 per sub-check) from a one-sentence description. Compare to Slice 5 Step 1, which gives specific text for floor and ceiling anchors. | Medium | Add at least a floor (5%) and ceiling (100%) prototype for both 2.2a and 2.2b. The improvement-plan.md (lines 90-91) gives more detail than the PRD -- the PRD should reference or incorporate it. |
| 4 | 7.3a N/A for "non-AI products" is the most dangerous specification gap. See Q3 below. | High | Requires explicit guidance on AI detection heuristics. |
| 4 | The maturity modifier for 4.1 uses "1M+ users or $10M+ revenue" as the threshold. How does the auditing agent determine user count or revenue? These figures are often not public. The improvement-plan.md (line 99) says "60M users, $2.7B valuation" for AllTrails, but that came from external knowledge, not the product surface. | Medium | Specify the data source: "Use publicly reported figures (app store download counts, press releases, Crunchbase). If no public figures exist, use the 'early product' anchors. Do not guess." |
| 4 | Tests say 7.3a should be N/A for Sparrow, Vexl, Coinbase. But Coinbase uses AI for customer support chatbots and fraud detection. This illustrates the AI detection problem directly -- see Q3. | Medium | Remove Coinbase from the "should be N/A" list or add a note that internal AI (fraud detection) does not trigger 7.3a since it is invisible to users. |
| 5 | Anchor rewrites for Cat 3 are the highest-effort, highest-risk work. The PRD gives specific floor/ceiling targets for 3.1 (Step 1) and 3.3 (Step 2) but only vague direction for 3.4 ("incorporate merged 3.2 concept") and 3.6 ("sharper distinction between 50% and 90%"). | Medium | Add prototype floor/ceiling text for 3.4 and 3.6 at the same level of specificity as 3.1 and 3.3. |
| 5 | Step 5 (tracking taxonomy for 5.5) has overlapping score ranges: "Infrastructure (70-90%)" overlaps with "First-party analytics (75-90%)." A self-hosted Plausible instance is both infrastructure and first-party analytics. | Low | Clarify that the taxonomy is a hierarchy (worst tracker type present sets the score), not a sum. If a product has infrastructure tracking (Sentry) AND standard surveillance (GA), the score is set by the worst: GA at 20-35%. |
| 5 | Step 7 says add "import without matching export" to 5.10 and 6.2 anchor text. But the No-Gos (line 187) say "Do NOT modify Cat 5's check structure." Anchor text modification is not structure modification -- this is fine. But worth noting the No-Go is about check structure (adding/removing checks), not anchor refinement. | None | No change needed. The No-Go is correctly scoped. |
| 5 | Depends on Slice 2 for the 3.2 merge into 3.4. This is correct. But Step 3 (3.4 rewrite) should explicitly say "verify 3.2 is removed before writing" to prevent the builder from working on 3.4 before Slice 2 is done. | Low | Add a verification step. |
| 6 | "Python script matches new 48-check structure" -- but if Slice 7 adds 8.4, it becomes 49. The script needs to handle both 48 and 49. | Low | The PRD acknowledges this in No-Gos line 186 ("max 49"). Slice 6 should note that if Slice 7 adds 8.4, the script needs another update. Or Slice 7 should include its own script update step (it does, in Step 5). This is handled. |
| 6 | Step 4 says "Re-score 5 products on ALL modified checks using new anchors." This re-scoring is done by the builder (Claude) applying new anchors to existing product knowledge. There is no re-fetching of product surfaces. If the original audit data is stale (products changed since the batch), the re-scoring will validate the anchors against outdated information. | Medium | Specify: "Re-score using the existing batch audit data (docs/audits/ or calibration batch). Do not re-fetch products. The goal is anchor discrimination, not absolute accuracy." |
| 6 | The script update must handle the `None`/N/A entries for 7.3a (which can be N/A for non-AI products). The current script handles None in check arrays (line 167: `if s is not None`), so this works. But 2.2a/2.2b and 7.3a/7.3b use lettered sub-check names. The script uses positional arrays, not named keys. The builder needs to know the array positions. | Low | Add a comment block to the script showing the position-to-check mapping for the modified categories: `# Cat 2: [2.1, 2.2a, 2.2b, 2.3]` etc. The PRD Step 1 includes this. Good. |
| 7 | Decision gate has no numeric thresholds. See Q5 below. | High | Needs specific criteria. |
| 7 | synthesis.md is listed as a modified file, but the PRD only says to update "dimensions section" if weights change. The synthesis.md also includes the category descriptions, check tables (lines 63-89), and the dimension weight table (lines 202-206). If Cat 3 drops from 6 to 5 checks or Cat 7 goes from 5 to 6, those tables need updating too. | Medium | Slice 7 should explicitly include: "Update synthesis.md check tables and counts for any category that changed." Or better: add synthesis.md to Slice 2 (when Cat 3 changes) and Slice 4 (when Cat 7 changes). |
| 7 | README.md is listed but no specific instructions for what to update. | Low | Add: "Update README.md weight table and check count if weights or check counts change." |

---

## Answers to Additional Questions

### Q1: How should merging 3.2 into 3.4 work without making 3.4 measure two things?

**Current state**: 3.4 (Self-Evident UI) measures navigation, undo/recovery, empty states, and error handling (scoring-reference.md lines 218-230). It is fundamentally about "can you use this without external help?" 3.2 (Physical Obviousness) measures whether controls look interactive -- affordances, visual cues, the 5-second rule (scoring-reference.md lines 190-202). These overlap at the concept level ("usable without instruction") but differ in what they examine: 3.4 looks at edge states and recovery; 3.2 looks at visual signaling.

**The improvement-plan.md** (line 34) says to merge "affordance quality beyond convention" -- the top-end discriminating concept from 3.2. This is the right instinct: 3.2's 50-75% range describes every professional product, but its 100% anchor ("interface teaches itself through progressive disclosure") is genuinely different from 3.4's current 100% anchor ("anticipates confusion and prevents it").

**Recommendation**: Do NOT rewrite 3.4 to cover both dimensions equally. Instead, add a single sentence to 3.4's 100% anchor: "Interactive elements teach their function through form -- controls signal capability through shape, color, and position without relying on convention alone." This keeps 3.4 focused on self-evidence while absorbing 3.2's only discriminating concept. The 5-25-50-75% anchors for 3.4 should remain focused on edge-state handling. If 3.2's affordance concept deserves equal weight, it should be its own check, not merged -- but the improvement-plan.md already argues it shouldn't be its own check (line 33: "every professional product meets the baseline").

### Q2: How does the agent determine product age for 1.2's N/A condition?

**Short answer**: It cannot do so reliably, and the PRD does not specify how.

Product age is knowable from: (a) domain WHOIS registration date, (b) Wayback Machine first snapshot, (c) app store "first published" date, (d) press releases or blog announcements. None of these are guaranteed accurate -- a domain can be registered years before a product launches, and WHOIS data is often privacy-protected.

The "no social media presence" half of the condition is more testable: search for official social accounts and check follower counts. But this creates a perverse incentive: a 3-month-old product that aggressively bought 50K bot followers would pass the 1.2 check normally (and presumably score low), while a 3-month-old product that ethically chose not to do social media would get N/A (scored more leniently).

**Recommendation**: Simplify the condition. Instead of "product < 6 months old AND no social media presence," use: "If the product has no discoverable social media presence and no evidence of community engagement (no followers, no testimonials, no community channels), score 1.2 as N/A." Drop the age requirement. The absence of social presence is the actual condition that makes 1.2 unevaluable -- the age is a proxy for it. A 2-year-old product with zero social presence is equally unevaluable on social authenticity. Document the source for this determination (app store listing date, Wayback Machine, or "no public record found").

### Q3: How does the agent determine whether a product uses AI? The N/A condition rewards non-disclosure.

This is the PRD's most significant specification gap.

**The problem in detail**: The current 7.3 scoring note (scoring-reference.md line 848) says "Products that don't use AI at all score 100% by default (nothing to disclose)." The PRD's proposed 7.3a would change this to N/A instead of 100%. This is philosophically better (absence of AI is not the same as transparent AI use). But it creates a new problem: **if a product uses AI internally but does not disclose it, the auditing agent cannot detect it, scores 7.3a as N/A, and the product receives no penalty.** A product that hides its AI use is treated identically to one that genuinely uses no AI.

The PRD's own test case illustrates this: Step 7 of Slice 4 says "7.3a should be N/A for Sparrow, Vexl, Coinbase (no AI in product)." But Coinbase uses AI for fraud detection, compliance screening, and customer support chatbots. The auditing agent, assessing from the product surface, would correctly see no AI content and score N/A. This is the right answer for 7.3a (there is no AI *content* to disclose), but it needs to be clear that 7.3a measures AI in user-facing content specifically, not AI in the product stack.

**Three detection approaches** (each with tradeoffs):

1. **Surface-only detection** (practical, imperfect): Check for visible AI indicators -- AI-generated content markers (Cat 1 overlap), chatbots, "AI-powered" claims in marketing, AI-related features in the UI. If none found, score N/A. This is honest about its limits but rewards non-disclosure.

2. **Marketing-claim cross-reference** (better, still gameable): If the marketing page says "AI-powered" but no AI content is labeled, score 7.3a low (disclosed in marketing, not at point of encounter). If marketing says nothing about AI and no AI is visible, score N/A. This catches the Vexl-style case where marketing claims AI but the product doesn't label it.

3. **Declare the scope explicitly** (recommended): Add to 7.3a's scoring notes: "This check measures user-facing AI content (generated text, AI summaries, chatbot responses, AI recommendations). Backend AI (fraud detection, spam filtering, recommendation algorithms) is out of scope for 7.3a. If no user-facing AI content is detected through surface inspection, score N/A. The auditor's inability to detect hidden AI use is an acknowledged limitation, not a loophole -- it is captured by the framework's 'Limitations' section."

**Recommendation**: Adopt approach 3. Add the scope declaration to 7.3a's anchor text. This is honest about the epistemological limit. The alternative (trying to detect all AI use from the surface) is impossible and would produce false classifications.

### Q4: Must the python script handle both old-format and new-format check arrays?

**No, and the PRD correctly does not require this.** The python script in SKILL.md is a template that the agent fills in at runtime -- it is not processing stored data. Each audit is a fresh run. The script template just needs to match the current check structure.

However, there is a secondary concern: **the calibration batch data** (11 products in docs/audits/ and docs/calibration/) was scored against the V1 structure (46 checks, with 3.2 present, without 2.2a/2.2b or 7.3a/7.3b). Slice 6, Step 4 says "Re-score 5 products on ALL modified checks." This re-scoring produces new check-level data in the V2 format. The old calibration data remains in V1 format.

**Recommendation**: No script backward-compatibility needed. But Slice 6 should explicitly state: "Old calibration data (V1 format) is not updated. V2 discrimination analysis uses only the 5 re-scored products. The full 11-product calibration data should be marked as V1-era in the batch-analysis.md or a note added to the V2 analysis."

### Q5: What thresholds trigger weight changes in Slice 7's decision gate?

The PRD says (Slice 7, Step 2):

> "Does Cat 6 still have >0.98 rank correlation with overall? Is Care effective influence still below 30%?"

These are thresholds for **triggering** the weight change. But the decision gate has no criteria for **how much** to change weights if triggered. It says "adopt Scheme A (Cat 5 to 20%, Cat 6 to 15%)" but this is a binary: adopt Scheme A or don't. There is no proportional response.

More importantly, the improvement-plan.md (lines 167-177) argues for a different logic: "After check sharpening, the effective influence numbers will change. If sharper Care-dimension checks widen their ranges, the Care dimension's effective influence rises from 22.6% toward its nominal 40% WITHOUT any weight changes. The weight shift may become unnecessary or need to be smaller."

The PRD's decision gate should capture this nuance.

**Recommendation**: Replace the binary decision gate with a graded response:

| Condition | Action |
|-----------|--------|
| Care effective influence >= 35% AND Cat 6 rank correlation < 0.95 | No weight changes needed. Phase 1 fixed it. |
| Care effective influence 30-35% AND Cat 6 rank correlation 0.95-0.98 | Partial shift: Cat 5 to 18%, Cat 6 to 17%. |
| Care effective influence < 30% AND Cat 6 rank correlation > 0.98 | Full Scheme A: Cat 5 to 20%, Cat 6 to 15%. |

Also add a criterion for 8.4: "Add 8.4 if 2+ of the re-scored free products still score >= 90% on Cat 8. If fewer than 2 cluster at 90%+, the current 3-check Cat 8 is sufficient."

---

## Top 3 Recommendations Before Building

### 1. Fix the 3-check minimum rule BEFORE any slices.

The text (scoring-reference.md line 29, check-inventory.md line 179) says "Minimum 3 applicable checks per category." The code (SKILL.md line 168) says `len(a) >= 2`. Cat 1 has 2 checks by design. When 1.2 goes N/A, Cat 1 becomes 1 check. The improvement-plan.md discusses this (lines 46-48) but leaves it unresolved. The PRD says "exempt Cat 1 from 3-check minimum" but does not specify whether to change the text, change the code, or add an explicit exemption.

**Action**: Decide now. The cleanest option: change the text to "Minimum 2 applicable checks per category" in both scoring-reference.md and check-inventory.md. This matches the existing code and is philosophically sound (Cat 1 is designed as a 2-check sentinel). Add a note: "If a category drops to 1 applicable check, exclude the entire category and redistribute weight."

### 2. Add AI detection scope to 7.3a before building Slice 4.

Without explicit scope, the builder will improvise a heuristic for "does this product use AI?" that may or may not match the framework's intent. This is the kind of ambiguity that produces the exact inconsistency the V2 improvements are designed to eliminate.

**Action**: Add to the PRD's Slice 4 Step 1: "7.3a measures user-facing AI content only (generated text, AI chatbots, AI summaries, AI recommendations). Backend AI (fraud detection, spam filtering, internal ML) is out of scope. If no user-facing AI content is detected through surface inspection, score N/A. Note this as an acknowledged limitation in the Audit Scope section."

### 3. Add anchor prototypes for 2.2a and 2.2b before building Slice 3.

Slices 3 and 4 are marked "uphill" because they require writing new anchors. Slice 5 provides specific floor/ceiling text for its anchor rewrites. Slices 3 and 4 do not. The improvement-plan.md contains more detailed descriptions (lines 90-91 for 2.2a/2.2b, lines 113-115 for 7.3a/7.3b) than the PRD. The builder should not have to cross-reference two documents to find the specification.

**Action**: Either inline the improvement-plan.md's anchor descriptions into the PRD's Slice 3 and 4 steps, or add explicit references: "For anchor writing guidance, see improvement-plan.md sections 1.1 and 1.3." The PRD should be self-contained for execution.

---

## Minor Issues (Fix During Build, Not Before)

1. **synthesis.md not in Slices 2-5 file lists**: synthesis.md has check tables for all categories (lines 63-89) that will be stale after check splits and removals. Either add synthesis.md to every slice that changes check counts, or add a single sync step in Slice 6.

2. **check-inventory.md Cat 1 and Cat 7 header weights are swapped**: Cat 1 header says 15% (line 13), Cat 7 header says 10% (line 122). Summary table (lines 150, 156) is correct at 10% and 15% respectively. Fix during Slice 2 when updating check-inventory.md.

3. **The PRD says 48 checks total after Phase 1**: Remove 3.2 (-1) + split 2.2 (+1) + split 7.3 (+1) = 47, not 48. Verify: V1 = 46 checks, -1 (3.2 removed) + 1 (2.2 split into 2.2a + 2.2b, net +1) + 1 (7.3 split into 7.3a + 7.3b, net +1) = 47. Wait -- removing 3.2 takes Cat 3 from 6 to 5 (-1). Splitting 2.2 takes Cat 2 from 3 to 4 (+1). Splitting 7.3 takes Cat 7 from 5 to 6 (+1). Net: 46 - 1 + 1 + 1 = 47. The PRD says 48 at lines 66, 139, 146. **This is a counting error.** The total should be 47, or 48 if Slice 7 adds 8.4. Verify and correct before building.

   UPDATE on recount: Wait. "Splitting" a check means one check becomes two. So 2.2 becomes 2.2a + 2.2b = net +1 check (was 1, now 2). Same for 7.3 -> 7.3a + 7.3b = net +1. Removing 3.2 = -1. Total: 46 - 1 + 1 + 1 = 47. The PRD's claim of 48 is off by 1. If 8.4 is added, it becomes 48 (not 49 as claimed in No-Gos line 186). Fix the count.

4. **scale-anchors/ directory exists** with 8 files matching the PRD's file list. PRD file list says `docs/scale-anchors/cat3-design.md` etc. -- confirmed these paths are valid.

5. **Overlap between Slice 5 Step 8 and the existing DNT anchor**: The current 5.5e anchor (scoring-reference.md lines 491-503) already describes silent DNT ignorance at the 5% level. Step 8 says add "acknowledged but dismissed DNT as explicitly worse than silent DNT ignorance." This needs careful placement -- "acknowledged but dismissed" should be at 5% (below the current "ignores DNT" at 5%), or it should redefine the 5% anchor. The builder needs to know which.
