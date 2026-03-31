> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as deep calibration reference.
# Text Slop Detection Reference

Self-contained reference for detecting AI-generated text in products.
Used by checks: 1.1 (LLM smell), 2.1 (economy of words), 2.3 (no throat-clearing)

## Banned Vocabulary (49 words)

Score: Count occurrences per 1,000 words of product text. Frequency-based, not binary.
- 0 per 1k words = clean
- 1-2 per 1k words = minor tells
- 3-5 per 1k words = likely AI-generated
- 6+ per 1k words = almost certainly unedited AI output

delve, tapestry, landscape, testament, vibrant, pivotal, crucial, intricate, meticulous, bolster, garner, underscore, interplay, multifaceted, nuanced, foster, leverage, utilize, commence, facilitate, encompass, paramount, groundbreaking, cutting-edge, game-changing, transformative, revolutionise, seamless, robust, comprehensive, endeavour, aforementioned, harnessing, spearheading, navigating, showcasing, highlighting, emphasizing, enhancing, unprecedented, remarkable, stunning, profound, epic, thought leader, synergy, pain points, value add, moving forward, touch base

## Banned Phrases (38 phrases)

Score: Presence of 2+ phrases in any single page = significant AI tell.

"In today's [adj] [noun]", "It's worth noting", "Not just X, but Y", "Let's dive in/deeper", "At its core", "In the realm of", "When it comes to", "A testament to", "This is where X comes in", "Whether you're a X or Y", "Unlock the power of", "Elevate your", "Streamline your", "Supercharge your", "Bridge the gap", "Move the needle", "Buckle up", "Take it to the next level", "Empower/empowering", "Harness the power of", "At the end of the day", "It goes without saying", "In a nutshell", "The bottom line is", "Rest assured", "Without further ado", "Having said that", "With that being said", "In light of", "As we navigate", "On a journey", "Pushing the boundaries", "Raising the bar", "Setting the stage", "Paving the way", "Breaking new ground", "Redefining [noun]", "The future of [noun]"

## Banned Openers (16 openers)

Score: Any product text (landing page, about page, docs, error messages, blog) opening with these = AI tell.

Certainly, Absolutely, Sure, Great question, That's a great point, I'd be happy to, However it's important to, Moreover, Furthermore, Additionally, Interestingly, Notably, Importantly, Indeed, In conclusion, To summarize

## Punctuation Thresholds

| Marker | Threshold | Significance |
|--------|-----------|-------------|
| Em dashes | >1 per 500 words | Single most cited AI marker |
| Exclamation marks | >1 per 1,000 words | Over-enthusiasm tell |
| Rule of Three | Lists of exactly 3 items | AI defaults to 3-item lists |
| Uniform sentence length | 3+ consecutive same-length sentences | Human writing varies naturally |
| Hedging seesaw | "On one hand... on the other..." without taking a position | AI avoids commitment |

## Structural Patterns

- **"Bold Prefix:" Bullet List**: Every bullet formatted as **Bold Summary Phrase:** followed by one explanatory sentence. THE #1 formatting tell.
- **"Zoom Out" Opening**: Over-contextualizing macro-trends instead of getting to the point. ("In today's fast-paced digital landscape...")
- **Symmetrical Paragraphs**: Every paragraph exactly 3-4 sentences. Human writing is chunky -- massive block followed by single punchy sentence.
- **"Conclusion" Header**: Literal `## Conclusion` or `## Final Thoughts` header.
- **"Crucially"/"Importantly" Crutches**: Fake transition words masking non-sequiturs.
- **Title Case Abuse**: Capitalizing concepts for false authority ("Our Advanced Algorithm System").

## Model-Specific First Words

| Model | Common First Words |
|-------|--------------------|
| ChatGPT | as, yes, sure, here, in, to, creating, certainly |
| Claude | in, from, this, how, yes, according, based |
| Grok | step, introduction, yes, creating |
| Gemini | my, creating, while, here |
| DeepSeek | based, yes, step, comprehensive |

## How to Use This Reference

1. Sample text from 3+ product surfaces (landing page, error messages, docs, onboarding, about page)
2. Count banned vocabulary per 1,000 words
3. Check for banned phrases (2+ = significant)
4. Check first sentences for banned openers
5. Measure punctuation densities against thresholds
6. Check for structural patterns (Bold Prefix lists, symmetrical paragraphs)
7. Score: density and variety of markers determines the 1.1 score per the scale anchors
