> **Note**: Operational scoring uses `docs/scoring-reference.md`. This file is preserved as deep calibration reference.
# Cat 3: Design & Interface — Scale Anchors

Reference: check-inventory.md

> **Scoring floor**: The minimum score for any check is 5% (not 0%). This prevents a single zero from catastrophically collapsing the geometric mean. A score of 5% indicates actively hostile behavior — the absolute worst case. Reserve it for products that deliberately harm users in this dimension.

---

## 3.1 Information Density

**What it measures**: How effectively the product uses screen real estate — items per viewport, intentional whitespace versus uniform padding, respect for the user's display.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Screen is hostile to information consumption. Massive hero images with no content. One item visible per viewport with the rest hidden behind pagination or infinite scroll. Whitespace is uniform padding — the same 48px gap between every element regardless of relationship. The product treats your 27" display like a phone screen. | Landing pages that are 90% stock photography, mobile-first designs that never adapted to desktop, single-item-per-screen e-commerce |
| 25% | Low density with poor whitespace logic. 2-3 items per viewport when 6-8 would fit naturally. Spacing doesn't communicate grouping — related items have the same gaps as unrelated ones. Content is there but spread so thin you spend more time scrolling than reading. | Most marketing-first SaaS dashboards, "modern" redesigns that halved information density |
| 50% | Adequate density, uninspired layout. Reasonable items per viewport for the content type. Whitespace is consistent but not communicative — it doesn't help you parse relationships. Nothing wastes space aggressively, but nothing optimizes for it either. Standard grid, standard spacing, standard everything. | Average web applications, default Bootstrap/Tailwind layouts without customization |
| 75% | Good density with intentional spacing. Screen real estate is respected. Whitespace communicates hierarchy — tight spacing within groups, generous spacing between groups. Information-rich without feeling cramped. The layout reveals the content's structure. | Linear's issue boards, Hacker News (extreme density, perfectly legible), Notion's table views |
| 100% | Density is a design decision, not an accident. Every viewport is packed with useful information. Whitespace is a tool — it groups, separates, and highlights. Resizing the window shows the layout was designed for multiple densities. The product shows you more because it respects your screen and your time. | Bloomberg Terminal (maximum density, trained users), Figma's canvas UI, well-designed financial dashboards |

**Scoring notes**: Count visible items per viewport at 1440px width. Compare spacing between related items versus unrelated items — if they're the same, whitespace is decorative, not functional. The window resize test is critical: slowly drag to ~800px and watch what happens. Products that degrade gracefully were designed; products that break were assembled.

---

## 3.2 Physical Obviousness

**What it measures**: Whether the product is usable without instruction — controls look interactive, affordances are clear, the interface communicates what it does through its form.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The interface hides its own functionality. Interactive elements look identical to static text. Navigation requires discovering invisible hover zones. Critical actions are behind unlabeled icons or gesture-only interactions with no fallback. Using the product requires a tutorial that doesn't exist. | Mystery-meat navigation sites, products where you must hover over blank areas to discover features, gesture-only mobile UIs with no visible controls |
| 25% | Controls exist but affordances are ambiguous. Flat design taken to the extreme — buttons look like text, links look like headings, interactive cards look like static content. Users must click experimentally to discover what's interactive. Icons are unlabeled and non-standard. | Ultra-minimal "design-forward" apps, products with icon-only toolbars using custom (non-standard) iconography |
| 50% | Most controls are identifiable but some require guessing. Primary actions are obvious, secondary actions less so. Standard patterns are followed for common features but custom UI elements lack clear affordances. A new user can complete the main flow but will miss secondary features. | Average web applications with a mix of clear and ambiguous controls |
| 75% | Interface communicates clearly. Buttons look clickable, inputs look fillable, draggable items look grabbable. Standard patterns used consistently. A new user can discover most features through visual exploration alone. Minor affordance gaps in edge-case features. | Basecamp's interface, Todoist, well-designed CRUD applications |
| 100% | The interface teaches itself. Every interactive element signals its capability through shape, color, or position. Disabled states explain why. Progressive disclosure reveals complexity only when needed. A user who has never seen the product can complete any flow by following visual cues alone. | Apple's best native apps (Calculator, Notes), Stripe Dashboard's action flows |

**Scoring notes**: Test with the "5-second rule" — show a screenshot to someone unfamiliar with the product. Can they identify the primary action within 5 seconds? Check for: buttons with clear boundaries, hover/focus states that confirm interactivity, labels on icons (or universally understood icons only), disabled states that explain themselves.

---

## 3.3 Design System Consistency

**What it measures**: Whether the product uses consistent visual tokens — spacing, type scale, color, and component patterns — across all pages and states.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | Visual chaos. Multiple type scales on the same page. Spacing values look random — 12px here, 17px there, 24px elsewhere with no system. Colors shift between pages. Components that serve the same function look different depending on where they appear. The product looks like it was built by 10 people who never spoke to each other. | Frankensteined WordPress sites with mixed plugins, products assembled from incompatible UI libraries |
| 25% | Inconsistency is the pattern. A design system may have been intended but wasn't enforced. Buttons come in 3 different styles. Spacing mostly works but breaks on secondary pages. **Window resize test**: drag to ~800px tablet width and the layout breaks — overlapping elements, orphaned components, broken grids. This is a strong signal of AI-generated code that was never tested at intermediate widths. | Products that look polished on the landing page but fall apart in settings/profile/secondary pages |
| 50% | Consistent within sections, inconsistent across them. The dashboard follows one system, the marketing site another, the settings page a third. Each section looks fine alone but navigating between them reveals the seams. Token values are close but not identical (14px vs 15px body text). | Many SaaS products with separately-designed marketing and app sections |
| 75% | Strong consistency with minor drift. One type scale, one spacing system, one color palette across all pages. Rare exceptions in legacy or rarely-visited pages. Components are clearly from the same system. The window resize test shows graceful degradation — the layout adapts, doesn't break. | Linear, Notion, Vercel Dashboard |
| 100% | Pixel-level consistency everywhere. Every page, every state, every edge case follows the same token system. New features look like they were always there. The design system is enforced by tooling, not just documentation. Resize to any width and the layout responds as a coherent system. | Stripe's Dashboard, Apple's native apps, Figma's interface |

**Scoring notes**: Check at least 5 pages including: landing/marketing, main feature, settings/profile, empty states, error states. Measure body text size, heading scale, spacing between components, and button styles. The window resize test (slowly drag to ~800px tablet width) is the highest-signal single test — AI-generated layouts almost always break at intermediate widths because they were generated for desktop and mobile, not the continuum between them.

---

## 3.4 Self-Evident UI

**What it measures**: Whether users can navigate, recover from mistakes, and handle empty/edge states without external help or prior training.

| Score | Behavioral Description | Product Example |
|-------|----------------------|-----------------|
| 0% (5% floor) | The product actively traps users. No undo for destructive actions. No back button or breadcrumbs. Empty states are dead ends — "No items found" with no explanation and no path forward. Errors provide no recovery path. Users must start over from scratch when something goes wrong. | Products with permanent delete (no confirmation, no undo), wizard flows with no back button, apps that lose your work on browser back |
| 25% | Navigation exists but edge states are neglected. Empty states show "No items found" with no call to action — the user stares at a blank screen wondering what to do. Error handling is present but unhelpful ("Something went wrong. Try again."). Undo exists for some actions but not others. Users can navigate the happy path but get stuck the moment something unexpected happens. | Products with dead-end empty states, inconsistent undo behavior, error messages that don't explain the problem |
| 50% | Happy path is self-evident, edge cases require learning. Main features are discoverable through the UI. Empty states exist but are generic. Undo works for common actions. A new user can complete the primary flow without help but will need documentation for advanced features. | Average web applications with adequate but not thoughtful UX |
| 75% | Most interactions are self-evident including edge cases. Empty states guide users toward their first action. Undo/back is available for all destructive operations. Error messages explain what happened and suggest fixes. A new user can explore confidently, knowing they can recover from mistakes. | Basecamp (undo on delete, meaningful empty states), Todoist, Notion |
| 100% | The product anticipates confusion and prevents it. Empty states are onboarding moments ("Your inbox is empty — here's how messages arrive"). Every destructive action has undo with a clear time window. Error messages are specific and actionable. The UI teaches its own mental model through progressive disclosure — complex features emerge naturally from simple ones. | Stripe's onboarding flow, Linear's contextual guidance, Gmail's undo-send |

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
| 0% (5% floor) | Accessibility is actively broken. Light gray text on white backgrounds. Tiny tap targets (under 24px). No semantic HTML — entire page is nested divs. Keyboard navigation impossible. Screen readers encounter an undifferentiated wall of content. The product is unusable for anyone with visual, motor, or cognitive needs. | Products with text below 3:1 contrast ratio, div-soup markup, no ARIA landmarks, mouse-only interactions |
| 25% | Accessibility was never considered. Focus states removed with `outline-none` and no replacement — keyboard users literally cannot see where they are. Some semantic HTML exists but inconsistently (headers skip levels, nav not marked). Tap targets are too small on mobile. Contrast fails on secondary text. Broken focus states (`outline-none` without replacement) are an AI code tell — LLMs remove outlines for aesthetics without understanding they're a critical accessibility feature. | Products with `outline-none` globally, skipped heading levels, buttons smaller than 44px on mobile |
| 50% | Basic accessibility present but incomplete. Contrast ratios pass on primary text, fail on secondary. Focus states exist but are the browser default (not styled). Semantic HTML used for main content but not navigation or forms. Tap targets adequate on most elements. A screen reader user can navigate the main flow with difficulty. | Average web applications that haven't explicitly broken accessibility but haven't invested in it |
| 75% | Deliberate accessibility effort visible. Contrast ratios pass everywhere. Custom focus styles that match the design system. Proper heading hierarchy. ARIA labels on icon buttons. Tap targets meet 44px minimum. A keyboard-only user can complete the primary flow. Minor gaps in dynamic content announcements. | Stripe Dashboard, GitHub, well-maintained component library products |
| 100% | Accessibility is a design constraint, not an afterthought. Exceeds minimum contrast ratios. Focus management handles dynamic content (modals trap focus, route changes announce). Skip-to-content links. Reduced-motion preferences respected. Screen reader experience is designed, not accidental. The product works well for everyone because it was built for the margins. | GOV.UK, BBC's web products, Apple's native accessibility features |

**Scoring notes**: Run a quick check: Tab through the page — can you see where focus is? Inspect body/secondary text contrast (4.5:1 minimum). Check heading hierarchy in the DOM. Test tap targets on mobile (44px minimum). The `outline-none` test is the single highest-signal check: search the CSS for `outline: none` or `outline: 0` — if present without a custom focus replacement, score 25% or below. This is a care signal, not a compliance audit.

---
