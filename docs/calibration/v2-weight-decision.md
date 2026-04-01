# V2 Weight Decision

**Date**: 2026-04-01
**Input**: v2-discrimination-analysis.md

---

## Decision Gate Results

### Weight Change Gate

| Condition | Threshold | Actual | Result |
|-----------|-----------|--------|--------|
| Care effective influence | < 30% | **24.8%** | Triggered |
| Cat 6 rank correlation with overall | > 0.98 | **1.0** (perfect) | Triggered |

**Mechanical verdict**: Full Scheme A triggered (Cat 5 → 20%, Cat 6 → 15%).

### 8.4 Sustainability Gate

| Condition | Threshold | Actual | Result |
|-----------|-----------|--------|--------|
| Free products scoring >= 90% on Cat 8 | >= 2 | **1** (Sparrow only, 95%) | Not triggered |

PodNews at 88% is closest but below the 90% threshold. **No 8.4 added.**

---

## Decision: No Weight Changes

Despite the mechanical gate triggering Full Scheme A, the weight changes are **not adopted**. Reasoning:

### 1. The gap is inherent, not a flaw

The discrimination analysis shows Care stdev improved from 11.6 → 12.6 (+8.6%), but Structure (26.8) still discriminates 2.1x better. This reflects the nature of what's measured:

- **Structural decisions are binary**: open vs closed source, custodial vs non-custodial, protocol vs platform. These create 70+ point spreads.
- **Craft attributes are a spectrum**: writing quality, design consistency, accessibility all compress because professional products converge on adequate-but-unremarkable craft. The natural spread is 30-40 points.

Shifting weight from Structure to Care would artificially reduce the influence of the framework's strongest, most reliable discriminator. It's like reducing the weight of a thermometer that works well because a broken barometer reads low.

### 2. Weight changes don't fix discrimination

Moving Cat 5 from 15% → 20% and Cat 6 from 20% → 15% would change the Care effective influence from 24.8% to ~28.3%. This crosses no meaningful threshold — it's a cosmetic change that reduces the influence of the framework's most architecturally sound measurements.

### 3. The Care dimension's role is ceiling differentiation

Structure separates D/F from B/C. Care separates B from A. Sparrow's Care score (77.4%) vs PodNews's (64.7%) = 12.7-point gap that contributes to the B vs C grade difference. This is the correct role — Care catches the nuances that distinguish good products from great ones.

### 4. Cat 6 rank correlation = 1.0 is a feature

The fact that sovereignty ranking perfectly predicts overall ranking validates the framework's thesis: "If they can rugpull you, everything else is decoration." This is the intended worldview, not a bug.

---

## Summary

| Decision | Outcome |
|----------|---------|
| Weight change (Scheme A) | **Not adopted** — gap is inherent |
| 8.4 sustainability check | **Not adopted** — threshold not met |
| V2 anchor changes | **Deployed** — improve Cat 2/3 discrimination |
| Total checks | **47** (unchanged from Phase 1) |
| Max possible (with 8.4) | Not applicable |

The V2 framework ships with 47 checks, original weights preserved, and sharper Care-dimension anchors. Phase 2 gate data documented here for future reference.
