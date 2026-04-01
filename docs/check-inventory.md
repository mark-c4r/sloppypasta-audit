# Sloppypasta Audit — V1 Check Inventory

This is the definitive V1 check list. All scale anchors, detection references, and the audit skill reference this document.

**Version**: V1 (HIGH measurability only)
**Total checks**: 47 (38 universal + 4 content-conditional + 5 app-type-conditional)
**Typical web app**: ~41 applicable checks

---

## Cat 1: Slop Detection — "Can you smell the AI?"

**Weight**: 10% · **V1 checks**: 2

| # | Check | Condition | Notes |
|---|-------|-----------|-------|
| 1.1 | LLM smell markers in text | Universal | Banned-word frequency (per 1000 words), em-dash density (>1/500 words), structural patterns (Bold Prefix lists, symmetrical paragraphs, Rule of Three), model-specific first words. See Detection Reference. |
| 1.2 | Social authenticity | Universal | *Merged from V3 1.4 + 1.5 + 7.6.* Are engagement metrics real? Are followers human? Is community genuine vs manufactured? Covers bot detection, dead internet signals, and audience legitimacy. |

---

## Cat 2: Writing & Thinking — "Does the text show a thinking human?"

**Weight**: 10% · **V1 checks**: 4

| # | Check | Condition | Notes |
|---|-------|-----------|-------|
| 2.1 | Economy of words | Universal | *Promoted from MEDIUM via banned-word frequency metric.* Count banned words/phrases per 1000 words (relative density, not binary). 49 banned words, 38 phrases, 16 openers. |
| 2.2a | Copy guides action | Universal | Does text tell you what to do, where you are, what went wrong? Error messages, empty states, labels, CTAs. |
| 2.2b | Copy shows authorship | Universal | Could this copy only exist in this product? Voice, specificity, personality vs. interchangeable template text. |
| 2.3 | No throat-clearing | `[if:content]` | No filler openings ("In today's landscape..."), no hedging seesaws, no padding paragraphs. Gets to the point. |

---

## Cat 3: Design & Interface — "Does the look show care?"

**Weight**: 10% · **V1 checks**: 5

| # | Check | Condition | Notes |
|---|-------|-----------|-------|
| 3.1 | Information density | Universal | Items per viewport. Respects screen real estate. Whitespace is intentional grouping, not uniform padding. |
| 3.3 | Design system consistency | Universal | Consistent tokens, spacing, type scale across pages. **Window resize test**: slowly drag to ~800px tablet — if layout breaks, AI generated it. |
| 3.4 | Self-evident UI | Universal | No tutorial needed. Undo/back available. Empty states are designed (not "No items found" dead ends). User control preserved. |
| 3.5 | Modal-free experience | Universal | No hostile modals: popup-on-load, newsletter overlays, login-wall interstitials. Functional dialogs (confirm delete) are fine. |
| 3.6 | Accessibility basics | Universal | Contrast ratios, tap target sizes, screen reader landmarks. **Slop marker**: broken focus states (`outline-none` without replacement) = AI code tell. Not WCAG compliance — care signal. |

---

## Cat 4: Product Craft — "Less is more"

**Weight**: 10% · **V1 checks**: 4

| # | Check | Condition | Notes |
|---|-------|-----------|-------|
| 4.1 | Shipped ready | Universal | Core flow works on first use. No spinner-for-everything, no placeholder data ("John Doe", "+20.1%"), no brutal error handling ("Something went wrong"). |
| 4.2 | Orphaned features | Universal | Every feature accessible, working, connected. No dead settings, broken links, "coming soon" placeholders, empty dashboards. |
| 4.3 | Show me the code | Universal | Builder-mode check. `console.log("here")` in production, inline styles mixed with Tailwind, debug remnants = shipped without review. |
| 4.4 | Iteration visible | Universal | *Restored from V1 (CC-2).* Changelogs, release notes, visible commit history, hard decisions documented. Ship-ugly-iterate-publicly requires visible iteration. |

---

## Cat 5: Product Conduct — "How does it behave?"

**Weight**: 15% · **V1 checks**: 10

| # | Check | Condition | Notes |
|---|-------|-----------|-------|
| 5.1 | No access gates | Universal | No paywalls, forced signups, or login walls blocking content. Instagram fuck-you pattern = 0%. |
| 5.2 | No manufactured urgency | Universal | No countdown timers, "only 3 left," fake scarcity, limited-time offers designed to prevent thinking. |
| 5.3 | No nag/re-engagement | Universal | No notification overload, push spam, "we miss you" emails, badge-count manipulation. |
| 5.4 | No attention harvesting | Universal | No infinite scroll, autoplay next, dopamine gamification, streak mechanics. Natural endpoints exist. |
| 5.5 | Privacy & tracking composite | Universal | 8 sub-checks computing single score (see composite spec below). |
| 5.6 | RSS or equivalent | `[if:content]` | Machine-readable content feed available. Static tools, protocols, CLI apps = N/A. |
| 5.7 | Cancel/leave in one click | Universal | Account deletion, unsubscribe, data removal — one step, not a dark pattern maze. |
| 5.8 | No double-dipping | Universal | Paid = no ads. Don't charge AND monetize attention. |
| 5.9 | No product coercion | Universal | No "download our app" nag, no "better in Chrome" banners, no forced app-store redirect on mobile. |
| 5.10 | No dark patterns | Universal | *Moved from V3 3.5.* Confirmshaming, hidden costs, trick questions, roach motels, bait-and-switch, forced continuity. |

### 5.5 Privacy & Tracking Composite Specification

Check 5.5 is a composite of 8 sub-checks. Score = geometric mean of applicable sub-checks.

| Sub | Check | Condition | What it measures |
|-----|-------|-----------|-----------------|
| 5.5a | Cookie count | Universal | Zero ideal. First-party session OK. Third-party = bad. Count is the metric. |
| 5.5b | Third-party tracker count | Universal | Network inspector. Zero = ideal. Each tracker penalizes. |
| 5.5c | Analytics philosophy | Universal | None (best) → self-hosted privacy-respecting (Plausible/Umami) → hosted privacy (Fathom) → GA → GA + multi-tracker (worst). |
| 5.5d | Cookie consent quality | Universal | No banner needed (best) → reject-all prominent → accept-all prominent → accept-all dark pattern → content-blocked-until-accept (worst). |
| 5.5e | DNT respect | Universal | Honors Do-Not-Track header → ignores it → no mechanism at all. |
| 5.5f | Minimal permissions | `[if:mobile]` | Requests only what's needed for core function. Each unnecessary permission penalizes. |
| 5.5g | Telemetry opt-in | `[if:mobile]` | Telemetry defaults OFF, user opts in (best) → defaults ON, user can opt out → no control (worst). |
| 5.5h | No background data collection | `[if:mobile]` | No data collection when app is not in active use. |

Mobile sub-checks (5.5f–h) are N/A for web-only products — excluded from the composite geomean.

---

## Cat 6: Sovereignty & Privacy — "Can they rugpull you?"

**Weight**: 20% · **V1 checks**: 13 (8 universal + 5 conditional)

| # | Check | Condition | Notes |
|---|-------|-----------|-------|
| 6.1 | Rugpull resistance | Universal | Can they change terms, raise prices, remove features, shut down unilaterally? Protocol = resistant. Platform = vulnerable. |
| 6.2 | Exit cost zero | Universal | Data export in standard formats. No vendor lock-in. Can you leave with your data today? |
| 6.3 | Identity sovereignty | Universal | Keypair (best) → pseudonymous account → email account → phone-verified → gov ID required (worst). |
| 6.4 | Protocol vs platform | Universal | Open protocol (best) → platform with open API → platform with restricted API → walled garden (worst). |
| 6.5 | Self-hostable or auditable | Universal | Can you run it yourself? Can you verify what it does? Self-host (best) → auditable source → trust-but-verify → black box (worst). |
| 6.6 | Privacy-preserving payment | Universal | Accepts Lightning/ecash/Monero (best) → on-chain crypto → privacy card service → credit card only (worst). Credit-card-only = identity permanently linked to purchase. |
| 6.7 | Source code availability | Universal | FOSS with active maintenance (best) → source-viewable → proprietary free → proprietary paid (worst). |
| 6.8 | Provenance traceable | `[if:content]` | *Restored from V1 (CI-5).* Content signed, timestamped, attributed. Cryptographic provenance (Nostr events, signed commits) is ideal. |
| 6.9 | Distribution independence | `[if:mobile]` | Sideloadable APK + F-Droid (best) → App Store + sideload → App Store only (worst). |
| 6.10 | No Google Play Services dependency | `[if:mobile]` | Works on GrapheneOS/CalyxOS/LineageOS → degrades gracefully → requires Play Services (worst). |
| 6.11 | Key management sovereignty | `[if:identity]` | NIP-07/NIP-46 external signing (best) → app holds key with export → custodial key management (worst). |
| 6.12 | Relay/node independence | `[if:messaging/social]` | Works with any relay/node (best) → recommended set → specific relays required (worst). |
| 6.13 | Custodial vs non-custodial | `[if:payments]` | Non-custodial (best) → custodial with withdrawal → fully custodial (worst). |

---

## Cat 7: Honesty & Transparency — "Does it tell you the truth?"

**Weight**: 15% · **V1 checks**: 6

| # | Check | Condition | Notes |
|---|-------|-----------|-------|
| 7.1 | Business model visible | Universal | Can you see how they make money? Explicit pricing/model (best) → implied → ambiguous → hidden/misleading (worst). |
| 7.2 | No marketing exaggeration | Universal | Claims match reality. No "revolutionary," "AI-powered everything," vaporware promises. |
| 7.3a | AI content transparency | Universal | If AI used in user-facing content, is it disclosed at point of encounter? N/A if no user-facing AI detected. |
| 7.3b | Human authorship signal | Universal | Does content show evidence of human creation? Voice, opinions, personal references, irregular rhythm. |
| 7.4 | No degraded free experience | Universal | Free tier is genuinely useful, not crippled to force upgrade. Feature hostage-taking penalized. |
| 7.5 | Dialogue, not broadcast | `[if:content]` | *Restored from V1 (VH-4).* Feedback channel exists: reply mechanism, issue tracker, public discussion forum. Can you talk back? |

---

## Cat 8: Economic Alignment — "Who captures the value?"

**Weight**: 10% · **V1 checks**: 3

| # | Check | Condition | Notes |
|---|-------|-----------|-------|
| 8.1 | Native money vs ads | Universal | Revenue from value exchange — sats, subscriptions, one-time purchase (best) → mixed → pure ad/attention extraction (worst). |
| 8.2 | Pay per service | Universal | PPQ.AI model ideal. Bus-ticket subscription honest. Netflix inertia billing = worst. Pricing reflects actual value delivered. |
| 8.3 | No coerced upsells | Universal | No guilt trips, no feature hostage, no artificial limitations designed to force tier upgrade. |

---

## Summary

| Cat | Name | V1 Checks | Weight |
|-----|------|-----------|--------|
| 1 | Slop Detection | 2 | 10% |
| 2 | Writing & Thinking | 4 | 10% |
| 3 | Design & Interface | 5 | 10% |
| 4 | Product Craft | 4 | 10% |
| 5 | Product Conduct | 10 | 15% |
| 6 | Sovereignty & Privacy | 13 | 20% |
| 7 | Honesty & Transparency | 6 | 15% |
| 8 | Economic Alignment | 3 | 10% |
| **Total** | | **47** | **100%** |

**Dimension breakdown**:
- Care (Slop + Writing + Design + Craft) = 40%
- Structure (Conduct + Sovereignty) = 35%
- Signal (Honesty + Economic) = 25%

---

## Conditional Activation Reference

Checks tagged with a condition activate based on what the product does. If a conditional check doesn't apply, it's **excluded from the category geomean** (N/A). If it applies and isn't fulfilled, it **penalizes the score**.

| Tag | Activates when | Example products |
|-----|---------------|-----------------|
| `[if:content]` | Product publishes or curates editorial content | Blogs, news sites, podcasts, social feeds |
| `[if:mobile]` | Product distributed as mobile/desktop app | Native apps, PWAs with install prompts |
| `[if:identity]` | Product manages user identity (login, profiles, keys) | Social networks, messaging apps, wallets |
| `[if:messaging/social]` | Product has communication or community features | Chat apps, forums, social networks |
| `[if:payments]` | Product handles money (wallets, subscriptions, V4V) | Wallets, exchanges, tipping services |

**Minimum 2 active checks per category** required. If conditional exclusions drop a category below 2, exclude the entire category and redistribute its weight proportionally across remaining categories.

---

## V3 → V1 Number Mapping

| V3 # | V1 # | Check | Status |
|------|------|-------|--------|
| 1.1 | 1.1 | LLM smell markers | Kept |
| 1.2 | — | Visual monoculture | Dropped: overlap with 3.1. Visual assessment → Cat 3 only. |
| 1.3 | — | Mid-curve convergence | Deferred: MEDIUM |
| 1.4 | 1.2 | Social authenticity | Merged with 1.5 + 7.6 |
| 1.5 | — | Dead internet signals | Merged into V1 1.2 |
| 2.1 | 2.1 | Economy of words | Promoted from MEDIUM via banned-word frequency |
| 2.2 | 2.2a | Copy guides action | Split from 2.2 |
| — | 2.2b | Copy shows authorship | Split from 2.2 |
| 2.3 | — | Proof of thought | Deferred: MEDIUM |
| 2.4 | 2.3 | No throat-clearing | Kept |
| 2.5 | — | Distinctive voice | Deferred: MEDIUM |
| 2.6 | — | Writing shows study | Deferred: LOW-MED |
| 3.1 | — | Visual distinctiveness | Deferred: MEDIUM (absorbed V3 1.2 markers) |
| 3.2 | 3.1 | Information density | Kept |
| 3.3 | 3.2 | Physical obviousness | Kept |
| 3.4 | — | Intentional hierarchy | Deferred: MEDIUM |
| 3.5 | 5.10 | No dark patterns | Moved to Cat 5 |
| 3.6 | 3.3 | Design system consistency | Kept |
| 3.7 | 3.4 | Self-evident UI | Kept |
| 3.8 | 3.5 | Modal-free experience | Kept |
| 3.9 | 3.6 | Accessibility basics | Kept |
| 4.1 | — | Opinionated software | Deferred: MEDIUM (borderline) |
| 4.2 | — | Half not half-assed | Deferred: MEDIUM (merged with 4.5) |
| 4.3 | 4.1 | Shipped ready | Kept |
| 4.4 | 4.2 | Orphaned features | Kept (expert-recommended) |
| 4.5 | — | Aerodynamic | Merged into V3 4.2 (deferred) |
| 4.6 | — | Build for decades | Deferred: MEDIUM |
| 4.7 | 4.3 | Show me the code | Kept |
| *CC-2* | 4.4 | Iteration visible | Restored from original V1 |
| 5.1 | 5.1 | No access gates | Kept |
| 5.2 | 5.2 | No manufactured urgency | Kept |
| 5.3 | 5.3 | No nag/re-engagement | Kept |
| 5.4 | 5.4 | No attention harvesting | Kept |
| 5.5 | 5.5 | Privacy composite | Kept (8 sub-checks) |
| 5.6 | 5.6 | RSS or equivalent | Kept |
| 5.7 | 5.7 | Cancel/leave | Kept |
| 5.8 | — | Resilience to takedown | Deferred: MEDIUM |
| 5.9 | 5.8 | No double-dipping | Kept |
| 5.10 | 5.9 | No product coercion | Kept |
| 6.1 | 6.1 | Rugpull resistance | Kept |
| 6.2 | 6.2 | Exit cost zero | Kept |
| 6.3 | 6.3 | Identity sovereignty | Kept |
| 6.4 | 6.4 | Protocol vs platform | Kept |
| 6.5 | — | Namespace independence | Deferred: MEDIUM |
| 6.6 | 6.5 | Self-hostable or auditable | Kept |
| 6.7 | — | Information asymmetry | Removed: overlaps 5.5 privacy composite |
| 6.8 | — | Economic privacy | Deferred: MEDIUM |
| 6.9 | — | Algorithm transparency | Deferred: MED-HIGH |
| 6.10 | 6.6 | Privacy-preserving payment | Kept |
| 6.11 | 6.7 | Source code availability | Kept |
| *CI-5* | 6.8 | Provenance traceable | Restored from original V1 |
| 6.12 | 6.9 | Distribution independence | Kept |
| 6.13 | 6.10 | No Google Play Services dep. | Kept |
| 6.14 | — | Push notification independence | Deferred: MEDIUM |
| 6.15 | 6.11 | Key management sovereignty | Kept |
| 6.16 | 6.12 | Relay/node independence | Kept |
| 6.17 | 6.13 | Custodial vs non-custodial | Kept |
| 7.1 | 7.1 | Business model visible | Kept |
| 7.2 | 7.2 | No marketing exaggeration | Kept |
| 7.3 | 7.3a | AI content transparency | Split from 7.3 |
| — | 7.3b | Human authorship signal | Split from 7.3 |
| 7.4 | — | Marketing as enthusiasm | Deferred: MEDIUM |
| 7.5 | — | Honest about limitations | Deferred: MEDIUM |
| 7.6 | — | Earned audiences | Merged into V1 1.2 |
| 7.7 | 7.4 | No degraded free experience | Kept |
| *VH-4* | 7.5 | Dialogue, not broadcast | Restored from original V1 |
| 8.1 | 8.1 | Native money vs ads | Kept |
| 8.2 | 8.2 | Pay per service | Kept |
| 8.3 | — | Creator value flows through | Deferred: MEDIUM |
| 8.4 | 8.3 | No coerced upsells | Kept |
| 8.5 | — | Curation rewarded | Deferred: LOW-MED |

---

## Deferred to V2

These checks from the V3 inventory did not make V1 due to measurability or overlap:

| V3 # | Check | Measurability | Reason |
|------|-------|--------------|--------|
| 1.2 | Visual monoculture | HIGH | Overlap with 3.1. Visual assessment consolidated in Cat 3. Markers absorbed into deferred 3.1. |
| 1.3 | Mid-curve convergence | MEDIUM | Needs reference examples to score repeatably across auditors. |
| 1.5 | Dead internet signals | MEDIUM | Merged into V1 1.2 (social authenticity). |
| 2.3 | Proof of thought | MEDIUM | Requires deep reading, not surface check. |
| 2.5 | Distinctive voice | MEDIUM | Subjective — needs multi-agent consensus for reliability. |
| 2.6 | Writing shows study | LOW-MED | Too judgment-dependent for single-agent V1. |
| 3.1 | Visual distinctiveness | MEDIUM | Absorbed 1.2 visual monoculture markers. Full visual assessment needs trained eye + multi-agent. |
| 3.4 | Intentional hierarchy | MEDIUM | Needs design expertise, not binary check. |
| 4.1 | Opinionated software | MEDIUM | Borderline. Include in V2 with strong scale anchors. |
| 4.2 | Half not half-assed | MEDIUM | Merged with 4.5 (aerodynamic). Same construct: deliberate restraint. Needs multi-agent for V2. |
| 4.5 | Aerodynamic | MEDIUM | Merged into 4.2. |
| 4.6 | Build for decades | MEDIUM | Dependency audit requires builder-mode access. |
| 5.8 | Resilience to takedown | MEDIUM | Hard to test externally without infrastructure knowledge. |
| 6.5 | Namespace independence | MEDIUM | Jargon-heavy, hard to score without protocol knowledge. |
| 6.7 | Information asymmetry | MEDIUM | Removed: concept captured by 5.5 privacy composite (tracker counting, shadow profiling). |
| 6.8 | Economic privacy | MEDIUM | Borderline. May upgrade to V2 with payment-flow analysis. |
| 6.9 | Algorithm transparency | MED-HIGH | Conditional `[if:feed/social]`. Upgrade candidate for V2. |
| 6.14 | Push notification independence | MEDIUM | Requires infrastructure analysis beyond external audit. |
| 7.4 | Marketing as enthusiasm | MEDIUM | Judgment call — genuine enthusiasm vs manufactured hype is subjective. |
| 7.5 | Honest about limitations | MEDIUM | Vague without specific anchors. Needs calibration examples. |
| 7.6 | Earned audiences | MEDIUM | Merged into V1 1.2 (social authenticity). |
| 8.3 | Creator value flows through | MEDIUM | Hard to verify externally — revenue share is often private. |
| 8.5 | Curation rewarded | LOW-MED | Nearly always N/A for non-social products. Weak measurability even when applicable. |
