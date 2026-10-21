# Tailwind CSS micro-interactions

Load when the project already uses Tailwind. Same stack ladder: utilities first, Motion only when utilities cannot.

**Prefer shared `mi-*` classes** ([shared-classes.md](shared-classes.md)) over repeating long utility strings. Use the recipes below to **define** the kit once with `@apply`, then consume `mi-press`, `mi-shake`, etc. in components.

## Utility map

| Need | Prefer | Avoid |
|------|--------|-------|
| Press / hover scale | `transition-transform duration-150 ease-out` + `active:scale-[0.97]` / `hover:scale-[1.04]` | `transition-all`, large `scale-90` |
| Color / border / ring | `transition-colors duration-150` | Bundling with transform via bare `transition` when only color changes |
| Opacity enter/exit | `transition-opacity duration-200 ease-out` | Animating layout size |
| Translate toast | `transition-transform` + `translate-y-*` | `top` / `mt-*` animation |
| Spinner | `motion-safe:animate-spin` | `animate-spin` without reduced-motion gate |
| Custom one-shot | `animate-[name_320ms_ease-out_both]` + `@keyframes` in CSS | Built-in `animate-bounce` on frequent controls |

**Never** use `transition-all` — it fights the skill’s transform/opacity rule and risks CLS.

## Reduced motion (required)

Prefer **`motion-safe:`** so motion is opt-in:

```tsx
<button
  type="button"
  className="motion-safe:transition-transform motion-safe:duration-150 motion-safe:ease-out motion-safe:active:scale-[0.97]"
>
  Save
</button>
```

Or undo with **`motion-reduce:`**:

```tsx
className="transition-transform duration-150 active:scale-[0.97] motion-reduce:transition-none motion-reduce:active:scale-100"
```

Spinners:

```tsx
<svg className="size-5 motion-safe:animate-spin motion-reduce:animate-none" />
```

## Press vs hover

- **`active:`** — press feedback (works on touch)
- **`hover:`** — optional resting hint only; not the sole feedback (v4 `hover:` is hover-capable pointers only)
- Pair: `hover:scale-[1.03] active:scale-[0.97]` gated with `motion-safe:`

## Recipes

### Button press

```tsx
<button
  type="button"
  className="rounded-lg bg-zinc-900 px-4 py-2 text-white motion-safe:transition-transform motion-safe:duration-150 motion-safe:ease-out motion-safe:active:scale-[0.97]"
>
  Continue
</button>
```

### Toggle thumb

```tsx
<span
  aria-hidden
  className={[
    "pointer-events-none inline-block size-5 rounded-full bg-white",
    "motion-safe:transition-transform motion-safe:duration-150 motion-safe:ease-out",
    on ? "translate-x-5" : "translate-x-0",
  ].join(" ")}
/>
```

### Favorite pulse (one-shot class)

Toggle a class for ≤350ms; define keyframes once (CSS module or global):

```css
@keyframes mi-pop {
  0% { transform: scale(0.92); }
  55% { transform: scale(1.08); }
  100% { transform: scale(1); }
}
.mi-pop {
  animation: mi-pop 320ms cubic-bezier(0.22, 1, 0.36, 1) both;
}
@media (prefers-reduced-motion: reduce) {
  .mi-pop { animation: none; }
}
```

```tsx
<span className={celebrating ? "mi-pop inline-flex" : "inline-flex"}>{/* icon */}</span>
```

### Invalid shake

```tsx
<input
  aria-invalid={invalid}
  className={[
    "w-full rounded-lg border px-3 py-2 outline-none transition-colors duration-150",
    "focus-visible:ring-2 focus-visible:ring-offset-2",
    invalid ? "border-red-500 motion-safe:animate-[mi-shake_360ms_ease-in-out]" : "border-zinc-300",
  ].join(" ")}
/>
```

```css
@keyframes mi-shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-4px); }
  75% { transform: translateX(4px); }
}
```

Gate with `motion-safe:` so shake never runs under reduced motion.

### Success check

```tsx
<span
  className={[
    "inline-flex",
    "motion-safe:transition motion-safe:duration-200 motion-safe:ease-out",
    "motion-safe:transition-property-[opacity,transform]",
    success ? "scale-100 opacity-100" : "scale-75 opacity-0",
  ].join(" ")}
>
  {/* check icon */}
</span>
```

Arbitrary `transition-property` keeps opacity+transform without `transition-all`.

### Toast enter

```tsx
<div
  className={[
    "fixed bottom-4 right-4 rounded-lg bg-zinc-900 px-4 py-3 text-white",
    "motion-safe:transition-transform motion-safe:duration-200 motion-safe:ease-out",
    open ? "translate-y-0 opacity-100" : "translate-y-2 opacity-0",
    "motion-safe:transition-opacity",
  ].join(" ")}
/>
```

## Duration tokens (map to skill table)

| Skill band | Tailwind |
|------------|----------|
| 100–150ms press | `duration-100` / `duration-150` |
| 150–200ms hover | `duration-150` / `duration-200` |
| 200–300ms enter | `duration-200` / `duration-300` |
| Custom | `duration-[120ms]` |

Easing: `ease-out` default; `ease-[cubic-bezier(0.2,0,0,1)]` when matching design tokens.

## Don’t

- `transition-all` / bare `transition` when only transform should move
- `animate-bounce` / `animate-ping` on everyday chrome
- Hover-only press feedback
- Skipping `motion-safe` / `motion-reduce` on scale, translate, shake, spin
