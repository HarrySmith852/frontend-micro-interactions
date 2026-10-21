---
type: Decision
title: Shared mi-* interaction classes
description: Same micro-interaction must reuse the same canonical mi-* class across the product.
resource: .cursor/skills/frontend-micro-interactions/references/shared-classes.md
tags: [css, tailwind, micro-interactions, design-system]
timestamp: 2026-10-21T18:52:00Z
---

# Shared mi-* interaction classes

> Sources: Local skill decision (2026-10-21)
> Updated: 2026-10-21

## Summary

Identical interactions share one named class kit (`mi-press`, `mi-hover-lift`, `mi-colors`, `mi-fade`, `mi-pop`, `mi-shake`, `mi-toast`, `mi-spin`, `mi-toggle-thumb`, `mi-check`) plus state modifiers (`is-on`, `is-open`, `is-invalid`, `is-celebrating`, `is-success`). Define once (plain CSS or Tailwind `@apply`); do not invent per-component utility stacks for the same feel.
