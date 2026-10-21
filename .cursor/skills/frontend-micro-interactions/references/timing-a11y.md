# Timing, easing, a11y, performance

Load when choosing durations, curves, or reduced-motion behavior.

## Duration defaults

| Interaction | Duration | Notes |
|-------------|----------|-------|
| Press / toggle / checkbox | 100–160ms | Feel immediate |
| Tooltip / popover | 125–200ms | |
| Dropdown | 150–250ms | |
| Modal / drawer | 200–500ms | Larger = longer |
| Routine chrome cap | **≤~300ms** | Prefer shorter for high-frequency |
| Material large spatial | 400–500ms | Rare big moves only |
| Exit vs enter | Exit ~20% faster | Common craft rule |

NN/g band for UX animation: mostly 100–500ms; 500ms often feels slow for simple feedback.

## Easing

**Consensus:** strong **ease-out** for enters (responsive start). Never bare `ease-in` on UI chrome — slow start feels laggy.

| Use | Curve |
|-----|-------|
| Default UI / enter | `cubic-bezier(0.2, 0, 0, 1)` or `cubic-bezier(0.23, 1, 0.32, 1)` |
| On-screen morph | `ease-in-out` |
| Permanent exit (Material “gone”) | accelerate `cubic-bezier(0.3, 0, 1, 0.3)` |
| Temporary exit (retrievable) | ease-out / restful end |
| Press feedback | subtle `scale(0.96–0.97)` |

**Web default:** ease-out for enter *and* exit unless Material “gone forever” semantics matter.

Springs: keep bounce near 0 for serious UI; caution above ~0.4.

Avoid overshoot (`cubic-bezier(0.34, 1.56, …)`) unless brand is explicitly playful.

## Accessibility

### `prefers-reduced-motion: reduce`

- Drop non-essential **spatial** motion (translate, scale travel, shake, bounce)
- Keep instant state or short **opacity/color** dissolves
- Never leave shake/slide without a reduced-motion path
- Motion: `useReducedMotion()` — skip `whileHover`/`whileTap` scale when reduced

WCAG **2.3.3** (AAA): interaction-triggered motion animation must be disableable unless essential. Motion = size/shape/position illusion — not mere color/opacity.

WCAG **2.2.2**: auto-play >5s needs pause/stop/hide.

Motion must not be the **sole** channel for important information. Use `aria-pressed`, `aria-invalid`, `role="alert"`.

## Performance

- Animate **`transform` and `opacity` only**
- Never `transition: all` — name properties
- Avoid animating `width` / `height` / `top` / `left` / `margin` / `padding` (layout + CLS risk)
- Target compositor-friendly ~60fps (~16.7ms/frame)
