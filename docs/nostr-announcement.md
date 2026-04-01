# Nostr Announcement Draft

## Short Version (Nostr note)

Shipped the Sloppypasta Audit — an open-source framework for scoring whether products are built with care or shipped as AI slop. 8 categories, 46 checks, geometric mean scoring, scale anchors for every check. Run it on anything.

Built as a Claude Code skill. Repo: https://github.com/mark-c4r/sloppypasta-audit

#sloppypasta #bitcoin #nostr #sovereignty

## Long Version (NIP-23 or blog)

Most products in the Bitcoin/Nostr space claim to value sovereignty and craft. Few have a structured way to prove it. The Sloppypasta Audit is an open-source framework that scores products across 8 categories — from AI slop detection to economic alignment — using 46 checks with behavioral scale anchors.

Scoring uses geometric means, not arithmetic. A product that nails design but surveils its users can't average its way to a good grade. Every check has anchored descriptions at 0/25/50/75/100 so two auditors looking at the same product reach the same score.

The framework ships as a Claude Code skill (run `/sloppypasta-audit` on any product) and as a standalone reference doc anyone can use manually. It's been calibrated against Boris (77%, B) and Twitter/X (31%, F). The checks, anchors, and methodology are all open — run it on products you use, publish the results, help improve the framework.

Repo: https://github.com/mark-c4r/sloppypasta-audit
