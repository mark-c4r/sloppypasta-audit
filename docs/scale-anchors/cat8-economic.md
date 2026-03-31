> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as deep calibration reference.
# Cat 8: Economic Alignment — Scale Anchors

Reference: check-inventory.md

> **Scoring floor**: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension.

---

## 8.1 Native Money vs Ads

**What it measures**: Whether the product's revenue comes from direct value exchange (users pay for value) or from monetizing user attention (ads, data selling, sponsored content).

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Pure attention extraction. The product is free because YOU are the product. Revenue comes entirely from advertising and data monetization. The product's incentives are perfectly misaligned with yours — they profit by keeping you looking at ads, not by delivering value. Every design decision optimizes for ad impressions, not user outcomes. | Ad-supported social media (Facebook, Instagram), free mobile games funded by ads, "free" tools that sell behavioral data, Google Search (ad-funded) |
| 25% | Primarily ad-funded with some direct revenue. The product makes most of its money from ads but has a paid tier or supplementary revenue. The paid tier exists but the economic gravity is ad revenue. Product decisions still optimize for engagement (ad impressions) over user value. The paid tier is insurance, not the business. | YouTube (ad-primary, Premium exists), Spotify (ad-supported free tier drives most usage), Twitter/X (ad revenue primary, subscription secondary) |
| 50% | Mixed revenue — genuine split between ads and user payments. Both revenue streams are meaningful. The product balances user experience against ad revenue without fully committing to either. Paid users get an ad-free experience (indicating the team knows ads degrade the product). A transitional state — better than pure ads, not yet clean. | Hulu (ad + subscription tiers), news sites with subscriptions and ads, freemium products with ad-supported free tier |
| 75% | Revenue primarily from user payments. Subscriptions, one-time purchases, or transaction fees fund the product. Ads may exist marginally (affiliate links, sponsorship in a newsletter) but don't drive product decisions. The product's economic incentives are mostly aligned with user satisfaction. | Most paid SaaS (Basecamp, Linear, Notion paid), paid mobile apps, subscription newsletters with occasional sponsors |
| 100% | Pure value exchange. Revenue comes exclusively from users paying for the service — sats, subscriptions, one-time purchases, donations. Zero ads, zero data monetization, zero sponsored content. The product makes money when it delivers value and loses money when it doesn't. Incentives are perfectly aligned: what's good for the user is good for the business. | PPQ.AI (pay per query), Signal (donations), Pinboard (one-time payment), Bitcoin mining software, Lightning-native services |

**Scoring notes**: Identify all revenue streams. Check for: display ads, sponsored content, affiliate links, data sharing partnerships ("partners" in privacy policy), ad tracking scripts. The distinction between 75% and 100% is whether any non-user revenue exists. Disclosed affiliate links in content are minor (75% ceiling). Hidden ad tracking in a paid product is a significant penalty (drops to 50% or below). Products with no revenue yet (pre-monetization) score based on their stated model — if no model is stated, assume the worst.

---

## 8.2 Pay Per Service

**What it measures**: Whether pricing reflects actual value delivered — pay for what you use versus subscription inertia billing that profits from forgotten accounts.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Predatory subscription mechanics. Free trial auto-converts to paid with minimal warning. Cancellation is deliberately difficult (see 5.7). The product profits primarily from people who forgot they're subscribed. Pricing is designed around inertia — the ideal customer is one who pays indefinitely and never uses the product. Annual billing pushed aggressively to lock in revenue regardless of usage. | Gym memberships (profit model = people who don't show up), free-trial-to-subscription traps, products with dark-pattern auto-renewal |
| 25% | Subscription model disconnected from value. Monthly/annual subscription regardless of usage level. A user who logs in once per month pays the same as one who uses it daily. No usage-based component. No pause option. The subscription runs whether you're getting value or not. Pricing optimizes for recurring revenue, not value delivery. | Netflix (pays whether you watch or not), SaaS products with flat monthly fees and no usage component, subscriptions without pause or usage adjustment |
| 50% | Honest subscription with tiered value. Subscription pricing with tiers that roughly map to usage or value received. Lower tiers for lower usage. The pricing isn't perfect but the tiers acknowledge that different users get different value. Easy to downgrade tiers. Annual pricing is a discount, not a lock-in. | Standard tiered SaaS (Notion, Figma with per-seat pricing), products with starter/pro/team tiers mapping to real usage differences |
| 75% | Bus-ticket subscription. Like a monthly transit pass — you pay for a month of access and it's priced such that moderate use justifies the cost. Clear value for the billing period. Easy to cancel, no penalty, no lock-in. The subscription feels like buying a month of service, not signing a contract. Pause available when not needed. | Basecamp (flat rate, clear value), well-priced monthly subscriptions with easy cancel and pause, products where the monthly cost is obviously justified by monthly use |
| 100% | Pay per service — you pay for what you use, nothing more. Per-query, per-transaction, per-minute, or one-time purchase. Zero payment when the product delivers zero value. No subscription to forget about, no recurring charge to justify. The pricing model structurally prevents the product from profiting when it's not serving you. | PPQ.AI (pay per query — ideal model), AWS Lambda (pay per invocation), Pinboard (one-time payment), Lightning micropayments, one-time purchase software |

**Scoring notes**: Check: what happens if you stop using the product for 3 months but stay subscribed? If the answer is "you pay $X/month for nothing" — that's the inertia billing problem. Score based on how closely pricing tracks value delivery. The ideal: $0 when you don't use it, fair price when you do. Bus-ticket subscriptions (75%) are honest because moderate usage obviously justifies the cost. Netflix-style subscriptions (25%) profit from the gap between subscription cost and actual viewing. Pay-per-use (100%) eliminates the gap entirely.

---

## 8.3 No Coerced Upsells

**What it measures**: Absence of guilt trips, feature hostage-taking, and artificial limitations designed to pressure users into upgrading to a higher tier.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Upselling through hostage-taking. Core features deliberately broken or removed at lower tiers to create artificial pain. "Want to export your data? Upgrade to Pro." "Need more than 3 projects? Enterprise tier only." The free/lower tier is designed as a punishment that makes upgrading feel like relief. Features that cost nothing to provide are locked behind higher tiers solely to create pressure. | Products that lock data export behind paid tiers, "free" plans with 3-item limits on data that costs nothing to store, products where the free tier is deliberately degraded each quarter to drive conversions |
| 25% | Aggressive upselling at friction points. Upgrade prompts appear when you hit a limit, when you try a locked feature, and on a schedule regardless of behavior. Confirmshaming on decline ("No thanks, I'll stick with my limited plan"). Features are locked with prominent "Upgrade" badges creating visual clutter. The product makes you feel bad for not paying more. | Products with "Upgrade" badges on every locked feature, SaaS with upgrade modals at every limit, products with guilt-trip decline copy on upsell prompts |
| 50% | Moderate upselling that's occasionally annoying. Upgrade prompts at natural moments (hitting a limit) without emotional manipulation. Locked features are visible but not shoved in your face. The occasional "Did you know Pro can do X?" prompt. Upselling exists but isn't the dominant experience. Decline is neutral and easy. | Standard freemium products with tasteful upgrade prompts, SaaS with "Upgrade" links in menus without aggressive promotion |
| 75% | Non-coercive upselling. Paid features are discoverable but never pushed. Limits are communicated matter-of-factly ("You've used 8 of 10 projects"). No emotional manipulation, no guilt trips, no artificial urgency. Upgrade is a calm option, not a nagging demand. The product earns upgrades through demonstrated value, not manufactured frustration. | Basecamp (no upsells — one tier), Linear (clear pricing, no pressure), products where the upgrade path is visible but quiet |
| 100% | Zero upselling or purely value-driven upgrade path. Either one tier exists (nothing to upsell to) or the upgrade is so obviously valuable that no selling is needed. No prompts, no badges, no "upgrade" buttons in the nav. If you upgrade, it's because you genuinely need more and the product made it easy to find — not because it made your current experience unpleasant. | PPQ.AI (pay per use, no tiers), Signal (free, no paid tier), one-price products, open source tools with optional paid hosting |

**Scoring notes**: Use the free/lower tier for a real task. Count upsell prompts encountered in a 30-minute session. Check: are locked features shown with prominent "Upgrade" badges? Does hitting a limit trigger an emotional prompt? Is the decline option neutral or shaming? Evaluate whether limits feel like product decisions (genuinely different value tiers) or artificial pressure (features that cost nothing to provide locked behind higher tiers). The test: would a reasonable person feel manipulated?

---
