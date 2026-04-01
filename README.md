# The Sloppypasta Audit

A framework for evaluating whether digital products are built with care or shipped as AI-generated slop. Measures craft, sovereignty, honesty, and economic alignment across 8 categories (46 checks).

Built for the Bitcoin/Nostr community. Useful for anyone who gives a damn.

## What It Measures

| Category | Weight | Question |
|----------|--------|----------|
| Slop Detection | 10% | Can you smell the AI? |
| Writing | 10% | Does the text show a thinking human? |
| Design | 10% | Does the look show care? |
| Craft | 10% | Less is more? |
| Conduct | 15% | How does it behave? |
| Sovereignty | 20% | Can they rugpull you? |
| Honesty | 15% | Does it tell you the truth? |
| Economic | 10% | Who captures the value? |

## How to Use

### As a Claude Code Skill

1. Copy `.claude/skills/sloppypasta-audit/` to your `~/.claude/skills/` directory
2. Copy `docs/` to `~/Coding/sloppypasta-audit/docs/` (the skill reads reference files from here)
3. Invoke: `/sloppypasta-audit [URL or product name]`

### As a Manual Audit

1. Read `docs/synthesis.md` for the full framework
2. Score each check using the scale anchors in `docs/scale-anchors/`
3. Compute geometric means per the scoring methodology
4. Assign a grade

### As a Community Tool

Run the audit on any public product and publish the results. Link back to this repo.

## Scoring

Geometric mean, not arithmetic. Low scores drag disproportionately. You can't compensate for a structural failure with nice fonts.

- **A** (85-100): Sovereign, crafted, honest.
- **B** (70-84): Solid. Gaps fixable with intention.
- **C** (55-69): Some care visible. Structural problems.
- **D** (40-54): Platform thinking. Attention extraction.
- **F** (0-39): Surveillance product, sloppypasta factory, or both.

## Repository Structure

```
sloppypasta-audit/
├── .claude/skills/sloppypasta-audit/
│   └── SKILL.md              # The Claude Code skill
├── docs/
│   ├── synthesis.md           # Full framework document
│   ├── check-inventory.md     # 46 checks across 8 categories
│   ├── scale-anchors/         # Scoring anchors (0-100) per check
│   │   ├── cat1-slop-detection.md
│   │   ├── cat2-writing.md
│   │   ├── ...
│   │   └── cat8-economic.md
│   ├── reference/             # Detection reference docs
│   │   ├── slop-text-markers.md
│   │   ├── slop-visual-markers.md
│   │   └── sovereignty-checks.md
│   └── calibration/           # Calibration run results
│       ├── boris-audit.md
│       ├── twitter-audit.md
│       └── calibration-notes.md
├── README.md
└── LICENSE
```

## Philosophy

Read the axioms in `docs/synthesis.md`. Short version: digital content has zero cost to copy, protocols can't de-platform you, payments can't be faked, and the best products ship less. This framework operationalizes those beliefs.

## Contributing

- Run the audit on a product and publish the results
- File issues for checks that produce inconsistent scores
- Propose improved scale anchors with real product examples
- Submit calibration runs on new products

## License

MIT
