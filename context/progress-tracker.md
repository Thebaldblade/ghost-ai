# Progress Tracker

Update this file whenever the current phase, active feature, or implementation state changes.

## Current Phase

- Phase 1 — Foundation

## Current Goal

- Next feature spec after `02-editor.md` (02 complete).

## Completed

- 01 Design system (2026-11-24): shadcn/ui initialized (Radix base, Nova preset, CSS variables). Added Button, Card, Dialog, Input, Tabs, Textarea, ScrollArea in `components/ui/` (unmodified). lucide-react installed. `lib/utils.ts` exports `cn()`. Dark theme tokens from `ui-context.md` are in `app/globals.css`, and shadcn variables are mapped onto them. Verified: `tsc` clean, `next build` passes with all components imported, `cn()` merge tests pass, and compiled CSS has no light values.
- 02 Editor chrome (2026-11-24):
  - [x] `components/editor/editor-navbar.tsx`: `h-14` top bar with left, center and right sections. The left section holds the sidebar toggle (`PanelLeftOpen` / `PanelLeftClose`), the right section is empty, and the bar uses `bg-surface` with a bottom border. Props: `isSidebarOpen`, `onToggleSidebar`.
  - [x] `components/editor/project-sidebar.tsx`: a floating overlay that slides in from the left and does not push content. Props: `isOpen` and an optional `onClose`. It has a "Projects" header with a close button, Tabs for My Projects and Shared (each with an empty state), and a full-width "New Project" button with a `Plus` icon.
  - [x] `components/editor/editor-dialog.tsx`: the dialog pattern, a wrapper around shadcn `Dialog` with `title`, `description`, `footer` (actions) and `children`. Styled with tokens (`rounded-3xl`, `bg-elevated`). No real dialogs are built yet.
  - [x] Verified: `tsc` is clean and `eslint` reports no errors. The only warning is a pre-existing unused `Button` import in `app/page.tsx`. Components are not mounted on a page yet.

## In Progress

- None.

## Next Up

- Next feature spec in `context/feature-specs/`.

## Open Questions

- Add unresolved product or implementation questions here.
- Which route hosts the editor (where navbar + sidebar get mounted)? Not defined in specs yet.

## Architecture Decisions

- Theming: the Ghost AI tokens (`--bg-*`, `--text-*`, `--accent-*`, `--state-*`) are the source of truth in `:root`. shadcn variables (`--background`, `--primary`, ...) point at them, so there is no light palette. `<html>` always carries the `dark` class so shadcn `dark:` variants apply.
- `cn()` comes from shadcn's `cn` package (a clsx + tailwind-merge replacement) through `lib/utils.ts`. It needed no extra config for custom tokens.
- Editor chrome is controlled from outside: navbar and sidebar take open state through props, and the future editor page owns the state. The sidebar is `absolute`, so its workspace container must be `relative` (below the navbar).
- Dialogs: feature dialogs compose `EditorDialog` rather than restyling `components/ui/dialog.tsx`.
- Tailwind runs through the `@tailwindcss/turbopack` loader in `next.config.ts`; there is no PostCSS config.

## Session Notes

- Add context needed to resume work in the next session.
