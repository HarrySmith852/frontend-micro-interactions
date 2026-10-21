# High-ROI patterns

Load when implementing a specific control type. Prefer CSS or Tailwind per the skill stack ladder. Tailwind recipes: [tailwind.md](tailwind.md).

## Button / press acknowledgement

- Immediate pressed / pending / loading visual within ~100ms
- CSS `:active { transform: scale(0.96) }` + short transition
- Tailwind: `motion-safe:active:scale-[0.97]` + `transition-transform duration-150` (not hover-only)
- Disable or show spinner on submit — never “don’t click again” copy alone

## Wait feedback ladder

| Wait | Feedback |
|------|----------|
| <1s | Often no spinner (flashy spinner feels worse) |
| ~2–9s | Looped spinner / indeterminate |
| ≥10s | Percent-done or remaining estimate |

Progress indicators raise wait tolerance; hung 99% bars destroy trust.

## Toggle / switch

- Must **apply immediately** (light-switch mental model)
- If Save is required → use checkbox/radio instead
- Optimistic UI + revert on failure; pending state while server confirms
- Feedback: thumb `transform` + high-contrast color (not color alone)
- `aria-pressed` or switch role per design system

## Favorite / like

- Immediate, local, brief, reversible (second tap undoes)
- CSS scale pulse ≤350ms on the icon — no particle/glow defaults
- Pair with undo snackbar if the action feels irreversible elsewhere

## Form validation

- Field-adjacent message: **text + icon + color** (never color alone)
- `aria-invalid` + `role="alert"` / `aria-describedby`
- Timing:
  - **Never** yell on empty focus or mid-keystroke
  - Consumer SaaS: blur/inline on hard fields after user finishes
  - High-stakes / a11y-first: submit-time + error summary + move focus (GOV.UK style)
- Invalid shake: ≤400ms CSS; **disabled** under reduced motion

## Toast / undo

- Enter/exit: opacity + small `translateY`
- Undo after delete / archive / favorite when cost of error is high
- Keep utilitarian; rare brand delight beside undo is OK if sporadic

## Drag and drop

- Ghost preview + drop-zone highlight
- Sibling items ease aside ~100ms before release
- Activation threshold so pointer noise isn’t a grab
- Reshuffle when dragged item’s **center** crosses neighbor

## Anti-patterns

| Anti-pattern | Why it hurts |
|--------------|--------------|
| Mid-typing form scolding | Breaks flow (Baymard) |
| Toggle with no real effect | Breaks mental model |
| Decorative peripheral loaders | Motion-sensitive periphery steals attention |
| Artificial min animation on common paths | Taxes every repetition |
| High-frequency chrome animation | Makes fast apps feel slow |
