---
name: sloppypasta-audit
description: >
  Run the Sloppypasta Audit on a product. Scores craft, sovereignty, honesty,
  and AI slop detection across 8 categories (47 checks). Outputs a graded
  markdown scorecard with improvement suggestions. Use when the user says
  /sloppypasta-audit or asks to audit a product.
allowed-tools: Bash(python3 -c *, curl *), Read, Grep, Glob, WebFetch, WebSearch, Write
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

### Reference File

Read ONE file before scoring — it contains all 47 checks, scale anchors, detection markers, and scoring procedures:

```
~/Coding/sloppypasta-audit/docs/scoring-reference.md
```

Do NOT read individual scale anchor files or detection references separately. Everything is consolidated in this file.

### Scoring Procedure

For each V1 check in the inventory:

1. Read the scale anchor for that check
2. If the check has a detection reference (Cat 1 text markers, Cat 3 visual markers, Cat 6 sovereignty), read the relevant reference file
3. Examine the product against the behavioral descriptions at each anchor level (0%, 25%, 50%, 75%, 100%)
4. Assign a score from 5 to 100 (5% floor -- never assign below 5)
5. Record a one-sentence justification citing the specific observation that determined the score
5a. If the score is below 70%, the justification MUST include one specific observation: a URL, code pattern, exact text quote, or screenshot description. Generic justifications like "seems low quality" are not sufficient.
6. If the check has a conditional tag and the condition does not apply to this product, mark N/A

**Score ALL checks in ALL categories before computing any aggregates. Do not skip categories.**

All category-specific guidance (detection markers, test procedures, composite specs) is inline in `scoring-reference.md` next to each check.

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

**Minimum check threshold**: If a category has fewer than 2 applicable checks after N/A exclusions, exclude the entire category and redistribute its weight proportionally across remaining categories. (Cat 1 has 2 checks by design -- this is intentional, not an exclusion trigger.)

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
| 1 | Slop Detection | 0.10 |
| 2 | Writing & Thinking | 0.10 |
| 3 | Design & Interface | 0.10 |
| 4 | Product Craft | 0.10 |
| 5 | Product Conduct | 0.15 |
| 6 | Sovereignty & Privacy | 0.20 |
| 7 | Honesty & Transparency | 0.15 |
| 8 | Economic Alignment | 0.10 |

**Weight redistribution**: If any category is excluded (fewer than 2 applicable checks), redistribute its weight proportionally. Multiply each remaining weight by `1 / (1 - excluded_weight)`.

Example: If Cat 8 (0.10) is excluded, each remaining weight is multiplied by `1 / 0.90 = 1.111`.

### Grade Assignment

| Grade | Score Range | Meaning |
|-------|------------|---------|
| A | 85-100 | Exceptional -- sets the standard |
| B | 70-84 | Good -- clear care, minor gaps |
| C | 55-69 | Mediocre -- functional but uninspired |
| D | 40-54 | Poor -- significant issues across dimensions |
| F | 0-39 | Failing -- actively hostile or negligent |

### Verify Computation

After computing scores manually, verify with python3:

```bash
python3 -c "
import math
# Fill in ALL check scores. Use None for N/A checks.
cat_checks = {
    1: [XX, XX],
    2: [XX, XX, XX, XX],  # 2.1, 2.2a, 2.2b, 2.3
    3: [XX, XX, XX, XX, XX],  # 3.1, 3.3, 3.4, 3.5, 3.6 (3.2 removed)
    4: [XX, XX, XX, XX],
    '5.5': [XX, XX, XX, XX, XX, XX, XX, XX],  # 5.5a-h, None if N/A
    5: [XX, XX, XX, XX, 'composite', XX, XX, XX, XX, XX],
    6: [XX, XX, XX, XX, XX, XX, XX, XX, XX, XX, XX, XX, XX],
    7: [XX, XX, XX, XX, XX, XX],  # 7.1, 7.2, 7.3a, 7.3b, 7.4, 7.5
    8: [XX, XX, XX],
}
weights = {1:0.10, 2:0.10, 3:0.10, 4:0.10, 5:0.15, 6:0.20, 7:0.15, 8:0.10}
sub55 = [max(s,5) for s in cat_checks['5.5'] if s is not None]
if sub55:
    comp55 = math.exp(sum(math.log(s) for s in sub55)/len(sub55))
    print(f'5.5 composite: {comp55:.1f}% ({len(sub55)} sub-checks)')
else:
    comp55 = None
    print('5.5: N/A')
cat_checks[5][4] = comp55
cats = {}
for c in [1,2,3,4,5,6,7,8]:
    a = [max(s,5) for s in cat_checks[c] if s is not None]
    if len(a) >= 2:
        cats[c] = math.exp(sum(math.log(s) for s in a)/len(a))
    else:
        print(f'Cat {c}: excluded ({len(a)} checks)')
w = sum(weights[c] for c in cats)
adj = {c: weights[c]/w for c in cats}
o = math.exp(sum(adj[c]*math.log(cats[c]) for c in cats))
for c in sorted(cats): print(f'Cat {c}: {cats[c]:.1f}%')
print(f'Overall: {o:.1f}%')
grade = next(g for t,g in [(85,'A'),(70,'B'),(55,'C'),(40,'D'),(0,'F')] if o>=t)
print(f'Grade: {grade}')
"
```

If the script output differs from your manual calculation by more than 1 point, use the script's result.

---

## Phase 4: Generate Report

Output a markdown report with this structure. Save to `~/Coding/sloppypasta-audit/docs/audits/YYYY-MM-DD-[product-slug].md`.

**Grade assignment**: Always use the python script's grade output from Phase 3. Never compute or override the grade manually. If the script output and your judgment disagree, the script wins.

```markdown
# Sloppypasta Audit: [Product Name]

**Date**: YYYY-MM-DD
**URL**: [product URL]
**Type**: [web app / mobile app / CLI / protocol / etc.]
**Audit Mode**: External (V1, single-agent)
**Conditions**: [list of activated tags, e.g. "[if:content], [if:identity]"]
**Applicable Checks**: [X] of 46 ([Z] conditional activated, [W] N/A)

---

## Audit Scope

**Surfaces assessed**: [list of surfaces directly examined — e.g., landing page, pricing page, about page, terms of service, app store listing]
**Surfaces via proxy**: [surfaces inferred but not directly accessed — e.g., mobile app behavior inferred from responsive site, payment flow inferred from pricing page]
**Surfaces not assessed**: [surfaces that exist but could not be examined — e.g., native mobile app (no device available), admin dashboard (requires account)]
**Limitations**: [any constraints on the audit — e.g., "External audit only — no account created, no payment flow tested, no mobile app installed"]

---

## Overall: [XX]% -- Grade [A/B/C/D/F]

[One paragraph summary. Lead with strengths. Frame weaknesses as improvement
paths. Specific observations, not generic praise or criticism. No weasel words.]

---

## Category Breakdown

### Cat 1: Slop Detection -- [XX]% (weight: 10%)

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
| 1 | Slop Detection | XX% | 10% | N/N |
| 2 | Writing & Thinking | XX% | 10% | N/N |
| 3 | Design & Interface | XX% | 10% | N/N |
| 4 | Product Craft | XX% | 10% | N/N |
| 5 | Product Conduct | XX% | 15% | N/N |
| 6 | Sovereignty & Privacy | XX% | 20% | N/N |
| 7 | Honesty & Transparency | XX% | 15% | N/N |
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

Source: github.com/mark-c4r/sloppypasta-audit | Framework: docs/scoring-reference.md
```

---

## Voice

- Lead with strengths. Even F-grade products do something right.
- Specific observations, not generic praise or criticism. Cite what you saw.
- Match language to score: 50% is mediocre, 75% is good, 85%+ deserves praise.
- Every low score connects to an improvement path: "here's what 75% looks like."

---

## Orchestrator Instructions (Multi-Agent Mode)

When running this audit from an orchestrator that can dispatch sub-agents, use parallel scoring for faster execution and bias isolation.

### Phase 1: Gather (orchestrator)
- Read `docs/scoring-reference.md`
- WebFetch/WebSearch product pages
- Determine product type, conditional tags, applicable vs N/A checks

### Phase 2: Dispatch 3 scoring agents in parallel

Each agent receives: raw fetched page content + product type + conditional tags + N/A list + their reference slice + WebFetch/WebSearch access for independent verification.

Each agent scores independently and returns ONLY check scores + justifications. Agents do NOT compute category or overall scores.

For checks scoring below 70%, justifications must include one specific observation (URL, code pattern, exact text, screenshot description). Generic justifications are not sufficient.

| Agent | Categories | Also needs from scoring-reference.md |
|-------|-----------|--------------------------------------|
| craft-scorer | Cat 1-4 (15 checks) | Text Slop Markers (after 1.1, used by 2.1, 2.3), Visual Slop Markers (after 3.6, used by 4.1, 4.3) |
| conduct-scorer | Cat 5 (10 + 8 sub-checks) | 5.5 sub-check scales |
| structure-scorer | Cat 6-8 (22 checks) | Sovereignty test procedures (inline in Cat 6) |

### Phase 3: Aggregate (orchestrator)
- Collect score tables from all 3 agents
- Compute 5.5 composite from conduct-scorer's sub-check scores
- Run python3 verification (Phase 3 script above)
- Write full report

### Agent output format

Each agent returns ONLY a scores table:

```
| # | Check | Score | Justification |
|---|-------|-------|---------------|
| N.N | Name | XX% | One sentence citing specific observation |
```

For 5.5, the conduct-scorer returns individual sub-check scores (5.5a-h). The orchestrator computes the composite.

### Fallback

If an agent fails, the orchestrator scores those categories directly. Note in the report Summary paragraph.
