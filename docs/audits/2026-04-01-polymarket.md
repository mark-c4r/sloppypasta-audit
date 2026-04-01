# Sloppypasta Audit: Polymarket

**Date**: 2026-04-01
**URL**: https://polymarket.com
**Type**: Web app + mobile apps (iOS, Android)
**Audit Mode**: External (V1, single-agent)
**Conditions**: `[if:content]`, `[if:identity]`, `[if:payments]`, `[if:mobile]`
**Applicable Checks**: 45 of 46 (1 N/A: 6.12 relay/node independence)

---

## Overall: 46% -- Grade D

Polymarket is the world's largest prediction market by volume, backed by a $2B investment from ICE (NYSE parent) and valued near $20B. It demonstrates competent product execution in its core trading interface -- the market card layout is information-dense, the landing page avoids typical marketing bloat, and the developer documentation with SDKs in three languages shows genuine builder infrastructure. Where Polymarket fails the Sloppypasta framework is in the categories it weights most heavily: sovereignty, privacy, honesty, and product conduct. The platform runs Google Analytics and TikTok Pixel surveillance-grade tracking, DNT is ignored, the US version requires government ID, and the international version -- while more permissive -- still operates as a centralized platform that can freeze accounts and modify terms unilaterally. The NYT investigation documenting hundreds of false and misleading social media posts, combined with the UMA governance attack that resolved a $7M market incorrectly without refunds, reveals a platform whose honesty claims ("source of truth", "News 2.0") diverge substantially from observable behavior. The economic model -- recently expanding taker fees across most categories -- creates a house-takes-a-cut dynamic that aligns Polymarket's incentives with trading volume rather than prediction accuracy. A well-built product on hostile infrastructure.

---

## Category Breakdown

### Cat 1: Slop Detection -- 54% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 1.1 | LLM smell markers | 65% | Landing page copy is lean and data-forward -- market cards display probabilities and volumes without marketing language; no banned words detected in the primary UI; the "World's Largest Prediction Market" tagline is factual, not aspirational; however, social feed content (NewsWire partnership) has generated hundreds of misleading posts per the NYT investigation, and blog content could not be fetched for direct analysis. |
| 1.2 | Social authenticity | 45% | 3.8M Twitter/X followers with an official data partnership with X; engagement is real but inflated by the platform's controversy-driven visibility; the CNN investigation found coordinated wallets making suspiciously timed bets (six wallets profiting $1.2M on Iran strikes); Israeli Air Force members interrogated for insider trading on the platform; community is genuinely large but includes manipulation signals that undermine authenticity. |

---

### Cat 2: Writing & Thinking -- 57% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 2.1 | Economy of words | 60% | The trading interface is admirably minimal -- market cards show outcome pairs, probabilities, and volume without filler; category navigation (Politics, Sports, Crypto) is clean; the footer regulatory disclaimer is necessarily wordy but appropriately placed; documentation reads naturally with technical precision; marketing copy avoids superlatives on the main product pages. |
| 2.2 | Copy is interface design | 55% | Market descriptions are functional and guide trading decisions; probability displays and outcome labels are clear; however, the US version's waitlist experience frustrated users ("shouldn't have been released until it was ready"); Android users reported confusion about geographic restrictions after downloading; error handling in edge cases (market resolution disputes) relies on external UMA documentation rather than in-product guidance. |
| 2.3 | No throat-clearing | 55% | `[if:content]` Market descriptions get to the point -- outcome conditions are stated directly without preamble; documentation opens with actionable content ("Build on the world's largest prediction market"); however, the blog could not be directly analyzed (ECONNREFUSED), and social feed content has been documented as spreading misinformation rather than providing clean analysis, suggesting the content arm prioritizes engagement over substance. |

---

### Cat 3: Design & Interface -- 56% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 3.1 | Information density | 65% | The market listing page is genuinely dense -- multiple market cards per viewport with probability percentages, volume metrics, and time metadata; category filters with horizontal scrolling are space-efficient; the card-based layout communicates grouping through visual proximity; whitespace is functional rather than decorative; competitive with financial trading interfaces in density. |
| 3.2 | Physical obviousness | 60% | Primary trading actions (buy Yes/No) are visually clear; market cards are obviously interactive; category navigation is standard tab pattern; however, the relationship between the international and US versions is confusing -- users report downloading the app only to discover they can't use it in their region; the proxy wallet system and USDC mechanics require understanding that the interface doesn't fully explain. |
| 3.3 | Design system consistency | 60% | Consistent card layout across market categories; teal brand accent is applied uniformly; dark/light mode toggle present; typography hierarchy works within the trading interface; spacing is consistent across market cards; however, the gap between the polished trading UI and the rougher edges (blog unreachable, social feeds spreading misinformation, US waitlist) suggests inconsistency across the broader product surface. |
| 3.4 | Self-evident UI | 55% | Core trading flow (browse markets, buy shares) is discoverable through visual exploration; probability display is intuitive; however, advanced mechanics (UMA resolution, proxy wallets, USDC bridging) require documentation; new users with no crypto experience face a learning cliff beyond the initial market browsing; the product is self-evident for viewing but not for participating. |
| 3.5 | Modal-free experience | 50% | Fresh visit shows market content without login walls for browsing; however, cookie consent implementation exists and the product uses tracking that would require consent banners in EU jurisdictions; the US version gates behind waitlist/invite; mobile app reportedly prompts for phone number for waitlist; these gates, while partially functional, interrupt the path to core value. |
| 3.6 | Accessibility basics | 50% | Standard web application patterns suggest baseline semantic HTML; mobile app on Android requests 0 permissions which is positive; however, no specific accessibility effort is documented or visible; the financial data display (probabilities, charts) requires visual acuity; no evidence of screen reader optimization, custom focus states, or ARIA landmarks beyond framework defaults. |

---

### Cat 4: Product Craft -- 53% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 4.1 | Shipped ready | 55% | The international trading platform works -- markets load, trades execute, resolutions happen; the core loop functions for experienced crypto users; however, the US launch was delayed and remains invite-only with a waitlist, Android users gave it 3.0 stars citing an app that "shouldn't have been released," and the UMA governance attack that resolved a $7M market incorrectly without refunds demonstrates that edge cases in the resolution system are genuinely broken. |
| 4.2 | Orphaned features | 50% | Core trading features work; SDKs in Python, TypeScript, and Rust are actively maintained (recent commits March 2026); 96 GitHub repositories show active development; however, the US version is effectively an orphaned launch (promised but not delivered at scale), the social feed experiment generates misinformation, and market resolution via UMA has proven unreliable in adversarial conditions. |
| 4.3 | Show me the code | 45% | SDKs and API clients are open source under MIT license; documentation is built with Mintlify and reads professionally; however, the core platform code is not open source -- only SDKs and tools are published; the TikTok Pixel and Google Analytics scripts in production indicate tracking infrastructure that a review-conscious codebase would question; the polymarket-cli has 2K+ stars suggesting genuine developer adoption. |
| 4.4 | Iteration visible | 65% | Official changelog at docs.polymarket.com documents changes with specific technical detail (fee percentages, API endpoint parameters, breaking changes flagged); SDK repos show recent commits; however, changelog entries are developer-focused (API changes, fee structures) rather than user-facing feature documentation; no public blog post explaining development philosophy or decisions was accessible during audit (blog returned ECONNREFUSED). |

---

### Cat 5: Product Conduct -- 43% (weight: 15%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 5.1 | No access gates | 55% | Market browsing is available without an account -- probabilities, volumes, and outcomes visible to unauthenticated visitors; trading requires account creation (reasonable for a financial product); the international version accepts email or crypto wallet; the US version gates behind full KYC; scored as reasonable gating for a financial product with genuine free browsing of core informational value. |
| 5.2 | No manufactured urgency | 60% | "Ending Soon" and "Trending" categories exist but reflect real market dynamics -- prediction markets have genuine time constraints (events happen on specific dates); no countdown timers on fabricated scarcity; no "only X shares left" messaging; the urgency in prediction markets is inherent to the product category rather than manufactured; however, the platform's social feeds amplify time-sensitive events in ways that create trading pressure. |
| 5.3 | No nag/re-engagement | 45% | Mobile app with push notification infrastructure exists; email marketing for the waitlist and platform updates; the X partnership creates a social media presence that constantly surfaces Polymarket data as engagement content; no evidence of "we miss you" campaigns, but the X integration means Polymarket content appears in users' feeds through the platform partnership rather than user opt-in. |
| 5.4 | No attention harvesting | 45% | Markets have natural endpoints (they resolve), which is positive; however, the market listing page is an infinite scroll of betting opportunities; "Trending" and "Popular" categories encourage browsing beyond intent; the X partnership and social feed integration extend Polymarket's attention surface beyond the app itself; gamification is inherent in the trading mechanic (profit/loss as score). |
| 5.5 | Privacy & tracking composite | 23% | See sub-check breakdown below. |
| 5.6 | RSS or equivalent | 30% | `[if:content]` No RSS feed for market data or blog content; API exists for programmatic access to market data (documented with SDKs), but API access is a developer tool, not a content syndication mechanism; third-party tools like Adjacent News provide RSS feeds of Polymarket-derived content, but the platform itself does not offer RSS; market data is accessible via API but content consumption requires the Polymarket interface. |
| 5.7 | Cancel/leave in one click | 40% | No specific account deletion documentation was found in search results; withdrawal of funds is documented and fee-free (USDC withdrawal with only gas fees); however, for the US version with full KYC, the identity data submitted cannot be "withdrawn"; the international version's proxy wallet system means positions must be closed before leaving; no evidence of a one-click account deletion flow. |
| 5.8 | No double-dipping | 50% | The platform recently expanded taker fees across most trading categories (March 2026) while also running surveillance-grade analytics (GA + TikTok Pixel); fees are the primary revenue model (not ads), but the tracking infrastructure suggests user data is also a value stream; the X data partnership explicitly combines Polymarket data with X's advertising infrastructure; not traditional double-dipping (no display ads) but the tracking layer alongside fees creates a dual extraction model. |
| 5.9 | No product coercion | 45% | The mobile web experience reportedly pushes app downloads; US users who downloaded the app found it didn't work in their region; the platform operates differently across jurisdictions without clear pre-download disclosure; the X partnership creates a platform-specific distribution channel; however, the core web product works across browsers without browser-specific degradation. |
| 5.10 | No dark patterns | 50% | No confirmshaming detected in the trading interface; pricing (fee structure) is documented though the recent fee expansion was controversial; no pre-checked boxes or trick questions observed; however, the fee implementation uses "dynamic probability-based pricing" which obscures the actual cost (fees vary by market probability), and the UMA resolution system's refusal to refund a governance-attacked market resolution could be characterized as a roach motel for funds. |

#### 5.5 Privacy & Tracking Sub-Checks

| Sub | Check | Score | Justification |
|-----|-------|-------|---------------|
| 5.5a | Cookie count | 30% | Session and persistent cookies are used; third-party cookies for analytics confirmed in privacy policy; the combination of GA and TikTok Pixel implies multiple tracking cookies from different domains; scored at 30% for heavy cookie use including third-party tracking cookies from ad networks. |
| 5.5b | Third-party tracker count | 20% | Google Analytics and TikTok Pixel confirmed in page source; TikTok Pixel is an advertising tracker that builds cross-site profiles; GA is standard surveillance analytics; the combination of two major tracking platforms (Google + TikTok) with different data collection purposes places this in the heavy tracking range. |
| 5.5c | Analytics philosophy | 25% | Google Analytics (surveillance-grade, user sessions tracked with identifiers) plus TikTok Pixel (advertising tracker, cross-site profiling) constitutes a standard surveillance analytics stack; data flows to both Google's and TikTok's ecosystems for cross-site profile building; maps to the 25% anchor. |
| 5.5d | Cookie consent quality | 25% | Cookie consent mechanism exists but implementation details could not be fully verified; the presence of surveillance-grade tracking (GA + TikTok) that fires on page load suggests pre-consent tracking; standard implementation that likely uses accept-prominent design given the industry norm. |
| 5.5e | DNT respect | 5% | No evidence that Polymarket honors DNT headers; tracking behavior appears identical regardless of DNT setting; GA and TikTok Pixel are not configured to respect DNT by default; the platform's privacy policy does not mention DNT respect; maps to the floor score. |
| 5.5f | Minimal permissions | 40% | `[if:mobile]` Android app reportedly requests 0 permissions, which is positive; however, uses 23 libraries; iOS app exists but specific permission details were not fully verified; the low permission count is better than average for a financial app; scored conservatively. |
| 5.5g | Telemetry opt-in | 30% | `[if:mobile]` No evidence of opt-in telemetry controls in the mobile app; the web platform's analytics (GA + TikTok) suggest telemetry defaults to ON; no documented opt-out toggle for analytics collection; scored at 30% for likely default-ON with unclear opt-out. |
| 5.5h | No background data | 40% | `[if:mobile]` No specific reports of excessive background data collection; the app's 0-permission Android footprint suggests limited background capability; however, push notification infrastructure exists for market updates; scored conservatively as functional background activity with limited tracking evidence. |

---

### Cat 6: Sovereignty & Privacy -- 39% (weight: 20%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 6.1 | Rugpull resistance | 30% | A single company (Adventure One QSS Inc. / QCX LLC) controls the platform; history of unilateral changes includes expanding taker fees across categories, pulling a nuclear detonation market after backlash, and refusing refunds on a governance-attacked resolution; terms include broad modification clauses; the ICE investment creates institutional backing but also institutional control; the UMA oracle was centralized to a whitelist after the governance attack, reducing community control. |
| 6.2 | Exit cost zero | 45% | USDC positions can be withdrawn to external wallets with no platform fee (only gas); however, open positions must be sold before withdrawal; trading history and market participation data is platform-held; the proxy wallet system means on-chain data exists but is tied to Polymarket's smart contract infrastructure; KYC data (US version) cannot be "exported" or deleted; functional exit for funds but not for identity data. |
| 6.3 | Identity sovereignty | 50% | International version accepts email, Google account, or crypto wallet -- email maps to 50% per the scale anchor; crypto wallet connection provides pseudonymous access (higher sovereignty); US version requires government ID (5%); scoring the international version as the primary product since it serves the majority of users; the blended experience centers on email-based identity. |
| 6.4 | Protocol vs platform | 25% | Polymarket is a platform with a restricted API; the CLOB API enables third-party trading bots and data access, but the platform controls market creation, resolution, and terms; if Polymarket disappears, user positions and markets disappear with it (despite on-chain settlement, the market logic is platform-controlled); the UMA oracle centralization (whitelist) further concentrates resolution authority; API access exists but the platform sets all the rules. |
| 6.5 | Self-hostable or auditable | 40% | SDKs and API clients are open source (MIT); core platform code is proprietary; smart contracts on Polygon are publicly verifiable on-chain; however, the trading engine, market creation logic, and resolution infrastructure are closed source; you can audit the smart contracts and build API clients but cannot run your own Polymarket instance; source-viewable for contracts, closed for the platform. |
| 6.6 | Privacy-preserving payment | 50% | Accepts 22 cryptocurrency tokens including Bitcoin (on-chain) across 13 chains; credit card via MoonPay also available; on-chain crypto is pseudonymous but publicly traceable on the blockchain; no Lightning Network support found; the crypto deposit option provides moderate payment privacy but on-chain transactions are permanently recorded; maps to the 50% anchor for on-chain crypto acceptance. |
| 6.7 | Source code availability | 50% | 96 repositories on GitHub, primarily SDKs, API clients, and tools under MIT license; polymarket-cli has 2K+ stars; however, the core platform (trading engine, market creation, resolution, frontend) is proprietary; the open source components are developer tools for interacting with the platform, not the platform itself; maps to source-viewable/open-core rather than fully open source. |
| 6.8 | Provenance traceable | 25% | `[if:content]` Market outcomes show attributed creator and resolution sources; however, the NYT investigation found hundreds of false/misleading posts in Polymarket's social feeds with no provenance verification; market descriptions have timestamps but no cryptographic signing; the UMA resolution system was demonstrated to be manipulable by whale token holders, undermining the integrity of market outcomes as "truth." |
| 6.9 | Distribution independence | 25% | `[if:mobile]` Available on both App Store and Google Play; no F-Droid presence; no direct APK download documented; the web app provides browser-based access as a fallback; distributed through standard app store gatekeepers with web fallback; maps to the 25% anchor for multiple stores without sideloading. |
| 6.10 | No Google Play Services | 50% | `[if:mobile]` The Android app requests 0 permissions which suggests minimal Play Services dependency; however, uses 23 libraries (some may include Google dependencies); no specific testing on de-Googled phones documented; scored at 50% for moderate likely dependency with some workaround potential via the web interface. |
| 6.11 | Key management sovereignty | 50% | `[if:identity]` International version: a 1-of-1 multisig proxy wallet is deployed on Polygon, controlled by the user's EOA (MetaMask or MagicLink); the user's keys remain in their wallet (MetaMask) and control the proxy; however, the proxy wallet system adds platform infrastructure between the user and their funds; MagicLink users have less sovereignty than MetaMask users; maps to custodial-with-export (user controls EOA but proxy wallet is Polymarket infrastructure). |
| 6.13 | Custodial vs non-custodial | 50% | `[if:payments]` Smart contract settlement means Polymarket doesn't directly hold user funds in a traditional custodial model; the proxy wallet is user-controlled via EOA; however, the platform can modify smart contract parameters, whitelist UMA proposers, and change fee structures affecting user funds; the governance attack incident showed that market resolution (which determines fund distribution) is vulnerable to manipulation and the platform refused refunds; architecturally non-custodial but operationally the platform controls the rules governing fund distribution. |

---

### Cat 7: Honesty & Transparency -- 43% (weight: 15%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 7.1 | Business model visible | 50% | Fee structure is documented (taker fees vary by probability, geopolitical markets fee-free); the recent fee expansion was announced in the changelog; however, the fee model is complex ("dynamic probability-based pricing") and not prominently displayed for casual users; the $2B ICE investment and $20B valuation suggest the business model extends beyond trading fees but this isn't explained to users; you can find how they make money by looking at the docs, but they don't proactively tell you. |
| 7.2 | No marketing exaggeration | 35% | "The World's Largest Prediction Market" is factually verifiable; however, the platform positions itself as "News 2.0" and a "source of truth" while the NYT documented hundreds of false and misleading social media posts; the social feed experiment has been characterized as a "misinformation machine" by multiple outlets; Jeff Bezos publicly denied a Polymarket claim about him; the marketing claims about truth and accuracy diverge significantly from the documented reality of the platform's content output. |
| 7.3 | AI disclosed and labeled | 40% | The platform uses AI-generated market summaries and curated news articles per community engagement documentation; Grok integration via X partnership generates AI content alongside market data; however, the boundary between AI-generated summaries and human-created market descriptions is not clearly labeled at the point of encounter; the social feeds that spread misinformation may include AI-generated content without labeling; AI use is acknowledged at the platform level but not at the content level. |
| 7.4 | No degraded free experience | 50% | Market browsing (probabilities, volumes, outcomes) is freely accessible without an account; the core informational value -- seeing what prediction markets think about world events -- is available without payment; however, trading (the core action) requires an account and funds; the US version is invite-only, making the experience literally inaccessible for most US users; the free tier is genuine for information consumption but the product's primary value (trading) is gated. |
| 7.5 | Dialogue, not broadcast | 40% | `[if:content]` GitHub repositories accept issues and PRs on the SDKs; help center exists at help.polymarket.com; however, the UMA governance attack was acknowledged but no refunds were issued despite community outcry; the response to the NYT misinformation investigation was a generic spokesperson statement about "investing in moderation tools"; the platform broadcasts market data through X partnership but community input on market rules, resolution disputes, and content moderation appears performative rather than substantive. |

---

### Cat 8: Economic Alignment -- 41% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 8.1 | Native money vs ads | 45% | Primary revenue is trading fees (taker fees), not advertising; however, the TikTok Pixel indicates advertising infrastructure (tracking conversions from TikTok ads, which means Polymarket is buying ads and tracking user behavior for ad optimization); the X data partnership creates a mutual data-sharing arrangement with an ad-funded platform; no display ads in the product, but the tracking infrastructure serves advertising objectives; mixed -- fees are the revenue but advertising is the growth engine. |
| 8.2 | Pay per service | 35% | Taker fees are per-trade, which structurally aligns with pay-per-service; however, the "dynamic probability-based pricing" model means fees are opaque and variable (peaking at 1.56% at 50% probability, tapering toward 0% at certainty); the fee structure was recently expanded across almost all categories; a user who doesn't trade pays nothing, which is positive; but the variable fee model obscures the actual cost of each trade, functioning more like a casino take than transparent per-service pricing. |
| 8.3 | No coerced upsells | 45% | No tiered subscription model -- all users access the same trading features; no "upgrade to Pro" prompts; however, the fee structure creates an indirect pressure: geopolitical markets are fee-free while other categories charge fees, which steers trading behavior toward fee-generating markets; the MoonPay integration for card deposits involves conversion spreads that aren't prominently disclosed; no traditional upselling but the fee architecture creates implicit steering. |

---

## Score Summary

| Cat | Name | Score | Weight | Checks |
|-----|------|-------|--------|--------|
| 1 | Slop Detection | 54% | 10% | 2/2 |
| 2 | Writing & Thinking | 57% | 10% | 3/3 |
| 3 | Design & Interface | 56% | 10% | 6/6 |
| 4 | Product Craft | 53% | 10% | 4/4 |
| 5 | Product Conduct | 43% | 15% | 10/10 |
| 6 | Sovereignty & Privacy | 39% | 20% | 12/13 |
| 7 | Honesty & Transparency | 43% | 15% | 5/5 |
| 8 | Economic Alignment | 41% | 10% | 3/3 |
| **Overall** | | **46%** | | **Grade D** |

---

## Priority Improvements

### 1. Remove Surveillance Analytics

**Check**: 5.5b Third-party trackers (current: 20%), 5.5c Analytics philosophy (current: 25%)
**Observed**: Google Analytics and TikTok Pixel fire on page load, creating a surveillance analytics stack that feeds data to two of the world's largest advertising platforms. For a financial product handling real money, this is a trust violation. TikTok Pixel in particular is an advertising tracker that builds cross-site profiles of Polymarket users.
**Target**: Replace GA + TikTok Pixel with self-hosted Plausible or Umami. This would raise 5.5b to 75%, 5.5c to 75%, and the 5.5 composite from 23% to approximately 45%, lifting Cat 5 by roughly 5 points and the overall score by approximately 1 point.
**Impact**: Beyond the score improvement, removing advertising trackers from a financial platform is a basic trust requirement.

### 2. Resolve the "Source of Truth" Claim vs. Misinformation Reality

**Check**: 7.2 No marketing exaggeration (current: 35%)
**Observed**: Polymarket positions itself as "News 2.0" and a "source of truth" while the NYT documented hundreds of false and misleading posts in its social feeds, and Jeff Bezos publicly denied a claim the platform made about him. The gap between marketing claims and documented reality is the check's core concern.
**Target**: Either invest genuinely in content moderation to match the "source of truth" positioning, or stop making that claim. Honest marketing about what prediction markets actually are (aggregated speculation with known manipulation vulnerabilities) would score higher than aspirational claims that invite debunking.
**Impact**: Improving from 35% to 60% would raise Cat 7 by approximately 8 points, lifting the overall score by approximately 1-2 points.

### 3. Transparent Fee Structure

**Check**: 8.2 Pay per service (current: 35%)
**Observed**: "Dynamic probability-based pricing" means fees vary by market probability, peaking at 1.56% at 50% and tapering to 0% at certainty. This is a complex fee model that obscures the actual cost of trading. The recent expansion of fees across almost all categories (previously fee-free) was announced through the changelog but felt unilateral to users.
**Target**: Display the exact fee for each trade at the point of purchase. Show "This trade will cost you X in fees" before execution. Transparent per-trade fee display would move toward 50-60%.
**Impact**: Improving from 35% to 55% would raise Cat 8 by approximately 6 points, lifting the overall score by approximately 1 point.

### 4. Address Resolution System Reliability

**Check**: 4.1 Shipped ready (current: 55%), 6.1 Rugpull resistance (current: 30%)
**Observed**: The UMA governance attack that resolved a $7M market incorrectly without refunds demonstrated a fundamental failure in the resolution system. The subsequent centralization of UMA proposals to a whitelist reduced the attack surface but also reduced decentralization. Users who bet correctly by factual standards lost money because the resolution mechanism was manipulated.
**Target**: Publish a resolution guarantee or insurance mechanism. If a market is resolved through manipulation, affected users should have a documented recourse path. This would improve 4.1 toward 65% and 6.1 toward 40%.
**Impact**: Improving both checks would raise Cat 4 and Cat 6 by approximately 3-5 points each.

### 5. Account Deletion and Data Portability

**Check**: 5.7 Cancel/leave (current: 40%), 6.2 Exit cost (current: 45%)
**Observed**: No documented account deletion process was found. Fund withdrawal is documented and fee-free, but identity data (especially for US KYC users) has no documented deletion path. Trading history and market participation data is platform-held with no export mechanism beyond individual trade records.
**Target**: Implement self-service account deletion with data export in standard formats (CSV/JSON of trading history, portfolio snapshots). Document the process publicly. This would move 5.7 toward 60% and 6.2 toward 55%.
**Impact**: Improving both checks would raise Cat 5 and Cat 6 by approximately 2-3 points each.

---

## Methodology

This audit uses the Sloppypasta Framework V1 -- 46 checks across 8 weighted categories, scored on a 5-100% scale with a 5% floor. Category scores are geometric means of applicable checks. The overall score is a weighted geometric mean of category scores with weights: {1:0.10, 2:0.10, 3:0.10, 4:0.10, 5:0.15, 6:0.20, 7:0.15, 8:0.10}. Geometric means penalize low scores disproportionately -- a single 10% score drags harder than a single 90% helps.

**Note on data gathering**: Product information was gathered from the live landing page at polymarket.com, official documentation at docs.polymarket.com, help center at help.polymarket.com, GitHub organization (96 repositories), and extensive web research including NYT, CNN, Bloomberg, CoinDesk, and CJR investigations. The blog at blog.polymarket.com returned ECONNREFUSED during the audit. Privacy policy and Terms of Service pages rendered as navigation shells without substantive content via WebFetch, requiring reliance on web search results for policy details. Mobile app data was gathered from App Store and Google Play listings and reviews. The audit evaluates the international (primary) version unless otherwise noted, with US version differences called out where they materially affect scoring.

Source: polymarket.com | Framework: docs/scoring-reference.md
