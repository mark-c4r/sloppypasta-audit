# Cat 2: Writing & Thinking — Scale Anchors

Reference: check-inventory.md

> **Scoring floor**: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension.

---

## 2.1 Economy of Words

**What it measures**: Banned-word and phrase density per 1000 words — how much filler, hedging, and corporate bloat infects the product's text.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Text is padding held together by buzzwords. Banned-word density above 10 per 1000 words. Every sentence hedges, qualifies, or restates the previous one. Reading it teaches you nothing. The text exists to fill space, not to communicate. | AI-generated "About Us" pages, enterprise SaaS marketing copy ("leverage synergies to drive holistic solutions") |
| 25% | Bloated but communicative. Banned-word density 5-10 per 1000 words. The point is in there somewhere, buried under qualifiers and corporate-speak. You could cut 40% of the text and lose zero meaning. | Most B2B SaaS product pages, corporate blog posts |
| 50% | Functional but unedited. Banned-word density 2-5 per 1000 words. Gets the job done without being painful. Occasional filler phrases but the ratio of signal to noise is adequate. A first draft that could use a red pen pass. | Average indie product documentation, standard README files |
| 75% | Clean and purposeful. Banned-word density under 2 per 1000 words. Each paragraph earns its place. Rare instances of filler are isolated, not systemic. Someone edited this and asked "does this sentence add anything?" | Stripe's documentation, Linear's product copy |
| 100% | Every word works. Zero banned-word density. No hedging, no qualifiers, no padding. Dense with meaning. Reading it feels like the writer respects your time. Could not be shortened without losing information. | Basecamp's "Getting Real" essays, Apple's original product copy under Jobs |

**Scoring notes**: Use the 49 banned words, 38 phrases, and 16 openers list for quantitative measurement. Calculate density per 1000 words of product-facing text (UI copy, docs, marketing). Ignore user-generated content. A product with 200 words of perfect copy scores higher than one with 2000 words of mediocre copy — economy means knowing when to stop writing.

---

## 2.2 Copy Is Interface Design

**What it measures**: Whether the product's text actively guides, orients, and instructs users — or whether it's decorative filler disconnected from the interface.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Copy actively misleads or obstructs. Button labels don't match actions. Error messages are meaningless ("Error: null"). Placeholder text shipped to production ("Lorem ipsum" or "Add description here"). The text makes the product harder to use. | Products with "Click here" buttons everywhere, error modals showing stack traces, shipped placeholder text |
| 25% | Copy exists but doesn't guide. Generic labels ("Submit", "Cancel", "OK") that could belong to any product. Empty states say "No items found" with no next step. Onboarding text is marketing copy pasted into a tooltip. The text occupies space without earning it. | Products with dead-end empty states ("No results"), generic form labels, tooltip text copied from the marketing site |
| 50% | Copy is correct but passive. Labels accurately describe features. Error messages name the problem. But the text doesn't anticipate what the user needs next. No proactive guidance, no personality, no awareness of context. Functional but forgettable. | Average web apps with accurate but generic copy |
| 75% | Copy works as a guide. Empty states suggest actions ("No projects yet — create your first one"). Error messages explain what happened AND what to do. Labels use the user's vocabulary, not the developer's. The text anticipates confusion and prevents it. | Basecamp's interface copy, Notion's empty states, Linear's contextual help |
| 100% | Copy is inseparable from the interface. Remove the text and the product breaks. Labels teach the product's mental model. Microcopy handles edge cases gracefully. The voice is consistent, the tone matches the moment (serious for errors, encouraging for empty states). The text is the interface. | Stripe's API documentation (copy IS the product), Superhuman's command labels |

**Scoring notes**: Test by reading only the text with the visual design removed. Does the copy alone tell you where you are, what you can do, and what happens next? Score empty states, error messages, onboarding text, and button labels separately — the worst one anchors the score.

---

## 2.3 No Throat-Clearing

**What it measures**: Whether content gets to the point or wastes the reader's time with filler openings, hedging seesaws, and padding paragraphs.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Every piece of content opens with a preamble about itself. "In today's rapidly evolving landscape..." or "As we all know..." before any substance. Paragraphs alternate between Position A and Position B without committing. The content is a time tax on the reader. | AI-generated blog posts that open with "In the world of...", content-mill articles, most LinkedIn thought leadership |
| 25% | Frequent throat-clearing that delays substance. Most articles need 2-3 paragraphs before the point arrives. Some hedging seesaws ("On one hand... on the other hand... ultimately...") that avoid taking a position. The useful content is there but you have to dig for it. | Corporate blogs, most Medium articles, enterprise product documentation |
| 50% | Occasional filler but substance arrives within the first paragraph. Some articles open strong, others lapse into preamble. Hedging appears but doesn't dominate. The writer has a point and mostly gets to it, with occasional detours. | Average tech blogs, decent product changelogs |
| 75% | Consistently gets to the point. First sentence of each piece earns attention. Rare instances of padding and they're usually in transitional paragraphs, not openings. When presenting multiple sides, the writer's position is clear. | Signal's blog posts, Tailwind CSS documentation, Pinboard's feature descriptions |
| 100% | Opens with the point. Every paragraph advances the argument. No filler openings, no hedging seesaws, no padding. If the writer isn't sure about something, they say "I don't know" rather than hedge for three paragraphs. Dense, direct, respectful of the reader's time. | Craig Mod's essays, Maciej Ceglowski's talks, patio11's writing |

**Scoring notes**: This check applies only to products that publish editorial content (`[if:content]`). Static tools, protocols, and CLI apps without content sections are N/A. Evaluate the first 3 paragraphs of each content piece — throat-clearing concentrates at openings. A product with 5 excellent articles and 2 throat-clearers scores on the pattern, not the exceptions.

---
