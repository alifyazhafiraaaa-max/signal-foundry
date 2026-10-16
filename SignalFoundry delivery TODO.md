# SignalFoundry delivery TODO

## Workspace shell and navigation

- [x] Desktop-first application shell provides a persistent workspace rail, workspace switcher, grouped navigation, top-bar search, profile menu, and responsive fallback for narrower screens.
- [x] Shell exposes Dashboard, Signals, Problems, Opportunities, Prioritisation, Experiments, Decisions, Customers, Segments, Settings, Pricing, and marketing/auth routes.
- [x] Use a calm neutral palette with Signal Mint as the single accent; include visible focus states, readable type, and keyboard-friendly controls.

## Fictional data and core workflow

- [x] Seed the app with realistic fictional demo data for customer segments, customers, signals, problems, opportunities, experiments, decisions, and activity.
- [x] User can capture a signal with title, customer, source, segment, urgency, product area, and note; new signals appear in the inbox and update counts.
- [x] User can search and filter signals by free text, source, urgency, segment, and status, and can export the visible inbox as CSV.
- [x] User can review recurring problems, link problems to opportunities, and see evidence counts.
- [x] Opportunity scoring visibly combines frequency, severity, willingness to pay, strategic fit, and estimated effort; the scoring logic remains editable in the prioritisation view.
- [x] Prioritisation view includes a table and impact/effort matrix with transparent scores and next action labels.
- [x] Experiment tracker exposes hypothesis, method, success metric, owner, and result/status.
- [x] Decision log records build/test/investigate/defer/decline choices, reasoning, linked evidence, and dates.

## Platform and data foundation

- [x] Preserve Manus OAuth session plumbing and authenticated tRPC context from the starter.
- [x] Expand Drizzle schema with additive workspace-domain tables for future durable CRUD.
- [x] Keep Express health endpoint and production build path intact.
- [x] Publish a route manifest covering all user-facing page routes.

## Validation and handoff

- [x] Run `pnpm check` and resolve actionable TypeScript diagnostics.
- [x] Run `pnpm build` and resolve build failures.
- [x] Start the configured dev server and verify `/api/health`, `/manus-routes.json`, and the main preview route.
- [x] Save a checkpoint containing the completed app.
- [x] Include an admin testing checklist and post-MVP recommendations in the handoff response.
