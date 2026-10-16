# SignalFoundry implementation plan

## Scope

Build a polished desktop-first customer-discovery workspace for solopreneurs and small product teams. The first shipped slice prioritises the daily operating loop: review signal health, capture a new signal, triage and filter the inbox, group recurring problems, score opportunities transparently, review prioritisation, track experiments, and log decisions. The app also includes customer/segment views, workspace settings, a marketing landing route, auth entry points, pricing, fictional seed data, and CSV export.

The MVP uses fictional demo records and browser persistence for interactive preview flows so the app is immediately usable without requiring a live identity in the demo. The server remains database-ready: the existing Manus OAuth/session plumbing is preserved, the Drizzle schema expands to the core workspace entities, and the tRPC surface provides a clear path for durable CRUD once a signed-in workspace is connected.

## Implementation approach

- **Frontend:** React + TypeScript + Wouter + Tailwind utilities with a custom visual system. A single workspace shell provides consistent navigation, a desktop-optimised review canvas, keyboard-visible controls, search, filters, modals, responsive fallbacks, and explicit empty/loading/error patterns.
- **State:** Fictional seed data is kept in a typed module and hydrated into localStorage for reversible demo CRUD interactions. New signals and decision rows update the dashboard immediately. CSV export serialises the currently visible collection.
- **Backend:** Preserve the managed Express/tRPC starter and add typed workspace-domain tables and router placeholders around the existing authenticated context. Keep route contracts narrow and additive so a future database-backed implementation can replace the demo persistence without a UI rewrite.
- **Deployment:** Use the starter’s `pnpm dev`, health endpoint, Dockerfile, and managed database capability. Add a static route manifest before preview verification.

## Design

### Candidate movements

- 0.06 — Swiss editorial operations: restrained layout, hard edges, high information density.
- 0.08 — Soft neo-brutalist studio: warm surfaces, ink outlines, mint action color.
- 0.04 — Quiet enterprise utility: cool grey panels, deep navy navigation, precise status language.

### Chosen direction: Swiss editorial operations with a soft neo-brutalist edge

- **Design Movement:** editorial product operations — a calm command center that treats customer language as evidence, not clutter.
- **Core Principles:** signal before status; transparent scoring; compact but breathable information; obvious next actions.
- **Color Philosophy:** warm off-white surfaces make long review sessions easy on the eyes; deep navy is reserved for structure and trust; Signal Mint is the ownable action color used for decisions, positive movement, and focus.
- **Layout Paradigm:** a persistent left rail anchors the workspace while pages use split review panels, wide tables, and stacked insight bands instead of centered marketing grids.
- **Signature Elements:** mint “evidence” highlights, outlined score pills, and tiny horizontal signal-density bars.
- **Interaction Philosophy:** every control explains what changes; state is visible in the row; destructive actions are secondary; filters are reversible and keyboard-friendly.
- **Animation:** subtle 150–220ms ease-out transitions for drawers, status changes, and row hover; no decorative motion that competes with evidence review.
- **Typography System:** Plus Jakarta Sans for UI and headings; IBM Plex Mono for IDs, scores, and small data labels. Use strong 700–800 headings with 13–14px labels and comfortable table line-height.
- **Brand Essence:** customer evidence to confident product decisions; focused, candid, practical.
- **Brand Voice:** direct, observant, and founder-friendly. Example lines: “Turn scattered feedback into a build decision.” “The pattern is getting louder.”
- **Wordmark & Logo:** an abstract three-bar foundry mark: three uneven mint bars pressed into a navy square, suggesting raw signals becoming a shaped product.
- **Signature Brand Color:** Signal Mint `#39D6B0`.

## Project structure

- `client/src/App.tsx` — route composition and workspace shell.
- `client/src/data/demo.ts` — typed fictional entities, seed data, CSV helpers, and scoring helpers.
- `client/src/index.css` — visual tokens, layout primitives, and responsive/accessibility polish.
- `server/routers.ts` — auth plus typed domain router entry points.
- `drizzle/schema.ts` — users plus workspace and discovery entity tables for future persistence.
- `public/manus-routes.json` — preview/public route declaration.

## Delivery workflow

1. Create the typed demo domain model and plan/TODO artifacts.
2. Implement the shell, routes, dashboard, inbox, prioritisation surfaces, and capture flows.
3. Add server/domain schema scaffolding and route manifest.
4. Run type checks and production build; fix all actionable errors.
5. Start Preview, verify health and route manifest, then checkpoint the working version.
6. Review the core flows and finish with admin test notes and post-MVP recommendations.
