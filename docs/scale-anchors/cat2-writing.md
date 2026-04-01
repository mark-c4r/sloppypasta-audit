> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as deep calibration reference.
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

## 2.2a Copy Guides Action

**What it measures**: Whether the product's text tells you what to do, where you are, and what went wrong. Error messages, empty states, labels, CTAs.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | No guidance anywhere. Error messages say "Error." Empty states are blank. Button labels don't match actions ("Click here" everywhere). Placeholder text shipped to production. The user must guess every action — the text is actively hostile to comprehension. | Products with "Click here" buttons everywhere, stack trace error modals, "Lorem ipsum" in production |
| 25% | Generic labels that could belong to any product. "Submit", "Cancel", "OK" — nothing product-specific. Empty states say "No items found" with no next step. Error messages name the error code but not the fix. Onboarding text is marketing copy pasted into tooltips. The text occupies space without guiding action. | Dead-end empty states, generic form labels, "Something went wrong" errors |
| 50% | Labels accurately describe features. Error messages name the problem. But the text doesn't anticipate what the user needs next — no proactive guidance, no awareness of context. You can figure out what to do, but the copy doesn't help you. Functional but passive. | Average web apps with accurate but generic copy |
| 75% | Copy actively guides. Empty states suggest specific actions ("No projects yet — create your first one"). Error messages explain what happened AND what to try next. Labels use the user's vocabulary, not the developer's. The text anticipates confusion and prevents it before the user feels lost. | Basecamp's empty states, Notion's contextual help, Linear's error messages |
| 100% | Every state has specific, actionable copy. Errors explain what went wrong AND what to try. Empty states suggest next steps with specific CTAs. Labels disambiguate without tooltips. The copy alone — without any visual design — tells you where you are, what you can do, and what happens next. | Stripe's API documentation (copy IS the product), Superhuman's command labels |

**Scoring notes**: Test by reading only the text with the visual design removed. Score empty states, error messages, onboarding text, and button labels separately — the worst one anchors the score. A product with excellent labels but dead-end empty states scores on the weakest element.

---

## 2.2b Copy Shows Authorship

**What it measures**: Whether the copy could only exist in this product. Voice, specificity, personality — or interchangeable template text.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | All copy is interchangeable template text. "Welcome to [Product]. Get started today!" Nothing identifies this as a specific product. You could swap the product name and the copy would fit anywhere. Zero voice, zero personality, zero specificity. The copy was generated, not written. | AI-generated SaaS landing pages, white-label products with find-and-replaced names |
| 25% | Copy has a consistent tone but no distinctive voice. Professional, competent, forgettable. "We help teams collaborate more effectively." True of any product. Domain-specific jargon appears but doesn't reveal a perspective. The copy sounds like it was written by someone who read the brief but doesn't use the product. | Generic B2B SaaS copy, most corporate product pages |
| 50% | Occasional personality breaks through. Most copy is standard but some moments — an error message, a loading screen, a tooltip — reveal a human made a deliberate choice. The voice isn't consistent but it's present in spots. You can tell someone cared about some of the words. | Products with one memorable 404 page but generic everything else |
| 75% | Copy has a recognizable voice. Reading the text without the product name, you could identify it. Specific references, domain language, opinions about how things should work. The copy reflects the team's perspective, not a template. Personality is consistent across surfaces, not just sprinkled in easter eggs. | Basecamp ("We don't do that here"), Pinboard's feature descriptions, Linear's opinionated product copy |
| 100% | Copy has a distinctive voice that could not exist in any other product. Specific references, opinions, humor, or domain language that only this team would write. The writing has idiosyncratic rhythm, personal vocabulary, and a perspective that permeates every surface. Remove the logo and you'd still know the product. | Craig Mod's products, Panic's apps (Transmit, Nova), Superhuman's entire copy voice |

**Scoring notes**: Read the product's copy with the brand name removed. Could this text belong to any other product in the same category? If yes, score below 50%. Products with template-derived copy ("Built for teams who value...") score 25% regardless of polish. Voice consistency matters — one memorable 404 page doesn't compensate for generic everything else.

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
