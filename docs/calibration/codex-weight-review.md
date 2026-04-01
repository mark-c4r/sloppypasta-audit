# Adversarial Weight Review

**Date**: 2026-03-31
**Reviewer**: Opus (adversarial mode)
**Scope**: Weight distribution, check quality, grade boundaries, blind spots
**Data**: 11-product calibration batch + framework documentation

---

## 1. Critique of Current Weights

### The stated intent vs. the measured reality

The framework claims to measure five things: (1) sloppy patterns, (2) dark patterns across UI/payments/identity, (3) writing/visual sloppiness, (4) laziness or scammy practices, and (5) whether a user FEELS respected. The current weights tell a different story.

**The framework does not measure "feels respected." It measures "architecturally sovereign."** These overlap but they are not the same thing. A user of AllTrails (41%, D) feels respected every time they use the app -- the trails load, the maps work, the reviews are helpful. They do not feel the 20% sovereignty score. They will never encounter the lack of Lightning payments. They will never try to self-host AllTrails. The framework says AllTrails is a D product. A D product is described as "platform thinking, attention extraction, carelessness." AllTrails is not careless. It is structurally closed. Those are different failures.

Conversely, a user of Boris (77%, B) encounters default Tailwind, missing empty states, and silent error swallowing on first use. They FEEL the rough edges immediately. The framework gives Boris a B because its architecture is sound. The architecture is invisible to most users. The rough edges are not.

**The weight distribution is philosophically coherent but experientially wrong.** If the intent is "does the user feel respected," Care (40%) should dominate. If the intent is "can this product betray you," Structure (35%) should dominate. The framework tries to serve both masters and ends up serving sovereignty almost exclusively because of the geometric mean's amplification of Cat 6's wide range.

### Specific weight failures

**Cat 6 at 20% is not the problem. The problem is that Cat 6 has the widest range (74 points) AND the highest weight.** Weight and discrimination are multiplicative in the geometric mean. Cat 6's effective influence is approximately weight * variance = 20% * 26.8 = 5.36, while Cat 3's is 10% * 8.7 = 0.87. Cat 6 has 6x the effective influence of Cat 3. The Spearman rank correlation of 0.991 confirms this: Cat 6 rank IS the overall rank. The other 7 categories are decorative noise in the ranking.

**Cat 8 at 10% is underweighted relative to its discrimination.** Cat 8 has stdev 26.8 (tied with Cat 6 for highest), range 75, and excellent discrimination. It cleanly separates V4V/donation products from ad-funded ones. At 10% weight, its signal is muffled. The batch analysis itself notes this: "Cat 8 at 10% weight is the most 'underweighted' strong discriminator."

**Cat 2 and Cat 3 at 10% each are correctly weighted but poorly measured.** The problem is not their weight -- it is that their checks produce 30-point ranges instead of 70-point ranges. Increasing their weight would amplify noise, not signal. The checks need sharper teeth, not more influence.

**Cat 1 at 10% with only 2 checks is structurally fragile.** Two checks means one bad score catastrophically drags the category via geometric mean. Sloppypasta Audit's own Cat 1 score (30%) is driven almost entirely by 1.2 Social Authenticity (15%) -- a check that penalizes a brand-new product for not having a community yet. A category with 2 checks and 10% weight is a coin flip pretending to be a measurement.

### The calibration-notes.md contradiction

The calibration notes from the 2-product run concluded "No weight changes needed" and "weights validated." The batch analysis from the 11-product run also concluded "No weight or boundary changes needed." Both conclusions are drawn from data that shows Cat 6 determining 10 of 11 rank positions. This is not validation -- it is confirmation bias. The framework was designed to prioritize sovereignty, and when it prioritizes sovereignty, the analysis says "working as designed." The tautology prevents self-correction.

---

## 2. Alternative Weight Distributions

### Scheme A: "Felt Respect" (experience-first)

Reweight toward what users actually encounter. Reduce sovereignty's dominance without eliminating it.

| Cat | Name | Current | Proposed | Delta | Rationale |
|-----|------|---------|----------|-------|-----------|
| 1 | Slop Detection | 10% | 10% | 0 | Hold. Low check count limits upside. |
| 2 | Writing & Thinking | 10% | 10% | 0 | Hold until checks are sharpened. |
| 3 | Design & Interface | 10% | 10% | 0 | Hold until checks are sharpened. |
| 4 | Product Craft | 10% | 10% | 0 | Hold. Moderate discrimination. |
| 5 | Product Conduct | 15% | 20% | +5 | Conduct IS the felt experience. 23.5 stdev, excellent discrimination. |
| 6 | Sovereignty & Privacy | 20% | 15% | -5 | Still the largest single category. Reduces rank-determining dominance. |
| 7 | Honesty & Transparency | 15% | 15% | 0 | Hold. Good discrimination, appropriate weight. |
| 8 | Economic Alignment | 10% | 10% | 0 | Hold. Tempting to increase but 3 checks are thin. |

**Dimensions**: Care 40%, Structure 35%, Signal 25% (unchanged in aggregate -- the shift is within Structure)

**Effect on the batch**: From the sensitivity table, shifting 5% from Cat 6 to Cat 5 produces:
- Fountain: D -> C (55.3%). The most affected product -- its conduct (50%) is higher than its sovereignty (39%).
- AllTrails: gains ~1.5 pts. Stays D but moves away from F boundary.
- Vexl: gains ~1.3 pts. Stays C.
- Boris: loses ~0.5 pts. Stays B.
- Sparrow: loses ~0.6 pts. Stays B.
- No product flips more than 1 grade.

**The case for this scheme**: Conduct (how the product behaves toward you right now) is more actionable than sovereignty (how the product's architecture could theoretically betray you). A builder who reads "improve your conduct score" can fix dark patterns, remove login walls, and add RSS feeds this week. A builder who reads "improve your sovereignty score" faces "become a protocol" -- which is an architectural decision that may be impossible post-launch. If the framework wants to help builders improve, Conduct is the more useful lever.

**The case against**: This softens the framework's most distinctive feature -- its insistence that architecture matters more than behavior. Many frameworks already measure conduct. Few measure sovereignty. Softening sovereignty makes this framework less differentiated.

### Scheme B: "Discrimination-Weighted" (let the data decide)

Weight each category proportional to its demonstrated discrimination power (stdev). This removes philosophical bias and lets the measurement quality drive influence.

| Cat | Name | StDev | Normalized | Proposed Weight | Current |
|-----|------|-------|------------|----------------|---------|
| 6 | Sovereignty | 26.8 | 17.4% | 17% | 20% |
| 8 | Economic | 26.8 | 17.4% | 17% | 10% |
| 5 | Conduct | 23.5 | 15.3% | 15% | 15% |
| 7 | Honesty | 17.2 | 11.2% | 11% | 15% |
| 1 | Slop | 15.3 | 9.9% | 10% | 10% |
| 4 | Craft | 10.7 | 7.0% | 7% | 10% |
| 2 | Writing | 9.5 | 6.2% | 6% | 10% |
| 3 | Design | 8.7 | 5.7% | 6% | 10% |
| | **Total** | **153.8** | | **~89%** | |

Redistributed to sum to 100% (rounding):

| Cat | Proposed | Current | Delta |
|-----|----------|---------|-------|
| 1 | 10% | 10% | 0 |
| 2 | 7% | 10% | -3 |
| 3 | 7% | 10% | -3 |
| 4 | 8% | 10% | -2 |
| 5 | 16% | 15% | +1 |
| 6 | 18% | 20% | -2 |
| 7 | 12% | 15% | -3 |
| 8 | 22% | 10% | +12 |

**Dimensions**: Care 32%, Structure 34%, Signal 34%

**The biggest move**: Cat 8 jumps from 10% to 22%. This is the most provocative change -- it says "follow the money" is as important as "can they rugpull you." The data supports it: Cat 8 has the same stdev as Cat 6 (26.8) and excellent discrimination. It separates V4V products from ad-funded products as cleanly as Cat 6 separates open protocols from platforms.

**Effect on the batch**: Cat 8 at 22% would significantly widen the gap between high-Cat-8 products (Sloppypasta 100%, Boris 93%, Sparrow 95%) and low-Cat-8 products (Twitter 25%, AllTrails 36%, Coinbase 41%). Several D-range products would drop toward F. The framework becomes harsher on ad-funded products.

**The case for**: This scheme is empirically grounded. It says "weight what separates good from bad, not what you wish separated good from bad." Categories 2, 3, and 4 get demoted not because they are unimportant but because they fail to differentiate -- every product scores 50-80% on writing regardless of quality. Giving them 10% each is giving 30% weight to noise.

**The case against**: Discrimination power is sample-dependent. With 11 products (7 of which are Bitcoin/sovereignty-adjacent), the discrimination stats reflect this sample's variance, not universal variance. Cat 2 and Cat 3 might discriminate strongly in a sample that includes AI-generated landing pages, WordPress template sites, and hand-crafted indie tools. The sample is too small and too ideologically clustered to treat stdev as ground truth. Additionally, 22% on Economic Alignment with only 3 checks means each check carries 7.3% of the total score -- enormous single-check influence.

### Scheme C: "Fixed Care Floor" (protect the experiential signal)

Accept that Care categories discriminate weakly NOW but protect their influence so they can discriminate when checks improve. Increase Cat 8 moderately. This is the conservative option.

| Cat | Name | Current | Proposed | Delta |
|-----|------|---------|----------|-------|
| 1 | Slop Detection | 10% | 10% | 0 |
| 2 | Writing & Thinking | 10% | 10% | 0 |
| 3 | Design & Interface | 10% | 10% | 0 |
| 4 | Product Craft | 10% | 10% | 0 |
| 5 | Product Conduct | 15% | 15% | 0 |
| 6 | Sovereignty & Privacy | 20% | 17% | -3 |
| 7 | Honesty & Transparency | 15% | 13% | -2 |
| 8 | Economic Alignment | 10% | 15% | +5 |

**Dimensions**: Care 40%, Structure 32%, Signal 28%

**Effect on the batch**: Small movements. Cat 8 increase helps high-Cat-8 products (Boris, Sparrow, Sloppypasta gain ~1 point each) and hurts low-Cat-8 products (Twitter, AllTrails, Coinbase lose ~0.5 points each). Cat 6 decrease slightly lifts C/D-range products. Net effect: Sparrow might cross the A boundary (84% + ~1.4 = ~85.4%). No other grade flips.

**The case for**: Minimal disruption. Acknowledges Cat 8 is underweighted without making a dramatic philosophical shift. Preserves the framework's identity while making a data-justified correction.

**The case against**: This is a half-measure that changes nothing meaningful. The rank correlation between Cat 6 and overall would drop from 0.991 to approximately 0.98. Cat 6 still determines the ranking. If you are going to change weights, change them enough to matter.

### Recommendation

**Scheme A is the best option IF the framework's stated intent (user feels respected) is genuine.** The 5% shift from Cat 6 to Cat 5 is the minimum effective dose. It keeps sovereignty as the largest category while giving conduct -- the most directly experiential structural category -- more influence.

**Scheme B is the correct option IF the framework wants to be empirically honest**, but it requires more calibration data (30+ products across diverse categories) before the stdev numbers are trustworthy.

**Scheme C is the safe option** and should be the default if the creator is not ready to commit to a philosophical shift.

However, I want to be clear: **weight changes alone will not fix the fundamental problem.** Cat 6 dominates because it has the widest range, not just the highest weight. Even at 15% weight, Cat 6's range (74 points) dwarfs Cat 3's range (30 points). The only way to reduce Cat 6's dominance is to either compress Cat 6's range (by raising its floor -- giving partial credit more generously to closed-source products) or expand other categories' ranges (by sharpening their checks). The latter is the better path.

---

## 3. Five Most Problematic Checks

### 1. Check 3.2 -- Physical Obviousness (Range: 15, StDev: 5.6)

**The worst check in the framework.** Every product scores between 55% and 70%. The check asks "are controls identifiable?" -- a baseline that every professional product meets because standard UI patterns (buttons, inputs, links) have converged. The scale anchors describe a 0% product where "interactive elements look identical to static text" -- this is a 2008 Flash microsite problem, not a 2026 product problem.

**Fix**: Kill it or merge it into 3.4 (Self-Evident UI). Physical obviousness is a subset of self-evident UI, not a separate dimension. Alternatively, rewrite the check to measure "affordance quality beyond convention" -- does the product use visual design to communicate function in ways that go beyond standard patterns? This would separate Sparrow's UTXO interface (genuinely communicative) from Twitter's standard feed (follows patterns, communicates nothing about its data model).

### 2. Check 2.2 -- Copy Is Interface Design (Range: 25, StDev: 8.9)

**Measures too many things at once.** The check conflates: (a) is copy functional (guides, orients), (b) is copy specific (not generic), (c) is copy well-written (clear, concise), and (d) is copy intentional (someone designed it, not defaulted it). These are four different quality dimensions bundled into one score. Claude Code at 80% and PodNews at 75% both score high but for completely different reasons -- CLI error messages vs. editorial navigation. Coinbase at 55% and Polymarket at 55% score the same for completely different failures -- confusing vs. sparse.

**Fix**: Split into two checks: "Copy guides action" (functional -- does it tell you what to do?) and "Copy shows authorship" (craft -- could this copy only exist in this product?). The first measures interface design. The second measures care. Currently they cancel each other out into a mushy middle score.

### 3. Check 7.3 -- AI Disclosed and Labeled (Range: 35, StDev: 11.8)

**Conceptually confused.** Products that do not use AI (Sparrow 90%, Vexl 85%) score near-identically to products that ARE AI and disclose it (Claude Code 80%). The check rewards absence of AI the same as responsible disclosure of AI. A product that uses zero AI and a product that is built on AI but is transparent about it are being measured on the same scale for different reasons.

The batch analysis identifies this: "The check rewards absence of AI the same as responsible disclosure of AI, which may not be the intended signal."

**Fix**: Split into two separate signals. One measures "AI content transparency" (if AI is used, is it disclosed?). The other measures "human authorship signal" (does the content show evidence of human creation?). The first is a conduct check (honesty about tools). The second is a craft check (overlaps with Cat 1). Currently the check mixes them and produces a score that means different things for different products.

### 4. Check 4.1 -- Shipped Ready (Range: 30, StDev: 9.6)

**Fails to account for product maturity.** AllTrails at 65% (60M users, $2.7B valuation, subscription billing bugs) and PodNews at 65% (pre-launch solo dev, rough edges) score identically. These are radically different failure modes. Billing bugs in a product with 60M paying users are worse than rough edges in a pre-launch tool -- they indicate organizational dysfunction, not just "not ready yet." A pre-launch product is expected to have gaps. A product with $2.7B in funding is not.

The batch analysis identifies this exact problem but proposes no fix.

**Fix**: Add a maturity modifier. Products with >1M users or >$10M revenue should have their "shipped ready" expectation raised by one anchor level. A 60M-user product with billing bugs should not score above 50%. A pre-launch product with rough edges should score 50-65% without penalty inflation. The scale anchors should state: "For mature products (1M+ users), the 50% anchor is: core flow works but secondary flows have issues. For early products, the 50% anchor is: core flow mostly works with workarounds needed."

### 5. Check 1.2 -- Social Authenticity (Range: varies wildly, Mean: unclear)

**Punishes newness.** The Sloppypasta Audit's own score of 15% on this check -- producing a Cat 1 score of 30% -- demonstrates the problem. A brand-new product with zero community scores nearly at the floor because it has no followers, no engagement, no community. The check conflates "manufactured social proof" (bad) with "no social proof yet" (neutral). A product with bought followers and a product with no followers both score low, but for opposite reasons.

The batch analysis notes this is "a known artifact of auditing a just-launched product where community cannot exist yet." Known artifacts are bugs, not features.

**Fix**: Add a "pre-community" N/A condition. If a product is less than 6 months old and has no social media presence, 1.2 should score N/A rather than penalizing. The check is designed to catch manufactured social proof, not to punish products that have not had time to build an audience. Alternatively, rewrite the anchors so that "no social presence" scores 50% (neutral -- no evidence of fraud OR authenticity) rather than 15% (near-floor).

---

## 4. The A-Grade Question

### "No product reaches A" -- feature or bug?

**It is currently a feature masking a bug.**

The feature: the geometric mean makes A genuinely hard. It requires no catastrophic weakness. A product at 85% overall needs every category above approximately 65-70% (depending on weights), with strong categories compensating. This prevents gaming -- you cannot reach A by being amazing at sovereignty and terrible at design.

The bug: the A boundary is unreachable for the products this framework most wants to celebrate. Sparrow Wallet -- open source, non-custodial, privacy-preserving, Lightning-enabled, self-hostable, no tracking, no accounts, community-maintained -- scores 84%. One point below A. It is held back by Cat 3 Design (71%) because it has rough desktop UI edges and missing RSS feeds.

The philosophical question: **should a product lose a letter grade because its desktop UI has rough edges, when every other dimension is near-excellent?** The framework says yes -- "you can't compensate for genuine weakness in one check by over-delivering on another." But 71% in Design is not a genuine weakness. It is a competent-but-unpolished interface for a security-critical tool where the designers correctly prioritized function over aesthetics.

### What would need to change for A to be reachable?

Three paths:

**Path 1: Lower the A boundary to 82%.** Simple. Sparrow becomes A. Boris stays B (77%). The gap between B and A narrows from 15 points to 12 points. Risk: devalues the A grade. "Rarely achieved" is more meaningful than "achievable with strong effort."

**Path 2: Fix the weakest checks so they discriminate.** If Cat 3 checks had 50-point ranges instead of 30-point ranges, Sparrow's design might score higher (or lower -- sharper checks cut both ways). More importantly, the overall score would be based on real measurement rather than noise. The current Cat 3 score is 71% +/- approximately 8 points of measurement uncertainty. Sparrow might actually be an 80% design product with better checks. This is the correct long-term path but requires significant work.

**Path 3: Cap the geomean drag.** Introduce a rule: no single category's drag can exceed X points from the unweighted mean. This softens the geometric mean's punishment of the weakest category. Risk: fundamentally changes the scoring philosophy. The geometric mean's harshness is the framework's core identity.

### Recommendation

**Leave the A boundary at 85% but acknowledge in the framework documentation that reaching A requires excellence in craft, not just architecture.** The current synthesis document says "Rare" for A-grade. It should say: "Requires both sovereign architecture AND polished craft. A product with excellent sovereignty but rough design is a B, not an A. This is intentional -- architecture without craft is infrastructure, not a product."

The A grade SHOULD be achievable. Sparrow is 1 point away. Signal would likely score A. Bitcoin Core might. A hand-crafted Nostr client with good design could. The fact that no product in this sample reached A is a sampling artifact (7 of 11 products are Bitcoin-adjacent, which selects for sovereignty strength and design weakness), not a framework bug.

---

## 5. Biggest Blind Spot

### The framework does not measure reliability or performance.

The framework measures what a product IS (architecture, design, economics) but not what it DOES (uptime, speed, error rate). There is no check for:

- **Does it work when you need it?** A Bitcoin wallet that is beautifully designed, fully sovereign, and open source but crashes 20% of the time is a bad product. The framework would give it a B.
- **Is it fast enough to use?** A 6-second page load is disrespectful of the user's time. The framework has no check for performance. PodNews and Fountain could load in 200ms or 20 seconds and score identically.
- **Does it degrade gracefully?** When the network drops, when the server is slow, when the API returns errors -- what does the user see? Check 4.1 (Shipped Ready) touches this but only measures "does the core flow work on first use," not "does it work reliably over time."

This matters for the "feels respected" intent. Nothing makes a user feel less respected than a product that wastes their time through slowness or unreliability. A user will tolerate rough design (Boris at 58% Cat 3) if the product is fast and reliable. They will not tolerate beautiful design if the product hangs, crashes, or loses their work.

**Why this is the BIGGEST blind spot**: Every other gap identified in the batch analysis (rugpull severity, tracking taxonomy, audit scope) is a refinement of an existing dimension. Reliability/performance is an entirely missing dimension. The framework measures 8 categories of "what is this product?" and zero categories of "does this product work?"

### Secondary blind spot: sustainability / viability

The batch analysis itself identifies this: "The framework has no check for long-term viability. Vexl (grant-funded) and PodNews (no visible revenue model) score 95% on economic alignment because they charge nothing."

"Charges nothing and has no revenue" is not economic alignment. It is pre-economic. A product with no business model is a hobby project or a grant-dependent experiment. The framework rewards the absence of a business model the same way it rewards a well-aligned business model. This is a category error.

A product that charges nothing, has no revenue, depends on grants, and could disappear when the grant runs out is not more economically aligned than a product that charges $5/month and sustains itself. The first product's alignment is accidental -- it has not yet faced the pressure to monetize. The second product's alignment is proven -- it sustains itself through value exchange.

**Fix**: Add a "sustainability signal" modifier to Cat 8. Products with no revenue and no stated business model get capped at 75% on Cat 8 (honest but unproven), not 95-100% (perfect alignment). The 100% anchor should require demonstrated sustainability -- the product has been self-sustaining for >1 year through its stated model, not just "it's free and has no ads."

---

## Summary of Recommendations

| Priority | Action | Impact |
|----------|--------|--------|
| 1 | Kill or merge check 3.2 (Physical Obviousness) | Removes the framework's least useful check |
| 2 | Add pre-community N/A condition to check 1.2 | Fixes the newness penalty bug |
| 3 | Shift 5% weight from Cat 6 to Cat 5 (Scheme A) | Reduces sovereignty rank-determination from 0.991 to ~0.95 |
| 4 | Split check 2.2 into "guides action" + "shows authorship" | Sharpens the weakest Care-dimension check |
| 5 | Add maturity modifier to check 4.1 | Fixes the AllTrails = PodNews equivalence |
| 6 | Cap Cat 8 at 75% for products with no revenue model | Fixes the sustainability blind spot |
| 7 | Split check 7.3 into AI transparency + human authorship | Fixes conceptual confusion |
| 8 | Add reliability/performance check to Cat 4 or new Cat | Fills the biggest measurement gap |
| 9 | Increase Cat 8 to 15% (Scheme C minimum) | Reflects Cat 8's demonstrated discrimination |
| 10 | Document A-grade requirements explicitly | Sets expectations without changing boundary |

### What I would NOT change

- **The geometric mean.** It is the framework's best feature. Harsh, anti-gaming, philosophically sound.
- **The 5% floor.** Correct balance between punishment and collapse prevention.
- **The conditional check system.** Elegant solution to product-type variance.
- **Cat 5's 10 checks.** Best-designed category in the framework. Wide range, clear anchors, actionable signals.
- **The axioms.** They are good axioms. The weights just need to match them better.

---

## Appendix: Data Tables Used

### Rank comparison (Cat 6 vs Overall vs Cat 5 vs Cat 8)

| Product | Overall Rank | Cat 6 Rank | Cat 5 Rank | Cat 8 Rank |
|---------|-------------|-----------|-----------|-----------|
| Sparrow | 1 | 1 | 3 | 2 |
| Boris | 2 | 1 | 2 | 3 |
| Sloppypasta | 3 | 3 | 1 | 1 |
| Vexl | 4 | 4 | 5 | 2 |
| PodNews | 5 | 6 | 4 | 4 |
| Claude Code | 6 | 6 | 6 | 7 |
| Fountain | 7 | 5 | 8 | 7 |
| Polymarket | 8 | 5 | 9 | 9 |
| AllTrails | 9 | 10 | 10 | 10 |
| Coinbase | 10 | 9 | 9 | 9 |
| Twitter/X | 11 | 11 | 11 | 11 |

Cat 6 rank matches overall rank for 9/11 products (only AllTrails/Coinbase swap).
Cat 5 rank matches for 5/11 products.
Cat 8 rank matches for 4/11 products.

### Effective influence (weight * stdev)

| Cat | Weight | StDev | Effective Influence | Share of Total |
|-----|--------|-------|-------------------|---------------|
| 6 | 20% | 26.8 | 5.36 | 28.6% |
| 5 | 15% | 23.5 | 3.53 | 18.8% |
| 8 | 10% | 26.8 | 2.68 | 14.3% |
| 7 | 15% | 17.2 | 2.58 | 13.7% |
| 1 | 10% | 15.3 | 1.53 | 8.2% |
| 4 | 10% | 10.7 | 1.07 | 5.7% |
| 2 | 10% | 9.5 | 0.95 | 5.1% |
| 3 | 10% | 8.7 | 0.87 | 4.6% |
| **Total** | | | **18.77** | |

Cat 6 commands 28.6% of effective influence despite 20% nominal weight.
Cats 2+3+4 combined (30% nominal weight) have 15.4% effective influence.
The "Care" dimension (40% nominal) has 22.6% effective influence.
The "Structure" dimension (35% nominal) has 47.4% effective influence.
