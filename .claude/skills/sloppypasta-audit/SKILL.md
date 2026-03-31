---
name: sloppypasta-audit
description: >
  Run the Sloppypasta Audit on a product. Scores craft, sovereignty, honesty,
  and AI slop detection across 8 categories (46 checks). Outputs a graded
  markdown scorecard with improvement suggestions. Use when the user says
  /sloppypasta-audit or asks to audit a product.
allowed-tools: Bash(curl *), Read, Grep, Glob, WebFetch, WebSearch, Write
---

# Sloppypasta Audit

Run a scored product audit for craft, sovereignty, honesty, and AI slop detection.

## Usage

Invoke: `/sloppypasta-audit [URL or product name]`

Example: `/sloppypasta-audit https://boris.bar`
Example: `/sloppypasta-audit ppq.ai`
Example: `/sloppypasta-audit Twitter`

---

## Phase 1: Gather Product Information

1. Accept input: URL, product name, or both
2. If URL provided, use WebFetch to load:
   - Landing page / home page
   - About page (if exists)
   - Pricing page (if exists)
   - Documentation or help (if exists)
   - Terms of service (if exists)
3. If product name only, use WebSearch to find the product, then fetch as above
4. Determine product type: web app, mobile app, desktop app, CLI tool, protocol, library
5. Determine applicable conditional tags based on product features:

| Tag | Activates when | Example products |
|-----|---------------|-----------------|
| `[if:content]` | Product publishes or curates editorial content | Blogs, news sites, podcasts, social feeds |
| `[if:mobile]` | Product distributed as mobile/desktop app | Native apps, PWAs with install prompts |
| `[if:identity]` | Product manages user identity (login, profiles, keys) | Social networks, messaging apps, wallets |
| `[if:messaging/social]` | Product has communication or community features | Chat apps, forums, social networks |
| `[if:payments]` | Product handles money (wallets, subscriptions, V4V) | Wallets, exchanges, tipping services |

6. Note which conditional checks activate and which are N/A

---

## Phase 2: Score Each Check

### Reference Files (Read Before Scoring)

Read these files to understand the checks, score levels, and detection methods:

**Check inventory** (the definitive check list):
```
~/Coding/sloppypasta-audit/docs/check-inventory.md
```

**Scale anchors** (behavioral descriptions at each score level):
```
~/Coding/sloppypasta-audit/docs/scale-anchors/cat1-slop-detection.md
~/Coding/sloppypasta-audit/docs/scale-anchors/cat2-writing.md
~/Coding/sloppypasta-audit/docs/scale-anchors/cat3-design.md
~/Coding/sloppypasta-audit/docs/scale-anchors/cat4-craft.md
~/Coding/sloppypasta-audit/docs/scale-anchors/cat5-conduct.md
~/Coding/sloppypasta-audit/docs/scale-anchors/cat6-sovereignty.md
~/Coding/sloppypasta-audit/docs/scale-anchors/cat7-honesty.md
~/Coding/sloppypasta-audit/docs/scale-anchors/cat8-economic.md
```

**Detection references** (cheat sheets for specific check types):
```
~/Coding/sloppypasta-audit/docs/reference/slop-text-markers.md
~/Coding/sloppypasta-audit/docs/reference/slop-visual-markers.md
~/Coding/sloppypasta-audit/docs/reference/sovereignty-checks.md
```

### Scoring Procedure

For each V1 check in the inventory:

1. Read the scale anchor for that check
2. If the check has a detection reference (Cat 1 text markers, Cat 3 visual markers, Cat 6 sovereignty), read the relevant reference file
3. Examine the product against the behavioral descriptions at each anchor level (0%, 25%, 50%, 75%, 100%)
4. Assign a score from 5 to 100 (5% floor -- never assign below 5)
5. Record a one-sentence justification citing the specific observation that determined the score
6. If the check has a conditional tag and the condition does not apply to this product, mark N/A

**Score ALL checks in ALL categories before computing any aggregates. Do not skip categories.**

### Category-Specific Scoring Guidance

**Cat 1 (Slop Detection)**: Use `slop-text-markers.md` for check 1.1. Count banned words per 1,000 words of product text. Measure em-dash density. Check for structural patterns. For 1.2, examine social media presence for bot signals.

**Cat 3 (Design)**: Use `slop-visual-markers.md` for visual assessment. Perform the window resize test (drag to ~800px). Check CSS for purple/indigo defaults, Inter font, uniform padding. Check behavioral tells (empty states, error handling, focus states).

**Cat 5 (Conduct)**: Score check 5.5 as a composite -- score each of the 8 sub-checks (5.5a-5.5h) individually, then compute their geometric mean. For web-only products, sub-checks 5.5f, 5.5g, 5.5h are N/A and excluded from the composite.

**Cat 6 (Sovereignty)**: Use `sovereignty-checks.md` for test procedures and scoring scales. Follow the specific test methods described for each check. Conditional checks (6.8-6.13) activate only when the product matches the condition tag.

---

## Phase 3: Compute Scores

### 5% Floor

Before any computation, enforce the floor: any check score below 5 is set to 5. This prevents a single zero from catastrophically collapsing the geometric mean.

### Category Score (Geometric Mean)

For each category, compute the geometric mean of all applicable (non-N/A) check scores:

```
category_score = (check_1 * check_2 * ... * check_N) ^ (1/N)
```

Where N = number of applicable checks (N/A checks excluded).

**Minimum check threshold**: If a category has fewer than 3 applicable checks after N/A exclusions, exclude the entire category and redistribute its weight proportionally across remaining categories.

### Overall Score (Weighted Geometric Mean)

```
overall = product(category_score_i ^ weight_i) for all included categories
```

Equivalently:

```
ln(overall) = sum(weight_i * ln(category_score_i))
overall = exp(ln(overall))
```

Category weights:

| Category | Name | Weight |
|----------|------|--------|
| 1 | Slop Detection | 0.15 |
| 2 | Writing & Thinking | 0.10 |
| 3 | Design & Interface | 0.10 |
| 4 | Product Craft | 0.10 |
| 5 | Product Conduct | 0.15 |
| 6 | Sovereignty & Privacy | 0.20 |
| 7 | Honesty & Transparency | 0.10 |
| 8 | Economic Alignment | 0.10 |

**Weight redistribution**: If any category is excluded (fewer than 3 applicable checks), redistribute its weight proportionally. Multiply each remaining weight by `1 / (1 - excluded_weight)`.

Example: If Cat 8 (0.10) is excluded, each remaining weight is multiplied by `1 / 0.90 = 1.111`.

### Grade Assignment

| Grade | Score Range | Meaning |
|-------|------------|---------|
| A | 85-100 | Exceptional -- sets the standard |
| B | 70-84 | Good -- clear care, minor gaps |
| C | 55-69 | Mediocre -- functional but uninspired |
| D | 40-54 | Poor -- significant issues across dimensions |
| F | 0-39 | Failing -- actively hostile or negligent |

---

## Phase 4: Generate Report

Output a markdown report with this structure. Save to `~/Coding/sloppypasta-audit/docs/audits/YYYY-MM-DD-[product-slug].md`.

```markdown
# Sloppypasta Audit: [Product Name]

**Date**: YYYY-MM-DD
**URL**: [product URL]
**Type**: [web app / mobile app / CLI / protocol / etc.]
**Audit Mode**: External (V1, single-agent)
**Conditions**: [list of activated tags, e.g. "[if:content], [if:identity]"]
**Applicable Checks**: [X] of 46 ([Z] conditional activated, [W] N/A)

---

## Overall: [XX]% -- Grade [A/B/C/D/F]

[One paragraph summary. Lead with strengths. Frame weaknesses as improvement
paths. Specific observations, not generic praise or criticism. No weasel words.]

---

## Category Breakdown

### Cat 1: Slop Detection -- [XX]% (weight: 15%)

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| 1.1 | LLM smell markers | XX% | [one sentence with specific observation] |
| 1.2 | Social authenticity | XX% | [one sentence with specific observation] |

[Repeat for all 8 categories. Include N/A checks with "N/A" in Score column
and condition tag in Justification.]

---

## Score Summary

| Cat | Name | Score | Weight | Checks |
|-----|------|-------|--------|--------|
| 1 | Slop Detection | XX% | 15% | N/N |
| 2 | Writing & Thinking | XX% | 10% | N/N |
| 3 | Design & Interface | XX% | 10% | N/N |
| 4 | Product Craft | XX% | 10% | N/N |
| 5 | Product Conduct | XX% | 15% | N/N |
| 6 | Sovereignty & Privacy | XX% | 20% | N/N |
| 7 | Honesty & Transparency | XX% | 10% | N/N |
| 8 | Economic Alignment | XX% | 10% | N/N |
| **Overall** | | **XX%** | | **Grade [X]** |

---

## Priority Improvements

[3-5 specific, actionable improvements sorted by expected impact on overall
score. Each improvement:]

### 1. [Improvement Title]

**Check**: [N.N check name] (current: XX%)
**Observed**: [what you found -- specific, factual]
**Target**: [what 75% looks like for this check -- from the scale anchor]
**Impact**: Improving from XX% to ~75% would raise [Category Name] by
approximately [Y] points, lifting the overall score by ~[Z] points.

[Repeat for 3-5 improvements]

---

## Methodology

This audit uses the Sloppypasta Framework V1 -- 46 checks across 8 weighted
categories, scored on a 0-100% scale with a 5% floor. Category scores are
geometric means of applicable checks. The overall score is a weighted geometric
mean of category scores. Geometric means penalize low scores
disproportionately -- a single 10% score drags harder than a single 90% helps.

Source: github.com/[repo] | Framework: docs/synthesis.md
```

---

## Voice Guidelines

**Wise sage, not teenage dunker.** The audit exists to help builders improve. Every word serves that purpose.

- **Lead with strengths**: Acknowledge what's done well before identifying gaps. Even an F-grade product does something right.
- **Specific, not vague**: "Error messages show generic 'Something went wrong' text with no recovery path (4.1: 25%)" -- not "error handling could be better."
- **Calibrated language**: Don't say "great" for 50%. 50% is mediocre. 75% is good. 85%+ deserves praise. Match language to score.
- **No slop in the audit**: The report must pass its own Cat 2 checks. No weasel words, no throat-clearing, no filler, no Bold Prefix lists.
- **Improvement-focused**: Every low score connects to a specific improvement path. "Here's what 75% looks like" is more useful than "this is bad."
- **Honest about uncertainty**: If you can't fully evaluate a check from external observation, say so. "Could not verify -- scored conservatively at 50%" is better than a confident wrong score.
- **Product-only scope**: Audit the artifact, not the company. Don't speculate about internal culture, team size, or business strategy. Score what you can observe.
