---
title: "The Smell Test — Philosophical Framework for Evaluating Internet Products"
captured: 2026-03-30
tags: [bitcoin, nostr, sovereignty, writing, ai-agents, methodology, 37signals]
---

## Core Thesis

The internet's original sin was lacking native money. This forced attention to become the surrogate currency, spawning two failure modes: surveillance advertising (sell eyeballs) and subscription hell (sell access via credit IOUs). Both optimize for screen time over truth, producing walled gardens, algorithmic addiction, censorship, and — with LLMs — an avalanche of "sloppypasta" content generated without care. The antidote is not a better platform but a return to protocols: free speech protocols (Nostr) paired with free money protocols (Bitcoin/Lightning) enable products built on sovereignty, craft, and value alignment. A product either respects these principles or it participates in the decay.

## Axioms (Non-Negotiable Truths)

These are foundational beliefs from which all heuristics derive. They are not directly testable per product — they are the worldview.

**A1. Information wants to be free** — Digital content has zero marginal cost of reproduction. Paywalls and DRM fight the nature of information and lose. Products must work WITH this property, not against it. [[gigi-freedom-of-value-v4v-2021]]

**A2. Protocols have speakers; platforms have users** — Platforms can de-platform. Protocols cannot. Free speech platforms are an oxymoron. Only free speech protocols can guarantee expression. [[gigi-speaking-freely-protocols-vs-platforms-2024]]

**A3. Cryptography is necessary but not sufficient** — Keys handle private integrity. Proof-of-work handles public integrity. Without computational proof, you fall back to trusting authorities. [[gigi-cryptography-not-enough-2022]]

**A4. Monetary value is human action distilled** — Sats cannot be faked the way views, downloads, and comments can. "Talk is cheap. Sats are not." [[gigi-attention-terrible-currency-thread]]

**A5. Identity is prismatic** — Humans present differently across contexts. Forcing a single legal identity onto all interactions is surveillance, not identity. Pseudonymity is a feature, not a bug. [[gigi-true-names-not-required-pseudonymity-2020]]

**A6. Smart is not wise** — LLMs can pattern-match but cannot care. Caring requires embodiment, pain, desire, and mortality. Products that replace human judgment with LLM output produce "mid" content by definition. [[gigi-caring-about-sloppypasta-2026]], [[vervaeke-ai-coming-thresholds-2023]]

**A7. Freedom by design, not by policy** — "Don't be evil" fails. "Can't be evil" works. Liberty must be a property of the system, not a permission granted by an operator. Exit costs must approach zero. [[sovereign-engineering-philosophy-manifesto]]

**A8. Scope is the variable, not time** — Build less. Make opinionated software. Say no by default. Half, not half-assed. Constraint is a blessing, not a limitation. [[37signals-getting-real-key-chapters]], [[37signals-pod-say-no-by-default]]

---

## Heuristic Categories

### I. Content Integrity (Anti-Slop) — Weight: 20%

Does this product resist the flood of low-care, machine-generated content?

| # | Heuristic | Test | Sources |
|---|-----------|------|---------|
| CI-1 | **No detectable LLM smell** | Check for: negation structures, em-dash density, false emphasis, sycophantic patterns, "mid" authority voice | [[dergigi-internet-left-me-slop-sovereignty]], [[gigi-caring-about-sloppypasta-2026]] |
| CI-2 | **Human editorial judgment visible** | Is there evidence of curation, selection, editorial voice — not just aggregation? | [[37signals-writing-craft-for-llm-voice]], [[svn-deep-dive-editorial-voice-broadsheet]] |
| CI-3 | **Proof of care** | Did someone stand behind this content? Named author, iteration history, corrections? | [[gigi-caring-about-sloppypasta-2026]], [[37signals-pod-software-as-art]] |
| CI-4 | **Information density** | High signal-to-noise ratio? Or padded with filler, related articles, engagement bait? | [[sovereign-engineering-ep06-winds-of-ai]] (information calories) |
| CI-5 | **Provenance verifiable** | Can you trace content to its origin? Signed, timestamped, attributed? | [[sovereign-engineering-ep08-navigating-the-vibe]] (signed knowledge) |
| CI-6 | **No drive-by contributions** | If open-source: are AI-generated PRs filtered? Is maintainer craft protected? | [[tldraw-blocking-ai-contributions-2026]], [[gigi-caring-about-sloppypasta-2026]] |

### II. Sovereignty & Privacy — Weight: 20%

Does this product respect user autonomy and resist surveillance?

| # | Heuristic | Test | Sources |
|---|-----------|------|---------|
| SP-1 | **The rugpull test** | Can this product/platform rugpull its users? If yes, it fails sovereignty. | [[sovereign-engineering-philosophy-manifesto]], [[gigi-nostr-tier2-scan-heuristics]] |
| SP-2 | **Exit cost near zero** | Can you export your data, content, identity, relationships? In what format? | [[sovereign-engineering-philosophy-manifesto]], [[gigi-speaking-freely-protocols-vs-platforms-2024]] |
| SP-3 | **Pseudonymity supported** | Can you use the product without revealing your legal identity? No biometrics, no government ID? | [[gigi-true-names-not-required-pseudonymity-2020]] |
| SP-4 | **No surveillance by default** | Analytics, tracking pixels, third-party scripts? What data is collected and why? | [[dergigi-internet-left-me-slop-sovereignty]], [[gigi-attention-terrible-currency-thread]] |
| SP-5 | **Protocol-based, not platform-locked** | Built on open protocols (RSS, Nostr, ActivityPub, SMTP) or proprietary APIs? | [[gigi-speaking-freely-protocols-vs-platforms-2024]] |
| SP-6 | **User controls the algorithm** | Can users see, modify, or disable recommendation/ranking logic? | [[sovereign-engineering-ep06-winds-of-ai]] (feed=slot machine) |
| SP-7 | **Self-hostable or verifiable** | Can you run your own instance, or at minimum audit the code? | [[sovereign-engineering-philosophy-manifesto]] (Cypherpunks Write Code) |

### III. Craft & Care — Weight: 15%

Was this product built with intention, discipline, and taste?

| # | Heuristic | Test | Sources |
|---|-----------|------|---------|
| CC-1 | **Opinionated, not configurable** | Does the product take a stand, or offer infinite options that hide indecision? | [[37signals-getting-real-key-chapters]], [[37signals-scan-pass-2026-03-30]] (aerodynamic product) |
| CC-2 | **Iteration depth visible** | Evidence of refinement: version history, changelog, blog posts about hard decisions? | [[gigi-building-boris-21-days-insanity-2025]], [[37signals-pod-principles-of-communication]] |
| CC-3 | **Words crafted, not generated** | Is the copy (error messages, onboarding, about page) written by someone who cares about language? | [[37signals-getting-real-key-chapters]] (Copywriting is Interface Design), [[svn-gruber-graham-spolsky-writing-voices]] |
| CC-4 | **Built less, not more** | Has the product said no to features? Is there evidence of deliberate omission? | [[37signals-pod-say-no-by-default]], [[37signals-getting-real-key-chapters]] (Start With No) |
| CC-5 | **No dark patterns** | Honest UI: clear unsubscribe, no guilt-tripping, no forced engagement loops? | [[37signals-how-we-communicate-philosophy]], [[sovereign-engineering-ep06-winds-of-ai]] |
| CC-6 | **Human pace** | Does the product respect human attention spans, or demand constant engagement? Async-first? | [[37signals-how-we-communicate-philosophy]], [[zechner-slowing-down-agentic-coding-2026]] |

### IV. Openness & Interoperability — Weight: 10%

Does this product play well with others and respect open standards?

| # | Heuristic | Test | Sources |
|---|-----------|------|---------|
| OI-1 | **RSS/feed available** | Does the product offer RSS, Atom, or equivalent syndication? | [[gigi-purple-text-orange-highlights-nostr-reading-2023]], [[37signals-pod-it-started-with-a-blog]] |
| OI-2 | **API access** | Is there a documented, stable API for programmatic access? | [[sovereign-engineering-philosophy-manifesto]] |
| OI-3 | **Data portability** | Can you export everything in a standard format (JSON, CSV, OPML, markdown)? | [[gigi-speaking-freely-protocols-vs-platforms-2024]] |
| OI-4 | **Open source (or auditable)** | Is the source code available for inspection? Can you fork it? | [[sovereign-engineering-philosophy-manifesto]] (Cypherpunks Write Code) |
| OI-5 | **Interop with sovereign stack** | Does the product work with Nostr, Lightning, Bitcoin, or other open protocols? | [[gigi-purple-text-orange-highlights-nostr-reading-2023]], [[gigi-vision-value-enabled-web-2022]] |

### V. Honesty & Transparency — Weight: 15%

Does this product tell you the truth about what it is and what it does?

| # | Heuristic | Test | Sources |
|---|-----------|------|---------|
| HT-1 | **Business model visible** | How does this product make money? Is it obvious, or hidden behind "it's free"? | [[gigi-attention-terrible-currency-thread]], [[gigi-freedom-of-value-v4v-2021]] |
| HT-2 | **No growth-hack language** | Marketing copy: authentic enthusiasm or corporate-speak, buzzword soup, "AI-powered"? | [[37signals-scan-pass-2026-03-30]] (marketing as transfer of enthusiasm) |
| HT-3 | **Honest about AI usage** | If AI is used, is it disclosed? Are AI-generated outputs labeled? | [[gigi-caring-about-sloppypasta-2026]], [[sovereign-engineering-ep08-navigating-the-vibe]] |
| HT-4 | **Changelog/transparency log** | Does the product communicate changes honestly? Or silently ship downgrades? | [[37signals-how-we-communicate-philosophy]] |
| HT-5 | **No manufactured urgency** | Countdown timers, "limited time," "X people viewing this now" — manipulation signals? | [[37signals-how-we-communicate-philosophy]] (urgency is poison) |

### VI. Voice & Humanity — Weight: 10%

Does this product sound human, or like a committee/algorithm wrote it?

| # | Heuristic | Test | Sources |
|---|-----------|------|---------|
| VH-1 | **Distinctive voice** | Can you tell who made this from the writing alone? Or is it generic? | [[svn-deep-dive-editorial-voice-broadsheet]], [[37signals-writing-craft-for-llm-voice]] |
| VH-2 | **Named humans visible** | Are there real people behind this product? About page with faces and stories? | [[gigi-caring-about-sloppypasta-2026]], [[37signals-pod-give-it-a-name]] |
| VH-3 | **Embodied perspective** | Does the content reflect lived experience, not just information aggregation? | [[gigi-caring-about-sloppypasta-2026]] (LLMs lack embodiment), [[sovereign-engineering-ep05-prompt-and-pray]] |
| VH-4 | **Conversations, not broadcasts** | Does the product enable dialogue, or just push content at you? | [[gigi-speaking-freely-protocols-vs-platforms-2024]] (DiaLogos), [[37signals-pod-principles-of-communication]] |

### VII. Wisdom & Restraint — Weight: 5%

Does this product know when to stop, when to say no, and when to be quiet?

| # | Heuristic | Test | Sources |
|---|-----------|------|---------|
| WR-1 | **Deliberate constraints** | Is the product constrained by design choice, not by limitation? | [[37signals-pod-say-no-by-default]], [[37signals-getting-real-key-chapters]] (Embrace Constraints) |
| WR-2 | **Respects silence** | Does the product leave you alone when you're not using it? No push notifications, no "we miss you" emails? | [[37signals-how-we-communicate-philosophy]] (silence is communication) |
| WR-3 | **Long-term thinking** | Is this built for decades or for the next funding round? | [[sovereign-engineering-philosophy-manifesto]] (Endurance), [[37signals-scan-pass-2026-03-30]] (Concept 2 standard) |
| WR-4 | **LLM as tool, not master** | If AI is used, does it build understanding or bypass it? | [[gigi-nostr-tier2-scan-heuristics]] ("Choose wisely" quote), [[sovereign-engineering-ep06-winds-of-ai]] |

### VIII. Value Alignment — Weight: 5%

Does this product align incentives between creators, users, and the product itself?

| # | Heuristic | Test | Sources |
|---|-----------|------|---------|
| VA-1 | **Value flows to creators** | Do content creators capture value, or does the platform extract it? | [[gigi-freedom-of-value-v4v-2021]], [[gigi-purple-text-orange-highlights-nostr-reading-2023]] |
| VA-2 | **No attention extraction** | Is the product designed to help you finish tasks, or to maximize time-on-app? | [[gigi-attention-terrible-currency-thread]], [[sovereign-engineering-ep06-winds-of-ai]] |
| VA-3 | **V4V or honest pricing** | Is there a direct value exchange? V4V, one-time purchase, transparent subscription? Or "free" with hidden costs? | [[gigi-freedom-of-value-v4v-2021]] |
| VA-4 | **Curation rewarded** | Does the system value discovery and curation, not just creation? | [[gigi-purple-text-orange-highlights-nostr-reading-2023]] (swarm highlights) |

---

## Scoring Model

### Grade Calculation

Each category has N heuristics. Each heuristic scores:
- **Pass (1.0)** — Clear evidence of compliance
- **Partial (0.5)** — Mixed signals or partial implementation
- **Fail (0.0)** — Clear evidence of violation or absence

Category score = sum of heuristic scores / max possible score × 100

Weighted overall = Σ (category score × category weight)

### Grade Bands

| Grade | Score | Meaning |
|-------|-------|---------|
| **A** | 85-100 | Gigi would use this. Sovereign, crafted, honest. |
| **B** | 70-84 | Solid with gaps. Fixable with intention. |
| **C** | 55-69 | Mediocre. Some care visible, but structural problems. |
| **D** | 40-54 | Problematic. Platform thinking, attention extraction, or slop. |
| **F** | 0-39 | Slot machine. Surveillance product. Sloppypasta factory. |

### Weight Calibration

| Category | Weight | Rationale |
|----------|--------|-----------|
| Content Integrity | 20% | Core to the anti-slop thesis — if content is slop, nothing else matters |
| Sovereignty & Privacy | 20% | Core to the freedom thesis — if you can be rugpulled, you're not sovereign |
| Craft & Care | 15% | The bridge between Gigi and 37signals — intention in building |
| Honesty & Transparency | 15% | The business model test — honest products don't hide how they make money |
| Openness & Interoperability | 10% | Protocol-first is important but not all products need to be protocols |
| Voice & Humanity | 10% | Distinctive voice matters but is secondary to structural properties |
| Wisdom & Restraint | 5% | Hard to test objectively but philosophically important |
| Value Alignment | 5% | V4V is aspirational for most products; don't penalize honest pricing |

---

## Complementary Voices

### DHH & Jason Fried (37signals)

37signals provides the **craft dimension** that Gigi's sovereignty philosophy needs. Where Gigi asks "is this free?" and "is this sovereign?", 37signals asks "is this well-made?" and "does this respect the user's time?" Key convergences:

- **Build less** = **Constraint as blessing** — both traditions see limitation as a design virtue
- **Copywriting is interface design** = **Words matter** — both insist on craft in every user-facing word
- **Opinionated software** = **Freedom by design** — both reject the "give users everything" approach
- **Silence is communication** = **Respect human pace** — both resist the constant-notification paradigm

The 37signals voice is pragmatic where Gigi is philosophical; together they form a complete evaluation framework.

### John Vervaeke

Vervaeke provides the **epistemological foundation** for why slop fails. His distinction between "smart" and "wise" underpins Gigi's argument that LLMs cannot care:

- Wisdom requires embodiment (physical experience, mortality, desire)
- Pattern matching (intelligence) is necessary but insufficient for meaning-making
- The "meaning crisis" parallels the "care crisis" in content creation

### Christoph Zechner

Zechner provides the **practitioner's discipline** — the operational rules for building with AI without losing craft:

- Rate-limit AI contributions; review everything
- Slow down deliberately when tools speed up
- Verification gates as the expression of caring

---

## Sources (All Vault Notes Feeding This Synthesis)

### Primary — Gigi Philosophy
- [[dergigi-internet-left-me-slop-sovereignty]]
- [[gigi-caring-about-sloppypasta-2026]]
- [[gigi-speaking-freely-protocols-vs-platforms-2024]]
- [[gigi-freedom-of-value-v4v-2021]]
- [[gigi-attention-terrible-currency-thread]]
- [[gigi-true-names-not-required-pseudonymity-2020]]
- [[gigi-cryptography-not-enough-2022]]
- [[gigi-cryptography-not-enough-baltic-honeybadger-2022]]
- [[gigi-vision-value-enabled-web-2022]]
- [[gigi-building-boris-21-days-insanity-2025]]
- [[gigi-freedom-money-bitcoin-magazine-2023]]
- [[gigi-purple-text-orange-highlights-nostr-reading-2023]]
- [[gigi-nostr-tier2-scan-heuristics]]
- [[stopsloppypasta-definition-2026]]
- [[sovereign-engineering-philosophy-manifesto]]
- [[sovereign-engineering-podcast-no-solutions]]
- [[sovereign-engineering-ep08-navigating-the-vibe]]
- [[sovereign-engineering-ep06-winds-of-ai]]
- [[sovereign-engineering-ep05-prompt-and-pray]]
- [[boris-nostr-reading-app]]
- [[ants-nostr-text-search]]

### Secondary — 37signals / Craft
- [[37signals-how-we-communicate-philosophy]]
- [[37signals-pod-principles-of-communication]]
- [[37signals-pod-say-no-by-default]]
- [[37signals-getting-real-key-chapters]]
- [[37signals-scan-pass-2026-03-30]]
- [[37signals-pod-agent-accessibility-basecamp]]
- [[37signals-writing-craft-for-llm-voice]]
- [[37signals-pod-software-as-art]]
- [[37signals-pod-it-started-with-a-blog]]
- [[37signals-pod-give-it-a-name]]
- [[svn-deep-dive-editorial-voice-broadsheet]]
- [[svn-gruber-graham-spolsky-writing-voices]]
- [[tldraw-blocking-ai-contributions-2026]]

### Secondary — SVN Editorial Archive (reinforcing Craft & Voice dimensions)
- [[svn-the-distance-editorial-project]]
- [[svn-eureka-were-editors]]
- [[svn-comments-not-engagement]]
- [[svn-constraints-nightmares-dreams-haters]]
- [[svn-is-group-chat-making-you-sweat]]
- [[svn-rework-wrong-things]]
- [[svn-saddleback-leather-storytelling]]
- [[svn-sharing-a-first-draft]]
- [[svn-tools-for-editing-rework]]
- [[svn-why-business-writing-awful]]
- [[svn-why-web-copywriting-sucks]]
- [[svn-writing-decisions-saving-space]]
- [[svn-chouinard-catalog-1972]]

### Tertiary — Methodology
- [[agentic-craft-thesis]]
- [[zechner-slowing-down-agentic-coding-2026]]
- [[vervaeke-ai-coming-thresholds-2023]]
