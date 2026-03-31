# Cat 4: Product Craft — Scale Anchors

Reference: check-inventory.md

> **Scoring floor**: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension.

---

## 4.1 Shipped Ready

**What it measures**: Whether the core flow works on first use — no placeholder data, no spinner traps, no brutal error handling. The product is genuinely ready for a stranger to use it.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The product shipped its development state. Placeholder data visible in production ("John Doe", "+20.1%", "$XX.XX"). Console errors on page load. Core flow broken — the thing the product is supposed to do doesn't work without workarounds. The user is unwillingly beta-testing an alpha. | Products with "Lorem ipsum" in production, demo data that was never replaced, broken checkout flows, 500 errors on primary actions |
| 25% | Core flow technically works but the experience is fragile. Spinner-for-everything — no optimistic UI, so every action feels like it might fail. Error handling is brutal: "Something went wrong" with no context, no recovery path, no explanation. Placeholder data appears in edge cases (empty avatars, "+0%" metrics). The product works if everything goes right and falls apart the moment anything doesn't. | Products with spinner traps (loading spinner on every interaction, no optimistic updates), generic error toasts, visible placeholder data in secondary views |
| 50% | Core flow is solid, secondary flows have rough edges. Primary feature works reliably on first use. Error messages exist but are generic. Loading states are handled but not elegant (spinners, not skeletons). A new user can accomplish the main task but encounters friction on their second or third session. | Average early-stage SaaS products with a working MVP and unpolished edges |
| 75% | Product feels ready. Core and secondary flows work reliably. Error handling is specific ("Your file is too large — maximum 10MB" rather than "Upload failed"). Loading states use skeletons or optimistic UI. Edge cases are handled, not ignored. A stranger can use the product without encountering any "not ready" artifacts. | Linear (shipped polished from day one), Notion's core editor experience, Vercel Dashboard |
| 100% | Indistinguishable from a mature product on first use. Zero placeholder data, zero spinner traps, zero brutal errors. Every state — loading, empty, error, success — is designed. The product handles network failures, edge cases, and unexpected input gracefully. You forget it's new because nothing reminds you. | Stripe's Dashboard, Superhuman's initial launch, Apple's first-party apps |

**Scoring notes**: Create a fresh account and complete the primary flow. Note every moment of friction: placeholder data, spinners longer than 200ms without visual feedback, error messages that don't explain the problem, states that feel unfinished. Spinner traps (no optimistic UI), brutal error handling ("Something went wrong"), and placeholder data in production are each individually sufficient for 25% or below.

---

## 4.2 Orphaned Features

**What it measures**: Whether every feature is accessible, working, and connected to the product — no dead settings, broken links, "coming soon" placeholders, or empty dashboards.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The product is a graveyard of abandoned features. Settings pages with toggles that do nothing. Navigation items leading to empty pages. "Coming soon" placeholders that have been there for months. Broken links throughout. The product has more dead features than living ones. | Abandoned SaaS products still accepting signups, products with "Beta" features from 2 years ago that never left beta |
| 25% | Multiple orphaned features visible. At least one nav item leads to an empty or broken page. Settings exist that have no visible effect. "Coming soon" or "Beta" labels on features that appear unmaintained. The product was clearly more ambitious than its maintenance capacity. | Products with empty "Analytics" dashboards, broken integrations listed as available, settings pages with nonfunctional toggles |
| 50% | Most features work but some are clearly neglected. Primary features are well-maintained. One or two secondary features feel stale (last updated months ago) or partially broken. No dead links, but some features are clearly not the team's priority. The product is functional but has visible maintenance debt. | Average SaaS with a working core and some neglected secondary features |
| 75% | All features are live and functional. No dead settings, no broken links, no "coming soon" placeholders. Features that were started are finished. If a feature is listed, it works. Minor signs of age in rarely-used features (slightly outdated UI) but everything functions. | Basecamp (deliberately few features, all maintained), Todoist, Pinboard |
| 100% | Every feature is not just functional but maintained. No feature exists that the team isn't actively caring for. Deprecated features are removed, not abandoned. The product has exactly the features it needs and zero it doesn't. The feature list reflects deliberate restraint, not accumulated ambition. | Signal (narrow scope, everything works perfectly), SQLite (exhaustive testing, nothing orphaned), Tailwind CSS |

**Scoring notes**: Click every navigation item and every settings toggle. Visit every page linked from the main navigation. Check for: empty pages, "coming soon" labels, broken links (404s), settings that toggle without visible effect, features listed in marketing but absent in product. One orphaned feature in a product with 50 features is less damaging than one in a product with 5.

---

## 4.3 Show Me the Code

**What it measures**: Builder-mode signals of care — whether the shipped code shows review discipline or whether debug remnants, inconsistent patterns, and development artifacts leaked into production.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Production code is a development environment. `console.log("here")`, `console.log("TODO")`, `// HACK:` comments visible in source. Debug endpoints exposed. Source maps in production revealing internal architecture. Environment variables visible in client-side code. The product shipped its development branch. | Products with debug logging in the browser console, exposed `.env` values in page source, commented-out code blocks visible in production JS |
| 25% | Development artifacts leaked through inadequate review. `console.log` statements in production (not debug-level logging, but literal development prints). Inline styles mixed with a CSS framework (Tailwind class on one element, `style="margin-top: 12px"` on the next). Dead code shipped (commented-out features, unused imports visible in source). The builder didn't do a final review pass. `console.log("here")` in production, inline styles mixed with Tailwind = shipped without review. | Products where opening DevTools console shows debug output, CSS that mixes paradigms within the same component, visible dead code in view-source |
| 50% | Code is clean but unremarkable. No debug artifacts, no mixed patterns, no dead code. But also no sign of deliberate craft — default configurations, standard patterns, nothing optimized. The code works and was reviewed, but not refined. | Average well-maintained web applications, standard framework starter projects in production |
| 75% | Code shows review discipline. Consistent patterns throughout. No debug artifacts. Performance basics covered (images optimized, no render-blocking resources). Error boundaries in place. The code reads like someone cared about the next person who would read it. | Well-maintained open source projects, Vercel's templates, well-run agency work |
| 100% | Production code is exhibition-quality. Consistent architecture, optimized bundles, thoughtful error boundaries, graceful degradation. No dead code, no debug artifacts, no mixed patterns. View-source reveals a codebase that was built with intention. Lighthouse scores in the 90s not from gaming but from genuine care. | Stripe's frontend, Linear's client code, thoughtfully built open source projects (Tailwind CSS source) |

**Scoring notes**: Open DevTools. Check the console for debug output. View page source for inline styles mixed with framework classes, commented-out code, and TODO comments. Check network tab for source maps, oversized bundles, and unoptimized assets. `console.log("here")` in production or inline styles mixed with Tailwind are individually sufficient for 25% or below — they indicate code was shipped without a review pass.

---

## 4.4 Iteration Visible

**What it measures**: Whether the product shows evidence of ongoing development — changelogs, release notes, visible commit history, documented decisions, and the scars of shipping and learning.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | No evidence the product has changed since launch. No changelog, no release notes, no blog posts about development, no visible version history. The product appears frozen — either abandoned or deliberately hiding its development process. A user cannot tell if it's actively maintained. | Abandoned products still online, "set and forget" SaaS with no visible updates in 12+ months |
| 25% | Iteration happened but isn't visible. The product has clearly been updated (new features exist) but there's no record of what changed or when. No changelog. Maybe a blog post from launch and nothing since. Users discover changes by accident. The development process is a black box. | Products that update silently, apps with no changelog or release notes, SaaS where features appear and disappear without explanation |
| 50% | Some iteration is documented but inconsistently. A changelog exists but is updated sporadically. Release notes for major versions but not minor ones. The product communicates big changes but not the ongoing work between them. You know it's maintained but can't follow the development story. | Products with quarterly blog posts about major features, apps with app-store-only release notes ("Bug fixes and improvements") |
| 75% | Iteration is consistently visible. Regular changelog or release notes. Blog posts about development decisions. The user can follow the product's evolution and understand why things changed. Hard decisions are documented, not hidden. The product visibly learns from its users. | Basecamp (public development blog, detailed changelogs), Linear (weekly changelog), Tailwind CSS (detailed release notes) |
| 100% | Development is part of the product's identity. Ship-ugly-iterate-publicly is visible. Early versions are acknowledged, not hidden. Changelogs include reasoning, not just feature lists. Commit history or development process is accessible. The product wears its iteration as a badge — you can see the journey from v1 to now and understand every turn. | Oxide Computer's development blog, Pinboard's feature blog, indie developers with public build logs, SQLite's fossil repository |

**Scoring notes**: Check for: changelog or release notes page, blog posts about development, visible version numbers, commit history (if open source), app store release notes quality. "Bug fixes and improvements" as the only release note format is worth 25-50% — it technically documents iteration but communicates nothing. Products that document decisions (why something changed, not just what changed) score higher than those that only list features.

---
