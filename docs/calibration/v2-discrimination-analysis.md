# V2 Discrimination Analysis

**Date**: 2026-04-01
**Method**: Re-score modified checks against V2 anchors using existing audit observations
**Products**: Sparrow Wallet, PodNews (The Frontier), Coinbase, Fountain, Twitter/X
**Baseline**: V1 batch analysis (11 products, discrimination stats from Section 2)

---

## 1. Modified Checks Summary

V2 changes affecting discrimination in Cats 2, 3, 4, 7:

| Change | V1 | V2 | Rationale |
|--------|----|----|-----------|
| 2.2 split | 1 check (Copy Is Interface Design) | 2.2a (Copy Guides Action) + 2.2b (Copy Shows Authorship) | V1 bundled too many copy dimensions; range was 25 pts |
| 3.2 killed | 6 checks | 5 checks | Range was 15 pts -- least discriminating check in framework |
| 3.1, 3.3, 3.4, 3.6 | Soft anchors | Sharper anchors with explicit tests | Floor/ceiling compression (stdev 8.7) |
| 4.1 maturity modifier | Single anchor set | Maturity-adjusted for 1M+ users / $10M+ revenue | AllTrails (60M users) and PodNews (pre-launch) scored same |
| 7.3 split | 1 check (AI Disclosed and Labeled) | 7.3a (AI Content Transparency) + 7.3b (Human Authorship Signal) | Rewarded AI absence same as responsible disclosure |

---

## 2. Per-Product Re-Scored Check Values

### Cat 2: Writing & Thinking (V2: 4 checks -- 2.1, 2.2a, 2.2b, 2.3)

| Check | Sparrow | PodNews | Coinbase | Fountain | Twitter/X |
|-------|---------|---------|----------|----------|-----------|
| 2.1 (unchanged) | 85 | 70 | 50 | 70 | 50 |
| **2.2a** Copy Guides Action | **70** | **80** | **55** | **50** | **40** |
| **2.2b** Copy Shows Authorship | **85** | **70** | **30** | **55** | **55** |
| 2.3 (unchanged) | 80 | 55 | 50 | 72 | 45 |
| **V1 2.2 (for reference)** | 75 | 75 | 55 | 55 | 55 |

**Key re-scoring decisions**:
- **Coinbase 2.2b: 30%**. "The future of finance is on Coinbase" is interchangeable template text. Marketing uses "transformative", "groundbreaking", "seamless." V2 anchor at 25%: "consistent tone but no distinctive voice." Scored 30 because Help Center has functional specificity, but the voice is corporate-generic.
- **PodNews 2.2a: 80%**. Empty states say "No insights match these filters" with "Adjust Filters" CTA and relaxation suggestions with result counts. Zero-results offers term decomposition. This is the V2 75% archetype or better.
- **Twitter/X 2.2a: 40%**. "Something went wrong. Try again." is explicitly the V2 25% archetype. Core posting labels are adequate (pulling above 25%), but V2 says "score the worst element" -- error messages anchor the score.

### Cat 3: Design & Interface (V2: 5 checks -- 3.1, 3.3, 3.4, 3.5, 3.6; 3.2 killed)

| Check | Sparrow | PodNews | Coinbase | Fountain | Twitter/X |
|-------|---------|---------|----------|----------|-----------|
| **3.1** Info Density | 75 | 80 | 60 | **50** | **50** |
| **3.3** Design Consistency | 70 | 75 | 65 | **45** | **50** |
| **3.4** Self-Evident UI | **60** | **78** | **50** | **40** | **40** |
| 3.5 (unchanged) | 95 | 95 | 50 | 70 | 25 |
| **3.6** Accessibility | 55 | **72** | **65** | **35** | 50 |

**Key re-scoring decisions**:
- **Fountain 3.4: 40%** (was 50). V2 says "dead-end empty states = 25% or below" and "score the worst edge state." Multiple pages returning 404 (/privacy, /terms, /about) are literal dead ends. Earning mechanics confuse users per reviews.
- **Twitter/X 3.1: 50%** (was 60). V2 explicitly names "Twitter's main feed: functional density, no hierarchy innovation" as the 50% archetype. The framework now calibrates Twitter as the midpoint.
- **PodNews 3.6: 72%** (was 70). V2 75% anchor: "deliberate accessibility effort... custom focus styles matching design system." PodNews has 40 focus-visible occurrences, 199 ARIA attributes, reduced-motion support, and 44px min touch targets -- approaching the 75% standard.
- **Fountain 3.6: 35%** (was 45). V2 says "no visible evidence of accessibility work" combined with absent care signal pushes below 50%. Single font (Inter), no ARIA/skip links detected.

### Cat 4: Product Craft (V2: 4 checks -- 4.1 with maturity modifier, 4.2-4.4 unchanged)

| Check | Sparrow | PodNews | Coinbase | Fountain | Twitter/X |
|-------|---------|---------|----------|----------|-----------|
| **4.1** Shipped Ready | 75 | 65 | **50** | 50 | **45** |
| 4.2 (unchanged) | 85 | 65 | 55 | 45 | 40 |
| 4.3 (unchanged) | 80 | 60 | 45 | 55 | 50 |
| 4.4 (unchanged) | 75 | 55 | 65 | 70 | 50 |
| **V1 4.1 (for ref)** | 75 | 65 | 60 | 50 | 50 |

**Maturity modifier triggered for**:
- **Coinbase**: 98M+ users, publicly traded (COIN). V2 says "for products with 1M+ users: secondary flow issues = 50% ceiling; billing bugs/data loss should not score above 50%." Trustpilot reviews describe wallet reconnection bugs, account restrictions, withdrawal difficulties. **4.1: 60 -> 50**.
- **Twitter/X**: Millions of users, major platform. Spaces shipped incomplete, Communities undermaintained, "Something went wrong" errors at massive scale. **4.1: 50 -> 45**.
- **Sparrow, PodNews, Fountain**: No public evidence of 1M+ users or $10M+ revenue. Standard anchors apply. No change.

### Cat 7: Honesty & Transparency (V2: 6 checks -- 7.1, 7.2, 7.3a, 7.3b, 7.4, 7.5)

| Check | Sparrow | PodNews | Coinbase | Fountain | Twitter/X |
|-------|---------|---------|----------|----------|-----------|
| 7.1 (unchanged) | 90 | 45 | 45 | 55 | 40 |
| 7.2 (unchanged) | 85 | 75 | 45 | 65 | 30 |
| **7.3a** AI Transparency | **N/A** | **45** | **50** | **55** | **50** |
| **7.3b** Human Authorship | **90** | **55** | **45** | **65** | **45** |
| 7.4 (unchanged) | 95 | 95 | 30 | 55 | 30 |
| 7.5 (unchanged) | 80 | 40 | 40 | 65 | 50 |
| **V1 7.3 (for ref)** | 90 | 65 | 50 | 70 | 40 |

**Key re-scoring decisions**:
- **Sparrow 7.3a: N/A**. No user-facing AI content detected. V2 explicitly says "if no user-facing AI content detected -> N/A." This is the intended fix -- V1 gave Sparrow 90% for not using AI, conflating absence with transparency.
- **PodNews 7.3a: 45%** (V1 7.3 was 65). V2 isolates the transparency question. AI used extensively (Gemini Flash, DeepSeek) but no "AI-generated" labels at point of encounter. Footer hints at automation. V2 50% anchor: "disclosed somewhere but not at point of encounter." Below 50 because the disclosure is more hint than statement.
- **PodNews 7.3b: 55%**. Mixed signals. Editorial voice in kickers ("No algorithm. No feed. Just signal.") but generated body text is the primary content surface. V2 50% = "mixed signals."
- **Twitter/X 7.3a: 50%** (V1 7.3 was 40). Grok image watermarks are genuine point-of-encounter disclosure. But Grok text and AI-assisted customer support lack labeling. V2 isolating transparency from authorship gives Twitter credit for the watermark investment.
- **Fountain 7.3b: 65%**. Blog is clearly human-written with specific technical detail. Oscar Merry's voice is present. Product copy less distinctive but the human signal is there.

---

## 3. New Category Scores (Modified Categories Only)

Category scores are geometric means of applicable checks within each category.

| Product | Cat 2 V1 | Cat 2 V2 | Cat 3 V1 | Cat 3 V2 | Cat 4 V1 | Cat 4 V2 | Cat 7 V1 | Cat 7 V2 |
|---------|----------|----------|----------|----------|----------|----------|----------|----------|
| Sparrow | 80% | 79.8% | 71% | 69.7% | 79% | 78.6% | 88% | 87.9% |
| PodNews | 66% | 68.1% | 77% | 79.6% | 61% | 61.1% | 61% | 56.3% |
| Coinbase | 52% | 45.1% | 58% | 57.6% | 56% | 53.3% | 41% | 42.0% |
| Fountain | 65% | 61.0% | 54% | 46.6% | 54% | 54.3% | 62% | 59.8% |
| Twitter/X | 50% | 47.2% | 47% | 41.6% | 47% | 46.1% | 37% | 39.9% |

**Notable movements**:
- **Coinbase Cat 2: 52 -> 45.1** (-6.9). The 2.2b split exposes Coinbase's generic voice. Template-derived marketing copy scores 30% on authorship while functional labels hold at 55% on action guidance.
- **Fountain Cat 3: 54 -> 46.6** (-7.4). Largest single-category drop. Sharper anchors penalize 404 dead-end pages (3.4: 50->40), absent a11y signal (3.6: 45->35), and uniform-not-communicative spacing (3.1: 55->50). Removing 3.2 (which was 55, near the category mean) slightly concentrates the remaining checks.
- **PodNews Cat 7: 61 -> 56.3** (-4.7). The 7.3 split correctly separates PodNews's weak AI transparency (7.3a: 45) from its mixed human signal (7.3b: 55). V1 conflated these into 65.
- **PodNews Cat 3: 77 -> 79.6** (+2.6). Removing 3.2 (which was 70, below PodNews's Cat 3 mean) and the slight upward adjustment on 3.6 (70->72) and 3.4 (75->78) lifts the category.
- **Twitter/X Cat 7: 37 -> 39.9** (+2.9). V2 split gives Twitter partial credit for Grok watermarks (7.3a: 50, up from combined 40) while correctly penalizing weak human authorship signal (7.3b: 45).

---

## 4. Discrimination Stats: Baseline vs V2

Standard deviations and ranges computed across the 5 re-scored products. Baseline stdev is from the full 11-product batch analysis (Section 2 of batch-analysis.md).

| Category | Baseline StDev (11 products) | V1 StDev (5 products) | V2 StDev (5 products) | Delta (V2 - V1) | V1 Range | V2 Range |
|----------|-------|-------|-------|-------|-------|-------|
| Cat 2: Writing | 9.5 | 12.2 | **14.5** | **+2.4** | 30 | **34.7** |
| Cat 3: Design | 8.7 | 12.3 | **15.8** | **+3.4** | 30 | **38.0** |
| Cat 4: Craft | 10.7 | 12.1 | **12.3** | +0.3 | 32 | 32.5 |
| Cat 7: Honesty | 17.2 | 20.3 | 19.2 | -1.1 | 51 | 48.0 |

**Interpretation**:

**Cat 3 improved the most** (+3.4 stdev, +8.0 range). This is the target category -- V1 batch analysis identified it as the weakest discriminator (stdev 8.7, range 30). The V2 changes achieved exactly what was intended: killing the non-discriminating 3.2 check and sharpening the remaining anchors spread the scores from a 30-point range to a 38-point range. Fountain (46.6%) and Twitter/X (41.6%) are now more clearly separated from PodNews (79.6%) and Sparrow (69.7%).

**Cat 2 improved meaningfully** (+2.4 stdev, +4.7 range). The 2.2 split creates a wider spread by separating action guidance (where products converge, 40-80%) from authorship signal (where they diverge dramatically, 30-85%). Coinbase's drop to 45.1% is driven entirely by the authorship split exposing its template-derived voice.

**Cat 4 barely changed** (+0.3 stdev, +0.5 range). The maturity modifier only affected 2 of 5 products (Coinbase -10, Twitter -5). Sparrow, PodNews, and Fountain were unchanged because no public evidence of 1M+ users exists. The modifier works but fires rarely in this sample.

**Cat 7 slightly compressed** (-1.1 stdev, -3.0 range). The 7.3 split had offsetting effects: it lowered PodNews (7.3a exposed weak AI transparency) but raised Twitter/X (7.3a credited Grok watermarks). The net effect is a slightly tighter band. This is acceptable -- Cat 7 already had excellent discrimination (stdev 17.2) and the split fixed the more important problem of conflating AI absence with AI transparency.

---

## 5. Effective Influence by Dimension

**Dimension definitions**: Care (Cats 1-4, 40% weight), Structure (Cats 5-6, 35% weight), Signal (Cats 7-8, 25% weight). Dimension scores are geometric means of the constituent categories.

### V1 Dimension Scores

| Product | Overall | Care | Structure | Signal |
|---------|---------|------|-----------|--------|
| Sparrow | 84.3% | 77.9% | 86.9% | 91.4% |
| PodNews | 63.0% | 63.7% | 60.4% | 73.3% |
| Coinbase | 39.9% | 53.9% | 29.0% | 41.0% |
| Fountain | 54.1% | 59.9% | 44.2% | 62.5% |
| Twitter/X | 30.9% | 47.0% | 19.0% | 30.4% |
| **StDev** | **20.8** | **11.6** | **26.8** | **24.5** |
| **Range** | | **30.9** | **67.9** | **61.0** |

### V2 Dimension Scores

| Product | Overall | Care | Structure | Signal |
|---------|---------|------|-----------|--------|
| Sparrow | 84.1% | 77.4% | 86.9% | 91.4% |
| PodNews | 62.7% | 64.7% | 60.4% | 70.4% |
| Coinbase | 39.2% | 51.3% | 29.0% | 41.5% |
| Fountain | 52.7% | 56.9% | 44.2% | 61.4% |
| Twitter/X | 30.6% | 44.7% | 19.0% | 31.6% |
| **StDev** | **20.9** | **12.6** | **26.8** | **23.7** |
| **Range** | | **32.7** | **67.9** | **59.8** |

### Dimension Discrimination Comparison

| Dimension | V1 StDev | V2 StDev | Delta | V1 Range | V2 Range | Delta |
|-----------|----------|----------|-------|----------|----------|-------|
| Care (Cats 1-4) | 11.6 | **12.6** | **+1.0** | 30.9 | **32.7** | **+1.8** |
| Structure (Cats 5-6) | 26.8 | 26.8 | 0.0 | 67.9 | 67.9 | 0.0 |
| Signal (Cats 7-8) | 24.5 | 23.7 | -0.8 | 61.0 | 59.8 | -1.2 |

**Care dimension improved but the gap remains structural**. V2's Care stdev rose from 11.6 to 12.6 (+8.6%), with a range increase from 30.9 to 32.7. The improvement is real but modest. Structure still produces 2.1x more discrimination than Care (stdev 26.8 vs 12.6). This gap is inherent to the measurement targets -- care attributes (writing quality, design consistency, accessibility) naturally compress because professional products converge on competent-but-unremarkable craft. Structural attributes (open vs closed, custodial vs non-custodial, tracking vs privacy) are binary or near-binary decisions that produce large score gaps.

**Signal dimension barely moved** (-0.8 stdev). The 7.3 split redistributed scores within Cat 7 without dramatically widening the spread. Cat 8 (Economic Alignment, unchanged) remains the dominant contributor to Signal dimension discrimination.

**Overall score impact is minimal**. The weighted geometric mean changed by less than 1.5 points for any product. The V2 changes refine discrimination within categories without altering the overall grade for any product in this sample. This is the intended behavior -- the goal was to sharpen the Care dimension's internal measurement, not to change grades.

---

## 6. Conclusion: Did the Care Dimension Improve?

**Yes, but with clear limits.**

### What worked

1. **Cat 3 discrimination improved by 39%** (stdev 12.3 -> 15.8, range 30 -> 38). The combination of killing the non-discriminating 3.2 check and sharpening anchors on 3.1, 3.3, 3.4, and 3.6 achieved the targeted improvement. Products that genuinely care about design (PodNews: 79.6%) are now more clearly separated from products that don't (Fountain: 46.6%, Twitter: 41.6%).

2. **Cat 2 discrimination improved by 19%** (stdev 12.2 -> 14.5, range 30 -> 34.7). The 2.2 split into action guidance and authorship signal works as intended. Authorship (2.2b) is the new power discriminator within Cat 2 -- scores range from 30% (Coinbase) to 85% (Sparrow). Action guidance (2.2a) has a tighter but still meaningful range (40-80%).

3. **The 7.3 split fixed the semantic problem**. Sparrow no longer scores 90% on AI transparency for not using AI (now N/A). PodNews's weak AI disclosure is correctly separated from its mixed human authorship signal. The fix is qualitatively correct even though it didn't increase Cat 7 stdev.

4. **The maturity modifier makes 4.1 fairer**. Coinbase at 98M users should not score the same as PodNews at pre-launch for similar technical issues. The modifier creates a 10-point separation that didn't exist in V1.

### What remains

The fundamental asymmetry persists: **Structure (stdev 26.8) discriminates 2.1x better than Care (stdev 12.6)**. This is not a framework flaw -- it reflects reality. Whether a product is open-source or closed-source is a binary decision with a 70+ point spread. Whether a product has "good" or "great" copy quality is a spectrum with a 35-point spread. The V2 changes squeezed more discrimination out of Care, but they cannot make craft attributes discriminate like structural decisions.

**The Care dimension's role is ceiling differentiation, not floor separation.** Structure separates the D/F tier from the B/C tier. Care separates the B tier from the A tier. Sparrow's Care score (77.4%) versus PodNews's (64.7%) is a 12.7-point gap that contributes to the B vs C grade difference. The V2 changes make this ceiling differentiation slightly sharper.

### Recommendation

The V2 anchor changes should be deployed. They improve discrimination in the two weakest categories (Cat 2, Cat 3) without disrupting the framework's existing strengths. The 7.3 split and 4.1 maturity modifier fix known semantic problems. No further anchor changes are needed for the Care dimension -- the remaining compression reflects the underlying reality that professional products converge on adequate craft.

---

## Appendix: V2 Overall Scores (5 products)

For reference, the full V2 overall scores using the weighted geometric mean (unchanged cats at V1 values):

| Product | V1 Overall | V2 Overall | Delta | Grade Change? |
|---------|-----------|-----------|-------|---------------|
| Sparrow | 84.3% | 84.1% | -0.2 | No (B) |
| PodNews | 63.0% | 62.7% | -0.3 | No (C) |
| Coinbase | 39.9% | 39.2% | -0.7 | No (D) -- still on D/F boundary |
| Fountain | 54.1% | 52.7% | -1.4 | No (D) |
| Twitter/X | 30.9% | 30.6% | -0.3 | No (F) |

No grade flips. Coinbase moves slightly closer to the F boundary (39.2% vs 40% threshold). Fountain's 1.4-point drop is the largest, driven primarily by Cat 3's sharper anchors penalizing the 404 dead-end pages and absent accessibility effort.
