---
name: frontend-micro-interactions
description: Use when implementing UI micro-interactions in code — hover/press feedback, toggles, likes/favorites, form validation motion, loading/success states, toasts, Tailwind transition/animate utilities, or when the user asks to add polish, delight, Framer Motion, or CSS animation to a control.
disable-model-invocation: true
---

# Frontend Micro-Interactions

Implement small, purposeful feedback in code. Prefer **CSS transitions / `@keyframes`**, or **Tailwind** utilities when the project already uses Tailwind; use **Framer Motion (Motion)** only when CSS/Tailwind cannot express the interaction cleanly.

## Stack ladder (required)

| Need | Use |
|------|-----|
| Hover, focus, press scale/opacity, color, simple enter/exit | CSS `transition` / `@keyframes`, **or Tailwind** `transition-*` / `motion-safe:` variants |
| Gesture-driven springs, layout animation, interruptible multi-step sequences, shared layout | Framer Motion / Motion |
| Timeline orchestration across many elements, canvas, complex scrubbing | Out of scope for this skill — do not reach for GSAP for a single control |

**Default:** CSS or Tailwind (match the repo). Justify Motion in one sentence if you use it.

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

## CSS pattern (plain CSS)

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

## Tailwind pattern (when the project uses Tailwind)

Prefer named transition properties — never `transition-all`. Use `active:` for press (touch-safe); gate motion with `motion-safe:` / `motion-reduce:`.

```tsx
<button
  type="button"
  aria-pressed={on}
  onClick={() => setOn((v) => !v)}
  className="motion-safe:transition-transform motion-safe:duration-150 motion-safe:ease-out motion-safe:hover:scale-[1.04] motion-safe:active:scale-[0.97]"
>
  {/* icon */}
</button>
```

More recipes (toggle, shake, toast, spinner): [Tailwind interactions](references/tailwind.md).

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

| Case | CSS | Tailwind |
|------|-----|----------|
| Button press | `:active` scale | `motion-safe:active:scale-[0.97]` + `transition-transform` |
| Toggle / switch | thumb `transform` | `translate-x-*` + `transition-transform` |
| Favorite / like | keyframe scale pulse | short `animate-[…]` or class + keyframes; Motion only if must cancel mid-flight |
| Invalid field | shake ≤400ms + `aria-invalid` | `motion-safe:animate-[mi-shake_…]`; never without motion gate |
| Success check | opacity + scale 150–250ms | `transition-opacity` + `scale-*` |
| Toast enter/exit | opacity + `translateY` | `transition-transform` + `transition-opacity` |

## Baseline failures this skill prevents

| Failure | Fix |
|---------|-----|
| Framer for simple hover/press | CSS / Tailwind ladder first |
| Shake with no reduced-motion | Always gate translate/shake (`motion-safe:` / media query) |
| Glow + particle "premium" defaults | Subtle scale/opacity only |
| Overshoot easing for form chrome | Linear/standard ease unless playful brand |
| `transition-all` in Tailwind | Use `transition-transform` / `transition-opacity` / `transition-colors` |

## Additional resources

Read only what the task needs (one level deep):

- [Principles & ROI](references/principles.md) — Saffer/NN/g model, ship order, frequency gate
- [Timing, a11y, performance](references/timing-a11y.md) — durations, easing, reduced-motion, compositor rules
- [High-ROI patterns](references/patterns.md) — button, wait, toggle, form, toast, drag
- [Tailwind interactions](references/tailwind.md) — utilities, `motion-safe:`, recipes
- [Sources](references/sources.md) — NN/g, Material, WCAG, Emil Kowalski, project report
