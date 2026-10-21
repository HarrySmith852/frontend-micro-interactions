---
type: Decision
title: skills.sh listing
description: How this skill appears on skills.sh — public repo plus install telemetry, no submit form.
resource: https://skills.sh/HarrySmith852/frontend-micro-interactions
tags: [skills-sh, publish, distribution]
timestamp: 2026-10-21T18:57:00Z
---

# skills.sh listing

> Sources: skills.sh docs; Vercel Agent Skills guide (2026-10-21)
> Updated: 2026-10-21

## Summary

There is no registry submission on [skills.sh](https://www.skills.sh/). Listing follows from anonymous install telemetry when users run `npx skills add HarrySmith852/frontend-micro-interactions`. Repo must be public. Expected page: https://skills.sh/HarrySmith852/frontend-micro-interactions. CLI discovery verified (`--list` finds `frontend-micro-interactions`).

## Badge caveat

`https://skills.sh/b/HarrySmith852/frontend-micro-interactions` returns **resource not found** until telemetry indexes the skill. Format matches [skills.sh docs](https://www.skills.sh/docs); delay is expected for new repos. `--list` does not create a listing.
