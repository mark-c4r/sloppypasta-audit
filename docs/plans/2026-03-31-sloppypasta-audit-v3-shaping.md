---
shaping: true
ticket: sloppypasta-audit
status: active
appetite: L
project: sloppypasta-audit
updated: 2026-03-31
---

# Sloppypasta Audit — Shaping Doc

## Frame

### Source
> "The test itself is reading as sloppypasta. The copy is low quality. The criteria seem weak, leaky, exaggerating, false positives." — User, Session 3
>
> "We want to master the craft of serving people. The good product can be recognized that it's serving people well." — User, Session 4
>
> "Not opinionated in this teenager slam dunk sense. More opinionated in that: we believe we know what the user wants. We have studied the user problem meticulously for years." — User, Session 4
>
> "Sloppypasta = AI-generated content created without care." — Gigi, dergigi.com

### Problem
Indie builders in the Bitcoin/Nostr community are shipping AI-assisted products with no structured way to evaluate whether the product feels sloppy, generic, or philosophically misaligned. The only options are enterprise WCAG checklists (wrong audience), vague intuition ("does it feel right?"), or no evaluation at all. A previous framework attempt (V1, 47 checks) was rejected because the framework itself read as sloppypasta.

### Outcome
A repeatable product audit that helps builders improve craft, detect AI slop, and align with sovereignty values — delivered as a Claude Code skill that outputs a scored report with actionable improvement suggestions. The framework itself must pass its own test.

---

## Requirements

| Req | Requirement | Status |
|-----|-------------|--------|
| R0 | Detect AI slop in products (text, visual, behavioral markers) | Core goal |
| R1 | Measure sovereignty/privacy alignment with cypherpunk values | Core goal |
| R2 | Repeatable scores — same product, same score if nothing changed | Must-have |
| R3 | Lean toward measurable/quantifiable checks over subjective judgment | Must-have |
| R4 | "Wise sage" tone — educate, don't shame; celebrate improvement paths | Must-have |
| R5 | Support diverse product types (web, mobile, desktop, CLI, protocol) | Must-have |
| R6 | Two audit modes: external visitor + builder self-audit | Must-have |
| R7 | Conditional check activation based on product type | Must-have |
| R8 | Scale differentiates meaningfully (20→40 hard, 80+ nearly impossible) | Must-have |
| R9 | Framework passes its own test — no slop in the audit itself | Must-have |
| R10 | Writing quality as standalone dimension (not lumped into "craft") | Must-have |
| R11 | Product craft / "less is more" as standalone dimension | Must-have |
| R12 | Economic alignment (V4V, pay-per-service) as dimension | Must-have |
| R13 | Automated detection where possible (CSS inspector, text scanner) | Nice-to-have |
| R14 | Output: radar chart + improvement roadmap + scorecard in markdown | Nice-to-have |
| R15 | Product-only scope — audit the artifact, not the company behind it | Must-have |

---

## Rabbit Holes (What Could Balloon Scope)
1. **WCAG compliance depth** — rejected by user. A11y is a slop marker, not a compliance checklist.
2. **Company-level signals** — funding source, lobbying, data sharing history. Out of scope (R15).
3. **Leaderboard / competitive ranking** — shifts tone from improvement to competition. No-go.
4. **Weight optimization** — intuition-matching on 5 products overfits. Use philosophical weights.
5. **Perfect repeatability** — some checks are inherently subjective. Accept MEDIUM measurability with agent rubrics.
6. **Copy/voice before criteria** — Session 3 mistake. Write copy LAST.

## No-Gos
- No enterprise WCAG compliance
- No company-level political evaluation
- No leaderboard or product ranking
- No "teenager maximalist" tone
- No copy writing until criteria are validated through calibration runs

---

## Shaping Stress-Test Results (3 experts)

### Fit Check Summary: 10 YES, 5 PARTIAL, 0 NO
Partials (R2 repeatability, R4 sage tone, R6 audit modes, R8 scale validation, R14 output format) are fixable with targeted decisions, not redesign.

### Critical Fixes (consensus across reviewers)
1. **Resolve 4 overlaps**: drop 1.2 (→3.1), merge 4.5→4.2, consolidate 1.4+1.5+7.6→"social authenticity", move 3.5→Cat 5
2. **Add conditional tags**: 5.6 [if:content], 6.9 [if:feed/social], 8.5 [if:social], 2.4 [if:content] — simple products penalized by irrelevant checks
3. **Restore 3 lost V1 checks**: CI-5 (provenance/signing), CC-2 (iteration visible), VH-4 (dialogue)
4. **5.5 sub-checks → composite**: 8 sub-checks compute one 5.5 score for geomean
5. **Accept bimodality**: 54% of checks = "protocol vs platform" discriminant. Report category scores always. Consider craft-mode weights for within-community use.

### Minimum Viable Shape (fits L appetite)
- Framework doc (synthesis.md V3) — all categories, anchors for 13 hardest checks only
- Single-agent skill with text scanner automation — no multi-agent, no CSS automation
- One calibration run on one product
- **Defer to V2**: multi-agent, visual automation, radar chart, builder mode, full anchors

### MVP 20 Checks (load-bearing subset)
1.1, 1.2, 2.2, 2.3, 3.3, 3.5, 3.9, 4.1, 4.3, 4.7, 5.1, 5.4, 5.5, 6.1, 6.2, 6.3, 6.4, 7.1, 7.2, 8.1

### Key Insights
- **Two constructs bolted together**: anti-slop craftsmanship + cypherpunk sovereignty alignment. Both necessary, neither sufficient.
- **Cat 2 (Writing) overbuilt**: only 2/6 checks survive MVP cut. Consider trimming. Codex: promote 2.1 with banned-word-frequency rubric (makes it HIGH measurability).
- **Cat 8 (Economic) nearly single-check**: consider merging into Honesty for MVP.
- **Gaming**: Cat 1 text markers trivially gameable (synonym swap). Cat 4+6 nearly impossible. Geomean is the strongest anti-gaming mechanism.
- **Calibration set needs**: Signal (privacy without Bitcoin), one sloppy Nostr client (tests whether sovereignty alone carries a score)
- **Missing anti-gaming**: require sampling from 3+ product surfaces (landing, errors, docs, onboarding) per text/design check

### Codex Review (revised with public accountability context)
Initial review (internal tool framing) said "over-engineered, ship 15 checks." Revised review (public tool framing) reversed:
- **Rigor is justified** — inconsistent public scores have negative value, worse than no framework
- **V1 = HIGH measurability only (~30-38 checks)** — enough coverage that no category feels empty, every check near-binary with scale anchor
- **Self-contained repo mandatory** — can't depend on /design-review or /qa (community members won't have them). Extract and inline relevant detection logic.
- **Single-agent for V1** — multi-agent consensus unlocks MEDIUM checks in V2, but HIGH checks don't need it
- **2 calibration products** — one expected-high (Boris/ppq.ai), one expected-low (Twitter). Validate directionality, ship.
- **"Ship ugly, iterate publicly"** — the plan's own axiom. Scale anchors don't need to be perfect, just specific enough that two operators score within 10 points.

---

## FINAL V1 SCOPE (Expert Consensus)

### What V1 ships
- **Open-source GitHub repo** at `~/Coding/sloppypasta-audit/`
- **Self-contained skill** — SKILL.md + reference docs (slop markers, sovereignty checks, scale anchors). No external skill dependencies.
- **~30-38 HIGH-measurability checks** across all 8 categories
- **Scale anchors** (0/25/50/75/100) for every V1 check — behavioral descriptions first, product examples second
- **Geometric mean scoring with 5% floor** — category geomean → weighted overall geomean
- **Weights set from philosophy** — sovereignty/content integrity highest, economic alignment lower. Validated (not optimized) against 2 calibration products.
- **Single-agent execution** — one Claude Code session, one pass, one markdown report
- **Output**: markdown scorecard with category breakdown, overall grade, 3-5 priority improvement suggestions in sage tone
- **Calibrated on 2 products**: one expected-high (Boris or ppq.ai), one expected-low (Twitter/X)

### V1 Check Set (HIGH measurability only)
| Cat | Checks | Count |
|-----|--------|-------|
| 1 Slop Detection | 1.1 LLM smell, 1.2 visual monoculture, 1.4 bot/social authenticity | 3 |
| 2 Writing | 2.1 economy of words (promoted w/ banned-word frequency), 2.2 copy is interface design, 2.4 no throat-clearing | 3 |
| 3 Design | 3.2 info density, 3.3 physical obviousness, 3.5→5 dark patterns (moved), 3.6 design consistency, 3.7 self-evident UI, 3.8 modals (hostile only), 3.9 a11y basics | 6 |
| 4 Craft | 4.1 opinionated, 4.3 shipped ready, 4.7 show me the code | 3 |
| 5 Conduct | 5.1 access gates, 5.2 manufactured urgency, 5.3 nag/reengagement, 5.4 attention harvesting, 5.5 privacy composite, 5.6 RSS [if:content], 5.7 cancel/leave, 5.9 double-dipping, 5.10 coercion, 3.5 dark patterns (moved here) | 10 |
| 6 Sovereignty | 6.1 rugpull, 6.2 exit cost, 6.3 identity, 6.4 protocol vs platform, 6.6 self-hostable, 6.10 privacy payment, 6.11 source availability + conditionals | 7+ |
| 7 Honesty | 7.1 business model, 7.2 marketing exaggeration, 7.3 AI disclosed, 7.7 degraded free experience | 4 |
| 8 Economic | 8.1 native money vs ads, 8.2 pay per service, 8.4 no coerced upsells | 3 |
| **Total** | | **~39 + conditionals** |

### What defers to V2
- MEDIUM/LOW-MED checks (distinctive voice, writing shows study, mid-curve convergence, etc.)
- Multi-agent consensus scoring
- Radar chart visualization
- Builder self-audit mode
- Automated CSS/text scanning agents
- Additional calibration products (Signal, sloppy Nostr client, Linear)
- Full 55-check inventory

---

## PRDs & IMPLEMENTATION PLANS

Detailed PRDs for all 7 slices live in a companion file:
**`/Users/profile_1/.claude/plans/tidy-stargazing-steele-agent-a21473c37c9fc4d9b.md`**

1,617 lines. Each slice has: Objective, Inputs, Deliverables, Steps, Acceptance Criteria, Dependencies, Estimated Time.

```
V1 (Check Inventory) ──────┐
                            ├──→ V4 (Skill + Scoring) ──→ V5 (Calibration) ──→ V6 (Framework Doc) ──→ V7 (Ship)
V2 (Scale Anchors)   ──────┤
V3 (Detection Ref)   ──────┘
```

Total estimated: 8-10 hours across 2-3 sessions.

**IMPORTANT**: Both plan files (.claude/plans/) are EPHEMERAL. Must be copied to `~/Coding/sloppypasta-audit/docs/plans/` and git committed before /clear or session end.

---

## FORMAL SHAPING

### Fit Check: R × Selected Shape

| Req | Requirement | Status | V1 (39 HIGH checks) |
|-----|-------------|--------|---------------------|
| R0 | Detect AI slop (text, visual, behavioral) | Core goal | ✅ Cat 1 (3 checks) + detection reference lists |
| R1 | Measure sovereignty/privacy alignment | Core goal | ✅ Cat 6 (7+ checks) + Cat 5 (10 checks) |
| R2 | Repeatable scores | Must-have | ✅ All V1 checks are HIGH measurability = near-binary |
| R3 | Lean measurable over subjective | Must-have | ✅ MEDIUM/LOW deferred to V2 |
| R4 | Wise sage tone | Must-have | ✅ Deferred to framework doc copy (Phase 6) |
| R5 | Support diverse product types | Must-have | ✅ Conditional activation handles type differences |
| R6 | Two audit modes | Must-have | ❌ V1 = external only. Builder mode = V2. |
| R7 | Conditional check activation | Must-have | ✅ [if:payments/identity/messaging/social/mobile/content] |
| R8 | Scale differentiates meaningfully | Must-have | ✅ Geomean + 5% floor. Validated via 2-product calibration. |
| R9 | Framework passes own test | Must-have | ✅ Clean framework doc in Phase 6. Copy LAST. |
| R10 | Writing as standalone dimension | Must-have | ✅ Cat 2 (3 checks including promoted 2.1) |
| R11 | Product craft as standalone dimension | Must-have | ✅ Cat 4 (3 checks) |
| R12 | Economic alignment as dimension | Must-have | ✅ Cat 8 (3 checks) |
| R13 | Automated detection where possible | Nice-to-have | ❌ V1 = agent-scored. Text scanner automation = V2. |
| R14 | Radar chart + improvement roadmap | Nice-to-have | ❌ V1 = scorecard + improvement list. Radar = V2. |
| R15 | Product-only scope | Must-have | ✅ No company-level signals |

**Result: 12 ✅, 3 ❌ (all Nice-to-have or explicitly deferred to V2). Shape passes.**

### Parts Table

| Part | Mechanism | Flag |
|------|-----------|:----:|
| **P1** | **Check inventory cleanup** — resolve 5 overlaps, add conditional tags, restore 3 lost V1 checks, finalize ~39 check list | |
| **P2** | **Scale anchor docs** — 0/25/50/75/100 behavioral descriptions for each V1 check. Extremes first, midpoint second. One file per category. | |
| **P3** | **Scoring spec** — geomean formula, 5% floor, weight vector, N/A handling (exclude + redistribute weight), grade boundaries (set after calibration) | |
| **P4** | **Detection reference** — banned words (49), banned phrases (38), banned openers (16), punctuation thresholds, visual slop markers, behavioral tells. Self-contained, no external deps. | |
| **P5** | **SKILL.md** — single-agent audit flow: gather product → score checks per category → compute scores → render markdown report with improvement suggestions | |
| **P6** | **Calibration** — run on 2 products (expected-high + expected-low), validate directionality, adjust anchors/weights if absurd | |
| **P7** | **Framework doc** — public-facing synthesis.md. Clean, every word earned. Includes: philosophy, categories, checks, scoring, how-to-run. | |
| **P8** | **Repo packaging** — README, LICENSE (MIT), directory structure, vault captures, git push | |

### Slices (Vertical, Each Demo-able)

| Slice | Parts | Demo Output | Est. Time |
|-------|-------|-------------|-----------|
| **V1: Check Inventory** | P1 | Clean check list document — 39 checks, overlaps resolved, conditionals tagged | 30 min |
| **V2: Scale Anchors** | P2 | 8 anchor files (one per category) with 5-level scales for every check | 2-3 hr |
| **V3: Detection Reference** | P4 | Self-contained reference docs: slop-markers.md, sovereignty-checks.md, visual-markers.md | 1 hr |
| **V4: Skill + Scoring** | P3, P5 | Working SKILL.md that runs on a URL and outputs scored markdown report | 2 hr |
| **V5: Calibration** | P6 | Two complete audit reports (Boris + Twitter/X), weights validated | 1 hr |
| **V6: Framework Doc** | P7 | synthesis.md V3 — the public-facing document | 1 hr |
| **V7: Ship** | P8 | Public GitHub repo with README, pushed and posted on Nostr | 30 min |

---

# Sloppypasta Audit — Criteria Co-Design (Session 4)

## Context

Session 3 captured all source material (30+ vault notes, 112 heuristics) and attempted a framework that was rejected: "The test itself is reading as sloppypasta." The math is fine (geomean, 0-100%). The criteria themselves need collaborative redesign.

This session: cluster the 112 raw heuristics organically, anchor on the sloppypasta articles, then evaluate each cluster for inclusion in the audit — together.

---

## Heuristic Clusters (Anchored on Sloppypasta Articles)

Organized by distance from the core. Each cluster groups heuristics that *want* to be together — not forced.

### CORE: From the Sloppypasta Articles Themselves

These clusters emerge directly from "Caring about Sloppypasta," stopsloppypasta.ai, and "The Internet Left Me."

---

**C1. Care Detection — "Did someone give a damn?"**
The central thesis. Humans detect AI slop as *absence of care*. Not bad grammar, not factual errors — the pattern is that nobody stood behind this.
- H-064: Zero effort in → generic output out
- H-065: Anything worth anything took thousands of iterations with human thought
- H-067: Things done "on the side" are by definition done without care
- H-075: What is the ONE craft being mastered?
- H-077: AI-assisted (starting point for refinement) vs AI-generated (done) — the slop binary
- H-079: Quality at small scale, earned expansion
*Source weight: Gigi 70%, 37signals 30%*

**C2. LLM Smell — "You can tell"**
The detectable surface markers. Not the deepest test, but the most immediate one.
- H-059: Negation structures, em-dashes, rhythm shifts, false emphasis
- H-060: One-shot prompts produce "mid" output — LLMs are middle-of-the-curve machines
- H-062: Visual monoculture — vibe-coded apps all look the same
- H-101: Unchecked LLMs converge on JS/Reddit/SO conventions regardless of specs
*Source weight: Gigi 100%*

**C3. Writing Is Thinking — "You skipped the hard part"**
The effort asymmetry argument. Pasting raw output shifts YOUR cognitive work to the reader.
- H-069: Sender 10 seconds, recipient vets a wall of generic text
- H-070: Writing forces comprehension; skip writing, skip thinking
- H-074: Text used to carry innate proof-of-thought — a basic token of humanity
- H-072: Sharing raw AI output burns credibility — Boy Who Cried Wolf
- H-073: LLM verbosity increasing over time, worsening the asymmetry
*Source weight: stopsloppypasta.ai 80%, Gigi 20%*

**C4. Trust Erosion — "Now I have to verify everything you send me"**
The downstream consequence of slop at scale.
- H-071: LLM output = hallucination risk; all AI correspondence must be untrusted by default
- H-082: Each abstraction layer inherits trust debt from below
- H-085: Auto-generated tests are equally untrustworthy when the codebase itself is compromised
*Source weight: stopsloppypasta.ai 40%, Zechner 40%, Gigi 20%*

**C5. Wisdom vs Intelligence — "Smart but insufferable"**
LLMs are pattern matchers, not meaning makers. Smart without care = sycophancy.
- H-066: Smart without care produces "You're absolutely right!" sycophancy
- H-068: Pattern matching ≠ genuine understanding
- H-054: LLMs can build understanding OR bypass understanding — choose
*Source weight: Gigi 60%, Vervaeke 40%*

**C6. Monoculture — "Everything looks the same because nobody chose"**
The aesthetic collapse. When nobody makes deliberate choices, you get statistical averages.
- H-062: Visual monoculture parallels content monoculture (also in C2)
- H-060: Mid-curve regression — without direction, convergence on convention
- H-063: Counter-thesis: slop overabundance will force authenticity to the surface
*Source weight: Gigi 100%*

---

### INNER RING: Directly Related (Craft, Quality, Discipline)

These extend the core thesis into "how do you actually build things that aren't slop?"

---

**C7. Iteration Discipline — "How many rounds did this take?"**
The operational expression of care. Not "did you use AI?" but "did you iterate?"
- H-057: Thousands of iterations with human care — tool is AI, craft is human
- H-100: Dialogical development (question-first prompting) beats directive prompting
- H-105: Screenshots fed into multimodal agents — visual feedback loops
- H-065: (also in C1) — iteration depth as care proxy
*Source weight: Gigi/Boris 100%*

**C8. Restraint Over Feature Sprawl — "What did you say no to?"**
The 37signals contribution. Good products are defined by what they leave out.
- H-076: Features as proof of capability = slop. Restraint as proof of taste = craft.
- H-080: "Does this feature add craft or dilute focus?"
- H-075: (also in C1) — ONE craft being mastered
*Source weight: 37signals 70%, Gigi 30%*

**C9. Friction as Feature — "The hard part is the good part"**
Removing all friction removes understanding. Key management, explicit choices, manual review — these aren't bugs.
- H-033: Intentional friction makes users think
- H-088: Architecture, API, system gestalt should be written by humans
- H-054: (also in C5) — build understanding, don't bypass it
- H-102: "Just one more prompt" loop is addictive — knowing when to stop is the hardest skill
*Source weight: Zechner 40%, Gigi 40%, SovEng 20%*

**C10. Agent Discipline — "Did you leash the machine?"**
Specific to AI-assisted building. Not anti-AI, but pro-discipline.
- H-083: Agent errors compound — no human bottleneck means no pain feedback
- H-084: Agents have zero learning ability — repeat same errors indefinitely
- H-086: Agentic search has fundamentally low recall — bigger codebases = more duplication
- H-087: Good agent tasks: narrowly scoped, closeable, not mission-critical
- H-090: Orchestrated swarms remove human from loop — pain arrives too late
- H-078/H-089: Limit generation to what you can actually review
*Source weight: Zechner 70%, Gigi 30%*

**C11. Builder Accountability — "Who made this?"**
Can you find the human behind the product? Is their reputation staked?
- H-035: Builder identity and reputation staked on the product
- H-006: Demo Day forces honest self-assessment — shipping publicly
- H-104: Vibe-coding removes you from writing code but NOT from the subject matter
*Source weight: Gigi 60%, SovEng 40%*

**C12. Ship Ugly, Iterate Publicly — "Perfect is the enemy"**
Not contradicting care — complementing it. Ship imperfect WITH care, then improve.
- H-002: Working code shipped imperfectly beats perfect spec that never ships
- H-004: Chase 80-20; last 20% waits until idea survives contact with reality
- H-008: Start ugly, ship weekly, invite the world's critique
*Source weight: SovEng manifesto 100%*

---

### OUTER RING: Sovereignty, Economics, Architecture

These are the broader "internet philosophy" that the sloppypasta audit also wants to measure — the structural conditions that produce or prevent slop.

---

**C13. Rugpull Resistance — "Can this be taken away?"**
THE sovereignty test. If betrayal is technically possible, the system isn't sovereign.
- H-001: If operator betrayal is possible, not sovereign
- H-052: Without final settlement, you're on credit; they can deplatform you
- H-055: Frame as "can this be rugpulled?" not "do I own this?"
- H-110: "Don't be evil" fails; "can't be evil" (protocol enforcement) works
*Source weight: SovEng manifesto 40%, Gigi 60%*

**C14. Exit Cost Zero — "Can you leave?"**
Data portability, identity portability, social graph portability.
- H-003: Verify, fork, exit — non-negotiable rights
- H-031: Data flows freely in and out, no lock-in
- H-034: Can you take your data, identity, social graph?
- H-040: Content readable/exportable without platform (RSS, Nostr, markdown)
- H-043: Content moves between clients without lock-in
*Source weight: SovEng 30%, Gigi 70%*

**C15. Identity Sovereignty — "Keypair > Account"**
No accounts is ideal. Pseudonymity is essential. Government ID is always worst score.
- H-042: Identity without platform permission — keypair > account
- H-061: Pseudonymity should still be usable (litmus test for surveillance)
- H-112: Convenience infrastructure becomes oppression under different leadership
*Source weight: Gigi 100%. User preference: very strong.*

**C16. Surveillance & Chilling Effect — "Are you afraid to speak?"**
Privacy as precondition for all other freedoms.
- H-024: Active seeking vs passive algorithm-fed consumption
- H-026: Deplatforming/demonetization creates fear of expression
- H-050: Control the algorithm = control what people see
*Source weight: Gigi 80%, SovEng 20%*

**C17. Protocols Not Platforms — "Speakers, not users"**
The architectural ideal. Platforms centralize; protocols liberate.
- H-011: Does it depend on a single corporate API? (Substrate neutrality)
- H-013: Unix-pipe composability vs monolithic system
- H-019: Open networks improve each other emergently
- H-097: "A new platform doesn't fix this" — only protocols do
*Source weight: Gigi 80%, SovEng 20%*

**C18. V4V vs Attention Economy — "How does it make money?"**
Products without native money eventually become parasitic.
- H-025: Monetize through direct value exchange, not ads/attention
- H-096: Sats cannot be faked the way views/likes can — unforgeable value signal
- H-044: Does it reward discovery/curation, not just creation?
- H-045: Freely accessible with optional V4V, no paywalls
*Source weight: Gigi 90%, SovEng 10%. User: PPQ.AI as ideal, bus ticket OK, Netflix inertia billing bad.*

**C19. Information Calories — "Is this feed a slot machine?"**
Content quality, density, and respect for attention.
- H-020: Single-post-per-screen = slot machine. Multiple items = respects cognition.
- H-021: Engagement bait vs nutritious content (long-form, expert, curated depth)
- H-023: Maximize time-on-platform vs respect user's time
- H-029: Signal about nutritional value — can users distinguish depth from junk?
- H-030: Does it encourage creation as much as consumption?
*Source weight: Gigi/SovEng 80%, 37signals 20%*

**C20. Content Provenance — "Who signed this?"**
Cryptographic identity as antidote to slop. Not content filters — identity-grounded provenance.
- H-010: Can content be cryptographically signed by its creator?
- H-014: Can the user verify what knowledge sources were consulted?
- H-015: Does it distinguish human-created from AI-generated?
- H-047: Can you verify effort behind content? PoW > authority
- H-049: Verifiable timestamps for authenticity
*Source weight: Gigi 100%*

**C21. Self-Hosting & Verification — "Can you run your own?"**
The operational expression of sovereignty. Not everyone will, but the option must exist.
- H-032: Can users run their own instance, host their own data?
- H-058: Can users search their own content without a central index?
- H-106: Verification requires nothing outside the data itself
- H-108: Self-sovereignty requires holding your own keys, running your own node
*Source weight: Gigi/SovEng 50/50*

**C22. Transparency of Purpose — "Why does this exist?"**
The builder must be able to articulate purpose beyond growth/engagement.
- H-022: Can the builder articulate WHY beyond engagement/growth?
- H-028: (overlaps H-022) Teleological clarity
- H-041: Can users see where money goes? Payment splits visible?
- H-027: If AI is used, is it grounded in verifiable data?
*Source weight: Gigi/SovEng 70%, 37signals 30%*

**C23. Addiction Resistance — "Does it respect your time?"**
Freedom FROM Tech. The most respectful product is one you open, use, close.
- H-023: (also in C19) Time-on-platform maximization vs respect
- H-009: (A-009) Freedom Tech implies Freedom FROM Tech
*Source weight: Gigi 100%*

---

### PERIPHERY: Deep Crypto / Meta-Philosophical

These are valid but potentially too niche or abstract for a general product audit.

---

**C24. Proof of Work as Truth — "Unforgeable history"**
Bitcoin-specific. PoW bridges math and physics. Relevant? Or too deep for a product audit?
- H-107: Removing PoW reintroduces all Bitcoin's solved problems
- H-109: Accumulated PoW solidifies the past like "layers of amber"
- H-111: 9000 altcoins prove crypto ≠ monetary soundness
*Source weight: Gigi 100%*

**C25. Sound Money as Foundation — "Bitcoin is the base layer"**
Is this a product audit criterion or a philosophical axiom?
- H-007: Sound monetary foundation as moral imperative
- H-099: Digital content has zero marginal cost — can't sustain market price traditionally
*Source weight: Gigi 100%*

**C26. Speech-Money-Property Triad — "Restrict one, restrict all"**
Powerful concept but maybe too abstract to score.
- H-053: Controlling money, speech, or property gives control over the others
*Source weight: Gigi 100%*

**C27. Punctuated Equilibrium / Systems Collapse — "Thresholds, not timelines"**
Vervaeke's contribution. Meta-level: how we think about AI growth claims.
- H-091: Hyperbolic growth = punctuated equilibrium, not unlimited exponential
- H-092: System interactions grow exponentially until self-management = original problem
- H-093: Self-monitoring creates infinite regress
- H-094: Identify decision points where we can steer
- H-095: "Genuinely ignorant about how emergent properties arise"
*Source weight: Vervaeke 100%*

**C28. Personal Responsibility — "Sovereign means accepting risk"**
The philosophical foundation: freedom comes with responsibility.
- H-038: Sovereign systems require accepting some risk for freedom
*Source weight: SovEng 100%*

**C29. Build for Decades — "7-generation thinking"**
Long-term framing. Antifragile tooling, battle-tested primitives.
- H-005: Build for decades, not quarters
- H-039: Technology decisions with 7-generation consequences in mind
*Source weight: SovEng manifesto 70%, Gigi 30%*

---

---

## REVISED CATEGORY STRUCTURE V1 (Superseded by V2 below)
NOTE: Kept for reference. Scroll to V2 for current.

Based on user feedback: Writing & Product Craft each deserve standalone categories. Product Hygiene collects the measurable don'ts. Periphery (C24-C29) dropped — too abstract for product audit. Openness and Wisdom & Restraint absorbed into other categories.

### Category 1: Content Integrity — "Is this slop?"
*The core sloppypasta test. First thing auditors look at.*

| Check | What it measures | Measurability |
|-------|-----------------|---------------|
| LLM smell markers | Negation structures, em-dashes, sycophantic hedging, rhythm uniformity | Medium — pattern detection, automatable |
| Proof of thought | Does the text carry evidence of human thinking? Not just correct — considered. | Low-medium — requires reading |
| Someone stood behind it | Named author, corrections acknowledged, builder identity staked | High — presence/absence |
| Provenance traceable | Signed, timestamped, attributed content | High — verifiable |
| Care visible | Iteration depth, polish, attention to detail vs "shipped and forgot" | Medium — observable signals |
| Mid-curve check | Does everything converge on generic convention, or is there distinctiveness? | Medium — comparison against norms |

*Sources: Gigi (caring-about-sloppypasta, internet-left-me, stopsloppypasta), Zechner*

---

### Category 2: Writing & Communication — "Does the writing show thinking?"
*Standalone per user. Writing quality IS product quality. 37signals: "hire the better writer." Clear writing = clear thinking.*

| Check | What it measures | Measurability |
|-------|-----------------|---------------|
| Economy of words | Every sentence earns its place. No filler, no padding, no wall-of-text | Medium — word/insight ratio |
| Copy is interface design | Button labels, error messages, onboarding text — are these designed or defaulted? | High — read the UI |
| No weasel words | "Just", "simply", "it's worth noting", "moreover" — masks for vague thinking | High — word list, automatable |
| Authentic social presence | Is social media run by humans or bots/agencies? Real engagement or broadcast? | Medium — pattern detection |
| Marketing as enthusiasm transfer | Does marketing feel like genuine excitement or manufactured urgency? | Low-medium — judgment call |
| No throat-clearing | Opens with insight/stakes, not "In a recent development..." preamble | High — read first sentences |

*Sources: 37signals (Wordsmiths, Copywriting is Interface Design, How We Communicate, Writing Craft for LLM Voice), stopsloppypasta (writing-is-thinking), Gigi*

---

### Category 3: Product Craft — "Less is more"
*Standalone per user. The Satoshi principle: deep study → elegant minimal solution. Build half that kicks ass.*

| Check | What it measures | Measurability |
|-------|-----------------|---------------|
| Opinionated software | Takes a side. Not 47 toggles and "customize everything." Has a vision. | Medium — feature/config count |
| Half, not half-assed | Few features done well vs many done poorly. The 80/20 reframe. | Medium — feature completeness audit |
| Aerodynamic product | No drag. No burrs. Everything essential, nothing extraneous. | Medium — identify orphaned features |
| Restraint visible | What did they say NO to? Can you tell what was deliberately left out? | Low-medium — requires judgment |
| Craft mastery over expansion | Same few things done right in different ways. Knives, not battleships. | Medium — scope history |
| Constraints embraced | Built with limited resources and it shows as focus, not as poverty | Low — context-dependent |
| Build for decades | Will this work in 10 years? Antifragile dependencies, simple primitives. | Medium — dependency audit |

*Sources: 37signals (Getting Real — Build Less, Half Not Half-Assed, Start With No, Opinionated Software, Enough Is Enough), Gigi (agentic craft thesis), SovEng manifesto*

---

### Category 4: Product Hygiene — "The measurable don'ts"
*Specific, concrete, binary-ish tests. The least subjective category. Connected to "less is more" — absence of bad behavior IS good design.*

| Check | What it measures | Measurability |
|-------|-----------------|---------------|
| No access gates | No paywalls, email-harvesting modals, forced signups to view content | High — try to use it |
| No dark patterns | Cancel in one click, no guilt modals ("Are you SURE?"), no trick UI | High — interaction test |
| No manufactured urgency | No countdown timers, no "X people viewing", no artificial scarcity | High — visual scan |
| No nag/re-engagement | No pushy emails after signup, no "we miss you" drip campaigns | High — sign up, wait, observe |
| No surveillance by default | No tracking, analytics, fingerprinting without consent. Privacy = default. | High — inspect network, check policies |
| No growth-hack language | No "AI-powered revolutionary 10x" — authentic, not performing growth | High — read landing page |
| No orphaned features | No settings nobody uses, screens nobody visits, options "just in case" | Medium — feature audit |
| RSS or equivalent | Syndication without an account — basic interoperability | High — check for feed |

*Sources: cross-cutting. 37signals (Start With No — orphaned features), Gigi (paywalls, surveillance), user preferences (access gates, dark patterns)*

---

### Category 5: Sovereignty & Privacy — "Can they rugpull you?"
*The structural test. Your audience knows this matters — the audit quantifies how well they're doing it.*

| Check | What it measures | Measurability |
|-------|-----------------|---------------|
| Rugpull resistance | Can the operator lock you out, change terms, or seize assets? | High — contractual/technical analysis |
| Exit cost zero | Portable data in standard formats. Take everything with you. | High — try to export |
| Identity sovereignty | Keypair ideal → minimal account OK → email required = worse → gov ID = always lowest | High — signup flow |
| Protocol vs platform | Built on open protocols or proprietary lock-in? | High — architecture review |
| Algorithm control | Visible, modifiable feed/ranking, or opaque black box? | High — check settings/docs |
| Self-hostable or auditable | Can you run your own instance, or at minimum read the source? | High — check license, docker, docs |

*Sources: Gigi/SovEng (manifesto, ep08, freedom-money, true-names), user calibration (gov ID always worst, PPQ.AI ideal)*

---

### Category 6: Honesty & Transparency — "Does it tell you the truth?"
*Business model, purpose, AI use, limitations — all visible.*

| Check | What it measures | Measurability |
|-------|-----------------|---------------|
| Business model visible | If not obvious in 30 seconds, you're the product | High — visit pricing page |
| Teleological clarity | Builder can articulate WHY this exists beyond "growth" | Medium — read about page, mission |
| AI disclosed and labeled | When AI is used, it's transparent. Not passed off as human. | High — check for disclosure |
| Honest about limitations | Acknowledges what it doesn't do. No "everything for everyone." | Medium — read marketing claims |
| Profit as sovereignty | Independent/profitable vs VC-dependent? Financial sustainability visible? | Medium — check funding, business model |

*Sources: Gigi (ep06 teleology, ep08 knowledge transparency), 37signals (Why We Choose Profit, business model clarity)*

---

### Category 7: Economic Alignment — "Who captures the value?"
*How value flows. V4V ideal, pay-per-service acceptable, attention extraction = lowest.*

| Check | What it measures | Measurability |
|-------|-----------------|---------------|
| Native money vs ads | Monetizes through direct value exchange (sats, pay-per-use) or attention/ads? | High — check revenue model |
| Pay per service | PPQ.AI model ideal. Subscriptions honest when bus-ticket, theft when inertia-billing. | High — check pricing structure |
| Creator value flows through | Platform doesn't extract all value. Creators/contributors are compensated. | Medium — check revenue split, terms |
| Earned audiences | Growth through genuine quality vs purchased/manufactured reach | Medium — check social presence, ad spend |
| Curation rewarded | Discovery and curation valued, not just raw creation | Low-medium — check incentive structure |

*Sources: Gigi (attention-terrible-currency, V4V, vision-value-enabled-web, purple-text), 37signals (profit, marketing as enthusiasm)*

---

## What Changed vs Rejected Framework

| Rejected V1 (8 categories, 47 checks) | Revised V2 (7 categories, ~45 checks) |
|----------------------------------------|----------------------------------------|
| Craft & Care (6 checks) — too broad | Split into 3 standalone: Writing, Product Craft, Product Hygiene |
| Voice & Humanity (4 checks) — vague | Absorbed into Writing & Communication (specific, measurable) |
| Wisdom & Restraint (4 checks) — hard to measure | Absorbed into Product Craft (restraint) and Content Integrity (wisdom) |
| Openness (5 checks) — overlapped Sovereignty | RSS/API → Product Hygiene; portability → Sovereignty |
| Vague checks like "editorial judgment visible" | Replaced with specific: "named author, corrections acknowledged" |
| Missing: social media authenticity, bot detection | Added to Writing & Communication |
| Missing: marketing honesty, earned audiences | Added to Honesty and Economic Alignment |
| Missing: orphaned features, complexity diagnostic | Added to Product Hygiene and Product Craft |

## Key Principles Applied
- **Lean measurable**: each check rated for measurability. High > Medium > Low priority.
- **Not maximalist**: scale for improvement, not pass/fail. 20→40 is hard. 80→100 is mythical.
- **Wise sage, not teenage dunker**: audit celebrates 50% and shows path to 70%.
- **Periphery dropped**: PoW-as-truth, sound money axioms, speech-money-property triad, punctuated equilibrium — valid philosophy but not product tests.

---

## REVISED CATEGORY STRUCTURE V2

User's intuitive slop-recognition model + cypherpunk voices + measurability focus.

### Design Principles
- **Repeatability**: same product → same score. Lean measurable. For subjective checks: dispatch specialized sub-agents with tight instructions (UX agent, accessibility agent, honesty agent, craft agent) to reduce variance.
- **Wise sage**: celebrate 50%, show path to 70%. Not dunking.
- **Cypherpunk-informed**: Snowden, Swartz, Barlow, Torvalds, Curry, Ulbricht, Assange, Calle, Pirate Bay — their tests added where missing.

---

### Cat 1: Slop Detection — "Can you smell the AI?"
*The surface test. What triggers the "this is generated" alarm in a human reader.*

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 1.1 | LLM smell markers in text | HIGH | Negation rewrites, em-dashes, sycophantic hedging, hedge words ("notably", "it's worth noting"), uniform rhythm. Automatable via pattern detection. |
| 1.2 | Visual monoculture | HIGH | Inter font, purple gradients, generic card grids, identical hero layouts. Automatable via screenshot comparison. |
| 1.3 | Mid-curve convergence | MEDIUM | Everything converges on generic convention. Does the product look/read like everything else? |
| 1.4 | Bot-generated engagement | HIGH | Social media replies from bots, agency-run accounts, manufactured community. Check reply patterns, account ages, human-readable engagement. |
| 1.5 | Dead internet signals | MEDIUM | Is the "community" real? Are engagement metrics from humans or synthetic? Ratio of real interaction to automated. |

*Cypherpunk addition: Dead internet test (Calle). Bot transparency (Gleason).*

---

### Cat 2: Writing & Thinking — "Does the text show a thinking human?"
*Writing IS thinking. 37signals: "hire the better writer." Gigi: "writing is the process of chiseling out understanding."*

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 2.1 | Economy of words | MEDIUM | Every sentence earns its place. Signal-per-paragraph ratio. No filler. Stephen King: "2nd draft = 1st draft minus 10%." |
| 2.2 | Copy is interface design | HIGH | Read button labels, error messages, onboarding text. Designed or defaulted? "Submit" vs "Save" vs "Update" is a design decision. |
| 2.3 | Proof of thought | MEDIUM | Text carries evidence of thinking — positions taken, trade-offs acknowledged, not just assertions. |
| 2.4 | No throat-clearing | HIGH | Opens with insight/stakes, not "In a recent development..." preamble. Check first sentences. |
| 2.5 | Distinctive voice | MEDIUM | Can you identify this product's writing from 5 anonymous samples? Or does it sound like every SaaS landing page? |
| 2.6 | Writing shows study | LOW-MED | The Satoshi quality: you can tell the author deeply understands the problem, not just the solution. |

*Sources: 37signals (Wordsmiths, Copywriting is Interface Design), stopsloppypasta.ai, Gigi.*

---

### Cat 3: Design & Interface — "Does the look show care?"
*NEW per user. Visual slop is distinct from text slop. Vibe-coded apps all look the same.*

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 3.1 | Visual distinctiveness | MEDIUM | Does it look like it was designed, or like it was prompted? Generic AI aesthetic = lowest score. |
| 3.2 | Information density | HIGH | Single-post-per-screen = slot machine. Multiple items visible = respects cognition. Measurable: items per viewport. |
| 3.3 | Physical obviousness | HIGH | Interface communicates function without instruction. Cuisinart test: can you use it with oven mitts? |
| 3.4 | Intentional hierarchy | MEDIUM | Visual hierarchy guides attention. Not everything screaming for attention at once. |
| 3.5 | No dark patterns in UI | HIGH | Trick UI, misleading buttons, forced paths, guilt modals ("Are you SURE you want to leave?"). Binary checks. |

*Sources: 37signals (Design Drives Behavior, Great Design is Physical Obviousness), Gigi (visual monoculture).*

---

### Cat 4: Product Craft — "Less is more"
*The Satoshi principle. Build half that kicks ass. Opinionated from study, not from preference.*

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 4.1 | Opinionated software | MEDIUM | Takes a side. Not 47 toggles. Has a vision. Feature count as signal — fewer + intentional > many + scattered. |
| 4.2 | Half, not half-assed | MEDIUM | Few features done well vs many done poorly. Core functionality polished vs everything rough. |
| 4.3 | Shipped ready | HIGH | Does the core workflow actually work? Bugs in primary path = shipped before ready. Testable: try the main flow. |
| 4.4 | Orphaned features | HIGH | Settings nobody uses, screens nobody visits, options "just in case." Dead pages, empty states never designed. |
| 4.5 | Aerodynamic | MEDIUM | No drag. No burrs. Everything essential, nothing extraneous. Can identify what was deliberately left out. |
| 4.6 | Build for decades | MEDIUM | Simple dependencies, standard protocols, no vendor lock-in in the stack itself. Dependency audit. |
| 4.7 | Show me the code (Torvalds) | HIGH | Source available, readable, honest code quality. Not vaporware. |

*Sources: 37signals (Getting Real), Gigi (agentic craft), Torvalds ("talk is cheap"), SovEng manifesto.*

---

### Cat 5: Product Conduct — "How does it behave?"
*Renamed from "Hygiene." Measurable behavioral tests. Connected to "less is more" — absence of bad behavior IS good design.*

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 5.1 | No access gates | HIGH | No paywalls, email harvesting, forced signups to view. Aaron Swartz: rent-seeking on knowledge is hostile. |
| 5.2 | No manufactured urgency | HIGH | No countdown timers, "X people viewing", artificial scarcity. Visual scan. |
| 5.3 | No nag/re-engagement | HIGH | Sign up, wait, observe. No "we miss you" drip, no notification spam. |
| 5.4 | No attention harvesting | HIGH | No infinite scroll without stopping points, no autoplay, no dopamine gamification of likes, no pull-to-refresh slot machine. Touch grass signal: product has natural endpoints. |
| 5.5 | No surveillance by default | HIGH | No tracking/analytics/fingerprinting without consent. Metadata collection (Snowden): even if you don't read content, collecting who/when/how-often is surveillance. |
| 5.6 | RSS or equivalent | HIGH | Syndication without an account. Basic interoperability. Swartz co-created RSS — a litmus test. |
| 5.7 | Cancel/leave in one click | HIGH | No guilt, no 12-step cancellation, no "talk to retention team." |
| 5.8 | Resilience to takedown | MEDIUM | Survives single server failure, single jurisdiction ban. No single point of failure. (Pirate Bay test) |

*Sources: cross-cutting. Swartz (open access), Calle (touch grass, dead internet), Snowden (metadata), Pirate Bay (resilience), user (attention harvesting patterns).*

---

### Cat 6: Sovereignty & Privacy — "Can they rugpull you?"
*Structural sovereignty. Exit, identity, ownership.*

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 6.1 | Rugpull resistance | HIGH | Can operator lock you out, change terms, seize assets? Contractual + technical. |
| 6.2 | Exit cost zero | HIGH | Export everything in standard formats. Try it. |
| 6.3 | Identity sovereignty | HIGH | Scale: keypair (best) → minimal account → email → phone → gov ID (always lowest). |
| 6.4 | Protocol vs platform | HIGH | Open protocols or proprietary lock-in? |
| 6.5 | Namespace independence | MEDIUM | Exists without gatekeepers. Not dependent on Apple/Google/Spotify index. (Adam Curry) |
| 6.6 | Self-hostable or auditable | HIGH | Run your own instance, or read the source. |
| 6.7 | Information asymmetry | MEDIUM | Product shouldn't know more about you than you know about it. (Assange: radical transparency for the powerful, privacy for the individual.) |
| 6.8 | Economic privacy | MEDIUM | Can you transact without revealing identity? (Ulbricht, Calle: ecash, Lightning, no KYC.) |

*Sources: Gigi/SovEng, Snowden, Assange, Ulbricht, Curry, Calle, Barlow.*

---

### Cat 7: Honesty & Transparency — "Does it tell you the truth?"
*Business model, marketing claims, AI disclosure, purpose. Marketing exaggerations = dishonest character.*

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 7.1 | Business model visible | HIGH | If not obvious in 30 seconds, you're the product. |
| 7.2 | No marketing exaggeration | HIGH | No "best since fire", no screaming YouTube thumbnails, no "AI-powered revolutionary 10x." Cheap exaggerations = crookiness signal. |
| 7.3 | AI disclosed and labeled | HIGH | When AI is used, it's transparent. Not passed off as human. |
| 7.4 | Marketing as enthusiasm transfer | MEDIUM | Genuine excitement vs manufactured hype. Authentic promotion vs growth-hack noise. (37signals: "false enthusiasm makes you a liar.") |
| 7.5 | Honest about limitations | MEDIUM | Acknowledges what it doesn't do. No "everything for everyone." |
| 7.6 | Earned audiences | MEDIUM | Growth through quality vs purchased reach. Check: are followers real? Is engagement genuine? |

*Sources: 37signals (marketing, profit), Gigi, Torvalds ("show me the code"), user feedback on marketing exaggeration.*

---

### Cat 8: Economic Alignment — "Who captures the value?"
*How value flows. V4V ideal, pay-per-service acceptable, attention extraction = lowest.*

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 8.1 | Native money vs ads | HIGH | Direct value exchange (sats, pay-per-use) or attention/advertising? |
| 8.2 | Pay per service | HIGH | PPQ.AI model ideal. Subscriptions: bus-ticket honest, Netflix inertia = theft. |
| 8.3 | Creator value flows through | MEDIUM | Creators/contributors compensated, not extracted. Check: revenue split, terms. (Adam Curry: value splits visible.) |
| 8.4 | No coerced upsells | HIGH | No forced upgrade paths, no "premium to continue." (Ulbricht: voluntary exchange.) |
| 8.5 | Curation rewarded | LOW-MED | Discovery and curation valued, not just raw creation. |

*Sources: Gigi (V4V, attention), 37signals (profit), Curry (value splits), Ulbricht (voluntary exchange).*

---

## Measurability Summary

| Rating | Count | Meaning |
|--------|-------|---------|
| HIGH | 28 | Binary or near-binary. Try it, scan it, check the page. |
| MEDIUM | 17 | Observable patterns with trained eye. Sub-agent specialization helps repeatability. |
| LOW-MED | 3 | Judgment-dependent. Needs strongest agent instructions + multi-agent consensus. |

**Repeatability strategy for MEDIUM/LOW checks**: Dispatch 2-3 specialized sub-agents (e.g., UX-focused, honesty-focused, craft-focused) with very specific rubrics. Each scores independently. Final score = median of agent scores. This reduces single-agent bias. Build the rubrics as skill reference files with calibration examples.

---

## Naming Check

| V1 Name | V2 Name | Why |
|---------|---------|-----|
| Content Integrity | Slop Detection | More direct. "Can you smell the AI?" |
| Writing & Communication | Writing & Thinking | "Writing IS thinking" — the core thesis |
| (missing) | Design & Interface | NEW — visual slop distinct from text slop |
| Product Craft | Product Craft | Kept — user approved |
| Product Hygiene | Product Conduct | "How does it behave?" — less clinical than hygiene |
| Sovereignty & Privacy | Sovereignty & Privacy | Kept |
| Honesty & Transparency | Honesty & Transparency | Kept + marketing claims added |
| Economic Alignment | Economic Alignment | Kept |

---

---

## V3 ADDITIONS (Post-Cypherpunk + UX + FU Patterns Discussion)

### Scope Decision: Product-only
Audit tests what you can observe by using, reading, and inspecting the product itself.
Company history, politics, lobbying, regulatory capture = out of scope.

### Cat 3: Design & Interface — V3 additions

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 3.6 | Design system consistency | HIGH | Coherent font families, color palette, weight hierarchy. Or every page different? |
| 3.7 | Self-evident UI / User control | HIGH | Usable without tutorial. No onboarding popups needed. Undo/go-back available. Not trapped in flows. |
| 3.8 | Modal-free experience | HIGH | Count: how many modals before you can use the product? Zero = ideal. |
| 3.9 | Accessibility basics | HIGH | Color contrast 4.5:1+, touch targets 56px+, screen reader labels, logical focus order. Automatable. |

### Cat 5: Product Conduct — V3 additions/strengthening

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 5.4 | (strengthened) No attention harvesting | HIGH | Explicitly: infinite scroll without stopping points, autoplay, dopamine gamification of likes, pull-to-refresh slot machine, touch-grass signal (natural endpoints). |
| 5.5 | (strengthened) No surveillance by default | HIGH | Explicitly includes: shadow profiling (tracking non-users via pixels/fingerprinting), metadata collection (who/when/how-often even without reading content). Inspect network requests for 3rd-party trackers. |
| 5.9 | No double-dipping | HIGH | Paid product = no ads. Ad-supported = acknowledge it. Paying AND being tracked/advertised to is hostile. |
| 5.10 | No product coercion | HIGH | No "download our app" banners, no nagging to switch browser/platform, no forced updates. Count nag prompts. |

### Cat 6: Sovereignty — V3 revisions

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 6.9 | Algorithm transparency & choice | MED-HIGH | Is feed algorithm visible? Can user choose/modify? Dorsey: "Algorithm choice is the North Star." Opaque = lowest. |
| 6.10 | (revised) Privacy-preserving payment available | HIGH | Accepts Lightning/crypto/ecash = privacy option exists. Credit-card-only = identity linked by default. Simple check: visit payment page. |

### Cat 7: Honesty — V3 addition

| # | Check | Measurability | Notes |
|---|-------|--------------|-------|
| 7.7 | No degraded free experience | HIGH | Free tier deliberately worsened to coerce upgrade? Time-to-paywall, content-before-wall ratio. |

---

## FINAL CATEGORY SUMMARY (V3)

| Cat | Name | Checks | Avg Measurability |
|-----|------|--------|-------------------|
| 1 | Slop Detection | 5 | MED-HIGH |
| 2 | Writing & Thinking | 6 | MEDIUM |
| 3 | Design & Interface | 9 | HIGH |
| 4 | Product Craft | 7 | MEDIUM |
| 5 | Product Conduct | 10 | HIGH |
| 6 | Sovereignty & Privacy | 10 | HIGH |
| 7 | Honesty & Transparency | 7 | HIGH |
| 8 | Economic Alignment | 5 | HIGH |
| **Total** | | **~59** | |

Note: 59 checks is higher than initial ~50 target. User said "quality not quantity" — trim in next phase if any feel redundant. Many of the new additions (3.9 accessibility, 5.9 double-dipping, 5.10 coercion) are highly measurable and non-overlapping.

---

## Resources to Capture (post-plan-mode)

1. **6 Core UX Principles**: https://medium.com/@silverskytechnology/6-core-principles-of-ux-design-b3e79118ab94
   → Vault note: consistency, hierarchy, user control, accessibility, usability, context
2. **"Fuck You" Patterns (HN thread)**: https://news.ycombinator.com/item?id=27666455
   → Vault note: 15 specific anti-patterns with measurability ratings, real-world examples

---

---

## PRODUCT SCOPE & AUDIT MODES

### Product Types Supported
| Type | Coverage | Notes |
|------|----------|-------|
| Web apps | Full (~95% of checks) | Primary target |
| Mobile apps | Full + app-specific checks | Sideloading, Play Services, push independence |
| Desktop apps | Full | Source availability, distribution |
| CLI tools | ~70% | No visual design checks; writing/craft/sovereignty still apply |
| Protocols/Libraries | ~60% | Docs, naming, architecture, sovereignty; no conduct/UI |

### Two Audit Modes
1. **External audit** — any user can run. Tests what's observable: UI, behavior, marketing, payment options, export, source availability, distribution. ~85% of checks.
2. **Builder self-audit** — run on your own codebase. All checks available, including internal code quality, dependency tree, telemetry implementation. 100% of checks.

### Conditional Check Activation
Checks tagged as conditional activate based on what the product does:
- **[if:payments]** — activates when product handles money (wallets, subscriptions, V4V)
- **[if:identity]** — activates when product manages user identity (login, profiles, keys)
- **[if:messaging]** — activates when product has communication features
- **[if:social]** — activates when product has community/social features
- **[if:mobile]** — activates for mobile/desktop app distribution

If a conditional check doesn't apply (static blog → key management), it's **excluded from the geomean** (N/A). If it applies and isn't fulfilled, it **penalizes the score**.

### App-Specific Checks (added to Cat 6: Sovereignty)

| # | Check | Condition | Measurability |
|---|-------|-----------|---------------|
| 6.11 | Source code availability | Universal | HIGH — FOSS (best) → source-viewable → proprietary free → proprietary paid (worst) |
| 6.12 | Distribution independence | [if:mobile] | HIGH — Sideloadable APK + F-Droid (best) → App Store + sideload → App Store only (worst) |
| 6.13 | No Google Play Services dep. | [if:mobile] | HIGH — Works on GrapheneOS/CalyxOS → requires Play Services (worst) |
| 6.14 | Push notification independence | [if:mobile] | MEDIUM — Works without Apple/Google push → requires their infrastructure |
| 6.15 | Key management sovereignty | [if:identity] | HIGH — NIP-07/NIP-46 signing (best) → app holds key with export → custodial (worst) |
| 6.16 | Relay/node independence | [if:messaging/social] | HIGH — Works with any relay/node → specific relays required |
| 6.17 | Custodial vs non-custodial | [if:payments] | HIGH — Non-custodial (best) → custodial with export → fully custodial (worst) |

---

## COMPLETE CHECK INVENTORY (V3 Final)

### Cat 1: Slop Detection — "Can you smell the AI?" (5 checks)
| # | Check | Measurability |
|---|-------|--------------|
| 1.1 | LLM smell markers in text | HIGH |
| 1.2 | Visual monoculture | HIGH |
| 1.3 | Mid-curve convergence | MEDIUM |
| 1.4 | Bot engagement (bots-as-bots OK, bots-pretending-human = bad) | HIGH |
| 1.5 | Dead internet signals / inflated metrics | MEDIUM |

### Cat 2: Writing & Thinking — "Does the text show a thinking human?" (6 checks)
| # | Check | Measurability |
|---|-------|--------------|
| 2.1 | Economy of words | MEDIUM |
| 2.2 | Copy is interface design | HIGH |
| 2.3 | Proof of thought | MEDIUM |
| 2.4 | No throat-clearing | HIGH |
| 2.5 | Distinctive voice | MEDIUM |
| 2.6 | Writing shows study | LOW-MED |

### Cat 3: Design & Interface — "Does the look show care?" (9 checks)
| # | Check | Measurability |
|---|-------|--------------|
| 3.1 | Visual distinctiveness | MEDIUM |
| 3.2 | Information density (items per viewport) | HIGH |
| 3.3 | Physical obviousness (usable without instruction) | HIGH |
| 3.4 | Intentional hierarchy | MEDIUM |
| 3.5 | No dark patterns in UI | HIGH |
| 3.6 | Design system consistency | HIGH |
| 3.7 | Self-evident UI / user control (no tutorial needed, undo/back available) | HIGH |
| 3.8 | Modal-free experience | HIGH |
| 3.9 | Accessibility basics (contrast, targets, screen reader) | HIGH |

### Cat 4: Product Craft — "Less is more" (7 checks)
| # | Check | Measurability |
|---|-------|--------------|
| 4.1 | Opinionated software | MEDIUM |
| 4.2 | Half, not half-assed | MEDIUM |
| 4.3 | Shipped ready (core flow works) | HIGH |
| 4.4 | Orphaned features | HIGH |
| 4.5 | Aerodynamic (nothing extraneous) | MEDIUM |
| 4.6 | Build for decades | MEDIUM |
| 4.7 | Show me the code (Torvalds) | HIGH |

### Cat 5: Product Conduct — "How does it behave?" (10 checks)
| # | Check | Measurability |
|---|-------|--------------|
| 5.1 | No access gates (no paywalls, forced signups) | HIGH |
| 5.2 | No manufactured urgency | HIGH |
| 5.3 | No nag/re-engagement / notification overload | HIGH |
| 5.4 | No attention harvesting (infinite scroll, autoplay, dopamine gamification, natural endpoints) | HIGH |
| 5.5 | Privacy & tracking cluster (see sub-checks below) | HIGH |
| 5.6 | RSS or equivalent | HIGH |
| 5.7 | Cancel/leave in one click | HIGH |
| 5.8 | Resilience to takedown (no single point of failure) | MEDIUM |
| 5.9 | No double-dipping (paid = no ads) | HIGH |
| 5.10 | No product coercion (no "download our app" nag) | HIGH |

**5.5 Privacy & Tracking Sub-Checks:**
| # | Check | Condition | Measurability |
|---|-------|-----------|---------------|
| 5.5a | Cookie count (zero ideal, first-party session OK, third-party = bad) | Universal | HIGH |
| 5.5b | Third-party tracker count (network inspector, zero = ideal) | Universal | HIGH |
| 5.5c | Analytics philosophy (none → self-hosted privacy → hosted privacy → GA → GA+multi) | Universal | HIGH |
| 5.5d | Cookie consent quality (no banner needed = best → reject-all prominent → accept-all dark pattern → content-blocked) | Universal | HIGH |
| 5.5e | Do-not-track / DNT respect | Universal | HIGH |
| 5.5f | Minimal permissions (only what's needed) | [if:mobile] | HIGH |
| 5.5g | Telemetry opt-in (not opt-out) | [if:mobile] | HIGH |
| 5.5h | No background data collection | [if:mobile] | MEDIUM |

### Cat 6: Sovereignty & Privacy — "Can they rugpull you?" (10 core + 7 conditional = 17 checks)
| # | Check | Condition | Measurability |
|---|-------|-----------|---------------|
| 6.1 | Rugpull resistance | Universal | HIGH |
| 6.2 | Exit cost zero | Universal | HIGH |
| 6.3 | Identity sovereignty (keypair→account→email→gov ID) | Universal | HIGH |
| 6.4 | Protocol vs platform | Universal | HIGH |
| 6.5 | Namespace independence | Universal | MEDIUM |
| 6.6 | Self-hostable or auditable | Universal | HIGH |
| 6.7 | Information asymmetry | Universal | MEDIUM |
| 6.8 | Economic privacy | Universal | MEDIUM |
| 6.9 | Algorithm transparency & choice | Universal | MED-HIGH |
| 6.10 | Privacy-preserving payment (crypto/Lightning) | Universal | HIGH |
| 6.11 | Source code availability | Universal | HIGH |
| 6.12 | Distribution independence | [if:mobile] | HIGH |
| 6.13 | No Google Play Services dep. | [if:mobile] | HIGH |
| 6.14 | Push notification independence | [if:mobile] | MEDIUM |
| 6.15 | Key management sovereignty | [if:identity] | HIGH |
| 6.16 | Relay/node independence | [if:messaging/social] | HIGH |
| 6.17 | Custodial vs non-custodial | [if:payments] | HIGH |

### Cat 7: Honesty & Transparency — "Does it tell you the truth?" (7 checks)
| # | Check | Measurability |
|---|-------|--------------|
| 7.1 | Business model visible | HIGH |
| 7.2 | No marketing exaggeration | HIGH |
| 7.3 | AI disclosed and labeled | HIGH |
| 7.4 | Marketing as enthusiasm transfer (not manufactured) | MEDIUM |
| 7.5 | Honest about limitations | MEDIUM |
| 7.6 | Earned audiences | MEDIUM |
| 7.7 | No degraded free experience | HIGH |

### Cat 8: Economic Alignment — "Who captures the value?" (5 checks)
| # | Check | Measurability |
|---|-------|--------------|
| 8.1 | Native money vs ads | HIGH |
| 8.2 | Pay per service (PPQ.AI ideal, bus-ticket OK, Netflix inertia = worst) | HIGH |
| 8.3 | Creator value flows through | MEDIUM |
| 8.4 | No coerced upsells | HIGH |
| 8.5 | Curation rewarded | LOW-MED |

### Totals
- **Universal checks**: 59
- **Conditional checks**: 7 (activate based on product type)
- **Max possible**: 66 (if all conditionals activate)
- **HIGH measurability**: 40 (~60%)
- **MEDIUM**: 20 (~30%)
- **LOW-MED**: 3 (~5%)

---

## SCORING METHODOLOGY (Confirmed)

- **Per-check**: 0-100% sliding scale. Zeros rare — reserved for actively hostile behavior.
- **Category score**: Geometric mean of applicable checks within category
- **Overall score**: Weighted geometric mean of category scores
- **Conditional checks**: N/A if product type doesn't activate them (excluded from geomean). Penalized if activated and not fulfilled.
- **Grade scale**: A (85-100), B (70-84), C (55-69), D (40-54), F (0-39)
- **Calibration target**: most real products land 20-80%. Hard to improve from 40→60. Nearly impossible to reach 100.

**Category weights**: TBD — next step after checks are validated.

---

## BEHAVIORAL TELLS → AUDIT CHECK INTEGRATION

The Gemini behavioral tells aren't just detection markers — they strengthen specific audit checks:

| Behavioral Tell | Integrates Into | How |
|----------------|----------------|-----|
| Dead-end empty states ("No items found", no CTA) | 3.7 Self-evident UI | Empty states ARE interface design. No CTA = no one used this. |
| Spinner trap (no optimistic UI) | 4.3 Shipped ready | If every action spinner-waits, no one tested the feel. |
| Brutal error handling ("Something went wrong") | 4.3 Shipped ready | Generic errors = no one triggered an error during testing. |
| Broken focus states (outline-none, no replacement) | 3.9 Accessibility basics | Keyboard nav destroyed. Automatable check. |
| Window resize break (~800px tablet) | 3.6 Design system consistency | THE quick check. If tablet breaks, AI generated it. |
| console.log("here") in production | 4.7 Show me the code (builder mode) | Debug remnants = shipped without review. |
| Placeholder data ("John Doe", "+20.1%") | 4.3 Shipped ready | Placeholder data in production = not finished. |
| Inline styles mixed with Tailwind | 4.7 Show me the code (builder mode) | Quick-patched instead of properly fixed. |

These don't create new checks — they make existing checks more specific and testable. The scale anchors for 3.7, 3.9, 4.3, and 4.7 should explicitly reference these as scoring examples.

---

## IMPLEMENTATION PLAN

### Phase 1: Capture remaining sources → Vault
**This is the first execution step. All resources read during brainstorm need permanent vault notes.**

9 resources to capture. Each becomes a vault note with heuristics extracted.

| # | Resource | URL | Key Content for Vault Note |
|---|----------|-----|---------------------------|
| 1 | 6 Core UX Principles | medium.com/@silverskytechnology/... | Consistency, hierarchy, user control, accessibility, usability, context. Accessibility filled Cat 3 gap. |
| 2 | Fuck You Pattern (original) | cedwards.xyz/the-fuck-you-pattern/ | Instagram login forcing + IP blocking. Calibration example for 5.1 (0% score). |
| 3 | Fuck You Patterns (HN thread) | news.ycombinator.com/item?id=27666455 | 15 anti-patterns: double-dipping, shadow profiling, coercion, degraded free, complex opt-out. |
| 4 | Anti-AI-Slop Writing (words) | github.com/jalaalrd/anti-ai-slop-writing | 49 banned words, 38 phrases, 16 openers. Core reference for Cat 1.1 text scanner. |
| 5 | Anti-AI-Slop Writing (skill) | (same repo, SKILL.md) | Structural patterns, punctuation limits, model-specific first-word fingerprints. |
| 6 | Purple Gradient Websites | prg.sh/ramblings/... | Tailwind bg-indigo-500 infection, visual markers: Inter, 3-col grid, hero+CTA, rounded corners. |
| 7 | AI Purple Problem | dev.to/jaainil/... | OKLCH alternatives, detection methods, brand-first approach. |
| 8 | Blue-Purple Gradients | medium.com/@kai.ni/... | Training data pollution framing, reinforcement loop, border-radius/icon biases. |
| 9 | Gemini Slop Detection Matrix | (user-pasted, no URL) | Shadcn/UI, Bento Box, glassmorphism, Lucide, whitespace homogeneity, Bold Prefix, behavioral tells, tool fingerprints. |

After capture: update MOCs, research Kaya Keshu / Cashu, verify all 30+ existing notes indexed.

### Phase 2: Scale anchors → Reference docs
For each check, define 0/25/50/75/100 with real product examples:
- 0% = actively hostile (Instagram fuck-you pattern for access gates)
- 25% = bad but not hostile (aggressive but skippable login wall)
- 50% = mediocre (account required, creation is minimal)
- 75% = good (account optional, most features work without)
- 100% = ideal (no login, content just works)

Write as `~/Coding/sloppypasta-audit/docs/scale-anchors/` — one file per category.

### Phase 3: Weight calibration
- Start with equal weights, run calibration on 5 products
- Adjust weights so results match intuitive ordering
- Products for calibration: Boris, Basecamp, Twitter/X, ChatGPT, ppq.ai

### Phase 4: Agent workflow design
For MEDIUM/LOW measurability checks:
- Design specialized sub-agent rubrics (UX agent, craft agent, honesty agent)
- Each agent gets specific instructions + calibration examples
- Final score = median of 2-3 agent scores (repeatability)
- Build as skill reference files in `~/Coding/sloppypasta-audit/agents/`

### Phase 5: Calibration runs
- Run full audit on 5 real products (external mode)
- Compare scores against intuitive expectations
- Iterate: any check that produces inconsistent scores → tighten rubric or reclassify measurability
- Builder self-audit mode: test on one FOSS product (Boris?)

### Phase 6: Framework document
- Write the final synthesis.md LAST
- Every word earns its place (the framework must pass its own test)
- Include: categories, checks, scale anchors, scoring math, calibration examples
- The HTML overview (framework-overview.html) gets rebuilt to match

### Phase 7: Skill creation
- Build `/sloppypasta-audit` skill via `/skill-creator`
- External mode: dispatch sub-agents for each category
- Builder mode: additional code-level checks
- Output: scored report with category breakdown + improvement suggestions

---

---

## AUTOMATED DETECTION REFERENCE (for Cat 1 + Cat 3 sub-agents)

### Visual Slop Markers (CSS/Layout Inspection)
Automatable via screenshot analysis + CSS inspection:
- Purple/indigo accent colors (`bg-indigo-*`, `#5E6AD2`-family) — Tailwind default infection
- Inter, Roboto, or generic system font only — no serif/sans pairing
- 3-column feature grid with centered icons — the SaaS template
- Hero: centered text + gradient + CTA button — same hierarchy everywhere
- Uniform rounded corners on all elements
- Subtle shadows at 0.1 opacity on all cards
- Dark base (#0A0A0A) + neon accent — the "Linear aesthetic"
- Gradient text headlines (blue-to-purple)
- No asymmetric or creative layouts anywhere

Source: [Why Your AI Keeps Building the Same Purple Gradient Website](https://prg.sh/ramblings/Why-Your-AI-Keeps-Building-the-Same-Purple-Gradient-Website), [AI Purple Problem](https://dev.to/jaainil/ai-purple-problem-make-your-ui-unmistakable-3ono). Adam Wathan's Tailwind `bg-indigo-500` infected the ecosystem.

### Writing Slop Markers (Text Analysis)
Automatable via word/pattern scanning:

**49 Banned Vocabulary**: delve, tapestry, landscape, testament, vibrant, pivotal, crucial, intricate, meticulous, bolster, garner, underscore, interplay, multifaceted, nuanced, foster, leverage, utilize, commence, facilitate, encompass, paramount, groundbreaking, cutting-edge, game-changing, transformative, revolutionise, seamless, robust, comprehensive, endeavour, aforementioned, harnessing, spearheading, navigating, showcasing, highlighting, emphasizing, enhancing, unprecedented, remarkable, stunning, profound, epic, thought leader, synergy, pain points, value add, moving forward, touch base

**38 Banned Phrases**: "In today's [adj] [noun]", "It's worth noting", "Not just X, but Y", "Let's dive in/deeper", "At its core", "In the realm of", "When it comes to", "A testament to", "This is where X comes in", "Whether you're a X or Y", "Unlock the power of", "Elevate your", "Streamline your", "Supercharge your", "Bridge the gap", "Move the needle", "Buckle up", "Take it to the next level", "Empower/empowering", plus more

**16 Banned Openers**: Certainly, Absolutely, Sure, Great question, That's a great point, I'd be happy to, However it's important to, Moreover, Furthermore, Additionally, Interestingly, Notably, Importantly, Indeed

**Punctuation Tells**:
- Em dashes: >1 per 500 words = AI tell (the single most cited marker)
- Exclamation marks: >1 per 1,000 words
- Rule of Three: AI defaults to exactly 3 items in lists
- Uniform sentence length: 3+ consecutive same-length sentences
- Hedging seesaw: "On one hand... on the other..." without taking a position

**Model-Specific First Words**:
- ChatGPT: as, yes, sure, here, in, to, creating, certainly
- Claude: in, from, this, how, yes, according, based
- Grok: step, introduction, yes, creating
- Gemini: my, creating, while, here
- DeepSeek: based, yes, step, comprehensive

Source: [anti-ai-slop-writing skill](https://github.com/jalaalrd/anti-ai-slop-writing) (jalaalrd, 35+ banned phrases, 49 banned words, 16 openers, 10 structural patterns)

### Visual Slop Markers — Gemini Additions
From Gemini cross-reference (complementing the above):
- **Shadcn/UI Default Aesthetic**: slate-900 buttons, `rounded-md` everywhere, zero token customization. "The new Bootstrap." Perfectly competent, completely soulless.
- **Grid Overuse (Bento Box Default)**: `grid-cols-1 md:grid-cols-3` for everything — even when a vertical list is more readable.
- **Gratuitous Glassmorphism**: `backdrop-blur-md bg-white/10` on elements that don't overlap anything interesting.
- **Lucide Icon Redundancy**: Unedited 2px stroke-width Lucide/Heroicon next to every single menu item or button, even when text alone suffices.
- **Whitespace Homogeneity**: Uniform `p-4`/`gap-4` everywhere. No optical grouping — tight header-paragraph coupling vs loose section spacing is a human design skill AI lacks.
- **Hidden Scroll (mobile)**: `scrollbar-hide` with zero visual affordance that content is scrollable (no partial item peeking from edge).

### Writing Slop Markers — Gemini Additions
- **"Bolded Prefix:" Bullet List**: THE #1 formatting tell. Every bullet: **Bold Summary Phrase:** followed by one sentence of explanation. Humans rarely do this outside rigid technical docs.
- **"Zoom Out" Opening**: Over-contextualizing macro-trends instead of getting to the point. ("In today's fast-paced digital landscape...")
- **Symmetrical Paragraphs**: Every paragraph exactly 3-4 sentences. Human writing is chunkier — massive block followed by single punchy sentence.
- **"Conclusion" Header**: Literal `## Conclusion` or `## Final Thoughts` header.
- **"Crucially"/"Importantly" Crutches**: Fake transition words when concepts don't logically flow.
- **Title Case Abuse**: Capitalizing concepts for authority ("Our Advanced Algorithm System").

### Interaction/Behavioral Slop Markers — NEW CATEGORY (Gemini)
These are tells in how AI-generated products BEHAVE, not just how they look:
- **Dead-End Empty State**: "No items found." — no illustration, no empathy, no CTA to create the first item.
- **No Optimistic UI (Spinner Trap)**: Every button click → loading spinner → server round-trip. Humans add optimistic updates; AI almost never does.
- **Brutal Error Handling**: Generic "Something went wrong" toasts, no context, no retry button.
- **Broken Focus States**: `focus:outline-none` without `focus-visible:ring` replacement — destroys keyboard navigation.
- **Window Resize Break**: THE most reliable single UI marker. Drag browser width slowly — tablet (~800px) breaks with squashed columns, overlapping text. AI optimizes for exactly 375px and 1440px only.

### Tool-Specific Fingerprints
- **v0 / Lovable**: Sterile. Placeholder data: "John Doe", "Jane Smith", dashboard metrics showing "+20.1% from last month." Default data viz = generic unreadable bar chart.
- **Cursor / Bolt.new**: `console.log("here")` or `console.error(err)` left in production. Inline `style={{ marginTop: '10px' }}` mixed into Tailwind codebase — agent patched visually instead of fixing root class.

### Single Most Reliable Marker (Quick Check)
- **Text**: The "Bold Prefix:" list structure. Genuine humans rarely format thoughts this rigidly.
- **UI**: The Window Resize Test. Slowly drag browser width. If tablet breaks, AI generated it.

### Automation Strategy
Both visual and writing slop detection can be **fully automated** as sub-agent tasks:
1. **CSS inspector agent**: fetch page, extract font-family, colors, border-radius, shadow values. Count purple/indigo instances. Detect 3-column grids.
2. **Text scanner agent**: scan all visible text. Count banned words/phrases/openers. Calculate em-dash density, sentence length variance, exclamation density.
3. **Output**: objective score per marker. No judgment needed for pattern matching.

This makes Cat 1 (Slop Detection) the most automatable category — approaching 90%+ HIGH measurability with these reference lists.

---

---

## EXPERT REVIEW FINDINGS (4 Reviewers)

### Cross-Cutting Consensus
- **3 agents minimum** for subjective checks (not 2). 20-point max spread threshold. Log disagreement.
- **~11 checks can be cut** via 4 overlap clusters (see below)
- **5% score floor** — never assign 0. Prevents single-zero catastrophic geomean failure.
- **Missing Phase 0**: product data acquisition pipeline (crawler, viewport screenshots, network capture)

### From Chief Architect
- Add `[audit:external]` / `[audit:builder]` tags per check
- Add conditions: `[if:content]`, `[if:desktop]`, `[if:developer-facing]`
- Cat 6 (17 checks) vs Cat 8 (5 checks) imbalance — consider 5.5 sub-checks as composite score
- N/A accumulation: minimum 3 active checks per category, else exclude category and redistribute weight
- Golden set of 3-5 products for drift detection

### From A11Y Expert — USER DECISION: Mostly rejected
The audit is about sloppypasta detection, not WCAG compliance. Opinionated software is not optimized for everyone.
- **REJECTED**: Expanding 3.9 into 4 checks, mobile a11y, motion safety, screen reader, manual checklist
- **ACCEPTED as slop markers (move to Cat 1 detection reference)**: broken focus states, heading jumps, div-soup with onClick, ARIA decoration — these are AI code tells, not accessibility features
- **KEPT**: 3.9 as single light check — basic accessibility signals care, not compliance

### From Chief UX
- **Reorder categories** to match audit workflow: Conduct → Design → Writing → Slop Detection → Craft → Honesty → Sovereignty → Economic
- **Rename**: Economic Alignment → "Value Flow"; consider Product Craft → "Builder Discipline"
- **6 ambiguous checks**: 1.3 (needs reference examples), 2.6 (needs specific indicators), 4.5 (merge into 4.2), 6.5 (rename from jargon), 6.7 (overlaps 5.5), 8.5 (make conditional)
- **Rewrite D/F grade descriptions** — sage tone, not punitive
- **Output format**: radar chart + improvement roadmap (sorted by impact) + full scorecard. Markdown file. No leaderboard.
- **Add "How to run this audit" preamble**
- Missing checks: first-run onboarding experience, error recovery/resilience

### From Product Scientist
- **Set weights from philosophy**, not intuition-matching. Use calibration to validate, not optimize.
- **Run sensitivity analysis** with 3-4 weight schemes before committing
- **Scale anchors**: behavioral descriptions first, product examples second. Anchor from extremes inward (0% and 100% first).
- **Set grade boundaries AFTER calibration distribution** — current A/B/C/D/F thresholds may not match reality
- **Add confidence flag per check**: HIGH/MEDIUM/LOW. Low confidence → exclude, not default 50%.
- **Track test-retest reliability** from day one. Target r > 0.85 overall.
- **Watch for bimodal distribution** — sovereignty-native vs mainstream might cluster at opposite ends with empty middle
- **Report applicable check count alongside scores**: "Sovereignty: 68% (13/17 checks applicable)"
- Ban word frequency should be relative (per 1000 words), not binary presence

### Overlap Clusters to Resolve
1. **Dark patterns** (3.5) → move to Cat 5 (Product Conduct). Design should measure visual quality, not behavioral ethics.
2. **Restraint** (4.1, 4.2, 4.4, 4.5) → merge 4.5 (Aerodynamic) into 4.2 (Half not half-assed). Same concept.
3. **Bot/audience** (1.4, 1.5, 7.6) → merge 7.6 (Earned audiences) into Cat 1 or consolidate with 1.4/1.5.
4. **Privacy overlap** (6.7 Information asymmetry) → overlaps 5.5 surveillance. Remove 6.7 or merge.
5. **8.5 Curation rewarded** → make [if:social] conditional (LOW-MED, usually N/A).

**Net effect**: ~66 → ~55 checks after resolving overlaps + expanding a11y.

---

## RESOURCES TO CAPTURE (Phase 1 of execution)
See Phase 1 table above — 9 resources, all read during brainstorm, none yet in vault.
All content is in this conversation's context. Capture can proceed immediately on plan approval.

---

## SESSION HANDOFF PROMPT

Copy this into a fresh Claude Code session to continue:

```
Continue building the Sloppypasta Audit — a public open-source product assessment framework for the Bitcoin/Nostr community. Builders run it on their own products and publish scores. Community members run it on third-party products for accountability.

## Where we are

Session 4 completed: brainstorm → clustering → expert reviews → shaping → slicing → PRDs. Zero code shipped yet. The shaping is done. Time to build.

## Key files to read FIRST

1. `~/Coding/sloppypasta-audit/docs/plans/2026-03-31-sloppypasta-audit-v3-shaping.md` — the full shaping doc (categories, checks, scoring methodology, expert review findings, V1 scope)
2. `~/Coding/sloppypasta-audit/docs/plans/2026-03-31-sloppypasta-audit-v3-prds.md` — detailed PRDs for all 7 implementation slices
3. `~/Coding/sloppypasta-audit/docs/synthesis.md` — the existing (rejected) V1 framework doc. Axioms are good, keep them. Checks and categories are superseded by V3.
4. Memory: `/recall sloppypasta` for project context and locked decisions.

## What to build (in order)

7 slices. V2 and V3 can parallelize. Rest is sequential.

V1: Check Inventory — resolve 5 overlaps, restore 3 lost checks, add conditional tags, filter to ~39 HIGH-measurability checks. Output: docs/check-inventory.md
V2: Scale Anchors — 0/25/50/75/100 behavioral descriptions per check. One file per category in docs/scale-anchors/
V3: Detection Reference — banned words, visual markers, sovereignty checks. Three files in docs/reference/
V4: Skill + Scoring — SKILL.md with single-agent audit flow + geomean scoring with 5% floor
V5: Calibration — run on Boris + Twitter/X, validate directionality
V6: Framework Doc — rewrite synthesis.md as public-facing document
V7: Ship — README, LICENSE, GitHub push, Nostr announcement

## Locked decisions (do NOT re-discuss)

- Scoring: geometric mean at both levels, 0-100% scale, 5% floor (never zero)
- V1 = HIGH measurability checks only (~39). MEDIUM/LOW = V2.
- Single-agent execution for V1. Multi-agent consensus = V2.
- Self-contained repo — no dependency on /design-review or /qa skills
- Product-only scope — audit the artifact, not the company
- Weights set from philosophy, validated (not optimized) against 2 calibration products
- A11y = single light check as slop marker, not WCAG compliance
- "Wise sage" tone — educate, not shame. Copy written LAST.

## Start with Slice V1 (Check Inventory)

Read the V1 PRD, execute it, commit the output. Then proceed to V2+V3 in parallel.
```
