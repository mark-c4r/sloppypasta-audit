# Visual Slop Detection Reference

Self-contained reference for detecting AI-generated visual design in products.
Used by checks: 3.1 (information density), 3.2 (physical obviousness), 3.3 (design consistency), 3.4 (self-evident UI), 3.5 (modal-free), 3.6 (accessibility basics), 4.1 (shipped ready), 4.3 (show me the code)

## CSS/Layout Markers

Indicators that visual design was AI-generated without human refinement:

### Color
- Purple/indigo accent colors (`bg-indigo-*`, `#5E6AD2`-family) -- Tailwind default infection
- Dark base (#0A0A0A) + neon accent -- the "Linear aesthetic"
- Gradient text headlines (blue-to-purple)

### Typography
- Inter, Roboto, or generic system font as the ONLY font -- no serif/sans pairing
- No typographic hierarchy beyond size changes

### Layout
- 3-column feature grid with centered icons -- the SaaS template
- Hero: centered text + gradient + CTA button -- same hierarchy everywhere
- `grid-cols-1 md:grid-cols-3` for everything (Bento Box default)
- No asymmetric or creative layouts anywhere

### Decoration
- Uniform rounded corners on all elements
- Subtle shadows at 0.1 opacity on all cards
- Gratuitous glassmorphism (`backdrop-blur-md bg-white/10`) on non-overlapping elements
- Unedited Lucide/Heroicon (2px stroke-width) next to every menu item

### Spacing
- Uniform `p-4`/`gap-4` everywhere -- no optical grouping
- No tight header-paragraph coupling vs loose section spacing

## Component Framework Tells

- **Shadcn/UI Default**: slate-900 buttons, `rounded-md` everywhere, zero token customization. "The new Bootstrap."
- **v0/Lovable**: Sterile layouts. Placeholder data: "John Doe", "Jane Smith", dashboard metrics "+20.1% from last month." Generic bar charts.
- **Cursor/Bolt.new**: `console.log("here")` in production. Inline `style={{ marginTop: '10px' }}` mixed into Tailwind codebase.

## Behavioral/Interaction Tells

These are how AI-generated products BEHAVE, beyond appearance:

- **Dead-End Empty State**: "No items found." -- no illustration, no empathy, no CTA to create the first item
- **Spinner Trap**: Every button click leads to loading spinner and server round-trip. No optimistic UI.
- **Brutal Error Handling**: Generic "Something went wrong" toasts, no context, no retry
- **Broken Focus States**: `focus:outline-none` without `focus-visible:ring` replacement -- destroys keyboard navigation
- **Window Resize Break**: THE most reliable single marker. Drag browser to ~800px tablet width. Squashed columns, overlapping text = AI built for 375px and 1440px only.
- **Hidden Scroll**: `scrollbar-hide` with zero visual affordance that content is scrollable

## Quick Check: Single Most Reliable Markers

- **Text**: The "Bold Prefix:" list structure
- **Visual**: The Window Resize Test (drag browser width slowly)

## How to Use This Reference

1. Visit the product in a browser
2. Check CSS: font-family, primary colors, border-radius values, shadow values
3. Count purple/indigo color instances
4. Check layout: is it a 3-column grid? Is the hero centered-text + gradient + CTA?
5. Test at 800px viewport width (tablet) -- does it break?
6. Check empty states, error states, loading states
7. Score: density of markers determines the design check scores per scale anchors
