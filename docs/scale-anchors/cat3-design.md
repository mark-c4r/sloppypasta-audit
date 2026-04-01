> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as deep calibration reference.
# Cat 3: Design & Interface — Scale Anchors

Reference: check-inventory.md

> **Scoring floor**: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension.

---

## 3.1 Information Density

**What it measures**: How effectively the product uses screen real estate — items per viewport, intentional whitespace versus uniform padding, respect for the user's display.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Wall of undifferentiated content. No visual hierarchy — every element has equal weight, equal spacing, equal size. A wall of text with no headings, or a grid where every card is identical with no way to scan for what matters. The user must read everything to find anything. Alternatively: one giant hero image per viewport with content hidden below the fold. | Landing pages that are 90% stock photography, unformatted documentation dumps, content behind infinite scroll with no landmarks |
| 25% | Low density with poor whitespace logic. 2-3 items per viewport when 6-8 would fit. Spacing doesn't communicate grouping — related items have the same gaps as unrelated ones. Content is there but spread so thin you spend more time scrolling than reading. The layout treats a 27" display like a phone screen. | Most marketing-first SaaS dashboards, "modern" redesigns that halved density |
| 50% | Adequate density, uninspired layout. Reasonable items per viewport. Whitespace is consistent but not communicative — it doesn't help you parse relationships. Standard grid, standard spacing, standard everything. Twitter's main feed: functional density, no hierarchy innovation. | Average web apps, default Bootstrap/Tailwind layouts, Twitter's timeline |
| 75% | Density serves comprehension. Whitespace communicates hierarchy — tight within groups, generous between groups. Information-rich without feeling cramped. The layout reveals the content's structure at a glance. You can scan, not just scroll. Sparrow's UTXO interface: dense financial data made legible through spatial grouping. | Linear's issue boards, Hacker News, Sparrow wallet UTXO view, Notion's table views |
| 100% | Layout communicates data hierarchy without labels. The spatial arrangement alone tells you what's primary, secondary, and metadata. Every viewport is packed with information that's instantly scannable. Resizing the window shows the layout was designed for multiple densities. Density is a deliberate design decision that respects both the content and the user's time. | Bloomberg Terminal, Figma's canvas UI, well-designed financial dashboards |

**Scoring notes**: Count visible items per viewport at 1440px width. Compare spacing between related items versus unrelated items — if they're the same, whitespace is decorative, not functional. The window resize test is critical: slowly drag to ~800px and watch what happens. Products that degrade gracefully were designed; products that break were assembled.

---

## 3.3 Design System Consistency

**What it measures**: Whether the product uses consistent visual tokens — spacing, type scale, color, and component patterns — across all pages and states.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | No tokens, pure inline styles, inconsistent spacing. Multiple type scales on the same page. `style="margin-top: 12px"` next to `style="margin-top: 17px"` with no system. Colors are arbitrary hex values, not a palette. Components serving the same function look different on every page. The product looks like it was assembled from unrelated code snippets. | Frankensteined WordPress sites, AI-generated pages with inline styles, incompatible UI library mixtures |
| 25% | A design system was intended but not enforced. Buttons come in 3 styles. Spacing mostly works on the landing page but breaks on secondary pages. **Window resize test**: drag to ~800px and the layout breaks — overlapping elements, orphaned components, broken grids. Strong signal of AI-generated code never tested at intermediate widths. | Products polished on landing page, broken in settings/profile/secondary pages |
| 50% | Consistent within sections, inconsistent across them. Dashboard follows one system, marketing site another, settings page a third. Each section looks fine alone but navigating between them reveals seams. Token values are close but not identical (14px vs 15px body text). Standard framework defaults, competently applied. | Many SaaS products with separately-designed marketing and app sections |
| 75% | One type scale, one spacing system, one color palette across all pages. Components are clearly from the same system. The window resize test shows graceful degradation. Rare exceptions in legacy pages. The design system is documented and mostly enforced. | Linear, Notion, Vercel Dashboard |
| 100% | Custom design language that could not be mistaken for another product. Every page, state, and edge case follows the same token system. New features look like they were always there. The system is enforced by tooling, not documentation. Resize to any width and the layout responds as a coherent system. You recognize the product by its visual grammar alone. | Stripe's Dashboard, Apple's native apps, Figma's interface |

**Scoring notes**: Check at least 5 pages including: landing/marketing, main feature, settings/profile, empty states, error states. Measure body text size, heading scale, spacing between components, and button styles. The window resize test (slowly drag to ~800px tablet width) is the highest-signal single test — AI-generated layouts almost always break at intermediate widths because they were generated for desktop and mobile, not the continuum between them.

---

## 3.4 Self-Evident UI

**What it measures**: Whether users can navigate, recover from mistakes, and handle empty/edge states without external help or prior training.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Requires external documentation to use basic features. No undo for destructive actions. No back button or breadcrumbs. Controls don't signal what they do — flat text that's actually a button, icons with no labels, interactive elements indistinguishable from decoration. Empty states are dead ends. The user must read a manual or guess. | Products with permanent delete (no undo), unlabeled icon-only toolbars, wizard flows with no back button |
| 25% | Navigation exists but controls are ambiguous and edge states neglected. Buttons look like text, text looks like buttons. Empty states say "No items found" with no call to action. Undo exists for some actions but not others. Users can navigate the happy path by trial and error but get stuck at every branch point. | Dead-end empty states, flat UI where clickable and non-clickable elements look identical, inconsistent undo |
| 50% | Happy path is self-evident, edge cases require learning. Main features are discoverable. Controls generally look interactive. Empty states exist but are generic. Undo works for common actions. A new user can complete the primary flow without help but will need documentation for advanced features. | Average web applications with adequate but not thoughtful UX |
| 75% | Most interactions are self-evident including edge cases. Controls signal capability through shape, color, and position — buttons look pressable, links look followable, sliders look draggable. Empty states guide users toward their first action. Undo/back available for all destructive operations. A new user can explore confidently. | Basecamp (undo on delete, meaningful empty states), Todoist, Notion |
| 100% | Interface teaches itself through progressive disclosure. Complex features emerge naturally from simple ones. Controls signal capability through form alone — no labels needed for obvious interactions, labels provided for ambiguous ones. Empty states are onboarding moments. Every destructive action has undo with a clear time window. The UI's physical design communicates its logic. | Stripe's onboarding flow, Linear's contextual guidance, Gmail's undo-send |

**Scoring notes**: Test the three edge states: empty (new account, no data), error (trigger a failure), and recovery (try to undo or go back). Dead-end empty states ("No items found" with no CTA) are a strong signal of 25% or below — they indicate the developer only built the happy path. Score the worst edge state, not the average.

---

## 3.5 Modal-Free Experience

**What it measures**: Absence of hostile modals — popups-on-load, newsletter overlays, login-wall interstitials, cookie-wall content blockers. Functional dialogs (confirm delete, save changes) are fine.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The product is a modal delivery system. Popup on page load, newsletter overlay after 3 seconds, login wall behind the first modal, cookie consent blocking all content underneath. The user must dismiss 2-3 modals before seeing any content. The product literally stands between you and the thing you came for. | News sites with overlay + login wall + cookie wall stacked, Instagram's "log in to continue" on public content |
| 25% | Frequent hostile modals that interrupt natural use. Newsletter popup appears on every visit (not just first). "Download our app" interstitial on mobile. Login walls on content that should be public. The product lets you see content but nags you every session. | Sites with persistent newsletter popups, "get the app" interstitials on mobile web, Medium's read-limit modal |
| 50% | Occasional modals that are annoying but not blocking. Newsletter popup on first visit only, dismissible, doesn't return. Cookie consent is a banner, not a wall. One modal in the first session that stays dismissed. The product respects your choice after one interaction. | Average SaaS products with first-visit signup prompts, standard cookie banners |
| 75% | Modals reserved for genuine user-initiated actions. Confirmation dialogs for destructive operations. Save-before-leaving warnings. No marketing modals, no newsletter popups, no login walls on public content. The product never interrupts you to sell you something. | Basecamp, most well-designed developer tools, Hacker News |
| 100% | No interruptions of any kind. Content is accessible without any overlay, popup, or interstitial. If the product needs input, it uses inline UI, not modals. The interface never takes control away from the user. Even confirmation dialogs are replaced with undo patterns where possible. | Pinboard, Craig Mod's memberships site, static documentation sites (MDN, DevDocs) |

**Scoring notes**: Visit the product in a fresh browser (no cookies, no login) and count modals encountered before reaching primary content. Each hostile modal (popup, overlay, interstitial, wall) reduces the score. Functional modals (confirm delete, unsaved changes) don't count against the score. A cookie consent banner that blocks content until accepted counts as a hostile modal. A non-blocking cookie banner does not.

---

## 3.6 Accessibility Basics

**What it measures**: Fundamental accessibility care — contrast ratios, tap target sizes, screen reader landmarks, focus management. Not WCAG compliance — a care signal.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Accessibility is actively broken. Light gray text on white backgrounds (below 3:1 contrast). Tiny tap targets (under 24px). No semantic HTML — entire page is nested divs. Keyboard navigation impossible. Screen readers encounter an undifferentiated wall of content. Unusable for anyone with visual, motor, or cognitive needs. | Div-soup markup, no ARIA landmarks, mouse-only interactions |
| 25% | Accessibility never considered. Focus states removed with `outline-none` and no replacement — keyboard users cannot see where they are. Some semantic HTML but inconsistent (headers skip levels, nav not marked). Contrast fails on secondary text. Broken focus states are an AI code tell — LLMs remove outlines for aesthetics without understanding they're critical. | Products with `outline-none` globally, skipped heading levels, buttons under 44px on mobile |
| 50% | Basic accessibility present but accidental. Contrast passes on primary text, fails on secondary (placeholder text, captions, metadata). Focus states are browser defaults (not styled). Some ARIA labels on obvious elements (nav, main) but not on icon buttons or dynamic content. Semantic HTML in main content but not forms. A screen reader user can navigate the main flow with difficulty. The gap between this and 75% is intentionality — this product didn't break a11y, but it didn't design for it either. | Average web apps that haven't explicitly broken accessibility |
| 75% | Deliberate accessibility effort. Contrast ratios pass everywhere including secondary text. Custom focus styles matching the design system. Proper heading hierarchy. ARIA labels on all icon buttons. Tap targets meet 44px minimum. A keyboard-only user can complete the primary flow. The gap from here to 90%+: focus management on dynamic content (modals, route changes) and prefers-reduced-motion. | Stripe Dashboard, GitHub, well-maintained component library products |
| 100% | Systematic accessibility as a design constraint. Focus management handles dynamic content — modals trap focus, route changes announce to screen readers. Skip-to-content links. `prefers-reduced-motion` respected. `prefers-color-scheme` supported. Screen reader experience is designed, not accidental. Tested with actual screen readers (not just automated checks). The product works well for everyone because it was built for the margins. | GOV.UK, BBC's web products, Apple's native accessibility features |

**Scoring notes**: Run a quick check: Tab through the page — can you see where focus is? Inspect body/secondary text contrast (4.5:1 minimum). Check heading hierarchy in the DOM. Test tap targets on mobile (44px minimum). The `outline-none` test is the single highest-signal check: search the CSS for `outline: none` or `outline: 0` — if present without a custom focus replacement, score 25% or below. This is a care signal, not a compliance audit.

---
