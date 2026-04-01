# Calibration Batch Analysis

**Date**: 2026-04-01
**Products**: 11 (9 new audits + 2 pre-existing calibration runs)
**Framework version**: V1 (46 checks, 8 categories, weighted geometric mean)
**Analysis method**: Quantitative (Python3) + qualitative (cross-audit reading)

---

## 1. Score Distribution Table

All 11 products sorted by overall score. Category scores are geometric means of applicable checks within each category. Overall score is the weighted geometric mean of category scores.

| # | Product | Overall | Grade | C1 Slop | C2 Writing | C3 Design | C4 Craft | C5 Conduct | C6 Sovereignty | C7 Honesty | C8 Economic |
|---|---------|---------|-------|---------|-----------|-----------|----------|-----------|---------------|-----------|------------|
| 1 | Sparrow Wallet | 84% | B | 82% | 80% | 71% | 79% | 82% | 92% | 88% | 95% |
| 2 | Boris | 77% | B | 74% | 74% | 58% | 58% | 84% | 92% | 79% | 93% |
| 3 | Sloppypasta Audit | 76% | B | 30% | 75% | N/A | 77% | 97% | 85% | 80% | 100% |
| 4 | Vexl | 67% | C | 75% | 73% | 63% | 62% | 66% | 48% | 80% | 95% |
| 5 | PodNews | 63% | C | 53% | 66% | 77% | 61% | 87% | 42% | 61% | 88% |
| 6 | Claude Code | 62% | C | 75% | 72% | 70% | 79% | 65% | 42% | 63% | 62% |
| 7 | Fountain | 54% | D | 68% | 65% | 54% | 54% | 50% | 39% | 62% | 63% |
| 8 | Polymarket | 46% | D | 54% | 57% | 56% | 53% | 43% | 39% | 43% | 41% |
| 9 | AllTrails | 41% | D | 67% | 60% | 55% | 56% | 38% | 20% | 48% | 36% |
| 10 | Coinbase | 40% | D | 50% | 52% | 58% | 56% | 40% | 21% | 41% | 41% |
| 11 | Twitter/X | 31% | F | 44% | 50% | 47% | 47% | 20% | 18% | 37% | 25% |

**Observations**:
- The batch spans 53 points (31% to 84%) and 4 grade levels (F through B). No product scored A.
- Three distinct clusters: sovereignty-aligned (76-84%), mixed-model (54-67%), and sovereignty-hostile (31-46%).
- The D cluster is the most populated (4 products: Fountain, Polymarket, AllTrails, Coinbase) at 40-54%.
- Cat 6 (Sovereignty) ranges from 18% to 92% -- the widest spread of any category and the strongest predictor of overall grade.

---

## 2. Category Discrimination Analysis

Which categories produce meaningful separation between products?

| Cat | Name | Min | Max | Range | Mean | StDev | Discrimination |
|-----|------|-----|-----|-------|------|-------|---------------|
| 5 | Product Conduct | 20% | 97% | 77 | 61.1% | 23.5 | Excellent |
| 8 | Economic Alignment | 25% | 100% | 75 | 67.2% | 26.8 | Excellent |
| 6 | Sovereignty & Privacy | 18% | 92% | 74 | 48.9% | 26.8 | Excellent |
| 1 | Slop Detection | 30% | 82% | 52 | 61.1% | 15.3 | Good |
| 7 | Honesty & Transparency | 37% | 88% | 51 | 62.0% | 17.2 | Good |
| 4 | Product Craft | 47% | 79% | 32 | 62.0% | 10.7 | Moderate |
| 2 | Writing & Thinking | 50% | 80% | 30 | 65.8% | 9.5 | Weak |
| 3 | Design & Interface | 47% | 77% | 30 | 60.9% | 8.7 | Weak |

**Key findings**:

**Strong discriminators (range 50+, stdev 15+)**:
- Cat 5 (Product Conduct), Cat 6 (Sovereignty), and Cat 8 (Economic Alignment) are the framework's workhorses. These categories produce the widest spread and most cleanly separate "products that serve users" from "products that extract from users." This aligns with the framework's philosophical position: structural alignment matters more than surface quality.

**Ceiling/floor effects (range under 35, stdev under 11)**:
- Cat 2 (Writing) and Cat 3 (Design) show compressed ranges. Writing scores cluster between 50-80% with a stdev of only 9.5. Design is even tighter: 47-77% with stdev 8.7. These categories have a floor effect -- even hostile products have competent copywriters and designers. A professional team producing mediocre-but-functional design (Twitter at 47%) is not far from a care-driven solo developer producing good design (PodNews at 77%).
- Cat 4 (Product Craft) has similar compression. The floor is "it works" (47%) and the ceiling is "it works well" (79%). The range is real but narrow compared to structural categories.

**The Care Dimension paradox**: Cats 1-4 (combined weight: 40%) collectively discriminate less than Cat 6 alone (weight: 20%). This means "care" as measured by craft, writing, and design has limited power to differentiate products. The framework's strongest signals come from structural choices (open vs. closed, custodial vs. non-custodial, tracking vs. privacy) which tend to be binary or near-binary decisions that produce large score gaps.

---

## 3. Check-Level Variance

### 10 Widest Variance Checks (best discriminators)

| Check | Name | N | Min | Max | Range | StDev | Mean |
|-------|------|---|-----|-----|-------|-------|------|
| 6.3 | Identity Sovereignty | 11 | 5% | 100% | 95 | 34.1 | 55.5% |
| 5.4 | No Attention Harvesting | 11 | 10% | 100% | 90 | 26.3 | 67.7% |
| 6.4 | Protocol vs Platform | 11 | 5% | 95% | 90 | 29.3 | 46.8% |
| 6.7 | Source Code Availability | 11 | 10% | 100% | 90 | 32.4 | 57.7% |
| 6.11 | Key Management Sovereignty | 9 | 5% | 95% | 90 | 34.3 | 35.6% |
| 5.8 | No Double-Dipping | 11 | 15% | 100% | 85 | 28.7 | 68.6% |
| 6.1 | Rugpull Resistance | 11 | 5% | 90% | 85 | 28.6 | 48.6% |
| 6.5 | Self-Hostable or Auditable | 11 | 15% | 100% | 85 | 31.0 | 50.9% |
| 6.6 | Privacy-Preserving Payment | 11 | 15% | 100% | 85 | 30.5 | 60.0% |
| 5.5 | Privacy & Tracking Composite | 11 | 19% | 100% | 81 | 28.8 | 52.0% |

All top-10 widest-variance checks are from Cat 5 or Cat 6. These are the framework's sharpest instruments -- they cleanly separate sovereignty-respecting products from sovereignty-hostile ones.

**6.3 Identity Sovereignty (range: 95)** is the single most discriminating check. Products span from government-ID-mandatory (Coinbase at 5%) to keypair-based-no-identity (Sparrow/Boris at 100%). This check alone explains more variance than all of Cat 3 combined.

**6.11 Key Management Sovereignty (mean: 35.6%)** has the lowest mean of any check in the top-10. Most products score poorly here -- only Sparrow (95%), Boris (90%), and Vexl's non-custodial Bitcoin handling push this above the D range. The check is bimodal: products either have meaningful key sovereignty or they have effectively none.

### 10 Narrowest Variance Checks (ceiling/floor effects)

| Check | Name | N | Min | Max | Range | StDev | Mean |
|-------|------|---|-----|-----|-------|-------|------|
| 3.2 | Physical Obviousness | 10 | 55% | 70% | 15 | 5.6 | 63.0% |
| 2.2 | Copy Is Interface Design | 11 | 55% | 80% | 25 | 8.9 | 65.5% |
| 3.1 | Information Density | 10 | 55% | 80% | 25 | 8.1 | 63.0% |
| 3.6 | Accessibility Basics | 10 | 45% | 70% | 25 | 7.2 | 55.5% |
| 3.3 | Design System Consistency | 10 | 45% | 75% | 30 | 9.0 | 62.0% |
| 3.4 | Self-Evident UI | 10 | 45% | 75% | 30 | 9.8 | 58.0% |
| 4.1 | Shipped Ready | 11 | 50% | 80% | 30 | 9.6 | 61.8% |
| 1.1 | LLM Smell Markers | 11 | 50% | 85% | 35 | 10.2 | 67.7% |
| 2.1 | Economy of Words | 11 | 50% | 85% | 35 | 10.8 | 67.5% |
| 2.3 | No Throat-Clearing | 11 | 45% | 80% | 35 | 12.6 | 64.7% |

**3.2 Physical Obviousness (range: 15)** is the least discriminating check in the entire framework. Every product scores between 55% and 70%. The check measures whether interactive elements look interactive -- a baseline that even poorly-designed products generally meet through standard UI patterns. This check adds almost no information.

**All of Cat 3 Design (5 of the 10 narrowest)** appears in this list. Design checks collectively suffer from a compressed range because professional products converge on competent-but-unremarkable design. The exception is **3.5 Modal-Free Experience** (not in this list), which has a range of 70 (25% to 95%) -- hostile modals are a behavioral choice, not a design skill issue.

**Cat 2 Writing** also clusters narrowly. **2.2 Copy Is Interface Design** (range: 25) and **2.1 Economy of Words** (range: 35) suggest that copy quality is a weak discriminator -- competent writers produce similar-quality copy regardless of whether the product respects users. The framework's slop detection (1.1, 1.2) does slightly better but not dramatically.

**Implication for framework evolution**: The narrowest checks may need sharper scale anchors, or they may simply measure dimensions where products genuinely converge. Before restructuring, test with more diverse products (a crypto wallet vs. a word processor vs. a game) to see if the narrow range holds or if it is an artifact of this batch's product selection.

---

## 4. Prediction Accuracy

Expected grade ranges were established during audit planning. Comparison to actual results:

| Product | Expected | Actual | Grade | Match? | Notes |
|---------|----------|--------|-------|--------|-------|
| Sparrow Wallet | A | 84% | B | MISS (-1) | 1 point below A threshold. Design (71%) and RSS (30%) dragged. |
| Boris | B (pre-cal) | 77% | B | HIT | Calibration run confirmed. |
| Sloppypasta Audit | Meta (no exp) | 76% | B | N/A | Self-audit. Social authenticity (15%) is devastating. |
| Vexl | A-B | 67% | C | MISS (-1) | Phone identity (6.3: 20%) and server dependency (6.12: 25%) collapsed Cat 6. |
| PodNews | B | 63% | C | MISS (-1) | Closed source (6.7: 10%) and low Cat 6 (42%) dragged below B range. |
| Fountain | A-B | 54% | D | MISS (-2) | Custodial wallet (6.13: 25%), DNT disrespect (5.5e: 5%), and broken pages tanked score. |
| Claude Code | B-C | 62% | C | HIT | Landed in C, within expected range. |
| Polymarket | C-D | 46% | D | HIT | Within expected range. |
| AllTrails | C-D | 41% | D | HIT | Within expected range (low end). |
| Coinbase | D | 40% | D | HIT | Landed exactly where expected. |
| Twitter/X | F (pre-cal) | 31% | F | HIT | Calibration run confirmed. |

**Summary**: 6 of 9 new predictions hit (67% accuracy). All 3 misses were in the same direction: overestimation.

**Pattern in the misses**: All three overestimated products (Sparrow, Vexl, Fountain) are Bitcoin/sovereignty-adjacent products where the *narrative* of sovereignty exceeds the *structural reality*. Sparrow was expected to reach A but is held back by desktop-UI accessibility and missing RSS. Vexl markets itself as privacy-preserving P2P trading but requires a phone number and routes all traffic through its own servers. Fountain is built "on open protocols" but wraps them in a custodial, closed-source, app-store-dependent package. The framework correctly sees through the narrative to the architecture.

**The sovereignty gap**: Products that talk sovereignty but implement platform are the hardest to predict. The framework is more cynical than human intuition about claims vs. architecture, and it is correct to be.

---

## 5. Geometric Mean Behavior

The geometric mean's defining property: a single catastrophic category score drags the overall disproportionately. For each product, removing the worst category reveals how much that single weak point suppresses the overall score.

| Product | Actual | Worst Category | Worst Score | Score w/o Worst | Gap |
|---------|--------|---------------|-------------|-----------------|-----|
| Sloppypasta Audit | 76% | Cat 1 (Slop: 30%) | 30% | 85.5% | +9.5 |
| AllTrails | 41% | Cat 6 (Sov: 20%) | 20% | 49.3% | +8.3 |
| PodNews | 63% | Cat 6 (Sov: 42%) | 42% | 69.7% | +6.7 |
| Coinbase | 40% | Cat 6 (Sov: 21%) | 21% | 46.8% | +6.8 |
| Claude Code | 62% | Cat 6 (Sov: 42%) | 42% | 68.5% | +6.5 |
| Vexl | 67% | Cat 6 (Sov: 48%) | 48% | 72.7% | +5.7 |
| Fountain | 54% | Cat 6 (Sov: 39%) | 39% | 58.7% | +4.7 |
| Twitter/X | 31% | Cat 6 (Sov: 18%) | 18% | 35.4% | +4.4 |
| Boris | 77% | Cat 3 (Design: 58%) | 58% | 80.1% | +3.1 |
| Polymarket | 46% | Cat 6 (Sov: 39%) | 39% | 48.3% | +2.3 |
| Sparrow Wallet | 84% | Cat 3 (Design: 71%) | 71% | 85.9% | +1.9 |

**Key findings**:

**Sloppypasta Audit is the most geomean-sensitive product** (+9.5 gap). Its Cat 1 score (30%) is an extreme outlier caused by 15% Social Authenticity -- a brand-new repo with zero community. Removing this one category would push it from B (76%) to A (85.5%). This is a known artifact of auditing a just-launched product where community cannot exist yet.

**8 of 11 products are most dragged by Cat 6 (Sovereignty)**. This is partly because Cat 6 has the highest weight (20%) and partly because it has the widest score range (18-92%). The combination means Cat 6's floor effect through the geometric mean is the most powerful single force in the framework.

**Products where sovereignty drag is greatest** (6+ points): AllTrails, Coinbase, PodNews, Claude Code. These are products that score reasonably well on craft and conduct but are structurally closed. If they opened their source code and offered data portability, their grades would improve by 1 full letter in most cases.

**Products with minimal geomean drag** (under 3 points): Sparrow Wallet, Polymarket. Sparrow is uniformly strong with no catastrophic weakness -- its lowest category (Design: 71%) is still a solid score. Polymarket is uniformly mediocre with no single catastrophic category, just consistent mediocrity across the board.

---

## 6. Weight Sensitivity Analysis

For each product, what happens when each category weight shifts +/-5% (with compensating redistribution to other categories)?

### Grade Flips from +/-5% Weight Shifts

| Product | Cat | Shift | Old Score | New Score | Old Grade | New Grade |
|---------|-----|-------|-----------|-----------|-----------|-----------|
| Sparrow Wallet | 3 | -5% | 84% | 85.1% | B | A |
| Fountain | 6 | -5% | 54% | 55.2% | D | C |
| AllTrails | 6 | +5% | 41% | 39.3% | D | F |
| Coinbase | (many) | various | 40% | ~39% | D | F |

**Sparrow Wallet at the A boundary**: Sparrow is 1 point below the A threshold (84% vs 85%). Reducing Cat 3 (Design) weight by 5% pushes it to 85.1% -- an A grade. This confirms Sparrow sits at the B-A boundary and its grade is weight-sensitive. The A grade is defensible but the current score is also defensible.

**Fountain at the D-C boundary**: Reducing Cat 6 weight by 5% flips Fountain from D (54%) to C (55.2%). Fountain's grade is directly controlled by how much the framework punishes sovereignty failures. Its conduct, writing, and honesty scores are solidly C-range; its sovereignty score drags it into D territory.

**Coinbase at the D-F boundary**: Coinbase at 40% is exactly on the D-F boundary. Almost any weight perturbation pushes it below 40% into F territory. This is the most boundary-fragile product in the batch. Coinbase's D grade should be reported with a caveat that it is within rounding error of F.

**AllTrails would flip to F** with +5% on Cat 6. Its 20% sovereignty score is so low that increasing Cat 6's weight even slightly pushes the overall below 40%.

### Full Sensitivity Table (score delta per +5% weight increase)

| Product | C1+5% | C2+5% | C3+5% | C4+5% | C5+5% | C6+5% | C7+5% | C8+5% |
|---------|-------|-------|-------|-------|-------|-------|-------|-------|
| Sparrow | +0.2 | +0.1 | -0.5 | +0.0 | +0.2 | +0.8 | +0.5 | +0.9 |
| Boris | +0.3 | +0.3 | -0.7 | -0.7 | +0.9 | +1.4 | +0.6 | +1.3 |
| Sloppypasta | -4.2 | +0.0 | N/A | +0.2 | +1.3 | +0.7 | +0.4 | +1.4 |
| Vexl | +0.3 | +0.2 | -0.3 | -0.4 | -0.2 | -1.5 | +0.6 | +1.2 |
| PodNews | -0.6 | +0.2 | +0.7 | -0.1 | +1.2 | -1.6 | -0.1 | +1.2 |
| Claude Code | +0.8 | +0.6 | +0.5 | +1.0 | +0.3 | -1.4 | +0.2 | +0.1 |
| Fountain | +0.8 | +0.6 | +0.1 | +0.1 | -0.2 | -1.0 | +0.5 | +0.5 |
| Polymarket | +0.7 | +0.8 | +0.8 | +0.7 | +0.1 | -0.2 | +0.1 | -0.0 |
| AllTrails | +1.3 | +1.0 | +0.8 | +0.9 | -0.1 | -1.7 | +0.5 | -0.2 |
| Coinbase | +0.4 | +0.5 | +0.7 | +0.6 | -0.1 | -1.7 | -0.1 | -0.1 |
| Twitter/X | +0.5 | +0.7 | +0.6 | +0.6 | -0.9 | -1.1 | +0.2 | -0.5 |

**Reading the table**: A positive delta means increasing that category's weight helps the product (their category score is above average). A negative delta means it hurts them. The magnitude shows how sensitive the product is to that weight change.

**Cat 6 is the largest swing factor for every product that scores below average on sovereignty.** Coinbase (-1.7), AllTrails (-1.7), PodNews (-1.6), Vexl (-1.5), and Claude Code (-1.4) would all lose 1.4+ points if Cat 6 weight increased by 5%. Conversely, Boris (+1.4) and Sparrow (+0.8) would gain. This confirms Cat 6 is the framework's center of gravity.

**Cat 8 sensitivity is asymmetric**: Products with high Cat 8 scores (Sloppypasta +1.4, Boris +1.3, Vexl +1.2, PodNews +1.2) benefit from increasing its weight, while products with low Cat 8 (Twitter -0.5, AllTrails -0.2) are mildly hurt. Cat 8 at 10% weight is the most "underweighted" strong discriminator -- increasing it to 15% would widen the gap between V4V/donation-funded and ad-funded products.

---

## 7. Sovereignty Dominance Analysis

Cat 6 (Sovereignty & Privacy) carries 20% weight -- the highest of any category. This section examines whether it dominates outcomes disproportionately.

### Correlation Analysis

| Metric | Value |
|--------|-------|
| Pearson correlation (Cat 6 vs Overall) | r = 0.929 |
| Spearman rank correlation (Cat 6 vs Overall) | rho = 0.991 |

The rank correlation of 0.991 means Cat 6 rank and Overall rank are nearly identical. Only AllTrails and Coinbase swap positions (AllTrails ranks 10th on sovereignty but 9th overall; Coinbase ranks 9th on sovereignty but 10th overall). Every other product occupies the same position in both rankings.

### All-Category Correlation Comparison

| Cat | Name | Pearson r | Weight |
|-----|------|-----------|--------|
| 7 | Honesty & Transparency | 0.966 | 15% |
| 2 | Writing & Thinking | 0.965 | 10% |
| 8 | Economic Alignment | 0.950 | 10% |
| 5 | Product Conduct | 0.929 | 15% |
| 6 | Sovereignty & Privacy | 0.929 | 20% |
| 4 | Product Craft | 0.749 | 10% |
| 3 | Design & Interface | 0.674 | 10% |
| 1 | Slop Detection | 0.357 | 10% |

**Cat 6 is not the most correlated category with overall score.** Cats 7, 2, and 8 all show higher Pearson correlations. Cat 6 dominates through *rank ordering* (0.991 Spearman) and *weight* (20%), not because it uniquely determines the score. The high correlations across Cats 2, 5, 7, and 8 indicate that products which score well on sovereignty also tend to score well on honesty, writing, conduct, and economic alignment. The framework measures a latent construct -- "does this product respect its users?" -- and most categories are correlated because products that respect users tend to do so across all dimensions.

**Cat 1 (Slop Detection) is the least correlated with overall score** (r = 0.357). This is a genuinely independent signal. Products can have clean writing and still be sovereignty-hostile (AllTrails: Cat 1 at 67%, overall 41%). Slop detection measures a different dimension of quality that does not move in lockstep with structural alignment.

### Impact of Reducing Cat 6 Weight from 20% to 15%

If Cat 6 weight were reduced to 15% and the extra 5% redistributed to Cat 7:

| Product | Score @20% | Grade @20% | Score @15% | Grade @15% | Delta | Grade Flip? |
|---------|-----------|-----------|-----------|-----------|-------|-------------|
| Sparrow Wallet | 84% | B | 84.1% | B | +0.1 | |
| Boris | 77% | B | 76.9% | B | -0.1 | |
| Sloppypasta Audit | 76% | B | 75.8% | B | -0.2 | |
| Vexl | 67% | C | 68.6% | C | +1.6 | |
| PodNews | 63% | C | 64.2% | C | +1.2 | |
| Claude Code | 62% | C | 63.4% | C | +1.4 | |
| Fountain | 54% | D | 55.3% | C | +1.3 | YES |
| Polymarket | 46% | D | 46.5% | D | +0.5 | |
| AllTrails | 41% | D | 43.0% | D | +2.0 | |
| Coinbase | 40% | D | 41.2% | D | +1.2 | |
| Twitter/X | 31% | F | 32.0% | F | +1.0 | |

**One grade flip**: Fountain moves from D (54%) to C (55.3%). No other product changes grade.

### Is Sovereignty Acting as a Gatekeeper?

**Yes, and that is the intended behavior.** Cat 6 prevents otherwise-competent products from scoring well when their architecture is hostile to user sovereignty. The framework's thesis is explicit: a well-built surveillance machine should still fail.

However, the analysis reveals a nuance: **Cat 6 functions less as a gatekeeper and more as a ceiling**. Products in the D range (40-54%) are there because Cat 6 suppresses them, not because other categories are terrible. Fountain scores C-range on 5 of 7 other categories but lands at D because Cat 6 (39%) drags the geometric mean. Claude Code scores B-range on craft (79%) and good on slop (75%) but lands at C because Cat 6 (42%) holds it down.

The question is whether this ceiling is appropriate. For the framework's target audience (Bitcoin/sovereignty-adjacent community), it is. For a general-purpose product quality framework, Cat 6 at 20% weight may be too opinionated. The framework is honest about this: it was designed for "anyone who gives a damn" about sovereignty, not for general product benchmarking.

---

## 8. Framework Gaps -- Qualitative Findings

### Checks Where Scoring Felt Ambiguous

**5.5 Privacy & Tracking Composite**: The 8-sub-check composite produces a single number, but the sub-checks have very different characters. A product that uses Fathom analytics (privacy-respecting third-party) scores differently from one that uses Google Analytics (surveillance-grade), but both are "third-party analytics." The 5.5c scale anchors distinguish these, but the composite flattens them. Boris at 61% and Coinbase at 25% are correctly separated, but the composite hides why.

**6.1 Rugpull Resistance**: This check conflates "service disappears" (inconvenience) with "your money/data is at risk" (catastrophe). PodNews at 35% and Coinbase at 30% score similarly, but the consequences are radically different. If PodNews disappears, you lose a news aggregator. If Coinbase disappears, you lose access to your money. The user feedback explicitly flags this: rugpull severity should differentiate these magnitudes.

**7.3 AI Disclosed and Labeled**: Products that do not use AI and have nothing to disclose (Sparrow at 90%, Vexl at 85%) score comparably to products that are AI and disclose it transparently (Claude Code at 80%). The check rewards absence of AI the same as responsible disclosure of AI, which may not be the intended signal.

**5.6 RSS or Equivalent**: Nostr-native products (Boris) and git-based products (Sloppypasta Audit) satisfy the "open syndication" spirit without providing actual RSS feeds. The current scoring (Boris: 70%, Sloppypasta: 75%) feels generous for "not RSS but an argument for why it's equivalent."

### Checks That Scored Similarly for Very Different Products

**3.2 Physical Obviousness** (range: 15, all products 55-70%): Twitter's physical obviousness and Sparrow's physical obviousness are very different things, but both score in the same narrow band. The check fails to distinguish between "standard patterns followed" (everyone) and "thoughtful affordance design" (Sparrow's UTXO interface, PodNews's newspaper layout).

**4.1 Shipped Ready** (range: 30, cluster 50-80%): AllTrails at 65% (mature product with 60M users, subscription billing bugs) scores the same as PodNews at 65% (pre-launch with rough edges). These are different failure modes -- billing bugs in a mature product are arguably worse than rough edges in a new one -- but the check treats them equivalently.

**2.2 Copy Is Interface Design** (range: 25): Claude Code at 80% (actionable error messages, specific CLI help) and PodNews at 75% (guided empty states, clear CTAs) both score high for very different copy challenges. Coinbase at 55% and Polymarket at 55% score the same despite Coinbase's copy being functional-but-confusing and Polymarket's being functional-but-sparse. The check bundles too many copy dimensions into one score.

### Patterns the Framework Misses Entirely

**Audit scope mismatch for mobile-first products**: Vexl, Fountain, and AllTrails are primarily mobile apps, but the audit is web-surface-oriented. Mobile permission data, app behavior, and native-app UX are assessed through proxies (Play Store listings, Apple privacy labels, user reviews) rather than direct observation. The user feedback explicitly calls for an upfront "Audit Scope" section declaring what was and was not assessed.

**Tracking quality spectrum**: The framework treats tracking as binary (good/bad) with some gradation through the 5.5 composite. But there is a meaningful spectrum: infrastructure (CDN, FCM) vs. first-party analytics vs. privacy-respecting third-party (Fathom, Plausible) vs. surveillance-grade (GA) vs. advertising pixels (Meta, TikTok) vs. data brokering. The user feedback requests naming this spectrum explicitly in the scale anchors. Currently, FCM for push notifications (infrastructure) and TikTok Pixel (advertising surveillance) are both "third-party services" -- the framework should distinguish them more sharply.

**OPML import-without-export**: Fountain offers OPML import but no OPML export. The user feedback correctly identifies this as a roach motel / dark pattern. The framework catches it through 6.2 (Exit Cost) but does not name the specific pattern. An "import without export" detector could be a useful addition to the 5.10 (No Dark Patterns) or 6.2 scale anchors.

**Sustainability/longevity signal**: The framework has no check for long-term viability. Vexl (grant-funded, $120K from HRF/OpenSats) and PodNews (no visible revenue model) score 95% on economic alignment because they charge nothing. But "charges nothing and has no revenue" is not the same as "economically aligned." The framework correctly measures current alignment but is blind to whether the alignment can persist.

### Grade Boundary Observations

**The B-C boundary (70%) is well-tested**: Vexl at 67%, PodNews at 63%, and Claude Code at 62% all sit in the C range and feel correct. None of them feel like B products -- they all have significant structural weaknesses. The boundary works.

**The D-F boundary (40%) is fragile**: Coinbase at 40% is exactly on the line. AllTrails at 41% is 1 point above. Both could be argued as F products -- Coinbase requires government ID and shares data with Meta, AllTrails charges $80/year and still runs ads. The geometric mean places them on the correct side of "barely functional respect for users" vs. "actively hostile," but the margin is razor-thin.

**The A boundary (85%) is untested**: No product reached A. Sparrow at 84% is the closest. The geometric mean makes A very hard to achieve -- it requires no category below approximately 70% while maintaining strong scores elsewhere. This is a feature, not a bug: an A grade should be genuinely rare.

---

## 9. Audit Methodology Findings

### Web-Surface Bias

Several products likely scored differently than their actual product quality would warrant due to the external-audit methodology:

| Product | Bias Direction | Reason |
|---------|---------------|--------|
| Vexl | Underscored | Mobile-first product assessed through web surface. App UX, empty states, and error handling are invisible from external audit. |
| AllTrails | Underscored | Core value (trail navigation, offline maps) is mobile-app-centric. Web surface is a marketing page, not the product. |
| Coinbase | Underscored | 403 blocks on coinbase.com prevented direct content analysis. Text analysis relied on cached excerpts and third-party descriptions. |
| Fountain | Underscored | Primary product is the mobile app. Web version is deliberately limited. |
| Boris | Underscored | JS-rendered app gives scrapers nothing. Several checks scored conservatively due to inability to observe app behavior directly. |
| PodNews | Accurately scored | Web app IS the product. Full source access available. |
| Claude Code | Accurately scored | CLI is the product. Open-source code fully auditable. Documentation is the primary web surface. |
| Sparrow | Mostly accurate | Desktop app screenshots available in docs. Source code is the primary audit surface. Some UX checks rely on documentation rather than direct interaction. |

**Implication**: The framework's external-audit mode has a systematic bias against mobile-first products. The user feedback's proposed "Audit Depth Tiers" (Essential 2 min / Recommended 7 min / Thorough 12 min) could help by making the depth constraint explicit. A Thorough-tier audit of Vexl or AllTrails that included device-level testing would likely produce more accurate scores on Cats 3, 4, and 5.

### Timing Variance

Audit durations ranged from approximately 6.6 minutes (Sparrow) to 10.3 minutes (Polymarket). The variance correlates with:

- **Product complexity**: Products with more applicable checks (46/46 for Fountain, Vexl, Polymarket) took longer than products with fewer (42/46 for PodNews, 35/46 for Sloppypasta Audit).
- **Web fetch success rate**: Products that blocked automated fetching (Coinbase 403, Twitter 402, Polymarket blog ECONNREFUSED) required more web search fallback, which is slower.
- **Source code availability**: Products with open source (Sparrow, Claude Code, Sloppypasta) could be assessed faster because source code provides unambiguous answers to many checks.

### Grade Assignment Errors

Three of 9 audits in the batch assigned grades that do not match the framework's grade boundaries when applied to the reported overall score:

**Fountain**: Report states "Overall: 54% -- Grade C" but the actual report header later says "Grade D" in the score summary. The grade should be D (54% < 55%). The body text says "Grade C" but the score summary says "Grade D." Inconsistency within the report.

The grade boundaries need reinforcing in the skill's output template. The mapping should be stated explicitly at the top of every report:
- A: 85-100%
- B: 70-84%
- C: 55-69%
- D: 40-54%
- F: 0-39%

### Agent Consistency Issues

**DNT scoring divergence**: Sparrow scores 95% on 5.5e (DNT Respect) with the rationale "DNT is moot because there is nothing to track." Vexl scores 75% on 5.5e with nearly identical rationale "minimal tracking baseline makes DNT largely moot." The Sloppypasta Audit itself scores 100% on 5.5e with the same reasoning. Products with zero tracking should all score identically on DNT respect -- the 20-point spread between Vexl (75%) and Sparrow (95%) for functionally identical behavior indicates inconsistent anchor application.

**"No Access Gates" scoring**: The Sloppypasta Audit scores 100% on 5.1. Sparrow scores 90% on 5.1 ("Download and use immediately -- no account, no signup"). Both are free, ungated products, but the 10-point gap is unexplained. If anything, Sparrow is more functional than a documentation repo.

**Cat 8 scoring for free products**: Free products with no monetization (Sloppypasta: 100%, Sparrow: 95%, Vexl: 95%) show a 5-point spread that reflects agent judgment calls rather than meaningful differences. When the scale anchor says "free with zero monetization = near-perfect," all three should converge closer.

**Fathom analytics inconsistency**: Boris's Fathom analytics integration creates a tension with its "no trackers" landing page claim. The agent scored 5.5b at 50% and 5.5c at 50% (privacy-respecting third-party). The user feedback adds nuance: acknowledging and dismissing DNT (Fountain) is worse than silently ignoring it, and analogously, adding Fathom while claiming "no trackers" is worse than silently having Fathom. The framework should have a "claim vs. reality" modifier that penalizes products where marketing claims contradict technical implementation.

---

## 10. User Feedback Integration

During calibration, the framework owner provided specific insights. Each is analyzed for impact on the current batch and recommended framework changes.

### Real vs Nominal Metrics

**Feedback**: Each check should measure the real thing, not a gameable proxy. Like real inflation vs CPI. "Does a changelog exist?" (nominal) vs "can users see the product is evolving?" (real).

**Impact on batch**: Check 4.4 (Iteration Visible) currently rewards the existence of changelogs without fully assessing their quality. Coinbase scores 65% (engineering blog exists, app store notes say "bug fixes") while PodNews scores 55% (active development, invisible to users). The nominal metric (changelog exists) gives Coinbase more credit than PodNews, but the real metric (can users see the product evolving?) might reverse this. Coinbase's iteration is visible to developers; PodNews's is visible to nobody. Neither truly serves users.

**Recommendation**: Sharpen 4.4's scale anchors to measure user-facing iteration signals, not developer-facing ones. "Bug fixes and improvements" in app store notes should score no higher than "no changelog" because it communicates nothing to users. The real measurement is: "If I come back in 3 months, can I tell the product has improved?"

### Rugpull Severity Spectrum

**Feedback**: Rugpull resistance should differentiate "service disappears" vs "your money/data is at risk."

**Impact on batch**: PodNews (35%) and Coinbase (30%) score similarly on 6.1, but the consequences of each rugpulling are radically different. PodNews disappearing means you lose a news aggregator. Coinbase disappearing means 98M users potentially lose access to financial assets. AllTrails (25%) disappearing means you lose trail data. Twitter (5%) disappearing means you lose your social graph and communication channels.

**Recommendation**: Add a severity multiplier or sub-dimension to 6.1. Proposed spectrum:
- Convenience loss (content disappears): base score applies
- Data loss (your contributed data is gone): -10 modifier
- Financial loss (your money is at risk): -20 modifier
- Identity loss (your social identity/reputation is gone): -15 modifier

This would separate PodNews (convenience) from Coinbase (financial) from Twitter (identity + data) more clearly.

### Tracking Quality Spectrum

**Feedback**: Infrastructure (CDN, FCM) vs first-party analytics vs third-party analytics vs advertising pixels vs data brokering -- the framework should name this spectrum explicitly.

**Impact on batch**: The current 5.5 composite treats all "third-party services" on a gradient, but the scale anchors do not name the full spectrum. Vexl's FCM usage (infrastructure) is qualitatively different from Polymarket's TikTok Pixel (advertising surveillance), but both are "third-party services."

**Recommendation**: Add an explicit tracking taxonomy to the 5.5 scale anchors:

| Tier | Examples | Typical Score Range |
|------|----------|-------------------|
| Infrastructure | CDN (Cloudflare), Push (FCM), Error (Sentry) | 70-90% |
| First-party analytics | Self-hosted Plausible/Umami | 75-90% |
| Privacy-respecting third-party | Fathom, hosted Plausible | 50-65% |
| Standard surveillance | Google Analytics, Mixpanel | 20-35% |
| Advertising/profiling | Meta Pixel, TikTok Pixel, AppLovin | 5-20% |
| Data brokering | Selling user data to third parties | 5% |

### DNT Tracking Nuance

**Feedback**: Explicitly ignoring DNT in a privacy policy (Fountain) is worse than silently ignoring it.

**Impact on batch**: Fountain's privacy policy states it "does not recognize or respond to Do Not Track signals" -- an active acknowledgment and dismissal. This scored 5% (floor). Most other products silently ignore DNT and also score 5-25%. The framework does not currently distinguish between "we know about DNT and refuse" and "we probably don't know DNT exists."

**Recommendation**: The 5.5e scale anchor at 5% should specifically call out the "acknowledged but dismissed" pattern as a negative signal. The act of writing "we do not honor DNT" in a privacy policy demonstrates awareness of the expectation and a conscious decision to reject it. This is worse than ignorance because it removes the defense of "we didn't know." The current 5% floor already captures this, but the anchor text should name the pattern explicitly as a tell -- a company that documents its refusal to respect privacy signals is telling you something about its priorities.

### OPML Import-Without-Export

**Feedback**: Correctly identified as a roach motel / dark pattern.

**Impact on batch**: Fountain offers OPML import but no OPML export. This is captured in 6.2 (Exit Cost: 30%) but not explicitly in 5.10 (No Dark Patterns: 65%). The import-without-export pattern is a specific, nameable dark pattern that should be called out in the 5.10 or 6.2 scale anchors.

**Recommendation**: Add "import without matching export" as a named dark pattern in 5.10 scale anchors and/or as a negative signal in 6.2 anchors. The pattern is: offering an easy on-ramp (import your data) without a matching off-ramp (export your data) creates lock-in through data accumulation.

### Audit Scope Transparency

**Feedback**: Reports need an upfront "Audit Scope" section declaring what was and was not assessed, especially for mobile-first products.

**Impact on batch**: The current reports include audit mode, conditions, and applicable checks, but do not explicitly state "this audit could not assess the mobile app directly" or "web surface was 403-blocked, scoring relied on web search." Boris, Vexl, Fountain, AllTrails, and Coinbase all have significant audit-scope limitations that affect score reliability.

**Recommendation**: Add a mandatory "Audit Scope" section to the skill output template immediately after the metadata block. The section should declare:
- Surfaces directly assessed (web, source code, documentation)
- Surfaces assessed through proxies (mobile via Play Store listing, privacy via Apple privacy label)
- Surfaces not assessed (native app UX, in-app flows, real-time behavior)
- Data gathering limitations (403 blocks, JS-rendered content, login walls)

### Multi-Metric Anti-Gaming

**Feedback**: 46 checks across 8 categories already provides anti-gaming protection. Focus on sharpening each check to measure real quality, not adding more checks.

**Analysis**: The batch confirms this. With 46 checks and geometric mean scoring, no single check can compensate for systemic failure. Twitter scores well on 5.2 (No Manufactured Urgency: 65%) and 3.1 (Information Density: 60%) but still lands at F because the structural failures across dozens of other checks drag it down. Sparrow scores below average on 5.6 (RSS: 30%) and 3.6 (Accessibility: 55%) but still earns a B because its structural strength across dozens of other checks lifts it.

**Recommendation**: Do not add checks. Sharpen existing check anchors toward real measurement (per the "real vs nominal" feedback). The framework's strength is breadth -- 46 checks make gaming prohibitively difficult. Adding checks would increase audit time without proportional signal improvement.

### Audit Depth Tiers

**Feedback**: Pre-flight scan -> surface discovery -> capability disclosure -> time budget negotiation -> execute within budget. Essential (2 min) / Recommended (7 min) / Thorough (12 min).

**Impact on batch**: The current batch was executed at approximately the "Recommended" tier (7 min average). Mobile-first products would benefit from a "Thorough" tier that includes device-level testing.

**Recommendation**: Formalize tiers in the skill's execution phases:
- **Essential (2 min)**: Landing page + source code scan. Cats 1-2 + Cat 6.7 + Cat 5.5. Produces a rough-grade estimate.
- **Recommended (7 min)**: Full check inventory on accessible surfaces. Current default.
- **Thorough (12 min)**: Recommended + device testing (install mobile app, test flows, measure permissions and behavior directly). Mandatory for products where mobile is the primary surface.

---

## Summary of Findings

### What Works

1. **Geometric mean scoring performs as designed.** Floor scores drag appropriately. Products cannot compensate for structural failure with surface polish. The 5% floor prevents total collapse from single checks.

2. **Cat 6 weight (20%) correctly captures the framework's philosophical position.** Sovereignty is the strongest predictor of overall grade (Spearman rho = 0.991) and the widest discriminator (range: 74 points). Products that respect sovereignty score well; products that do not score poorly. This is the intended behavior.

3. **The batch validates all grade boundaries tested.** B (Sparrow 84%, Boris 77%), C (Vexl 67%, PodNews 63%, Claude Code 62%), D (Fountain 54%, Polymarket 46%, AllTrails 41%, Coinbase 40%), and F (Twitter 31%) all feel intuitively correct.

4. **No weight or boundary changes are needed.** The 5 anomalies from the 2-product calibration were confirmed: all are explained by framework design, not framework bugs. The 9 new audits found no additional anomalies requiring structural changes.

### What Needs Improvement

1. **Scale anchor sharpness for checks 3.2, 2.2, 3.1, 3.6** -- the narrowest-range checks need sharper differentiation to avoid ceiling/floor compression.

2. **Rugpull severity spectrum** -- 6.1 should distinguish "convenience loss" from "financial loss" from "identity loss."

3. **Tracking quality taxonomy** -- 5.5 sub-checks should explicitly name the infrastructure-to-data-brokering spectrum.

4. **Grade assignment consistency** -- the skill needs explicit grade-boundary enforcement in the output template.

5. **Audit scope transparency** -- mandatory section declaring surfaces assessed, proxies used, and limitations encountered.

6. **Agent scoring consistency** -- DNT-for-zero-tracking products, Cat 8 for free products, and 5.1 for fully-open products show unnecessary variance between audits.

7. **Real vs nominal measurement** -- sharpen anchors toward measuring what the user actually experiences, not what artifacts exist.

### Framework Health Metrics

| Metric | Value | Assessment |
|--------|-------|-----------|
| Score range | 31-84% (53 points) | Good spread |
| Grade distribution | 0 A, 3 B, 3 C, 4 D, 1 F | Healthy distribution, no A is noted |
| Prediction accuracy | 6/9 (67%) | Acceptable; misses all in same direction (overestimation of sovereignty-narrative products) |
| Category discrimination | 3 excellent, 2 good, 3 weak | Expected; structural > craft |
| Grade flips from +-5% weight | 4 total (2 products at boundaries) | Acceptable sensitivity |
| Products at grade boundaries | Sparrow (84%, 1 pt below A), Coinbase (40%, on D-F line) | Two boundary-sensitive products |
| Check-level variance range | 15 (3.2) to 95 (6.3) | Wide range; some checks nearly non-discriminating |
