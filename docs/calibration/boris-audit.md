# Sloppypasta Audit: Boris

**Date**: 2026-03-31
**URL**: https://read.withboris.com (landing: boris.bar intended, currently resolves via withboris.com)
**Type**: Web app (PWA-capable, Nostr-native reading/highlighting client)
**Audit Mode**: External (V1, single-agent)
**Conditions**: `[if:content]`, `[if:identity]`
**Applicable Checks**: 42 of 46 (5 conditional activated: 2.3, 5.6, 6.8, 6.11, 7.5; 4 N/A: 6.9, 6.10, 6.12, 6.13)

---

## Audit Scope

**Surfaces assessed**: read.withboris.com landing page (full source fetched); dergigi/boris-landing GitHub repo (Tailwind config inspected); dergigi/boris GitHub repo (CHANGELOG through v0.12.0, README, issues, ESLint config); Gigi's blog post on dergigi.com (zero banned-word density confirmed); Fathom analytics from v0.12.0 CHANGELOG; boris.bar (DNS NXDOMAIN).
**Surfaces via proxy**: App interior (three-pane layout, highlight panel, Explore page) from README, CHANGELOG, and landing page screenshots — app is fully JS-rendered. Empty-state behavior from README troubleshooting. NIP-46 remote signing from README.
**Surfaces not assessed**: Live app interior (JS-rendered, requires execution); actual cookie load; Fathom analytics runtime/DNT behavior; boris.bar canonical domain (NXDOMAIN); OG preview system; PWA installation flow.
**Limitations**: Full JS rendering means nearly all in-app UX scores (Cat 3, Cat 4) scored conservatively from README and CHANGELOG. Fathom confirmed via CHANGELOG but runtime behavior unverified. Primary domain boris.bar unreachable.

---

## Overall: 77% -- Grade B

Boris is a genuinely sovereign product that earns its score through architectural decisions rather than surface polish. Built on Nostr's open protocol with keypair-based identity, MIT-licensed source code, and a Value4Value economic model, it represents the kind of product the Sloppypasta framework was designed to reward. The writing across the landing page and README is clean, direct, and distinctly human -- notable given the product was entirely vibe-coded. Where Boris loses ground is in the craft categories: the landing page uses default Tailwind tokens with no customization, the app itself is a JS-rendered shell that gives scrapers nothing to work with, and the vibe-coded origins surface in code patterns that mix paradigms. These are honest rough edges on a v0.12.0 product, not design negligence. The sovereignty and economic alignment scores (92% and 93%) are among the strongest a product can achieve without being a bare protocol, while the design and craft scores (58% and 58%) reflect a builder who cares deeply about architecture and values but hasn't yet invested in visual refinement.

---

## Category Breakdown

### Cat 1: Slop Detection -- 74% (weight: 15%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 1.1 | LLM smell markers | 78% | Landing page and README text is clean of banned words; no em-dash clusters, no Bold Prefix lists, no symmetrical paragraphs; the line "Hello! I'm Boris. I like to read." is distinctly human; Gigi's building-boris blog post confirmed zero banned-word hits by WebFetch analysis. |
| 1.2 | Social authenticity | 70% | 10 GitHub stars is modest and genuine; Gigi's Nostr presence is authentic (active protocol contributor, author of 21 Lessons); no bot signals; engagement is small but real; community is nascent -- the Nostr reading ecosystem is young, so low numbers reflect reality, not fakery. |

---

### Cat 2: Writing & Thinking -- 74% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 2.1 | Economy of words | 72% | Landing page copy is lean -- "Boris does not and will never have ads, trackers, paywalls, subscriptions, or any other distractions" communicates a philosophy in one sentence; occasional padding in feature descriptions ("Whether you prefer to read on desktop, mobile, or tablet, Boris is there for you") but density is generally good. |
| 2.2 | Copy is interface design | 70% | README guides users through flows with clear steps ("Click Connect and approve with your usual Nostr signer"); FAQ answers real questions; empty-state handling in the app is uncertain from external observation -- "If something looks empty, try opening another article" in troubleshooting suggests the app doesn't handle empty states gracefully in the UI itself. |
| 2.3 | No throat-clearing | 80% | `[if:content]` Blog post opens with dialogue ("What could I demo next Friday?") -- no preamble, no landscape-setting; landing page hero opens with "Hello! I'm Boris. I like to read." -- gets to the point immediately; Gigi's writing consistently leads with the substance. |

---

### Cat 3: Design & Interface -- 58% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 3.1 | Information density | 55% | Landing page is a standard single-column marketing scroll with alternating text/image sections; feature sections use generous spacing that doesn't communicate grouping -- same padding between all features; the app's three-pane layout (bookmarks/article/highlights) is denser and more intentional, but the landing page is template-tier density. |
| 3.2 | Physical obviousness | 65% | The app's three-pane layout is conventional and immediately understandable; "Start Reading" CTA is clear; collapsible sidebars are standard reader patterns; the landing page navigation (Features, FAQ, Zaps) is straightforward; knocked down because the app is JS-rendered so non-JS visitors see nothing. |
| 3.3 | Design system consistency | 45% | Tailwind config has zero custom tokens (`theme: { extend: {} }`) -- pure defaults; landing page uses gray-800, orange-600, gradient accents; the alternating feature layout is a common template pattern (text-left/image-right, then reversed); dark mode support is implemented but the overall design reads as a Tailwind starter template with content swapped in. |
| 3.4 | Self-evident UI | 50% | README acknowledges "If something looks empty, try opening another article and coming back -- network data can arrive in bursts" which signals that empty/loading states are not fully designed; README says "Hover icons and counters to see what they do" -- hover-to-discover means affordances aren't self-evident; scored conservatively based on these admissions. |
| 3.5 | Modal-free experience | 90% | No newsletter popups, no forced signups, no cookie walls; the app connects to Nostr via a clean signer flow (user-initiated, not forced); no login wall on public content -- articles are viewable without connecting; no interstitials of any kind observed in the landing page source. |
| 3.6 | Accessibility basics | 50% | Landing page uses semantic headings (h1, h2, h3) with proper hierarchy; alt text on images ("Boris app screenshot showing purple text and orange highlights"); nav hamburger button has an SVG with `<title>Menu</title>`; however, nav button has `focus:outline-none` without a visible replacement -- this is the classic AI code tell from the slop-visual-markers reference; no ARIA landmarks observed beyond basic semantics. |

---

### Cat 4: Product Craft -- 58% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 4.1 | Shipped ready | 55% | Core reading flow works; the app is at v0.12.0 with known bugs (4 open issues including component consolidation); README troubleshooting section ("If something looks empty, try opening another article") acknowledges reliability gaps; Gigi himself says he hasn't entered "the last mile" of polishing; functional but visibly pre-1.0. |
| 4.2 | Orphaned features | 65% | Feature set is focused: reading, highlighting, bookmarks, explore; all listed features appear to be functional based on the changelog's active maintenance; no "coming soon" placeholders; 4 open issues are code quality (consolidation, refactoring) not broken features; some rough edges but no abandoned features. |
| 4.3 | Show me the code | 40% | Changelog reveals "Fathom analytics integration" was added in v0.12.0 -- analytics in a reading app marketed as having "no trackers" is a tension point; ESLint configured with strict rules (no-unused-vars as error, no-explicit-any as warn); but the product is entirely vibe-coded with zero hand-written code per Gigi's admission; mixed framework usage (applesauce SDK for Nostr, Vercel for hosting, Upstash Redis for OG previews); silent `.catch(() => {})` blocks were fixed in v0.12.0, meaning they existed in production previously. |
| 4.4 | Iteration visible | 80% | CHANGELOG follows Keep a Changelog format with Added/Changed/Fixed/Refactored sections; 2,500+ commits over 6 months; Gigi wrote a detailed public blog post about the development process; version numbers follow semver; the development story is public and honest, including admissions of mistakes and scope creep. |

---

### Cat 5: Product Conduct -- 84% (weight: 15%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 5.1 | No access gates | 90% | Articles are viewable without connecting a Nostr account; connecting adds personalization (your bookmarks, your highlights) but reading is ungated; no paywall, no forced signup; knocked from 100% only because the app is entirely JS-rendered -- without JavaScript, nothing loads at all. |
| 5.2 | No manufactured urgency | 90% | Zero countdown timers, zero scarcity signals; the "Pricing" section is crossed out and replaced with "Zaps" -- the pricing tiers are 0 sats / 2.1k sats / 69,420 sats, which are donation tiers with personality, not pressure tactics; "Hell yeah!" and "Let's gooo!" buttons are playful, not urgent. |
| 5.3 | No nag/re-engagement | 90% | No email collection, no push notifications, no "we miss you" campaigns; the app has no mechanism to contact users -- it connects to Nostr and renders locally; no notification system of any kind observed. |
| 5.4 | No attention harvesting | 85% | The reading experience has natural endpoints (you finish the article); bookmarks list is finite; highlight panel doesn't auto-load more content; the "Explore" page shows Nostr long-form content which could theoretically be infinite, but it's a separate tab, not injected into the reading flow; no streaks, no gamification. |
| 5.5 | Privacy & tracking composite | 61% | See sub-check breakdown below. |
| 5.6 | RSS or equivalent | 70% | `[if:content]` Boris itself doesn't publish an RSS feed, but it reads from the Nostr protocol which is itself an open syndication layer; content is addressable via naddr URIs; Gigi built Castr.me (Nostr-to-RSS translator) as a companion tool; the Nostr protocol serves the same purpose as RSS but through a different mechanism; not a traditional feed but the open protocol achieves the same goal. |
| 5.7 | Cancel/leave in one click | 85% | No account to cancel -- Boris connects to your Nostr identity via a signer; disconnecting is a single action; data lives on Nostr relays, not in Boris; there is nothing to delete because Boris stores nothing server-side; some local preferences in localStorage but clearing the browser handles that. |
| 5.8 | No double-dipping | 95% | Product is free and open-source; no ads, no data selling; the only monetization is voluntary zaps (Lightning tips); landing page explicitly states "Boris does not and will never have ads, trackers, paywalls, subscriptions, or any other distractions." |
| 5.9 | No product coercion | 90% | No "download our app" banners; works in any browser; PWA installation is mentioned in docs as optional ("If you install boris as a PWA...") but never pushed; no browser-specific messaging; no forced app-store redirect. |
| 5.10 | No dark patterns | 90% | Zero confirmshaming; "No thanks" equivalent buttons are neutral; pricing is transparent (free + optional zaps); no hidden costs; no trick questions; no pre-checked boxes; the "69,420 sats" tier is a Bitcoin community joke, not a dark pattern. |

#### 5.5 Privacy & Tracking Sub-Checks

| Sub | Check | Score | Justification |
|-----|-------|-------|---------------|
| 5.5a | Cookie count | 75% | Boris renders locally in the browser; no user accounts on the server side; likely minimal cookies (Vercel deployment may set a session cookie); no third-party advertising cookies; scored conservatively as could not verify cookie count directly. |
| 5.5b | Third-party tracker count | 50% | Fathom analytics was added in v0.12.0 per the CHANGELOG; Fathom is a hosted privacy-respecting analytics service but it is still a third-party tracker domain; no other trackers observed; Upstash Redis is used server-side for OG preview caching, not client-side tracking. |
| 5.5c | Analytics philosophy | 50% | Fathom is a hosted privacy-respecting analytics service (better than GA, worse than self-hosted Plausible); maps directly to the 50% anchor; tension with the "no trackers" marketing claim on the landing page. |
| 5.5d | Cookie consent quality | 90% | No cookie consent banner observed in the source; Fathom analytics is designed to not require consent banners (no personal data, no cookies by default); the product likely needs no consent mechanism. |
| 5.5e | DNT respect | 50% | Fathom claims to respect DNT but could not verify from external observation; scored at 50% as the analytics service is privacy-respecting but external verification of DNT behavior is not possible. |
| 5.5f | Minimal permissions | N/A | `[if:mobile]` -- Boris is a web app, not a native mobile app. |
| 5.5g | Telemetry opt-in | N/A | `[if:mobile]` -- Boris is a web app, not a native mobile app. |
| 5.5h | No background data | N/A | `[if:mobile]` -- Boris is a web app, not a native mobile app. |

---

### Cat 6: Sovereignty & Privacy -- 92% (weight: 20%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 6.1 | Rugpull resistance | 90% | Built on Nostr (open protocol) -- if Boris disappears, data persists on relays and can be accessed by any Nostr client; the app is MIT-licensed and forkable; however, the canonical instance runs on Vercel with Upstash Redis for OG previews, creating some centralization; protocol-level resistance is genuine but operational infrastructure has single points of failure. |
| 6.2 | Exit cost zero | 95% | Data lives on Nostr relays in standard event formats; highlights are NIP-84 events, bookmarks are standard Nostr bookmarks; no export needed because the data was never imported -- it lives on the protocol; any Nostr client can read Boris-created data; knocked from 100% because some local preferences in localStorage would be lost. |
| 6.3 | Identity sovereignty | 100% | Keypair-based identity via Nostr (nsec/npub); no email, no phone, no username; Boris connects via NIP-07 browser extension signing or external signer; "Boris doesn't ask for an email or create a new account -- it connects to your existing Nostr identity"; this is the gold standard per the scale anchor. |
| 6.4 | Protocol vs platform | 95% | Boris is a client for the Nostr protocol; multiple other clients exist (Damus, Primal, Amethyst); if Boris disappears, users switch clients; highlights use NIP-84 which other clients can read; slightly below 100% because NIP-85 (reading events) is Boris-proposed and not yet widely adopted, creating some Boris-specific data that other clients don't yet consume. |
| 6.5 | Self-hostable or auditable | 85% | Full source on GitHub under MIT license; TypeScript/Vite build -- `git clone && npm install && npm run dev` should work; however, the OG preview system depends on Vercel serverless functions and Upstash Redis, which adds self-hosting complexity beyond a simple clone; the core reading/highlighting functionality would work without these but social previews wouldn't. |
| 6.6 | Privacy-preserving payment | 90% | Zaps are Lightning-native payments; the pricing section links to a Nostr zapper; no credit card, no KYC; payment is pseudonymous through Lightning; slightly below 100% because zaps go through Nostr zap infrastructure which involves relay-mediated coordination, not raw bearer instruments like ecash. |
| 6.7 | Source code availability | 100% | Full source on GitHub under MIT license (permissive, not copyleft); actively maintained (last commit 2026-03-25, 2,500+ commits); 10 stargazers, 1 fork; open issues tracked publicly; this meets the highest anchor -- FOSS with active development and permissive license. |
| 6.8 | Provenance traceable | 85% | `[if:content]` Every highlight and annotation is a signed Nostr event tied to the author's keypair; content provenance is cryptographic by architecture; timestamps are protocol-level; a third party can verify who highlighted what using the author's npub; slightly below 100% because Boris renders web articles alongside Nostr-native content, and the web articles' provenance depends on the original source, not Boris. |
| 6.9 | Distribution independence | N/A | `[if:mobile]` -- Boris is a web app. PWA is optional. |
| 6.10 | No Google Play Services | N/A | `[if:mobile]` -- Boris is a web app. |
| 6.11 | Key management sovereignty | 90% | `[if:identity]` Boris uses NIP-07 browser extension signing (nos2x, Alby) -- keys never touch the app's servers; NIP-46 remote signing is supported; this is the gold standard per the scale anchor; knocked slightly from 100% because the extent of NIP-46 support could not be fully verified from external observation. |
| 6.12 | Relay/node independence | N/A | `[if:messaging/social]` -- Boris is a reading app, not a messaging/social platform. |
| 6.13 | Custodial vs non-custodial | N/A | `[if:payments]` -- Boris handles zaps (tipping) but is not a wallet or payment processor. |

---

### Cat 7: Honesty & Transparency -- 79% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 7.1 | Business model visible | 85% | The "Pricing" section is crossed out and replaced with "Zaps" -- immediately communicates that the product is free and funded by optional donations; "Boris is a labor of love and is developed by one guy" is transparent about the operation; V4V (Value4Value) model is explained in context; link to dergigi.com/support for additional ways to contribute. |
| 7.2 | No marketing exaggeration | 80% | Claims are grounded: "calm, fast, and focused reading experience" is accurate for a reader app; "free and open-source and always will be" is verifiable (MIT license on GitHub); no "revolutionary" or "AI-powered" language; the only stretch is "Boris does not and will never have ads, trackers, paywalls, subscriptions" while Fathom analytics was added in v0.12.0 -- Fathom is privacy-respecting but the "no trackers" claim creates tension. |
| 7.3 | AI disclosed and labeled | 70% | Gigi publicly disclosed that Boris was entirely vibe-coded (zero hand-written code) in a detailed blog post; however, this disclosure lives on dergigi.com, not on the Boris product itself or the landing page; a user who only visits read.withboris.com would not know the product was AI-generated; the blog post is honest but the product-level disclosure is absent. |
| 7.4 | No degraded free experience | 95% | There is only one tier -- free with all features; the zap tiers add "Show up as a supporter" and "Flames around your avatar" but do not remove any functionality; paying gets you cosmetic recognition and good feelings, not access; this is the V4V ideal. |
| 7.5 | Dialogue, not broadcast | 70% | `[if:content]` GitHub issues are open and active (4 open issues, PRs merged); Nostr itself enables replies; the landing page links to Nostr and GitHub for contact; however, there is no dedicated feedback mechanism, forum, or discussion space within the app itself; the "Help" link in the footer goes to a Nostr event, not a help page; dialogue exists through protocol-native channels but requires Nostr/GitHub fluency. |

---

### Cat 8: Economic Alignment -- 93% (weight: 10%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 8.1 | Native money vs ads | 95% | Revenue comes exclusively from voluntary Lightning zaps -- pure value exchange; zero ads, zero data monetization, zero sponsored content; the only revenue is sats sent by appreciative users; Fathom analytics does not monetize user data; knocked from 100% only because the project likely generates minimal revenue, which raises sustainability questions (though that's not what this check measures). |
| 8.2 | Pay per service | 90% | The V4V model means you pay what you want, when you want; 0 sats is explicitly an option with "All the features"; no subscription, no recurring charge, no inertia billing; the 2.1k sats suggested donation is a one-time zap, not a subscription; maps closely to the pay-per-service ideal though it's technically "pay what you want" rather than "pay per query." |
| 8.3 | No coerced upsells | 95% | The pricing section is deliberately playful -- tiers are "Free" / "Support Boris" / "Legend" with descriptions like "Fantastic numerology" and "Massive bragging rights" for the 69,420 sats tier; zero guilt, zero feature hostage-taking; the CTA buttons say "Hell yeah!" and "Let's gooo!" and "I love it." -- personality, not pressure; no upgrade nags anywhere in the app. |

---

## Score Summary

| Cat | Name | Score | Weight | Checks |
|-----|------|-------|--------|--------|
| 1 | Slop Detection | 74% | 15% | 2/2 |
| 2 | Writing & Thinking | 74% | 10% | 3/3 |
| 3 | Design & Interface | 58% | 10% | 6/6 |
| 4 | Product Craft | 58% | 10% | 4/4 |
| 5 | Product Conduct | 84% | 15% | 10/10 |
| 6 | Sovereignty & Privacy | 92% | 20% | 9/13 |
| 7 | Honesty & Transparency | 79% | 10% | 5/5 |
| 8 | Economic Alignment | 93% | 10% | 3/3 |
| **Overall** | | **77%** | | **Grade B** |

---

## Priority Improvements

### 1. Design System Customization

**Check**: 3.3 Design system consistency (current: 45%)
**Observed**: Tailwind config has zero custom tokens (`theme: { extend: {} }`) -- pure defaults. The landing page reads as a Tailwind starter template with content swapped in. No custom color palette, no custom spacing scale, no custom type hierarchy beyond Tailwind's defaults.
**Target**: At 75%, one type scale, one spacing system, and one color palette would be enforced across all pages, with the window resize test showing graceful degradation.
**Impact**: Improving from 45% to ~75% would raise Design & Interface by approximately 7 points, lifting the overall score by ~1 point.

### 2. Resolve the "No Trackers" Claim vs. Fathom Analytics

**Check**: 7.2 No marketing exaggeration (current: 80%) and 5.5b/5.5c (current: 50%/50%)
**Observed**: The landing page states "Boris does not and will never have ads, trackers, paywalls, subscriptions, or any other distractions." The v0.12.0 CHANGELOG adds "Fathom analytics integration." Fathom is privacy-respecting but is technically a third-party analytics service. The claim and the implementation are in tension.
**Target**: Either remove Fathom and switch to self-hosted Plausible/Umami (which would raise 5.5c to 75% and strengthen the marketing claim), or update the landing page copy to acknowledge the privacy-respecting analytics choice.
**Impact**: Switching to self-hosted analytics would raise the 5.5 composite from 61% to ~68%, improving Cat 5 by approximately 1 point and resolving the honesty tension.

### 3. Empty State and Error Handling

**Check**: 3.4 Self-evident UI (current: 50%) and 4.1 Shipped ready (current: 55%)
**Observed**: README troubleshooting says "If something looks empty, try opening another article and coming back -- network data can arrive in bursts." This indicates empty states are not designed. "Hover icons and counters to see what they do" means controls rely on hover discovery rather than visible affordances.
**Target**: At 75%, empty states would guide users toward their first action, and controls would be visually discoverable without hover.
**Impact**: Improving both checks to ~75% would raise Cat 3 by ~5 points and Cat 4 by ~4 points, lifting the overall score by ~1-2 points.

### 4. Code Quality Review Pass

**Check**: 4.3 Show me the code (current: 40%)
**Observed**: The product is entirely vibe-coded with zero hand-written code. Silent `.catch(() => {})` blocks existed in production until v0.12.0. Mixed infrastructure (Vercel serverless + Upstash Redis + client-side rendering) suggests architecture by accretion rather than design. The `focus:outline-none` without replacement in the nav button is a classic AI code tell.
**Target**: At 75%, consistent patterns throughout, no debug artifacts, performance basics covered, error boundaries in place.
**Impact**: Improving from 40% to ~65% would raise Cat 4 by approximately 7 points, lifting the overall score by ~1 point.

### 5. AI Provenance Disclosure on Product

**Check**: 7.3 AI disclosed and labeled (current: 70%)
**Observed**: Gigi's blog post on dergigi.com honestly discloses that Boris is entirely vibe-coded. But this disclosure doesn't appear on the Boris landing page or in the app. A user who only visits read.withboris.com has no way to know the product was AI-generated.
**Target**: At 75%, a brief note on the About or FAQ section acknowledging AI-assisted development would close this gap. Something like: "Boris was built using AI-assisted development -- read the full story."
**Impact**: Improving from 70% to 80% would raise Cat 7 by approximately 1 point.

---

## Methodology

This audit uses the Sloppypasta Framework V1 -- 46 checks across 8 weighted categories, scored on a 5-100% scale with a 5% floor. Category scores are geometric means of applicable checks. The overall score is a weighted geometric mean of category scores. Geometric means penalize low scores disproportionately -- a single 10% score drags harder than a single 90% helps.

**Note on data gathering**: The primary domain `boris.bar` does not currently resolve (DNS NXDOMAIN). Product information was gathered from the live app at `read.withboris.com`, the landing page source in the `dergigi/boris-landing` GitHub repository, the app source in `dergigi/boris`, Gigi's blog post about building Boris, and the project's CHANGELOG and README. The app itself is JS-rendered, making external content extraction limited -- several checks were scored conservatively where direct observation was not possible.

Source: github.com/dergigi/boris | Framework: docs/check-inventory.md
