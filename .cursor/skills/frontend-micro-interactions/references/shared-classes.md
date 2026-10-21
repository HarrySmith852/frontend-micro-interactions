# Shared interaction classes (required)

**Same interaction → same class name everywhere.** Do not invent new utility stacks per button, form, or toast. Create the kit once; reuse it.

## Rule

| Situation | Action |
|-----------|--------|
| Interaction already has a kit class | Reuse that class — do not duplicate utilities inline |
| New interaction type | Add **one** named class to the kit, then use it |
| One-off visual that isn’t a repeated pattern | Inline utilities OK **once**; promote to kit on second use |

## Canonical class names

Keep these names stable across the product:

| Class | Interaction |
|-------|-------------|
| `mi-press` | Press scale feedback on buttons / clickable chrome |
| `mi-hover-lift` | Optional hover scale (pair with `mi-press`, not alone) |
| `mi-colors` | Color / border / ring transitions |
| `mi-fade` | Opacity show/hide |
| `mi-pop` | One-shot favorite / success scale pulse (toggle class ≤350ms) |
| `mi-shake` | Invalid field shake (always motion-gated) |
| `mi-toast` | Toast enter/exit (opacity + translateY) |
| `mi-spin` | Loading spinner |
| `mi-toggle-thumb` | Switch thumb position transition |
| `mi-check` | Success checkmark scale + opacity |

State modifiers (add/remove; don’t rename):

- `is-on` / `is-open` / `is-invalid` / `is-celebrating` / `is-success`

## Plain CSS kit

Put once in `styles/mi.css` (or equivalent) and import globally:

```css
/* styles/mi.css */
.mi-press {
  transition: transform 150ms cubic-bezier(0.2, 0, 0, 1);
}
.mi-press:active {
  transform: scale(0.97);
}
.mi-hover-lift:hover {
  transform: scale(1.04);
}
.mi-hover-lift:active {
  transform: scale(0.97);
}

.mi-colors {
  transition: color 150ms cubic-bezier(0.2, 0, 0, 1),
    background-color 150ms cubic-bezier(0.2, 0, 0, 1),
    border-color 150ms cubic-bezier(0.2, 0, 0, 1),
    box-shadow 150ms cubic-bezier(0.2, 0, 0, 1);
}

.mi-fade {
  transition: opacity 200ms cubic-bezier(0, 0, 0.2, 1);
}

.mi-toggle-thumb {
  transition: transform 150ms cubic-bezier(0.2, 0, 0, 1);
}
.mi-toggle-thumb.is-on {
  transform: translateX(1.25rem);
}

.mi-check {
  opacity: 0;
  transform: scale(0.75);
  transition: opacity 200ms cubic-bezier(0, 0, 0.2, 1),
    transform 200ms cubic-bezier(0, 0, 0.2, 1);
}
.mi-check.is-success {
  opacity: 1;
  transform: scale(1);
}

.mi-toast {
  transition: opacity 200ms cubic-bezier(0, 0, 0.2, 1),
    transform 200ms cubic-bezier(0, 0, 0.2, 1);
  opacity: 0;
  transform: translateY(0.5rem);
}
.mi-toast.is-open {
  opacity: 1;
  transform: translateY(0);
}

@keyframes mi-pop-kf {
  0% { transform: scale(0.92); }
  55% { transform: scale(1.08); }
  100% { transform: scale(1); }
}
.mi-pop.is-celebrating {
  animation: mi-pop-kf 320ms cubic-bezier(0.22, 1, 0.36, 1) both;
}

@keyframes mi-shake-kf {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-4px); }
  75% { transform: translateX(4px); }
}
.mi-shake.is-invalid {
  animation: mi-shake-kf 360ms ease-in-out both;
}

.mi-spin {
  animation: spin 1s linear infinite;
}
@keyframes spin {
  to { transform: rotate(360deg); }
}

@media (prefers-reduced-motion: reduce) {
  .mi-press,
  .mi-hover-lift,
  .mi-colors,
  .mi-fade,
  .mi-toggle-thumb,
  .mi-check,
  .mi-toast {
    transition: none !important;
  }
  .mi-press:active,
  .mi-hover-lift:hover,
  .mi-hover-lift:active {
    transform: none !important;
  }
  .mi-pop.is-celebrating,
  .mi-shake.is-invalid,
  .mi-spin {
    animation: none !important;
  }
  .mi-check.is-success,
  .mi-toast.is-open {
    opacity: 1;
    transform: none;
  }
}
```

Usage — same classes on every matching control:

```tsx
<button type="button" className="mi-press mi-colors">Save</button>
<button type="button" className="mi-press mi-hover-lift">Icon</button>
<input className={`mi-colors mi-shake ${invalid ? "is-invalid" : ""}`} aria-invalid={invalid} />
<span className={`mi-pop ${celebrating ? "is-celebrating" : ""}`}>{/* heart */}</span>
```

## Tailwind kit (`@apply`)

If the project uses Tailwind, define the **same class names** once (e.g. in `src/styles/mi.css`):

```css
@layer components {
  .mi-press {
    @apply motion-safe:transition-transform motion-safe:duration-150 motion-safe:ease-out motion-safe:active:scale-[0.97];
  }
  .mi-hover-lift {
    @apply motion-safe:transition-transform motion-safe:duration-150 motion-safe:ease-out motion-safe:hover:scale-[1.04] motion-safe:active:scale-[0.97];
  }
  .mi-colors {
    @apply transition-colors duration-150 ease-out;
  }
  .mi-fade {
    @apply motion-safe:transition-opacity motion-safe:duration-200 motion-safe:ease-out;
  }
  .mi-toggle-thumb {
    @apply motion-safe:transition-transform motion-safe:duration-150 motion-safe:ease-out;
  }
  .mi-toggle-thumb.is-on {
    @apply translate-x-5;
  }
  .mi-check {
    @apply opacity-0 scale-75 motion-safe:transition motion-safe:duration-200 motion-safe:ease-out;
    transition-property: opacity, transform;
  }
  .mi-check.is-success {
    @apply opacity-100 scale-100 motion-reduce:scale-100;
  }
  .mi-toast {
    @apply opacity-0 translate-y-2 motion-safe:transition motion-safe:duration-200 motion-safe:ease-out;
    transition-property: opacity, transform;
  }
  .mi-toast.is-open {
    @apply opacity-100 translate-y-0 motion-reduce:translate-y-0;
  }
  .mi-spin {
    @apply motion-safe:animate-spin motion-reduce:animate-none;
  }
  .mi-shake.is-invalid {
    @apply motion-safe:animate-[mi-shake-kf_360ms_ease-in-out_both];
  }
  .mi-pop.is-celebrating {
    @apply motion-safe:animate-[mi-pop-kf_320ms_ease-out_both];
  }
}

@keyframes mi-shake-kf {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-4px); }
  75% { transform: translateX(4px); }
}
@keyframes mi-pop-kf {
  0% { transform: scale(0.92); }
  55% { transform: scale(1.08); }
  100% { transform: scale(1); }
}
```

Components only compose kit classes — no long duplicate `motion-safe:transition-transform…` strings.

## Anti-patterns

| Bad | Good |
|-----|------|
| Each button invents `duration-150 active:scale-95` vs `duration-100 active:scale-[0.97]` | All use `mi-press` |
| Copy-paste 8 utility classes on every toast | `mi-toast` + `is-open` |
| Rename to `btn-press`, `press-fx`, `scale-btn` for the same feel | Stick to `mi-press` |
