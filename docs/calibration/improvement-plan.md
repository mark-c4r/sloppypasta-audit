# Sloppypasta Audit: Consolidated Improvement Plan

**Date**: 2026-03-31
**Reviewer**: Opus 4.6 (adversarial consolidation)
**Inputs**: batch-analysis.md (11 products), codex-weight-review.md (adversarial review), synthesis.md (framework document), creator corrections on framing

---

## Framing Correction

The codex-weight-review created a false dichotomy: "user-felt quality" vs. "structural sovereignty." The creator has corrected this. The framework measures ALL forms of user disrespect at different timescales:

- **Visible laziness** (felt immediately): sloppy writing, broken pages, AI slop
- **Felt disrespect** (noticed during use): dark patterns, nag screens, urgency tricks
- **Hidden betrayal** (never perceived): surveillance tracking, data brokering, advertising pixels
- **Delayed traps** (discovered too late): can't withdraw funds, can't export, can't leave

These are not competing philosophies. They are four timescales of the same thing. A Coinbase user who cannot withdraw is not less disrespected because they did not feel it on day one. An AllTrails user being tracked by advertising pixels is not less spied on because the trails load fast. The framework catches all four. The question is whether the measurement instruments are sharp enough at each timescale.

With that corrected, the actual problem becomes clearer: **the Care-dimension checks are too blunt, not the weights too high.** The effective influence imbalance (Care: 40% nominal, 22.6% effective) is a measurement quality problem, not a philosophical one.

---

## Phase 0: Quick Wins (ship in one session, no re-calibration needed)

These changes improve framework quality without touching scoring mechanics. They can be applied, committed, and used immediately. Each is independent.

### 0.1 Kill Check 3.2 (Physical Obviousness)

**Status**: Unanimous recommendation across both analyses.

Check 3.2 has a 15-point range (55-70%) and 5.6 stdev. It is the worst check in the framework. Every professional product meets the baseline of "controls look interactive" because UI patterns converged a decade ago. The scale anchors describe failure modes from 2008 Flash microsites.

**Action**: Remove 3.2. Merge its best discriminating concept ("affordance quality beyond convention") into 3.4 (Self-Evident UI) as a sub-dimension in the scale anchors. Cat 3 drops from 6 checks to 5. This marginally increases each remaining check's influence within Cat 3, which is the correct direction since the remaining checks are all sharper.

**Risk**: None. This check adds no information. Removing it slightly improves Cat 3's discrimination.

### 0.2 Pre-Community Handling for Check 1.2 (Social Authenticity)

**Status**: Clear bug, not a design choice.

The framework's own audit scores 15% on 1.2, producing a Cat 1 of 30% and costing 9.5 points of geomean drag. A brand-new product with zero community scores near the floor because it has no followers. The check conflates "manufactured social proof" (the bad thing it should catch) with "no social proof yet" (a neutral state).

**Action**: Add an N/A condition: if a product is less than 6 months old AND has no social media presence, 1.2 scores N/A. The check exists to detect manufactured engagement, not to punish products that have not yet had time to build an audience.

**Why not "score 50%" instead**: The N/A approach is cleaner. A 50% score implies "neutral evidence" -- but for a brand-new product, there IS no evidence. That is what N/A means. Scoring 50% would also inject a mid-range score into the geometric mean that dilutes Cat 1's signal. N/A excludes the check from the mean entirely, which lets 1.1 (LLM Smell Markers) carry Cat 1 alone for new products. That is a better measurement.

**Caution**: Cat 1 has only 2 checks. If 1.2 goes N/A, Cat 1 is a single check. The conditional exclusion rule says "if conditional exclusions drop a category below 3 active checks, exclude the entire category." Two checks is already below 3, so this rule may need revisiting. One option: exempt Cat 1 from the 3-check minimum since it is designed as a 2-check sentinel. Another: accept that for pre-community products, Cat 1 is essentially "LLM smell markers" -- which is actually the more important check.

### 0.3 Audit Scope Section in Every Report

**Status**: No controversy. Pure improvement to report quality.

The skill output template should add a mandatory "Audit Scope" section immediately after metadata. It declares:

- **Directly assessed**: web surface, source code, documentation, API
- **Assessed via proxy**: mobile app (Play Store listing, Apple privacy label, reviews), privacy (third-party scanner results)
- **Not assessed**: native app UX, in-app flows, real-time behavior, performance
- **Limitations encountered**: 403 blocks, JS-rendered content, login walls, rate limiting

This is especially important for mobile-first products (Vexl, Fountain, AllTrails) where the web audit systematically underscores the actual product.

**Action**: Update the skill's output template. One-time change.

### 0.4 Grade Boundary Enforcement in Skill Output

**Status**: 3 of 9 agents in the batch assigned wrong grades. This is a template bug.

**Action**: The skill output must compute the grade programmatically from the score, not have the agent assign it by judgment. Add the grade boundary table (A: 85-100, B: 70-84, C: 55-69, D: 40-54, F: 0-39) to the top of every report and enforce it in the scoring section of the skill.

### 0.5 Actionable Findings in Reports

**Status**: Quality improvement. Reports should list specific evidence, not just scores.

When a check scores below 70%, the report should include at least one specific finding. Not "marketing claims exceed reality" but "landing page says 'decentralized' but all traffic routes through company servers at api.vexl.it." Not "broken pages detected" but "fountain.fm/settings returns 404, /discover loads empty state with no error message."

**Action**: Add a "Key Findings" sub-section to each category in the skill output template. Scored checks below 70% must cite specific evidence.

---

## Phase 1: Check Sharpening (requires anchor rewrites, then re-score a subset for validation)

These changes modify how existing checks measure. They require rewriting scale anchors and then re-scoring 3-5 products to validate the new anchors produce better discrimination. They do not change the check count, weights, or scoring math.

### 1.1 Split Check 2.2 (Copy Is Interface Design) into Two Checks

**The problem**: 2.2 bundles four dimensions -- functional guidance, specificity, writing quality, and authorship signal -- into one score. Claude Code at 80% and PodNews at 75% score high for completely different reasons. Coinbase and Polymarket both score 55% for opposite failures.

**Split into**:
- **2.2a "Copy guides action"**: Does the text tell you what to do, where you are, what happened? Measures interface function. Error messages that explain what went wrong and what to try. Empty states that suggest next steps. Labels that disambiguate.
- **2.2b "Copy shows authorship"**: Could this copy only exist in this product? Does it have a voice? Measures craft and care. Generic "Welcome to [Product]" vs. specific "Your wallet is empty. Start by receiving some sats."

Cat 2 goes from 3 checks to 4. This widens Cat 2's effective range and gives the Care dimension more discriminating power -- which is the core problem the framework needs to solve.

**Validation**: Re-score 2.2a and 2.2b for Sparrow, Boris, Claude Code, Coinbase, and Twitter. If the split produces a wider range than the original (target: 35+ point range per sub-check vs. current 25), keep it. If both sub-checks compress to the same 25-point range, the split added complexity without benefit -- revert.

### 1.2 Add Maturity Modifier to Check 4.1 (Shipped Ready)

**The problem**: AllTrails at 65% (60M users, $2.7B valuation, billing bugs) and PodNews at 65% (pre-launch, rough edges) score identically. These are radically different failure modes. Billing bugs in a product serving 60M paying users indicate organizational dysfunction. Rough edges in a pre-launch tool indicate "not ready yet."

**Fix**: Add maturity-adjusted anchors to 4.1. Not a separate modifier -- bake it into the anchor descriptions:

- **For mature products (1M+ users or $10M+ revenue)**: the 50% anchor becomes "core flow works but secondary flows have issues." Billing bugs in a paid product with millions of users should not score above 50%.
- **For early products (pre-launch or <10K users)**: the 50% anchor remains "core flow mostly works with workarounds needed." Rough edges are expected and normal.
- **The 80%+ anchor is the same for both**: "everything works, edge cases handled, errors are informative." Maturity is not an excuse for the best products.

This is not a "curve" or a "handicap." It is acknowledging that expectations scale with resources. A solo developer with rough edges and a $2.7B company with billing bugs are failing at different things.

### 1.3 Split Check 7.3 (AI Disclosed and Labeled) into Two Signals

**The problem**: Products that do not use AI (Sparrow 90%) score near-identically to products that ARE AI and disclose it (Claude Code 80%). The check rewards the absence of AI the same as responsible disclosure of AI.

**Split into**:
- **7.3a "AI content transparency"**: If AI is used anywhere (content generation, recommendations, summarization), is it disclosed? This is a conduct/honesty check. Products that do not use AI score N/A, not high.
- **7.3b "Human authorship signal"**: Does the content show evidence of human creation? Voice, specificity, references to personal experience, opinions that a model would hedge. This overlaps with Cat 1 but measures a different angle -- Cat 1 catches machine tells, this rewards human tells.

**Why split instead of just fixing the anchors**: The fundamental issue is that "does not use AI" and "uses AI transparently" are not on the same scale. They are answers to different questions. 7.3a asks "are you honest about your tools?" 7.3b asks "did a person write this?" Trying to measure both with one score produces a number that means different things for different products.

Cat 7 goes from 5 checks to 6. This is acceptable because Cat 7 already has good discrimination (stdev 17.2) and the split addresses a conceptual confusion, not a range problem.

### 1.4 Sharpen Remaining Cat 3 Anchors

After removing 3.2 (Phase 0), the remaining Cat 3 checks (3.1, 3.3, 3.4, 3.5, 3.6) still have compressed ranges. The batch analysis notes that 5 of the 10 narrowest-variance checks are in Cat 3.

**Action**: Rewrite scale anchors for 3.1, 3.3, 3.4, and 3.6 with sharper differentiation at the top and bottom. The current anchors describe a 50-70% zone that every professional product lands in. The rewritten anchors should push the floor lower (what does truly bad design look like?) and the ceiling higher (what does design-as-communication look like, beyond "follows conventions"?).

This is the hardest work in Phase 1. Good anchor rewriting requires looking at specific products and asking "what separates Sparrow's UTXO interface from Twitter's standard feed?" The answer is not "one is prettier" -- it is "one uses visual design to communicate its data model." Anchors that capture that distinction will produce wider ranges.

**Deferred question**: Should 3.5 (Modal-Free Experience) remain in Cat 3? It has a 70-point range (25-95%) -- dramatically wider than all other Cat 3 checks. It discriminates like a Cat 5 check because it measures behavior (hostile modals), not design skill. Moving it to Cat 5 would sharpen Cat 3's focus on design craft and give Cat 5 an 11th check that fits naturally. But this adds complexity for marginal benefit. Park this for now.

### 1.5 Tracking Quality Taxonomy in 5.5 Anchors

**Status**: Both analyses recommend this. No controversy.

Add explicit tier names to the 5.5 sub-check anchors:

| Tier | Examples | Score Range |
|------|----------|-------------|
| Infrastructure | CDN, push notifications (FCM), error monitoring (Sentry) | 70-90% |
| First-party analytics | Self-hosted Plausible/Umami, custom analytics | 75-90% |
| Privacy-respecting third-party | Fathom, hosted Plausible | 50-65% |
| Standard surveillance | Google Analytics, Mixpanel, Amplitude | 20-35% |
| Advertising/profiling | Meta Pixel, TikTok Pixel, AppLovin | 5-20% |
| Data brokering | Selling/sharing user data with data brokers | 5% |

This does not change what 5.5 measures. It makes the measurement vocabulary explicit so agents score consistently. Vexl's FCM (infrastructure) and Polymarket's TikTok Pixel (advertising surveillance) should not both be described as "third-party services" in anchor text.

### 1.6 Rugpull Severity Spectrum in 6.1 Anchors

**Status**: Recommended by batch analysis. Adds real discrimination.

Add severity context to the 6.1 scale anchors. Not a separate multiplier (that adds math complexity) -- bake it into the anchor descriptions:

- **Convenience-loss rugpull** (content service disappears, you lose access to an aggregator): assessed at face value. PodNews, AllTrails.
- **Data-loss rugpull** (your contributed content, history, or settings are gone): anchor drops by ~10 points. Twitter, Boris (if self-hosted data were at risk).
- **Financial-loss rugpull** (your money is at risk): anchor drops by ~20 points. Coinbase, Fountain (custodial wallet). This is the most severe form because the harm is concrete and potentially irreversible.
- **Identity-loss rugpull** (your social identity, reputation, or credential history is gone): anchor drops by ~15 points. Twitter, any platform with non-portable identity.

These are not additive modifiers. They are anchor guidance. The agent reads the product, identifies which kind of rugpull is at stake, and uses the appropriate anchor range.

---

## Phase 2: Structural Changes (require deliberate decision + full re-calibration)

These changes modify the framework's scoring mechanics. They should only be applied after Phase 0 and Phase 1 are complete and validated, because the sharper checks from Phase 1 will change the effective influence calculations and may make some Phase 2 changes unnecessary.

### 2.1 Weight Shift: Cat 5 (Conduct) 15% to 20%, Cat 6 (Sovereignty) 20% to 15%

**Recommendation**: Adopt Scheme A from the codex review, but ONLY after Phase 1 check sharpening is complete.

**Rationale with corrected framing**: This is not "felt quality vs. structural sovereignty." Both Cat 5 and Cat 6 measure structural respect for users. The shift says: "how the product behaves toward you right now" (Conduct: dark patterns, tracking, nag screens, attention harvesting) is at least as important as "how the product's architecture could theoretically betray you" (Sovereignty: open source, self-hostable, non-custodial).

Conduct catches the broadest range of disrespect. It includes visible (nag screens), felt (dark patterns), hidden (surveillance tracking), and some delayed (cancel maze) forms. Sovereignty catches a specific structural subset: can the architecture betray you? Both matter. But Conduct at 15% while Sovereignty at 20% implies architecture matters more than behavior. The corrected framing suggests they should be closer to equal, with Conduct slightly ahead because it covers more timescales.

**Why wait for Phase 1**: After check sharpening, the effective influence numbers will change. If sharper Care-dimension checks widen their ranges, the Care dimension's effective influence rises from 22.6% toward its nominal 40% WITHOUT any weight changes. The weight shift may become unnecessary or need to be smaller. Measure first, then decide.

**Effect on the batch** (from the sensitivity table): Fountain moves D to C (54% to 55.3%). No other grade flips. The shift is conservative -- it does not break the framework's ranking. Cat 6 remains the single largest category at 15%, just no longer dramatically dominant.

### 2.2 Cat 8 Sustainability Sub-Check

**The problem**: Products with no revenue and no business model score 95-100% on Cat 8 because they charge nothing. "Charges nothing and has no revenue" is not economic alignment -- it is pre-economic. Vexl (grant-funded) and PodNews (no visible revenue) both score 95%. A product that has not yet faced monetization pressure has not demonstrated alignment; it has merely not been tested.

**Fix**: Add a sustainability signal as a 4th check in Cat 8:

- **8.4 "Sustainable by design"**: Does the product have a visible, honest path to self-sustenance?
  - 80-100%: Self-sustaining through stated model for 1+ year (V4V, subscriptions, one-time purchase). Demonstrated, not theoretical.
  - 60-79%: Revenue model stated and plausible but not yet proven. Early-stage products with honest pricing.
  - 40-59%: Grant-funded or VC-funded with no stated transition plan. Sustainable today, uncertain tomorrow.
  - 20-39%: No visible revenue and no stated plan. Hobby project or pre-monetization.
  - 5-19%: Burns cash with no path forward. Or: revenue model exists but is misaligned (ad-funded while claiming alignment).

Cat 8 goes from 3 checks to 4. This gives Cat 8 more structural integrity (3 checks is thin for a category) and caps the scores of pre-economic products without punishing them harshly. A grant-funded product at 50% on 8.4 and 95% on 8.1-8.3 would get a Cat 8 of ~78% instead of 95%. That is a more honest measurement.

**This is the most debatable change in the plan.** Counter-argument: a product that charges nothing and runs no ads IS economically aligned with users right now. Punishing it for not having a business model is punishing it for a hypothetical future misalignment. The framework measures what IS, not what MIGHT BE.

Response to the counter-argument: the framework already measures hypotheticals in Cat 6. "Can they rugpull you?" is about what MIGHT happen, not what IS happening. AllTrails has not rugpulled anyone -- it just architecturally could. If the framework penalizes hypothetical architectural betrayal (Cat 6), it should also penalize hypothetical economic unsustainability (Cat 8). Consistency demands it.

### 2.3 Cat 8 Weight Increase to 15%

**Status**: Conditional on 2.2 (sustainability sub-check).

Cat 8 has stdev 26.8 (tied with Cat 6 for highest) and range 75. At 10% weight, its signal is muffled. The codex review's Scheme B proposed 22% (too aggressive). Scheme C proposed 15% (reasonable).

**If 2.2 is adopted**: Cat 8 with 4 checks at 15% weight is structurally sound. Each check carries 3.75% of the total score -- reasonable influence.

**If 2.2 is not adopted**: Cat 8 with 3 checks at 15% weight gives each check 5% of total score -- high single-check influence. Proceed with caution.

**Where does the 5% come from?** If the Cat 5/6 shift (2.1) is also adopted, the distribution becomes:

| Cat | Current | After 2.1 | After 2.1 + 2.3 |
|-----|---------|-----------|-----------------|
| 5 Conduct | 15% | 20% | 20% |
| 6 Sovereignty | 20% | 15% | 15% |
| 7 Honesty | 15% | 15% | 12% |
| 8 Economic | 10% | 10% | 13% |

Or, pulling from Cat 7 alone:

| Cat | Current | After all |
|-----|---------|-----------|
| 5 | 15% | 20% |
| 6 | 20% | 15% |
| 7 | 15% | 12% |
| 8 | 10% | 13% |

Dimensions: Care 40%, Structure 35%, Signal 25% (unchanged). The shift is entirely within Structure and Signal.

**Recommendation**: If adopting both 2.1 and 2.3, pull 5% from Cat 6 (to Cat 5) and 3% from Cat 7 (to Cat 8). This keeps Signal at 25% and Structure at 35%. The 2% remainder goes to Cat 8 from... nowhere clean. The math does not work without either changing dimension totals or making awkward splits. Consider: Cat 5 to 18%, Cat 6 to 15%, Cat 7 to 14%, Cat 8 to 13%. That is Care 40%, Structure 33%, Signal 27%. Close enough. But this is getting into the weeds of weight arithmetic that should be settled AFTER Phase 1 data is in.

**Decision**: Defer the exact weight numbers until after Phase 1 check sharpening produces new discrimination data. Then set weights based on actual effective influence, not pre-improvement estimates.

---

## Phase 3: Framework Extensions (optional, high effort, defer unless evidence demands)

These are ideas that surfaced during analysis but do not clearly pass the cost/benefit bar for a solo developer. They are recorded here so they are not lost, but they should not be prioritized over Phase 0-2.

### 3.1 Reliability/Performance Gap

The codex review identifies this as the "biggest blind spot": the framework measures what a product IS but not what it DOES (uptime, speed, error rate). A Bitcoin wallet that crashes 20% of the time is a bad product regardless of its architecture.

**Why defer**: Reliability and performance are extremely hard to measure from an external audit. You cannot determine uptime from a single visit. You cannot determine crash rate without sustained use. Page load time is measurable but varies by network, device, and caching. The audit already struggles with mobile-first products; adding performance metrics that require sustained observation would break the "external audit" constraint entirely.

**If pursued**: The most practical approach is a narrow "first-visit performance" check in Cat 4: does the product load within a reasonable time on a standard connection? Does it show content quickly or spin? This is observable from a single visit and discriminates between "loads in 200ms" and "loads in 20 seconds." But the range may be narrow (most professional products load in 1-3 seconds) and the check would discriminate weakly -- same problem as the Care-dimension checks today.

**Recommendation**: Note the gap in the framework's Limitations section. Do not add a check until there is evidence that performance discrimination is both measurable and meaningful across the target product set.

### 3.2 Audit Depth Tiers

Formalize Essential (2 min) / Recommended (7 min) / Thorough (12 min) tiers with different check subsets and fetch budgets.

**Why defer**: The current "Recommended" tier is working well enough. The main benefit is for mobile-first products, where "Thorough" would include device testing. But device testing requires the auditor to have the device, install the app, and test flows -- this is beyond what a Claude Code skill can automate. The tiers are useful documentation but low-priority for implementation.

**If pursued**: Define which checks are in each tier. Essential = Cats 1-2 + 6.7 + 5.5 (rough-grade estimate in 2 minutes). Recommended = all checks on accessible surfaces. Thorough = Recommended + device-level verification. Add a `--depth` flag to the skill.

### 3.3 Import-Without-Export as Named Dark Pattern

Add "import without matching export" to the 5.10 (No Dark Patterns) scale anchors and 6.2 (Exit Cost) anchors.

**Why this is Phase 3 not Phase 1**: It is a single line in two anchor documents. It could be done in Phase 1. But it is not a check-level change -- it is an anchor detail that will naturally be captured when 5.10 and 6.2 anchors are reviewed as part of Phase 1 work. No need to call it out separately.

### 3.4 "Claim vs. Reality" Modifier

Boris claims "no trackers" on its landing page but uses Fathom analytics. The framework should penalize products where marketing claims contradict technical implementation.

**Why defer**: This is already partially captured by 7.2 (No Marketing Exaggeration). The fix is sharper anchors for 7.2, not a new modifier. Add "marketing privacy claims vs. actual tracking behavior" as a specific dimension in 7.2's scale anchors during Phase 1 anchor work.

---

## Ideas Challenged and Killed

### Scheme B (Discrimination-Weighted Distribution)

The codex review proposed weighting categories proportional to their demonstrated discrimination (stdev). This would put Cat 8 at 22% and demote Cat 2 and Cat 3 to 7% each.

**Kill reason**: Discrimination power is sample-dependent. With 11 products (7 Bitcoin/sovereignty-adjacent), the stdev numbers reflect this sample's ideology, not universal product variance. Cat 2 and Cat 3 might discriminate strongly in a sample including AI-generated landing pages, WordPress templates, and hand-crafted indie tools. Additionally, 22% weight on 3 checks gives each check 7.3% of total score -- dangerously high single-check influence. And letting data drive weights removes the framework's philosophical foundation. The weights should express what the framework values, validated (not determined) by calibration data.

### Scheme C (Fixed Care Floor)

The codex review proposed Cat 6 to 17%, Cat 7 to 13%, Cat 8 to 15% as a "conservative" option.

**Kill reason**: Scheme C changes weights without changing what those weights amplify. Moving 3% from Cat 6 to Cat 8 changes the rank correlation from 0.991 to approximately 0.98. Cat 6 still determines the ranking. If you change weights, change them enough to matter (Scheme A) or do not change them at all. Half-measures consume decision-making energy for no measurable benefit.

### Path 1 (Lower A Boundary to 82%)

The codex review proposed lowering the A threshold so Sparrow could reach it.

**Kill reason**: The A grade should be genuinely hard to reach. "Rarely achieved" is a meaningful signal. The fact that no product in an 11-product batch reached A is a sampling artifact (sovereignty-strong, design-weak products dominate the sample), not a framework bug. Sparrow at 84% is 1 point away. Better Cat 3 anchors (Phase 1.4) may change Sparrow's design score in either direction. Fix the measurement instruments, not the grading scale.

### Path 3 (Cap Geomean Drag)

The codex review proposed limiting how much any single category can drag the overall score.

**Kill reason**: This fundamentally changes the framework's identity. The geometric mean's harshness IS the framework. "You cannot compensate for a structural failure with nice fonts" is the core thesis. Capping the drag softens this thesis for products that happen to have one terrible category. Those products SHOULD feel the drag. That is the point.

### Adding a 9th Category for Reliability/Performance

**Kill reason** (for now): Cannot be measured reliably from external audit. Would add audit time without proportional signal. The target product set (professional web/mobile products) mostly loads quickly. The check would produce the same compression problem as Cat 3 checks today. Note the gap in Limitations and revisit if calibration data from more diverse products reveals performance as a real discriminator.

---

## Principles for Check Design (Resisting Goodhart's Law)

The creator raised a fundamental question: how should checks measure the "real thing" instead of gameable proxies? This is the framework's version of Goodhart's Law -- when a measure becomes a target, it ceases to be a good measure.

### The Problem Illustrated

Check 4.4 (Iteration Visible) rewards the existence of changelogs. Coinbase scores 65% (engineering blog exists, app store notes say "bug fixes") while PodNews scores 55% (active development, invisible to users). The nominal metric (changelog exists) rewards Coinbase. The real metric (can a user tell the product is evolving?) might reverse the scores. "Bug fixes and improvements" communicates nothing.

This pattern repeats across the framework. Check 5.6 (RSS or Equivalent) rewards "RSS feed exists" -- but a dead RSS feed that has not been updated in 6 months is not the same as an active one. Check 6.7 (Source Code Availability) rewards "source is on GitHub" -- but an abandoned repo with no commits in 2 years is not the same as actively maintained open source.

### Five Principles for Real Measurement

**1. Measure the user's experience, not the artifact's existence.**

Bad: "Does a changelog exist?" (presence test)
Good: "Can a user who returns after 3 months tell the product has improved?" (experience test)

The presence test is gameable (create an empty changelog page). The experience test requires the artifact to actually serve its purpose. An agent evaluating the experience test must read the changelog and judge whether it communicates change to a user -- not just whether the URL resolves.

**2. Anchor to observable behavior, not declared intent.**

Bad: "Does the privacy policy say they respect user data?" (declaration test)
Good: "What do network requests reveal about data collection?" (behavior test)

Boris declares "no trackers" but runs Fathom. The behavior test catches the contradiction. The declaration test rewards the marketing copy. When anchors describe what to look for, they should describe observable behavior (network requests, actual data flows, testable claims) rather than policy documents.

This does not mean ignoring declarations. A product that declares good intentions and acts on them should score higher than one that acts well without declaring. But a product that declares good intentions and violates them should score lower than one that is honestly mediocre. Hypocrisy is worse than consistency.

**3. Score the floor, not the ceiling.**

Bad: "What is the best experience a user could have?" (optimistic path)
Good: "What is the worst experience a user is likely to have?" (realistic path)

The geometric mean already embodies this principle at the category level. Extend it to check-level assessment. When an agent encounters a product that is excellent for power users but confusing for new users, the check should score closer to the new user's experience. The floor IS the product for most users, because most users are not power users.

This is especially important for 4.1 (Shipped Ready). A product where the "core flow" works but onboarding is broken, or billing fails, or error messages are opaque, should be scored on the broken path, not the working one.

**4. Prefer binary-adjacent checks over spectrum checks where possible.**

The framework's best discriminators (6.3 Identity Sovereignty, 6.4 Protocol vs Platform, 5.4 No Attention Harvesting) tend to be binary-adjacent: the product either does the thing or does not. Products cluster at the extremes with a gap in the middle. This is because these checks measure architectural decisions that are inherently binary -- you either require government ID or you do not; you either have infinite scroll or you do not.

Spectrum checks (3.1 Information Density, 2.2 Copy Is Interface Design) produce compressed ranges because the "middle" is wide and most products land there. This is not necessarily bad -- some dimensions genuinely have a wide middle -- but check designers should ask: "Is there a sharper binary underneath this spectrum?" If yes, split the check around the binary. If no, the compressed range may be real and the check is measuring a dimension where products genuinely converge.

Example: 3.2 (Physical Obviousness) was a spectrum check on a dimension where every product converges. Killing it is correct. 2.2 was a spectrum check bundling multiple binaries (does copy guide? does copy show authorship?). Splitting it is correct.

**5. Beware the survivorship anchor.**

The framework calibrated against products that exist and are used. It did not calibrate against products that were abandoned, never launched, or are actively scamming users. The scale anchors reflect the range of professional products, not the range of all products. This creates a floor effect: even "bad" products in the calibration set (Twitter at 31%) are professionally built by large teams.

When writing anchors, explicitly describe what a 10% score looks like -- not just what a 50% or 80% score looks like. Many current anchors describe the 50-80% range in detail but leave the floor vague ("actively hostile" or "no effort visible"). Concrete floor examples prevent the range from compressing upward. What does 10% on Information Density actually look like? What does 15% on Copy Is Interface Design look like? If the anchor cannot describe a concrete product at that score, the check may have a structural floor effect that no anchor rewrite can fix.

### The OKR Counter-Metric Trap

The creator specifically asked about avoiding OKR-style counter-metrics. This is wise. Adding a "counter-check" for every check doubles complexity for marginal benefit. The better approach is already embedded in the framework:

**The geometric mean IS the counter-metric.** A product that games one check (inflate your changelog to boost 4.4) cannot compensate because 45 other checks across 7 other categories provide the counter-signal. The breadth of 46 checks with geometric mean scoring makes gaming any individual check futile. This is the framework's most underappreciated design feature.

The risk is not that individual checks get gamed. The risk is that entire categories get gamed. A product could theoretically optimize for Cat 6 (open source everything, self-host everything, use Lightning) while being terrible at Cat 5 (harvest attention, use dark patterns, spam notifications). The geometric mean punishes this because Cat 5 drags independently of Cat 6. The framework is already resistant to this pattern.

The remaining vulnerability is: a product could be "technically compliant" on every check while being soulless. Open source, no tracking, no dark patterns, Lightning payments, honest pricing -- but the product is a joyless, confusing, ugly experience that nobody wants to use. The Care dimension (40% weight) is supposed to catch this, but with its current compressed ranges, it does not bite hard enough.

**This is why Phase 1 (check sharpening) is the priority, not weight changes.** Sharper Care-dimension checks are the real counter-metric to architectural gaming.

---

## Execution Sequence

```
Phase 0 (one session, < 2 hours):
  0.1  Kill check 3.2
  0.2  Add pre-community N/A to 1.2
  0.3  Add audit scope section to skill template
  0.4  Enforce grade boundaries in skill
  0.5  Add actionable findings requirement

Phase 1 (2-3 sessions, requires validation re-scoring):
  1.1  Split 2.2 into 2.2a + 2.2b → rewrite anchors → re-score 5 products
  1.2  Add maturity context to 4.1 anchors → re-score AllTrails + PodNews
  1.3  Split 7.3 into 7.3a + 7.3b → rewrite anchors → re-score 5 products
  1.4  Sharpen Cat 3 anchors (3.1, 3.3, 3.4, 3.6) → re-score 3 products
  1.5  Add tracking taxonomy to 5.5 anchors
  1.6  Add rugpull severity to 6.1 anchors

  → After Phase 1: re-run discrimination analysis on re-scored products
  → Measure new effective influence percentages
  → Decide if Phase 2 weight changes are still needed

Phase 2 (1 session, requires full re-calibration):
  2.1  Weight shift: Cat 5 to 20%, Cat 6 to 15% (if still needed after Phase 1)
  2.2  Add 8.4 sustainability sub-check (if evidence supports)
  2.3  Cat 8 weight increase (if 2.2 adopted and effective influence data supports)

  → After Phase 2: re-score 5 products, validate no unintended grade flips

Phase 3 (defer indefinitely unless evidence demands):
  3.1  Reliability/performance — note in Limitations, do not add check
  3.2  Audit depth tiers — document, do not implement
  3.3  Import-without-export — add to anchor text during Phase 1 work
  3.4  Claim-vs-reality — add to 7.2 anchors during Phase 1 work
```

---

## What NOT to Change

Confirmed by all analyses. These are the framework's load-bearing walls:

- **Geometric mean scoring**: The framework's best feature. Harsh, anti-gaming, philosophically sound.
- **The 5% floor**: Correct balance between punishment and collapse prevention.
- **Conditional check system**: Elegant solution to product-type variance.
- **The 85% A-grade boundary**: Should be genuinely rare. Fix measurement, not the scale.
- **46-check breadth**: Anti-gaming protection. Do not add checks for the sake of it. (Phase 1 splits add 3 checks to reach 48 -- this is acceptable because each split addresses a documented measurement confusion, not a coverage gap.)
- **The axioms in synthesis.md**: Philosophically sound. The weights need to serve them better; the axioms themselves are correct.
- **Cat 5's 10-check design**: Best-designed category. Wide range, clear anchors, actionable signals.
- **The framework's opinionated stance on sovereignty**: This is not a general-purpose quality framework. It was built for people who care about sovereignty. That opinion is a feature.
