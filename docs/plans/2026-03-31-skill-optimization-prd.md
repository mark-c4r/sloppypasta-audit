---
ticket: sloppypasta-audit optimization
status: active
appetite: M
project: sloppypasta-audit
updated: 2026-03-31
files:
  - docs/scoring-reference.md
  - .claude/skills/sloppypasta-audit/SKILL.md
  - docs/scale-anchors/*.md
  - docs/reference/*.md
---

# Sloppypasta Audit Skill Optimization — Detailed PRD

## Problem

V5 calibration runs revealed two performance issues:

1. **Token waste**: Each audit agent reads 12+ reference files (~50K tokens) before scoring. Boris audit: 146K tokens, 86 tool calls, 16 min. Twitter/X: 112K tokens, 39 tool calls, 6.5 min.

2. **Scoring bias**: A single agent scoring all 46 checks sequentially risks cross-category halo/horn effects. A low Cat 3 (Design) score may unconsciously bias Cat 4 (Craft) scoring downward.

## Appetite

M (1-4 hours). Two sequential parts, each independently shippable.

## Solution

**Part A**: Consolidate 12 reference files into 1 operational scoring reference.
**Part B**: Restructure the skill for 3-agent parallel scoring with bias isolation.

---

## PART A: REFERENCE CONSOLIDATION

### A1. Create `docs/scoring-reference.md`

**Source files to consolidate (read all, then merge):**

| Source | Tokens | Content |
|--------|--------|---------|
| `docs/check-inventory.md` | 4,658 | Check list, conditions, notes |
| `docs/scale-anchors/cat1-slop-detection.md` | 1,257 | 2 checks |
| `docs/scale-anchors/cat2-writing.md` | 1,824 | 3 checks |
| `docs/scale-anchors/cat3-design.md` | 4,262 | 6 checks |
| `docs/scale-anchors/cat4-craft.md` | 3,004 | 4 checks |
| `docs/scale-anchors/cat5-conduct.md` | 12,097 | 10 checks + 8 sub-checks |
| `docs/scale-anchors/cat6-sovereignty.md` | 9,804 | 13 checks |
| `docs/scale-anchors/cat7-honesty.md` | 4,167 | 5 checks |
| `docs/scale-anchors/cat8-economic.md` | 2,606 | 3 checks |
| `docs/reference/slop-text-markers.md` | 1,092 | Banned words/phrases/openers |
| `docs/reference/slop-visual-markers.md` | 814 | CSS/layout/behavioral tells |
| `docs/reference/sovereignty-checks.md` | 1,520 | Test procedures + intermediate scales |
| **Total** | **~47,105** | |

**Target: ~30-35K tokens in one file.**

#### File structure

```markdown
# Sloppypasta Audit — Scoring Reference

> **Scoring floor**: The minimum score for any check is 5% (not 0%).
> This prevents a single zero from collapsing the geometric mean.
> 5% = actively hostile behavior. Reserve for deliberate harm.

## Conditional Tags

| Tag | Activates when |
|-----|---------------|
| `[if:content]` | Product publishes or curates editorial content |
| `[if:mobile]` | Product distributed as mobile/desktop app |
| `[if:identity]` | Product manages user identity |
| `[if:messaging/social]` | Product has communication or community features |
| `[if:payments]` | Product handles money |

## Category Weights

| Cat | Name | Weight | V1 Checks |
|-----|------|--------|-----------|
| 1 | Slop Detection | 15% | 2 |
| 2 | Writing & Thinking | 10% | 3 |
| 3 | Design & Interface | 10% | 6 |
| 4 | Product Craft | 10% | 4 |
| 5 | Product Conduct | 15% | 10 |
| 6 | Sovereignty & Privacy | 20% | 13 |
| 7 | Honesty & Transparency | 10% | 5 |
| 8 | Economic Alignment | 10% | 3 |

Minimum 3 applicable checks per category. Below 3 → exclude category,
redistribute weight proportionally.

---

## Cat 1: Slop Detection (weight: 15%, 2 checks)

### 1.1 LLM Smell Markers in Text [Universal]

Frequency of detectable AI-generated writing patterns.

| Score | Anchor | Archetype |
|-------|--------|-----------|
| 5% | Raw LLM dump. Multiple banned words per paragraph, em-dash >1/200w, Bold Prefix lists, symmetrical paragraphs, model openers. | SEO content farms |
| 25% | Detectable LLM with light editing. 3-6 banned/1Kw, occasional em-dash clusters, some structural patterns. | AI-assisted SaaS landing pages |
| 50% | Moderate editing of AI content. 1-3 banned/1Kw, em-dash normal, structures mostly broken up. | Company blogs with AI drafts |
| 75% | Rare markers. <1 banned/1Kw, no structural tells, human voice dominates. | Basecamp blog, indie product copy |
| 100% | Zero LLM markers. Idiosyncratic voice, irregular rhythm, personal vocabulary. | Julia Evans, Dan Luu, Craig Mod |

**Scoring**: Use banned-word list (49 words, 38 phrases, 16 openers) as primary quantitative signal. Em-dash density >1/500w is secondary. Structural patterns (Bold Prefix lists, Rule of Three, symmetrical paragraphs) are tertiary. Score on density, not binary.

### Detection: Text Slop Markers

[INLINE THE FULL CONTENT OF docs/reference/slop-text-markers.md HERE]
- Full banned vocabulary (49 words) with frequency thresholds
- Full banned phrases (38 phrases) with 2+ presence rule
- Full banned openers (16 openers)
- Punctuation thresholds table
- Structural patterns list
- Model-specific first words table

### 1.2 Social Authenticity [Universal]

[Same format: condensed anchor table + scoring notes]

---

[REPEAT FOR ALL 8 CATEGORIES, 46 CHECKS]

### Detection: Visual Slop Markers
[INLINE AFTER CHECK 3.6 — full content of docs/reference/slop-visual-markers.md]

### 5.5 Privacy & Tracking Composite [Universal]
[Include full composite spec with all 8 sub-checks inline]
[INLINE sovereignty-checks.md 5.5 section content into scoring notes]

### Cat 6 checks
[For each check 6.1-6.13, MERGE the test procedure from sovereignty-checks.md
 into the Scoring notes. Where sovereignty-checks.md has intermediate breakpoints
 (6.3 has 35% and 20%), ADD those as additional rows in the anchor table.]
```

#### Per-check condensation rules

For each of the 46 checks, apply these transformations:

1. **Header**: `### N.N Check Name [tag]` (add conditional tag in brackets)
2. **Description**: First sentence of "What it measures" (drop the rest — it's restated in the anchors)
3. **Table**: 3-column — Score | Anchor | Archetype
   - **Anchor column**: Preserve the behavioral description verbatim. Do NOT paraphrase or shorten the behavioral text — this is the scoring instrument.
   - **Archetype column**: Extract 1-3 product names from the Product Example column. If Product Example names 4+ products, keep the 2-3 most recognizable. Format: `ProductA, ProductB`
4. **Scoring notes**: Preserve verbatim. Append relevant detection procedure from reference files where applicable.
5. **Sovereignty reconciliation**:
   - **6.3 (Identity Sovereignty)**: sovereignty-checks.md defines 6 levels (100%, 75%, 50%, 35%, 20%, 5%) vs scale anchor's 5 levels (100%, 75%, 50%, 25%, 5%). Add 35% ("email + verification required") and 20% ("phone number required") as intermediate rows. The scale anchor's 25% ("Phone-verified identity") maps to sovereignty-checks.md's 20% — use the more detailed breakpoints.
   - **6.4 (Protocol vs Platform)**: Both sources define 5 levels but with different descriptions at 50% and 75%. **Precedence rule**: scale anchor behavioral descriptions win (they are the full scoring instrument). sovereignty-checks.md's shorter descriptions become the **Scoring** procedure (what to test), not the anchor (what to match).
   - **All other Cat 6 checks**: sovereignty-checks.md provides test procedures — merge these into the **Scoring** line below each check's anchor table. Do not duplicate scoring levels.
6. **5.5 Composite**: This is not a normal check. Use a subsection format under 5.5 with individual sub-check tables (5.5a-h). Each sub-check gets its own mini anchor table (3-5 levels) drawn from sovereignty-checks.md section "Privacy Composite Sub-Checks."
7. **Tag format**: Use `[Universal]` for universal checks and `[if:tag]` for conditional checks. Every check header must include one tag.

#### What NOT to do

- Do NOT paraphrase behavioral descriptions. They are the scoring instrument.
- Do NOT invent new archetypes. Only extract from existing Product Example text.
- Do NOT add commentary, explanations, or meta-text between checks.
- Do NOT reorder checks. Maintain category/check number order.

### A2. Refactor `SKILL.md`

Current skill file: `.claude/skills/sloppypasta-audit/SKILL.md` (258 lines, ~2,612 tokens)

#### Changes

**1. Replace Phase 2 reference file list (lines 52-78) with:**

```markdown
## Phase 1: Load Scoring Reference

Read ONE file before scoring:

```
~/Coding/sloppypasta-audit/docs/scoring-reference.md
```

This file contains all 46 checks, scale anchors, detection markers,
and scoring notes. Do NOT read individual scale anchor files or
detection references separately.
```

**2. Update allowed-tools line (line 8):**

```
allowed-tools: Bash(python3 -c *, curl *), Read, Grep, Glob, WebFetch, WebSearch, Write
```

**3. Add Phase 5: Verify (new, after Phase 3 Compute):**

```markdown
## Phase 5: Verify Computation

Run this python3 script to verify your geometric mean calculations.
Fill in your computed check scores (use None for N/A checks):

\```bash
python3 -c "
import math

# Fill in ALL check scores. Use None for N/A checks.
cat_checks = {
    1: [XX, XX],                    # 1.1, 1.2
    2: [XX, XX, XX],                # 2.1, 2.2, 2.3 (None if N/A)
    3: [XX, XX, XX, XX, XX, XX],    # 3.1-3.6
    4: [XX, XX, XX, XX],            # 4.1-4.4
    '5.5': [XX, XX, XX, XX, XX, XX, XX, XX],  # 5.5a-h (None if N/A)
    5: [XX, XX, XX, XX, 'composite', XX, XX, XX, XX, XX],  # 5.1-5.10
    6: [XX, XX, XX, XX, XX, XX, XX, XX, XX, XX, XX, XX, XX],  # 6.1-6.13
    7: [XX, XX, XX, XX, XX],        # 7.1-7.5 (None if N/A)
    8: [XX, XX, XX],                # 8.1-8.3
}
weights = {1:0.15, 2:0.10, 3:0.10, 4:0.10, 5:0.15, 6:0.20, 7:0.10, 8:0.10}

# Compute 5.5 composite first
sub55 = [max(s, 5) for s in cat_checks['5.5'] if s is not None]
if sub55:
    composite_55 = math.exp(sum(math.log(s) for s in sub55) / len(sub55))
    print(f'5.5 composite: {composite_55:.1f}% ({len(sub55)} sub-checks)')
else:
    composite_55 = None  # All sub-checks N/A (e.g., CLI tool)
    print('5.5 composite: N/A (no applicable sub-checks)')

# Replace composite placeholder in cat 5
cat5 = cat_checks[5]
cat5[4] = composite_55  # None if all sub-checks N/A

# Compute category geomeans
cats = {}
excluded = []
for c in [1,2,3,4,5,6,7,8]:
    applicable = [max(s, 5) for s in cat_checks[c] if s is not None]
    if len(applicable) < 2:  # Cat 1 has 2 by design; threshold for post-N/A drops
        excluded.append(c)
        print(f'Cat {c}: {len(applicable)} checks — EXCLUDED (< 2)')
        continue
    cats[c] = math.exp(sum(math.log(s) for s in applicable) / len(applicable))

# Redistribute weights
active_weight = sum(weights[c] for c in cats)
adj = {c: weights[c] / active_weight for c in cats}

# Weighted geomean
ln_overall = sum(adj[c] * math.log(cats[c]) for c in cats)
overall = math.exp(ln_overall)

for c in sorted(cats): print(f'Cat {c}: {cats[c]:.1f}%')
print(f'Overall: {overall:.1f}%')
grade = next(g for t,g in [(85,'A'),(70,'B'),(55,'C'),(40,'D'),(0,'F')] if overall >= t)
print(f'Grade: {grade}')
"
\```

If the script output differs from your manual calculation by more than 1 point,
use the script's result.
```

**4. Remove Category-Specific Scoring Guidance (lines 93-101):**

Delete the 4 paragraphs about Cat 1, Cat 3, Cat 5, Cat 6 — this guidance is now inline in scoring-reference.md next to each check.

**5. Condense Voice Guidelines (lines 248-258):**

Replace with:
```markdown
## Voice

- Lead with strengths. Even F-grade products do something right.
- Specific observations, not generic praise or criticism. Cite what you saw.
- Match language to score: 50% is mediocre, 75% is good, 85%+ deserves praise.
- Every low score connects to an improvement path: "here's what 75% looks like."
```

**6. Remove Methodology section from output template:**

The static methodology text at the bottom of every report is identical. Remove it from the template. Reports should end after Priority Improvements.

### A3. Add preservation headers

For each file in `docs/scale-anchors/` (8 files) and `docs/reference/` (3 files), prepend:

```markdown
> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as the deep calibration reference with full product examples.

```

### A4. Structural validation

After creating scoring-reference.md, run these checks:

```bash
# 1. Count check headings (should be 46)
grep -cE '^### [0-9]+\.' docs/scoring-reference.md

# 2. Count anchor level rows (should be 230 = 46 checks * 5 levels, plus intermediates)
grep -cE '^\| [0-9]+%' docs/scoring-reference.md

# 3. Verify sovereignty intermediate breakpoints exist
grep -E '^\| (20|35)%' docs/scoring-reference.md

# 4. Verify detection reference content was merged (spot checks)
grep -c 'delve, tapestry' docs/scoring-reference.md  # text markers
grep -c 'focus:outline-none' docs/scoring-reference.md  # visual markers
grep -c 'Can the operator unilaterally' docs/scoring-reference.md  # sovereignty

# 5. Verify file is readable in one Read call (< 2000 lines)
wc -l docs/scoring-reference.md

# 6. Python verification against known baselines
python3 -c "
import math
# Boris V5 scores
boris = {
    1: [78, 70], 2: [72, 70, 80],
    3: [55, 65, 45, 50, 90, 50], 4: [55, 65, 40, 80],
    '5.5': [75, 50, 50, 90, 50, None, None, None],
    5: [90, 90, 90, 85, 0, 70, 85, 95, 90, 90],  # 0=placeholder for composite
    6: [90, 95, 100, 95, 85, 90, 100, 85, None, None, 90, None, None],
    7: [85, 80, 70, 95, 70], 8: [95, 90, 95]
}
weights = {1:0.15, 2:0.10, 3:0.10, 4:0.10, 5:0.15, 6:0.20, 7:0.10, 8:0.10}
sub55 = [max(s,5) for s in boris['5.5'] if s is not None]
comp55 = math.exp(sum(math.log(s) for s in sub55)/len(sub55))
boris[5][4] = comp55
cats = {}
for c in [1,2,3,4,5,6,7,8]:
    a = [max(s,5) for s in boris[c] if s is not None]
    cats[c] = math.exp(sum(math.log(s) for s in a)/len(a))
w = sum(weights[c] for c in cats)
adj = {c: weights[c]/w for c in cats}
o = math.exp(sum(adj[c]*math.log(cats[c]) for c in cats))
print(f'Boris: {o:.1f}% (expected: 77%)')
assert 76 <= o <= 78, f'Boris score drift: {o:.1f}%'
print('PASS')
"
```

### A5. Acceptance criteria

- [ ] `docs/scoring-reference.md` exists with all 46 checks
- [ ] Each check has: header with tag, brief description, 3-column anchor table, scoring notes
- [ ] Behavioral descriptions are verbatim from scale anchors (not paraphrased)
- [ ] Archetype column has 1-3 compressed product hints per level
- [ ] Detection references (text markers, visual markers, sovereignty procedures) are inline
- [ ] Sovereignty intermediate breakpoints (6.3: 35%/20%) present as additional rows
- [ ] File is under 2000 lines (readable in single Read call)
- [ ] SKILL.md updated: single-file load, python3 verification, condensed voice, no methodology boilerplate
- [ ] All original files have preservation headers
- [ ] Structural validation passes (46 check headings, 230+ anchor rows, detection content present)
- [ ] Python verification reproduces Boris: 77% and Twitter: 31%

---

## PART B: MULTI-AGENT PARALLEL SCORING

### B1. Agent partitioning

Three scoring agents, partitioned by philosophical domain:

| Agent Name | Categories | Checks | Domain |
|------------|-----------|--------|--------|
| `craft-scorer` | Cat 1, 2, 3, 4 | 15 | Surface: text quality, visual design, product polish |
| `conduct-scorer` | Cat 5 | 10 + 8 sub | Behavioral: dark patterns, privacy, attention, access |
| `structure-scorer` | Cat 6, 7, 8 | 21 | Architectural: sovereignty, honesty, economics |

**Why this partition:**
- Bias isolation: a craft opinion doesn't infect a sovereignty assessment
- Domain coherence: each agent has one lens
- Load balance: 15 / 18 / 21 checks (roughly even with 5.5 sub-checks)

### B2. Orchestrator flow

**Key clarification**: Multi-agent mode is orchestrator-driven. The orchestrator (main session or parent agent) has native Agent tool access. The SKILL.md does NOT need Agent in its allowed-tools. Instead, the skill provides orchestrator instructions that the parent agent follows.

The SKILL.md adds a section at the end:

```
## Orchestrator Instructions (Multi-Agent Mode)

When running this audit from an orchestrator that can dispatch sub-agents,
use parallel scoring for faster execution and bias isolation.

### Phase 1: Gather (orchestrator does this)
- Read docs/scoring-reference.md
- WebFetch/WebSearch product pages (same as single-agent Phase 2)
- Determine product type, conditional tags, applicable vs N/A checks

### Phase 2: Dispatch 3 scoring agents in parallel
Each agent receives:
a) Raw fetched page content (not a summary — agents need raw evidence)
b) Product type + conditional tags + N/A check list
c) Their reference slice (see dependency map below)
d) WebFetch/WebSearch access for independent verification

Each agent scores independently and returns ONLY check scores + justifications.
Agents do NOT compute category or overall scores.

### Phase 3: Aggregate (orchestrator does this)
- Merge score tables from all 3 agents
- Run python3 verification
- Write the full report

### Reference Dependency Map (for slicing)

| Agent | Categories | Also needs |
|-------|-----------|------------|
| craft-scorer | Cat 1-4 | Text Slop Markers (used by 1.1, 2.1, 2.3), Visual Slop Markers (used by 3.x, 4.1, 4.3) |
| conduct-scorer | Cat 5 | 5.5 sub-check scales from sovereignty reference (5.5a-h) |
| structure-scorer | Cat 6-8 | Sovereignty test procedures (inline in Cat 6 checks) |

IMPORTANT: Text markers are placed after check 1.1 in the reference,
but also used by checks 2.1 and 2.3. The craft-scorer's slice MUST
include text markers. Similarly, visual markers (placed after 3.6)
are also used by 4.1 and 4.3 — include in the craft-scorer's slice.

### Agent output format

Each agent returns ONLY a scores table (no category scores, no analysis):

| # | Check | Score | Justification |
|---|-------|-------|---------------|
| N.N | Name | XX% | One sentence citing specific observation |
| N.N | Name | N/A | [if:tag] — condition does not apply |

For check 5.5, the conduct-scorer returns individual sub-check scores:
| 5.5a | Cookie count | XX% | ... |
| 5.5b | Third-party trackers | XX% | ... |
[etc.]

The orchestrator computes the 5.5 composite from sub-check scores.
```

### B3. Agent prompt template

Each scoring agent gets a prompt structured as:

```
You are scoring [DOMAIN] checks for a Sloppypasta Audit of [PRODUCT NAME].

## Product Information
Type: [web app / mobile app / etc.]
URL: [url]
Conditions: [list of activated tags]

## Raw Evidence (fetched by orchestrator)
[PASTE the raw WebFetch output from all gathered pages — landing, about,
pricing, docs, terms. This is the primary evidence. Do NOT rely on
summaries — use the raw page content.]

## Your Assignment
Score categories [N-M] only. Other categories are scored by separate agents.
Do NOT score checks outside your assignment.
Do NOT compute category scores or overall scores — the orchestrator does this.

## N/A Checks (mark these as N/A, do not score):
[list of N/A checks for this agent's categories]

## Scoring Reference
[PASTE the relevant slice of scoring-reference.md for this agent's categories.
Include ALL detection references used by any check in the slice — see
dependency map in SKILL.md.]

## Independent Verification
You have WebFetch and WebSearch access. If the raw evidence above is
insufficient to score a check (e.g., need to check social media presence
for 1.2, or inspect cookies for 5.5), fetch additional pages yourself.

If you cannot verify a check at all, score conservatively at 50% and note
"Could not verify — scored conservatively" in the justification.

## Instructions
1. For each applicable check, examine the evidence against the anchor levels
2. Assign a score from 5 to 100 (5% floor — never below 5)
3. Write one-sentence justification citing a specific observation
4. Return ONLY a scores table — no analysis, no category totals

## Output Format

| # | Check | Score | Justification |
|---|-------|-------|---------------|

For check 5.5 (conduct-scorer only), return sub-check scores:
| 5.5a | Cookie count | XX% | [observation] |
| 5.5b | Third-party trackers | XX% | [observation] |
[etc. for all applicable 5.5 sub-checks]
```

### B4. Reference slicing

The orchestrator reads the full `scoring-reference.md` and extracts per-agent slices:

| Agent | Sections to extract | Estimated tokens |
|-------|--------------------|-----------------|
| craft-scorer | Header + Cat 1-4 + Text Slop Markers + Visual Slop Markers | ~12K |
| conduct-scorer | Header + Cat 5 (including composite spec) | ~10K |
| structure-scorer | Header + Cat 6-8 (including sovereignty procedures) | ~14K |

Each agent gets ~10-14K tokens of reference (vs 50K in single-agent mode). The total across all agents is ~36K, but each individual agent's context is much lighter.

### B5. Fallback

If any scoring agent fails (timeout, error, incomplete results):
1. Log which agent failed and what checks are missing
2. The orchestrator scores those checks directly (single-agent fallback for affected categories only)
3. Note the fallback in the report Summary paragraph (e.g., "Cat 5 scored via fallback due to agent timeout")

### B6. Acceptance criteria

- [ ] SKILL.md includes multi-agent mode section with dispatch instructions
- [ ] Agent prompt template is complete and tested
- [ ] Orchestrator correctly slices scoring-reference.md into 3 chunks
- [ ] Scores from 3 agents correctly merge into full 46-check report
- [ ] Python verification works with merged scores
- [ ] Calibration re-run on Boris produces scores within ±5 points per category vs V5 baseline
- [ ] Wall time for multi-agent audit is demonstrably faster than single-agent
- [ ] Single-agent mode still works when skill is invoked directly

---

## Implementation sequence

1. A1: Create `docs/scoring-reference.md`
2. A2: Refactor SKILL.md (single-agent mode)
3. A3: Preservation headers on original files
4. A4: Structural validation
5. B2: Add multi-agent mode to SKILL.md
6. B3-B4: Agent prompt template + reference slicing
7. B6: Calibration verification (Boris re-run)

Parts A1-A4 commit together. Parts B2-B6 commit separately.

## Risks

| Risk | Mitigation |
|------|-----------|
| Condensed anchors lose scoring accuracy | Behavioral descriptions preserved verbatim; only Product Example column condensed to archetypes |
| sovereignty-checks.md intermediate breakpoints lost | Explicitly add 35%/20% as extra rows in consolidated table |
| Multi-agent scores diverge from single-agent | Calibration re-run with ±5 point threshold per category |
| scoring-reference.md exceeds Read tool limits | Target under 2000 lines; split into 2 files if needed |
| Agent prompt template too large for context | Slice estimation is 10-14K per agent — well within limits |
