# Progress Tracker

Update this file whenever the current phase, active feature, or implementation state changes.

## Current Phase

- Phase 1 — Foundation

## Current Goal

- Design system and UI primitives (`context/feature-specs/01-design-system.md`).

## Completed

- 01 Design system (2026-11-24): shadcn/ui initialized (Radix base, Nova preset, CSS variables). Added Button, Card, Dialog, Input, Tabs, Textarea, ScrollArea in `components/ui/` (unmodified). lucide-react installed. `lib/utils.ts` exports `cn()`. Dark theme tokens from `ui-context.md` are in `app/globals.css`, and shadcn variables are mapped onto them. Verified: `tsc` clean, `next build` passes with all components imported, `cn()` merge tests pass, and compiled CSS has no light values.

## In Progress

- None.

## Next Up

- Next feature spec in `context/feature-specs/`.

## Open Questions

- Add unresolved product or implementation questions here.

## Architecture Decisions

- Theming: the Ghost AI tokens (`--bg-*`, `--text-*`, `--accent-*`, `--state-*`) are the source of truth in `:root`. shadcn variables (`--background`, `--primary`, ...) point at them, so there is no light palette. `<html>` always carries the `dark` class so shadcn `dark:` variants apply.
- `cn()` comes from shadcn's `cn` package (a clsx + tailwind-merge replacement) through `lib/utils.ts`. It needed no extra config for custom tokens.
- Tailwind runs through the `@tailwindcss/turbopack` loader in `next.config.ts`; there is no PostCSS config.

## Session Notes

- Add context needed to resume work in the next session.
