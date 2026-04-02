# Sloppypasta Audit: The Sloppypasta Audit

**Date**: 2026-04-01
**URL**: https://github.com/mark-c4r/sloppypasta-audit
**Type**: Open-source framework / Claude Code skill (GitHub repo)
**Audit Mode**: External + Source (V1, single-agent, self-audit)
**Conditions**: [if:content]
**Applicable Checks**: 35 of 46 (1 conditional activated, 11 N/A)

---

## Audit Scope

**Surfaces assessed**: github.com/mark-c4r/sloppypasta-audit (full repository); docs/synthesis.md (em-dash density analyzed); README.md; docs/scoring-reference.md (full 21K-word document); SKILL.md; docs/check-inventory.md; docs/scale-anchors/ (8 files); docs/calibration/ (3 files); docs/reference/ (3 files); full git log (14 commits); Python verification script (executed); LICENSE file.
**Surfaces via proxy**: Claude Code skill invocation behavior from SKILL.md frontmatter — not triggered in a fresh session. Community engagement state from GitHub stars/forks/watchers at time of audit.
**Surfaces not assessed**: Skill runtime behavior when invoked via Claude Code; Nostr announcement distribution (unshipped); downstream audits produced by the skill.
**Limitations**: Self-audit — the auditor is the author. Cat 3 (Design & Interface) entirely N/A for a documentation repository. Social authenticity score reflects publication-date state.

---

## Overall: 76% -- Grade B

The Sloppypasta Audit is a well-crafted open-source framework with exceptional structural foundations: MIT-licensed, zero-dependency, zero-tracking, fully self-hostable, with all content in open markdown formats. Sovereignty (85%), Product Conduct (97%), and Economic Alignment (100%) are genuinely strong -- the framework practices what it preaches. The writing in synthesis.md is distinctive and opinionated, opening with "Two things broke the internet: no native money, and no taste" rather than the throat-clearing preambles it warns against. The main weakness is predictable for a just-launched project: zero community engagement (15% Social Authenticity) creates a severe drag through the geometric mean, collapsing Cat 1 to 30%. A secondary gap: the framework's own docs show elevated em-dash density (5-7 per 1000 words), tripping the very detection threshold it defines. The irony is instructive -- the framework catches tells its own authors didn't fully scrub. Content provenance relies on GitHub (platform-verified, not independently verifiable), and AI contribution is acknowledged in git commits but not disclosed in the documents themselves. Cat 3 (Design & Interface) is entirely N/A -- this is a documentation repo, not a visual product.

---

## Category Breakdown

### Cat 1: Slop Detection -- 30% (weight: 11.1%, adjusted)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 1.1 | LLM Smell Markers in Text | 60 | Zero banned words in synthesis.md and README.md. Voice is distinctive and opinionated throughout ("Useful for anyone who gives a damn"). No Bold Prefix patterns in the framework's own prose. No Conclusion headers, no zoom-out openings. However, em-dash density is elevated: 15 em-dashes in ~3000 words of synthesis.md (5 per 1000) and 140 in ~21000 words of scoring-reference.md (6.7 per 1000), both above the framework's own 1-per-500-words threshold. Many scoring-reference em-dashes occur in scale anchor descriptions (meta-content describing AI tells), but the pattern extends into authorial prose. |
| 1.2 | Social Authenticity | 15 | Zero stars, zero forks, zero watchers. One self-created issue (Nostr announcement). No external contributors, no community engagement. The repo was published on 2026-04-01 so the absence is honest, not manufactured -- but the geometric mean doesn't grade on a curve. A product with zero community presence cannot score higher regardless of how recently it launched. |

### Cat 2: Writing & Thinking -- 75% (weight: 11.1%, adjusted)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 2.1 | Economy of Words | 75 | Zero banned-word density across synthesis.md and README.md. Text is dense with meaning -- the seven axioms in synthesis.md each earn their place. "Every default is a decision" and "If the architecture allows betrayal, the only question is when" are tight, opinionated statements with no filler. The scoring reference is 21,000 words but each check description is necessarily detailed for repeatable scoring. No hedging, no qualifiers in product-facing text. |
| 2.2 | Copy Is Interface Design | 70 | README provides three clear usage paths (Claude Code skill, manual audit, community tool) with specific instructions. SKILL.md includes invocation examples. Scoring reference guides auditors step-by-step with phases and verification scripts. Repository structure is documented. But this is documentation, not interactive UI -- no error messages, empty states, or microcopy to evaluate. The copy guides but within the inherent limits of a static framework. |
| 2.3 | No Throat-Clearing | 80 | synthesis.md opens with "Two things broke the internet: no native money, and no taste." -- substance in the first sentence. Each axiom is stated directly without preamble. Category descriptions lead with their core question ("Can you smell the AI?", "Does the text show a thinking human?"). The Nostr announcement draft is similarly direct: "Shipped the Sloppypasta Audit -- an open-source framework for scoring..." No hedging seesaws, no padding paragraphs. The writing consistently takes positions. |

### Cat 3: Design & Interface -- N/A (excluded)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 3.1 | Information Density | N/A | No visual interface -- framework is markdown documentation in a git repo |
| 3.2 | Physical Obviousness | N/A | No visual interface |
| 3.3 | Design System Consistency | N/A | No visual interface |
| 3.4 | Self-Evident UI | N/A | No visual interface |
| 3.5 | Modal-Free Experience | N/A | No visual interface |
| 3.6 | Accessibility Basics | N/A | No visual interface |

Category excluded (0 applicable checks). Weight redistributed proportionally.

### Cat 4: Product Craft -- 77% (weight: 11.1%, adjusted)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 4.1 | Shipped Ready | 70 | Core flow works: clone repo, read scoring-reference.md, run audit. SKILL.md invocation is functional. Python verification script runs correctly. Five complete audit reports (PodNews, Fountain, Vexl, Polymarket, AllTrails) demonstrate the skill produces real output. No placeholder data anywhere. Minor rough edges: no published GitHub releases, no CHANGELOG file, contributing guidelines are brief. |
| 4.2 | Orphaned Features | 80 | Every documentation path referenced in README resolves: synthesis.md, check-inventory.md, scale-anchors/ (8 files), reference/ (3 files), calibration/ (3 files). SKILL.md references scoring-reference.md correctly. One minor orphan: docs/nostr-announcement.md is an unshipped draft with a corresponding open issue (#1). No dead links, no "coming soon" placeholders. |
| 4.3 | Show Me the Code | 80 | Clean markdown formatting throughout. Consistent commit message convention across 14 commits (type: scope -- description). SKILL.md uses proper YAML frontmatter with allowed-tools declaration. Python verification script is clean and functional. No debug artifacts, no TODO markers in shipped files. Plans directory shows development process without leaking into production docs. |
| 4.4 | Iteration Visible | 80 | 14 commits showing clear V1 through V7 progression. Commit messages document scope: "feat: V1 check inventory -- 46 checks across 8 categories" through "feat: V7 ship -- README, LICENSE, cleanup for public release". Plans directory preserves the shaping work (V3 shaping doc, V3 PRDs, skill optimization PRD). Calibration notes document framework refinement against Boris and Twitter/X. No CHANGELOG or release tags, but the development story is traceable through git history. |

### Cat 5: Product Conduct -- 97% (weight: 16.7%, adjusted)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 5.1 | No Access Gates | 100 | Public GitHub repo. All content accessible without signup, login, or payment. MIT license allows unrestricted use. |
| 5.2 | No Manufactured Urgency | 100 | No urgency tactics of any kind. No countdown timers, no scarcity signals, no "act now" pressure. |
| 5.3 | No Nag/Re-engagement | 100 | No notifications, no emails, no nagging. The product has zero re-engagement mechanisms. |
| 5.4 | No Attention Harvesting | 100 | No infinite scroll, no autoplay, no gamification, no streak mechanics. Content has clear boundaries (documents end). |
| 5.5 | Privacy & Tracking Composite | 100 | See sub-checks below. |
| 5.6 | RSS or Equivalent | 75 | No RSS feed, but the content is markdown files in a git repo -- git pull delivers all content updates in an open, machine-readable format. GitHub also provides Atom feeds for repos. Not traditional RSS but the distribution mechanism achieves the same goal through an even more open channel. |
| 5.7 | Cancel/Leave in One Click | 100 | No account to cancel. Delete your local clone and you're done. |
| 5.8 | No Double-Dipping | 100 | Free product with zero monetization. No ads, no data collection, no attention extraction. |
| 5.9 | No Product Coercion | 100 | No platform pushing. Works with any text editor. Claude Code skill is one option, manual audit is equally supported. |
| 5.10 | No Dark Patterns | 100 | Zero dark patterns. No conversion flows, no upsells, no manipulation of any kind. |

#### 5.5 Sub-Checks (composite: 100%)

| # | Sub-Check | Score | Justification |
|---|-----------|-------|---------------|
| 5.5a | Cookie Count | 100 | Framework itself sets zero cookies. Hosted on GitHub which has standard cookies, but the framework's distribution is a git clone. |
| 5.5b | Third-Party Tracker Count | 100 | No trackers. No JavaScript. No analytics. Pure markdown in a git repo. |
| 5.5c | Analytics Philosophy | 100 | No analytics of any kind. |
| 5.5d | Cookie Consent Quality | 100 | No cookies requiring consent. |
| 5.5e | DNT Respect | 100 | Nothing to track. DNT is moot. |
| 5.5f | Minimal Permissions | N/A | No mobile app [if:mobile] |
| 5.5g | Telemetry Opt-In | N/A | No mobile app [if:mobile] |
| 5.5h | No Background Data Collection | N/A | No mobile app [if:mobile] |

### Cat 6: Sovereignty & Privacy -- 85% (weight: 22.2%, adjusted)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 6.1 | Rugpull Resistance | 75 | MIT-licensed open source on GitHub. Anyone can fork at any time. Git history is preserved. The framework is documentation -- it survives the author's departure because the methodology is the product. Not protocol-level (it's a specification, not running infrastructure), but fork resistance is strong. |
| 6.2 | Exit Cost Zero | 100 | Everything is markdown files in a git repo. Data is already in open format on your machine after git clone. No export needed because the content was never locked up. |
| 6.3 | Identity Sovereignty | 100 | No identity required. No signup, no email, no account. Clone the repo anonymously and use it. |
| 6.4 | Protocol vs Platform | 75 | The framework is an open specification that anyone can implement independently. Multiple auditors can run the same checks without coordination. Manual audit path documented alongside the Claude Code skill. But the primary implementation (Claude Code skill) is coupled to one platform. The spec is open; the tooling is partially locked. |
| 6.5 | Self-Hostable or Auditable | 100 | git clone and you have everything. Zero dependencies. No server, no build step, no infrastructure required. Self-hosting is the only deployment model -- there is no hosted version. |
| 6.6 | Privacy-Preserving Payment | 100 | Free. No payment required. 100% by default per scoring procedure. |
| 6.7 | Source Code Availability | 100 | MIT license (permissive). Public GitHub repo. 14 commits showing active maintenance from initial concept through V7 release. Full source available for inspection, modification, and redistribution without restriction. |
| 6.8 | Provenance Traceable | 50 | Content is in git with timestamped, attributed commits. GitHub provides platform-verified provenance. But no GPG-signed commits, no cryptographic provenance beyond what git provides natively. Integrity is verifiable within GitHub's trust boundary but not independently. For a framework that values sovereignty, relying on platform-verified provenance is a gap. |
| 6.9 | Distribution Independence | N/A | No mobile app [if:mobile] |
| 6.10 | No Play Services Dependency | N/A | No mobile app [if:mobile] |
| 6.11 | Key Management Sovereignty | N/A | No identity management [if:identity] |
| 6.12 | Relay/Node Independence | N/A | No messaging/social features [if:messaging/social] |
| 6.13 | Custodial vs Non-Custodial | N/A | No payment handling [if:payments] |

### Cat 7: Honesty & Transparency -- 80% (weight: 16.7%, adjusted)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 7.1 | Business Model Visible | 90 | The business model is: none. MIT-licensed, free, no monetization. This is immediately clear from the LICENSE file and README. No hidden revenue streams, no data collection, no attention extraction. The framework is a commons contribution and presents itself as such. |
| 7.2 | No Marketing Exaggeration | 80 | README claims are verifiable: "46 checks across 8 categories" (true), "Geometric mean, not arithmetic" (true, demonstrated in synthesis.md). "Built for the Bitcoin/Nostr community" is accurate positioning. "Useful for anyone who gives a damn" is opinionated but not exaggerated. No superlatives, no "revolutionary." The Nostr draft's "Run it on anything" is mildly broad -- it requires a product to audit, not literally anything -- but not dishonest. |
| 7.3 | AI Disclosed and Labeled | 70 | Git commits include "Co-Authored-By: Claude" tags acknowledging AI contribution to the codebase. But the documents themselves -- synthesis.md, scoring-reference.md, README -- do not label AI's role in their creation. The irony is sharp: a framework built to detect AI-generated content doesn't fully disclose how much of its own content was AI-assisted. The writing reads as human-edited but the disclosure gap is real. |
| 7.4 | No Degraded Free Experience | 100 | One tier: free and complete. No premium features, no paid upgrades, no feature gating. Every user gets the full framework. |
| 7.5 | Dialogue, Not Broadcast | 65 | GitHub Issues enabled with one open issue. Contributing section in README invites: "Run the audit on a product and publish the results. File issues. Propose improved anchors with real product examples." The mechanisms for dialogue exist. But: no GitHub Discussions enabled, no community forum, no external contributors yet, no responses to outside feedback. The invitation to dialogue is genuine but entirely untested. |

### Cat 8: Economic Alignment -- 100% (weight: 11.1%, adjusted)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 8.1 | Native Money vs Ads | 100 | Free, no ads, no data monetization. Revenue comes from: nothing. The framework is a commons contribution funded by the author's time. Zero attention extraction. |
| 8.2 | Pay Per Service | 100 | Free. No subscription, no payment, no recurring charges. 100% by default per scoring procedure -- when no payment exists, there's no inertia billing problem. |
| 8.3 | No Coerced Upsells | 100 | Nothing to upsell. One tier, one experience, free. No upgrade pressure because there's nothing to upgrade to. |

---

## Score Summary

| Cat | Name | Score | Weight | Checks |
|-----|------|-------|--------|--------|
| 1 | Slop Detection | 30% | 11.1% | 2/2 |
| 2 | Writing & Thinking | 75% | 11.1% | 3/3 |
| 3 | Design & Interface | N/A | excluded | 0/6 |
| 4 | Product Craft | 77% | 11.1% | 4/4 |
| 5 | Product Conduct | 97% | 16.7% | 10/10 |
| 6 | Sovereignty & Privacy | 85% | 22.2% | 8/13 |
| 7 | Honesty & Transparency | 80% | 16.7% | 5/5 |
| 8 | Economic Alignment | 100% | 11.1% | 3/3 |
| **Overall** | | **76%** | | **Grade B** |

---

## Priority Improvements

### 1. Build Community Engagement

**Check**: 1.2 Social Authenticity (current: 15%)
**Observed**: Zero stars, forks, watchers, or external contributors. One self-created issue. The repo was published on April 1, 2026 with no external visibility yet.
**Target**: 50% looks like: genuine followers with real but surface-level interaction. 75% looks like: real humans discussing real use cases, filing bug reports, contributing improved anchors. Natural variation in engagement.
**Impact**: Improving from 15% to 50% would raise Cat 1 from 30% to 55%, lifting the overall score from 76% to approximately 82%. This is the single highest-leverage improvement because the geometric mean amplifies the floor drag of 15%.

### 2. Scrub Em-Dash Density in Framework Prose

**Check**: 1.1 LLM Smell Markers in Text (current: 60%)
**Observed**: synthesis.md has 5 em-dashes per 1000 words and scoring-reference.md has 6.7 per 1000 words. The framework's own 1-per-500-words threshold flags its own documentation. Many em-dashes in scoring-reference.md are in scale anchor descriptions (meta-content) but the pattern extends into authorial prose.
**Target**: 75% looks like: em-dash density under 1 per 1000 words, no structural tells, voice consistent and human. AI may have been used but the human's editing voice dominates completely.
**Impact**: Improving from 60% to 75% would raise Cat 1 from 30% to 34% (modest because 1.2 remains the floor drag), lifting overall by approximately 1 point. More importantly: the credibility gap of a slop-detection framework exhibiting its own detection markers is worth fixing regardless of score impact.

### 3. Disclose AI Contribution in Documentation

**Check**: 7.3 AI Disclosed and Labeled (current: 70%)
**Observed**: Git commits include "Co-Authored-By: Claude" tags, but synthesis.md, scoring-reference.md, and README do not label AI's role in their creation. A framework that detects AI tells should be transparent about its own AI-assisted authorship.
**Target**: 75% looks like: AI-generated or AI-assisted content labeled where it appears. Human-created content distinguishable from AI content. The user knows what they're reading. 100% looks like: "AI-drafted, human-edited" or "Framework co-developed with Claude Code."
**Impact**: Improving from 70% to 85% would raise Cat 7 from 80% to 83%, lifting overall by approximately 1 point. The credibility impact exceeds the score impact -- a slop-detection framework that openly labels its own AI assistance sets the standard it demands from others.

### 4. Add Cryptographic Provenance

**Check**: 6.8 Provenance Traceable (current: 50%)
**Observed**: Content provenance relies on GitHub's platform-verified timestamps and attribution. No GPG-signed commits. For a framework that values sovereignty and grades other products on cryptographic provenance, relying on platform-verified identity is inconsistent.
**Target**: 75% looks like: commits signed with keys controlled by the author, independently verifiable without trusting GitHub. GPG-signed tags on releases.
**Impact**: Improving from 50% to 75% would raise Cat 6 from 85% to 89%, lifting overall by approximately 2 points. This improvement aligns the framework's practice with its philosophy -- the scoring reference assigns 75% for "independently verifiable provenance."

### 5. Publish a CHANGELOG and GitHub Releases

**Check**: 4.4 Iteration Visible (current: 80%)
**Observed**: Iteration is traceable through 14 git commits and the plans directory, but no CHANGELOG file exists and no GitHub releases have been published. The development story requires reading git log to follow.
**Target**: 75% is already exceeded. 100% looks like: development is part of the product's identity, changelogs include reasoning, early versions acknowledged.
**Impact**: Improving from 80% to 90% would raise Cat 4 from 77% to 80%, lifting overall by less than 1 point. Low score impact but high usability impact -- releases and changelogs make the framework's evolution accessible without git literacy.

Source: github.com/mark-c4r/sloppypasta-audit | Framework: docs/scoring-reference.md
