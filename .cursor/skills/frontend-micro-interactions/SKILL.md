---
name: frontend-micro-interactions
description: Use when implementing UI micro-interactions in code — hover/press feedback, toggles, likes/favorites, form validation motion, loading/success states, toasts, or when the user asks to add polish, delight, or Framer Motion / CSS animation to a control.
disable-model-invocation: true
---

# Frontend Micro-Interactions

Implement small, purposeful feedback in code. Prefer **CSS transitions / `@keyframes`**; use **Framer Motion (Motion)** only when CSS cannot express the interaction cleanly.

## Stack ladder (required)

| Need | Use |
|------|-----|
| Hover, focus, press scale/opacity, color, simple enter/exit | CSS `transition` or short `@keyframes` |
| Gesture-driven springs, layout animation, interruptible multi-step sequences, shared layout | Framer Motion / Motion |
| Timeline orchestration across many elements, canvas, complex scrubbing | Out of scope for this skill — do not reach for GSAP for a single control |

**Default:** CSS. Justify Motion in one sentence if you use it.

## Decision recipe

Before coding, fill this (keep it short; do not invent a design doc):

1. **Trigger** — click / hover / focus / submit / system
2. **Feedback** — what changes (scale, opacity, color, position)
3. **Duration** — pick from the table below
4. **Reduced motion** — instant state or opacity-only substitute

Then implement with the stack ladder.

## Duration & easing

| Kind | Duration | Easing |
|------|----------|--------|
| Press / toggle / checkbox | 100–150ms | `ease-out` or `cubic-bezier(0.2, 0, 0, 1)` |
| Hover / focus ring / border | 150–200ms | same |
| Enter (tooltip, checkmark) | 150–250ms | decelerate `cubic-bezier(0, 0, 0.2, 1)` |
| Exit | 100–200ms | accelerate `cubic-bezier(0.3, 0, 1, 0.3)` |
| One-shot celebration (like) | ≤350ms total | CSS keyframes or one Motion spring — not both stacked |

Avoid overshoot springs (`cubic-bezier(0.34, 1.56, …)`) unless the product is explicitly playful.

Animate **transform** and **opacity** only. Never `transition: all`.

## Accessibility (non-negotiable)

```css
@media (prefers-reduced-motion: reduce) {
  .mi-animated {
    animation: none !important;
    transition: none !important;
  }
}
```

With Motion: `const reduce = useReducedMotion()` — skip scale/x/y/rotate; keep instant state or opacity fade.

**Never** leave shake, slide, or bounce without a reduced-motion path. Shake especially must disable under `prefers-reduced-motion`.

Expose state to AT: `aria-pressed`, `aria-invalid`, `role="alert"` for errors.

## Do / don't

**Do**
- One job per interaction (feedback for that control only)
- Match existing tokens/easings in the repo if present
- Keep celebration subtle (scale pulse or short opacity burst)

**Don't**
- Default to Framer Motion for hover/press alone
- Particle bursts, spark rings, radial glow halos, or multi-layer shadows for stock polish — celebration = icon scale/opacity pulse only
- Durations >400ms on frequent controls
- Animate layout properties (`top`, `width`, `height`) when transform works

## CSS pattern (preferred)

```tsx
<button
  type="button"
  className="mi-btn"
  aria-pressed={on}
  onClick={() => setOn((v) => !v)}
>
  {/* icon */}
</button>
```

```css
.mi-btn {
  transition: transform 120ms cubic-bezier(0.2, 0, 0, 1),
    opacity 120ms cubic-bezier(0.2, 0, 0, 1);
}
.mi-btn:hover { transform: scale(1.04); }
.mi-btn:active { transform: scale(0.96); }

@media (prefers-reduced-motion: reduce) {
  .mi-btn { transition: none; }
  .mi-btn:hover,
  .mi-btn:active { transform: none; }
}
```

## Motion pattern (when justified)

Use when you need interruptible press springs or sequenced favorited pop that CSS would turn into brittle timers:

```tsx
const reduce = useReducedMotion();

<motion.button
  type="button"
  aria-pressed={on}
  whileTap={reduce ? undefined : { scale: 0.96 }}
  transition={{ type: "spring", stiffness: 500, damping: 30 }}
/>
```

Keep Motion props minimal. Do not mix a CSS celebration keyframe *and* a Motion burst on the same action.

## Common cases

| Case | Approach |
|------|----------|
| Button press | CSS `:active` scale |
| Toggle / switch | CSS transition on thumb `transform` |
| Favorite / like | CSS keyframe scale pulse on toggle; Motion only if burst must cancel mid-flight |
| Invalid field | Short CSS shake (≤400ms) + `aria-invalid`; **disabled** under reduced motion |
| Success check | Opacity + scale 150–250ms CSS |
| Toast enter/exit | Opacity + `translateY`; CSS unless stacking/layout needs Motion |

## Baseline failures this skill prevents

| Failure | Fix |
|---------|-----|
| Framer for simple hover/press | CSS ladder first |
| Shake with no reduced-motion | Always gate translate/shake |
| Glow + particle "premium" defaults | Subtle scale/opacity only |
| Overshoot easing for form chrome | Linear/standard ease unless playful brand |
