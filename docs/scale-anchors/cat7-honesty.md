> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as deep calibration reference.
# Cat 7: Honesty & Transparency — Scale Anchors

Reference: check-inventory.md

> **Scoring floor**: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension.

---

## 7.1 Business Model Visible

**What it measures**: Whether you can see how the product makes money — explicit pricing, clear revenue model, no ambiguity about the value exchange.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Business model deliberately hidden or misleading. No pricing page, no revenue explanation, no mention of how the product sustains itself. Or worse: the product claims to be "free" while obviously monetizing user data or attention. The absence of a visible business model IS the business model — you're the product and they'd rather you not think about it. | "Free" social media platforms with no visible revenue explanation, data-broker-funded "free" tools, products where "if you're not paying, you're the product" and they're not telling you |
| 25% | Business model vaguely implied but not stated. Pricing page exists but is confusing or incomplete. Revenue sources are partially visible (ads are present, so presumably ad-funded) but not explained. Funded by VC with no path to revenue articulated. The product would rather you not ask how it makes money. | VC-funded products pre-monetization with no pricing page, freemium products where the paid tier is hidden or unadvertised, products with "Contact Sales" as the only pricing information |
| 50% | Business model visible but not prominent. Pricing page exists and is accurate. Revenue model is identifiable (subscription, ads, transaction fee) but not explained. You can figure out how they make money by looking around, but they don't proactively tell you. Standard transparency — better than hiding, less than honest. | Average SaaS with a pricing page, ad-supported products where ads are obviously the model, standard e-commerce |
| 75% | Business model clearly stated. Pricing page is prominent and complete. The product explains how it makes money and how that aligns with user interests. No hidden revenue streams. If there's a free tier, the funding model for free users is explained. The product treats its business model as a feature, not a secret. | Basecamp ("one price, forever" — pricing is a selling point), Pinboard (pricing on the homepage), products that explain "we charge you, not advertisers" |
| 100% | Business model is a trust signal. The product leads with how it makes money because the model itself builds trust. Pay-per-use pricing visible before signup. No hidden fees, no future pricing uncertainty. The business model is as transparent as the product itself. You know exactly what you're paying for, what the company earns, and how those incentives align with your interests. | PPQ.AI (pay-per-query, visible before use), Signal (donation-funded, publicly documented), Basecamp (per-company flat rate, publicly committed), 37signals' transparent pricing philosophy |

**Scoring notes**: Visit the product as a new user. Can you find how it makes money within 2 clicks from the homepage? Pricing page with clear tiers = minimum 50%. "Contact sales" as the only pricing option = 25%. No pricing information and no visible revenue model = 0%. Products that proactively explain WHY their business model benefits users score 75%+. VC-funded products with no revenue model yet are inherently risky for users — score based on what's visible, not what's planned.

---

## 7.2 No Marketing Exaggeration

**What it measures**: Whether the product's marketing claims match its actual capabilities. No "revolutionary," no vaporware promises, no AI-powered-everything hype.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Marketing is fiction. Claims bear no relationship to the product's actual capabilities. "Revolutionary AI" that's a wrapper around GPT-4 with a prompt. "Enterprise-grade" for a solo project with no tests. Features listed on the marketing page that don't exist in the product. The marketing sells a product that doesn't exist. | Vaporware products with feature lists for unbuilt features, "AI-powered" products that are basic CRUD with an API call, crypto projects with white papers describing nonexistent technology |
| 25% | Significant exaggeration. The product exists and works but the marketing oversells it. "Revolutionary" for incremental improvements. "Blazing fast" without benchmarks (or with misleading ones). "AI-powered" for minor AI features that aren't core. Superlatives dominate the copy. You'll be disappointed after signup because expectations were inflated. | Most AI-startup marketing in 2024-2026, SaaS products with "blazing fast" claims and no benchmarks, products with "enterprise-grade" in marketing and "beta" in the app |
| 50% | Marketing is optimistic but not dishonest. Claims are recognizable as the product you'll get, with some editorial generosity. "Easy to use" might be generous but it's not a lie. Feature descriptions are accurate but emphasize best-case scenarios. Standard marketing language — you expect some inflation and adjust accordingly. | Average SaaS marketing, products with accurate feature lists and mildly enthusiastic descriptions |
| 75% | Marketing matches experience. What you read is what you get. Features described are features that work. Performance claims are backed by evidence or caveated honestly ("fast for most workloads"). Limitations are acknowledged, not hidden. The marketing respects your intelligence — it persuades through demonstration, not superlatives. | Stripe (marketing matches product experience), Tailwind CSS (accurate descriptions with real examples), Basecamp (marketing IS the philosophy) |
| 100% | Marketing understates the product. Claims are conservative. The product is better than the marketing suggests. No superlatives, no buzzwords, no hype. Features are described functionally, not aspirationally. If anything, the marketing undersells — you discover capabilities the website didn't mention. The product speaks for itself. | Pinboard (understated everything), SQLite (documentation is the marketing), Signal (minimal marketing, product speaks), tools where the README is the entire marketing |

**Scoring notes**: Compare the marketing page to the actual product experience. Sign up and use the product — does it match? Check for: superlatives ("revolutionary", "blazing", "game-changing"), unsubstantiated claims ("AI-powered" without AI, "enterprise-grade" without enterprise features), and features listed in marketing that don't exist in the product. Products that demonstrate rather than claim score higher. "Show, don't tell" is the principle.

---

## 7.3a AI Content Transparency

**What it measures**: Whether user-facing AI content is disclosed at point of encounter. Scope: user-facing AI content only — generated text, AI chatbots, AI summaries, AI recommendations. Backend AI (fraud detection, spam filtering, internal ML) is out of scope.

**N/A condition**: If no user-facing AI content is detected through surface inspection → N/A. Note this as an acknowledged limitation in the Audit Scope section.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | AI content actively disguised as human. The product presents AI-generated text, images, or code as human-created work. Bylines on AI-written articles. "Hand-crafted" labels on AI-generated designs. The product profits from the illusion that humans did the work. Deliberately passing AI off as human is the core deception. | Content farms with AI articles under fake author names, "hand-made" products generated by AI, SEO spam disguised as expert writing |
| 25% | AI use is hidden through omission. The product uses AI significantly but never mentions it. No "AI-assisted" labels, no disclosure in about/methodology pages. Users reasonably assume human authorship because nothing suggests otherwise. The deception is passive, not active. | Products with AI-generated customer support pretending to be human agents, undisclosed AI writing |
| 50% | AI use disclosed but not at point of encounter. The product mentions AI somewhere (About page, blog post, FAQ) but doesn't label individual pieces of AI-generated content. A careful reader who investigates will find the disclosure. A casual user will encounter AI content without knowing its provenance. Disclosure exists but isn't functional. | Products with "we use AI" in the footer, AI-assisted products that disclose in Terms of Service but not in the UI |
| 75% | AI content labeled at point of encounter. AI-generated or AI-assisted content is marked where it appears ("Generated by AI," "AI-assisted"). Human-created content is distinguishable from AI content. The user knows what they're reading/using and can calibrate their trust accordingly. Minor gaps in labeling for edge cases. | ChatGPT (outputs clearly from AI), products with "AI-generated" badges on content, Google's AI overviews (labeled) |
| 100% | AI relationship is transparent and nuanced. Not just "AI" or "human" labels — the product explains the AI's role precisely. "AI-drafted, human-edited." "AI-suggested, human-approved." "AI-summarized from these sources." The user understands exactly how AI contributed to what they're seeing. AI is a disclosed tool, not a hidden ghost writer. | Products with detailed AI methodology pages, tools that show AI confidence scores, products that attribute AI contributions specifically |

**Scoring notes**: Score N/A for products with no detectable user-facing AI content (e.g., Sparrow, Vexl). For products where AI use is ambiguous (e.g., customer support chatbots that may or may not be AI), score based on what's detectable from the surface. A product that labels each AI-generated piece scores 75%. The rising baseline: as AI becomes ubiquitous, disclosure becomes more important, not less.

---

## 7.3b Human Authorship Signal

**What it measures**: Whether the content shows evidence of human creation — voice, opinions, personal references, irregular rhythm. Overlaps with Cat 1 but from the honesty dimension: "is this honest about its origins?"

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Content has zero human signal. Every text surface reads as machine-generated or template-derived. No opinions, no personal references, no irregular rhythm, no evidence that a human made deliberate word choices. The content is honest about nothing because there's nothing honest in it. | AI content farms, white-label products with zero original copy |
| 25% | Minimal human signal. Most content is generic or template-derived. Occasional human touches (a blog post, an about page) but the product's primary text surfaces show no evidence of human authorship. The product could have been generated by a well-prompted LLM and you wouldn't know the difference. | Products with AI-generated marketing and one human-written founder letter |
| 50% | Mixed signals. Some surfaces show clear human authorship (blog posts with opinions, error messages with personality) while others are generic or template-derived. The product isn't consistently honest about its origins — some content was clearly written, other content could be anything. | Products with strong blog content but generic app copy |
| 75% | Consistent human signal. Most content shows evidence of human creation — opinions, domain expertise, personal references, product-specific language. Voice is identifiable and consistent. The content is credibly human across most surfaces, with minor gaps in secondary copy. | Basecamp, Pinboard, indie products with strong founder voice |
| 100% | Unmistakably human. Writing has idiosyncratic voice, irregular rhythm, personal vocabulary, and references that no model would generate. Opinions are strong and specific. The content is not just human-written but distinctively so — you can tell who wrote it. The honesty of the content is self-evident. | Craig Mod's products, Julia Evans' work, patio11's writing — writing that could only come from one person |

**Scoring notes**: This check measures honesty of origins, not writing quality. A product with mediocre but clearly human-written copy scores higher than one with polished but indeterminate copy. Look for: personal anecdotes, specific opinions, irregular sentence structure, domain-specific humor, references to real experiences. Products where every surface reads as "could be AI, could be human" score 50% regardless of quality.

---

## 7.4 No Degraded Free Experience

**What it measures**: Whether the free tier is genuinely useful on its own, or whether it's deliberately crippled to force upgrades — feature hostage-taking.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Free tier is a trap. The product advertises "free" but the free experience is deliberately broken or useless. Core features are locked behind paywalls with no meaningful free alternative. The free tier exists solely to collect your data and nag you to upgrade. You can sign up for free and do nothing of value. | Products with "free" accounts that can only view, not create. "Freemium" where the free tier has no usable features. Mobile games where progress is gated behind payment every 5 minutes. |
| 25% | Free tier is a demo, not a product. Core functionality is technically available but crippled — aggressive limits (3 projects, 100 records), watermarks on output, "powered by" branding you can't remove, nag screens on every session. The free experience is designed to be frustrating enough to force an upgrade, not useful enough to be a product. | Freemium products with crippling limits designed to frustrate, design tools with watermarks, products with persistent upgrade nags |
| 50% | Free tier is usable but constrained. Genuine functionality with reasonable limits. You can accomplish real work but hit ceilings that naturally drive upgrades (storage limits, team size limits, feature caps). The constraints feel like real product decisions, not artificial punishment. Upgrade messaging exists but isn't aggressive. | Standard freemium SaaS (Notion free, Figma free, GitHub free), products with generous but bounded free tiers |
| 75% | Free tier is a real product. Full core functionality without crippling limits. Paid tier adds power-user features, team collaboration, or scale — not basic functionality. A user who never pays gets genuine value indefinitely. The free tier is good enough that paying feels like a choice, not a necessity. | Basecamp (personal tier is generous), GitHub free (unlimited public repos), products where free is a complete experience |
| 100% | No degraded experience at any tier. Either the product is fully free (donation/grant-funded), or there's only one tier (you pay or you don't use it — honest about the exchange). No artificial limitations designed to frustrate. If a free tier exists, it's indistinguishable from paid for individual use. | Signal (fully free, donation-funded), Wikipedia (free, donation-funded), PPQ.AI (pay per use — no free tier to degrade, no subscription to game), Claude Code (one entry price, no free tier to degrade), open source tools |

**Scoring notes**: Sign up for the free tier and use it for a real task. Ask: could someone genuinely use this product without paying, indefinitely? Does the free experience feel like a product or a demo? Count upgrade nags encountered during a 30-minute session. **Paid-only products**: If there is only one tier (pay or don't use it), score 100% — there is no degraded experience because there is no tier system. If multiple paid tiers exist, score based on whether lower tiers are genuinely useful or deliberately crippled to force upgrades. The check measures tier fairness, not the existence of payment. Pay-per-use products with no subscription score 100% — every use is a complete experience.

---

## 7.5 Dialogue, Not Broadcast

**What it measures**: Whether the product enables two-way communication — can users talk back? Is there a reply mechanism, issue tracker, public discussion forum, or feedback channel?

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Pure broadcast, no feedback channel. The product publishes content with no mechanism for response. No comments, no forum, no issue tracker, no reply-to email, no social media presence that responds. The product talks at you and has no interest in hearing back. Communication is one-directional by design. | Corporate websites with no contact information, content platforms with disabled comments and no forum, products with only a no-reply email address |
| 25% | Feedback channel exists but is performative. A contact form that goes into a black hole. A support email that auto-responds with ticket numbers and never resolves. Social media presence that only broadcasts, never responds to replies. Comments enabled but never replied to by the team. The illusion of dialogue without the substance. | Products with unresponsive support, corporate social media with zero engagement, blogs with comments enabled but never acknowledged |
| 50% | Functional feedback channel with limited dialogue. Support ticket system that resolves issues. Contact form with real responses. But no public discussion — feedback is private and one-to-one. Users can report problems but can't discuss the product with each other or influence direction publicly. The product listens but doesn't converse. | Standard SaaS with email support, products with help desks, blogs with moderated comments |
| 75% | Active public dialogue. Public issue tracker where users can see and discuss problems. Community forum or discussion space. The team responds to user feedback visibly. Feature requests are acknowledged and sometimes implemented. Users can influence the product's direction through public channels. | GitHub projects with active issue trackers, products with public roadmaps, Basecamp (public blog with responses), indie products with active community forums |
| 100% | Dialogue is built into the product's architecture. Reply mechanisms, public issue trackers, community-driven development, open RFC processes. Users don't just report — they contribute. The product's direction is a conversation between builders and users. Criticism is welcomed, not suppressed. The feedback loop is the product's immune system. | Open source projects with active contribution (SQLite, Linux), Nostr (protocol-level replies), products with public RFC/proposal processes |

**Scoring notes**: This check applies to content-publishing products (`[if:content]`). Check for: reply/comment mechanisms, public issue tracker (GitHub Issues, etc.), community forum, responsive social media presence, feedback form with real responses. Test the feedback channel — send a message and see if you get a human response. A product with a contact form that never responds scores the same as one with no contact form (25%). The test is whether dialogue actually happens, not whether the mechanism exists.

---
