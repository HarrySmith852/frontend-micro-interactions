# Principles & ROI

Load when scoping *what* to build before writing motion code.

## Definition

A micro-interaction is a **contained product moment that does one small task** (Dan Saffer). NN/g: a **trigger–feedback pair** — user/system trigger plus narrowly targeted contextual feedback. No feedback → not a micro-interaction. Multi-step features and always-on chrome are out of scope.

Separate **micro-interactions** (task feedback) from **micro-animations** (decorative polish that may auto-play).

## Four parts (design checklist)

1. **Trigger** — click, hover, focus, submit, gesture, or system condition
2. **Rules** — what can/cannot happen (invisible logic)
3. **Feedback** — visual / motion / copy / haptic that makes rules visible (near the control)
4. **Loops & modes** — how behavior changes on repeat visits; modes are rare — use sparingly

## Response-time ladder (NN/g)

| Limit | Feel |
|-------|------|
| ≤0.1s | Instantaneous — acknowledge presses here |
| ≤1.0s | Thought flow stays intact |
| ≤10s | Attention holds; then need progress / estimate |

## Ship order (highest ROI first)

1. Acknowledge primary controls within ~100ms (pressed / pending / loading)
2. Wait ladder: immediate start → spinner ~2–9s → percent-done ≥10s (skip flashy spinner under 1s)
3. Instant toggles (optimistic + revert on failure)
4. Well-timed form validation (field-adjacent; never yell on empty focus)
5. Undo after delete / favorite / archive
6. Drag previews / thresholds (reorder UIs)
7. Brand delight — rare, high-emotion only

## Frequency gate

| Frequency | Motion budget |
|-----------|---------------|
| 100+/day (palette, keyboard highlight) | Often **none** |
| Tens/day | Near-imperceptible |
| Occasional (modal) | Standard chrome timing |
| Rare / first-time | Optional delight |

## Core don’ts

- Entertainment animation during waits
- Many simultaneous animations
- Force users to wait for animation to finish
- Scroll-triggered body text that invents delay
- Ornamental glow/particles as “premium”
