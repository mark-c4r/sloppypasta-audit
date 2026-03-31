# The Sloppypasta Audit — Philosophical Framework

The internet had no native money, so it used attention instead. Two failure modes emerged: surveillance advertising and subscription hell. Both optimize for screen time over truth. Both produce walled gardens, algorithmic addiction, and censorship. And now, with LLMs, an avalanche of content nobody cared enough to stand behind.

The fix is not a better platform. The fix is protocols. Nostr for speech, Bitcoin for value, cryptography for identity. This framework checks whether a product respects those principles.

---

## Axioms

These are the worldview. They're not testable per product — they're what we believe.

1. **Information is free by nature.** Zero cost to copy. Paywalls and DRM fight this and lose.
2. **Protocols have speakers. Platforms have users.** You can't de-platform a speaker of a language.
3. **Cryptography is necessary but not sufficient.** Keys prove identity. Proof-of-work proves history.
4. **Sats are not fakeable.** Views, likes, comments — all faked at scale. Monetary value is human action distilled.
5. **Identity is prismatic.** One legal identity for everything is surveillance dressed as convenience.
6. **Smart is not wise.** LLMs pattern-match. They don't care. Caring requires embodiment.
7. **"Can't be evil" beats "don't be evil."** Policy fails. Architecture endures.
8. **Build less. Say no. Ship half.** Constraint is a design virtue.

---

## Categories & Heuristics

47 checks across 8 categories. Each scores 1 (pass), 0.5 (partial), or 0 (fail).

### I. Content Integrity — 20%

*Is this slop?*

- **CI-0** No access gates — paywalls, email-harvesting modals, forced signups to view content
- **CI-1** No LLM smell — negation reframes, sycophantic hedging, one-shot rhythm
- **CI-2** Editorial judgment visible — curation, not aggregation
- **CI-3** Someone stood behind it — named author, corrections acknowledged
- **CI-4** Dense, not padded — signal per paragraph, no filler
- **CI-5** Provenance traceable — signed, timestamped, attributed
- **CI-6** No drive-by contributions — AI-generated PRs filtered (if open-source)

### II. Sovereignty & Privacy — 20%

*Can they rugpull you?*

- **SP-1** The rugpull test — can the operator lock you out?
- **SP-2** Exit cost near zero — take everything with you in standard formats
- **SP-3** No identity harvesting — keypair ideal, gov ID always 0, "legally required" is not an excuse
- **SP-4** No surveillance by default — tracking, analytics, fingerprinting
- **SP-5** Protocol, not platform — open protocols or proprietary lock-in?
- **SP-6** You control the algorithm — visible, modifiable, or a black box?
- **SP-7** Self-hostable or auditable — run your own, or at least read the source
- **SP-8** Pay per service — sats in, service out. Subscriptions are honest when they're bus tickets, theft when they depend on people forgetting

### III. Craft & Care — 15%

*Did someone give a damn?*

- **CC-1** Opinionated — takes a side, not 47 toggles
- **CC-2** Iteration visible — changelogs, hard decisions documented
- **CC-3** Words written, not generated — error messages, onboarding, about page
- **CC-4** Less, on purpose — features cut, scope reduced, discipline of no
- **CC-5** No dark patterns — cancel in one click, no guilt modals
- **CC-6** Respects your time — open, get value, close. No dopamine hooks.

### IV. Openness — 10%

*Does it play with others?*

- **OI-1** RSS or equivalent — syndication without an account
- **OI-2** API access — documented, stable, usable
- **OI-3** Data portability — export everything in standard formats
- **OI-4** Source available — readable, forkable
- **OI-5** Sovereign stack compatible — works with Nostr, Lightning, Bitcoin

### V. Honesty — 15%

*Does it tell you the truth?*

- **HT-1** Business model visible — if not obvious in 30 seconds, you're the product
- **HT-2** No growth-hack language — authentic, not "AI-powered revolutionary 10x"
- **HT-3** Honest about AI — disclosed and labeled, not passed off as human
- **HT-4** No manufactured urgency — no countdown timers, no "X people viewing"

### VI. Voice & Humanity — 10%

*Is a human in there?*

- **VH-1** Distinctive voice — identifiable, not generic SaaS copy
- **VH-2** Humans visible — real names, real faces, not "our team of innovators"
- **VH-3** Lived experience — embodied knowledge, not aggregated research
- **VH-4** Dialogue, not broadcast — can you talk back?

### VII. Wisdom & Restraint — 5%

*Does it know when to shut up?*

- **WR-1** Constraints are deliberate — limited by choice, not accident
- **WR-2** Can't nag you — holds no contact data (ideal), or never uses it for re-engagement
- **WR-3** Decades, not quarters — will it work in 10 years?
- **WR-4** AI builds understanding — helps you learn, not replaces your thinking

### VIII. Value Alignment — 5%

*Who captures the value?*

- **VA-1** Value reaches creators — not extracted by the platform
- **VA-2** Your attention isn't the product — helps you finish, not keeps you scrolling
- **VA-3** Honest exchange — V4V, pay-per-use, or genuinely fair subscription. Not inertia billing.
- **VA-4** Curators get value — discovery and curation rewarded, not just creation

---

## Scoring: Geometric Mean

Multiply, don't add. That's the whole insight.

**Category score** = geometric mean of heuristic scores within that category.
**Overall score** = weighted geometric mean of category scores.

A zero on any heuristic kills its category. A dead category kills the overall. Beautiful typography doesn't save a surveillance product. FTX had great design.

### The math

```
category = (h1 × h2 × ... × hN) ^ (1/N)
overall  = cat1^w1 × cat2^w2 × ... × cat8^w8
score    = overall × 100
```

In Excel:
```
category = IF(MIN(scores)=0, 0, EXP(AVERAGE(LN(scores))))
overall  = IF(MIN(cats)=0, 0, EXP(SUMPRODUCT(weights, LN(cats)))) * 100
```

### Why geometric, not arithmetic

Arithmetic: add and divide. A zero in a 20%-weighted category just loses 20 points. Makeup elsewhere. A scammer with good design gets a C.

Geometric: multiply. A zero anywhere — zero. Integrity is not a line item. It's a prerequisite.

### Grades

| Grade | Score | Meaning |
|-------|-------|---------|
| **A** | 85–100 | Sovereign, crafted, honest. |
| **B** | 70–84 | Solid. Gaps fixable with intention. |
| **C** | 55–69 | Some care visible. Structural problems. |
| **D** | 40–54 | Platform thinking. Attention extraction. Carelessness. |
| **F** | 0–39 | Surveillance product, sloppypasta factory, or fraud. |

### Weights

| Category | Weight | Why |
|----------|--------|-----|
| Content Integrity | 20% | If the content is slop, nothing else matters. |
| Sovereignty & Privacy | 20% | If they can rugpull you, everything else is decoration. |
| Craft & Care | 15% | The difference between "built" and "shipped." |
| Honesty | 15% | If you can't see the business model, you are it. |
| Openness | 10% | Not every product is a protocol. Interop still matters. |
| Voice & Humanity | 10% | A human should be visible. Structure outweighs style. |
| Wisdom & Restraint | 5% | Hard to measure. Still matters. |
| Value Alignment | 5% | V4V is aspirational. Honest pricing is sufficient. |

---

## Sources

Synthesized from 30+ vault notes. Primary voices: Gigi (Sovereign Engineering, dergigi.com), 37signals (Getting Real, REWORK podcast, SVN), Vervaeke (meaning crisis, embodiment), Zechner (agentic discipline).

Full source list with wikilinks: `vault/notes/tech/editorial/gigi-internet-philosophy-synthesis.md`
