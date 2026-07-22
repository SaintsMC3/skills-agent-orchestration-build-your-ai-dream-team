# Project Pulse implementation plan

## Summary
Build a small static Project Pulse dashboard for Mona's contributors. The Orchestrator coordinates the work, the Designer owns the visual experience, and the Coder implements the app files and launch configuration. The dashboard should clearly show active projects, owners, status, recent activity, priority, and contributor-friendly summaries in a polished card-based layout.

## Ordered implementation steps
1. Confirm the data shape in `app/project-data.json` so the dashboard has a stable top-level `projects` array with `name`, `owner`, `status`, `recentActivity`, and `priority`.
1. Design the dashboard structure in `app/index.html` around a clear Project Pulse title, readable project cards, and semantic content that matches the data model.
1. Apply the visual system in `app/styles.css` with responsive layout, visible project cards, status badges, clear priority treatment, and deterministic CSS hooks such as `.dashboard` and `.project-card`.
1. Add `.vscode/launch.json` so the Run Project Pulse Dashboard configuration serves from `${workspaceFolder}/app` and opens `index.html` instead of a directory listing.
1. Validate that the static dashboard opens cleanly, renders the expected project information, and uses the launch configuration as intended.

## File assignments
- `app/project-data.json`: Coder owns the project data shape and writes the deterministic JSON payload.
- `app/index.html`: Coder owns the semantic dashboard markup and the structure for project cards.
- `app/styles.css`: Designer owns the dashboard styling, hierarchy, spacing, and responsive behavior.
- `.vscode/launch.json`: Coder owns the strict JSON launch configuration for opening the dashboard from `app/`.

## Responsibilities
- Designer: define the visual language for Project Pulse, including project cards, status badges, priority emphasis, readable spacing, contrast, and responsive behavior.
- Coder: implement the app files, keep the JSON deterministic, wire the dashboard markup to the project data, and create the launch configuration with no comments and valid JSON only.
- Orchestrator: sequence the work, resolve dependency order, and verify the final handoff against the brief.

## Dependencies between steps
- `app/project-data.json` should be agreed first so the HTML and CSS can target the same project fields.
- `app/index.html` and `app/styles.css` can proceed after the data shape is known.
- `.vscode/launch.json` depends on the app directory structure and must point at the completed `app/index.html`.
- Final validation depends on all four files being present and internally consistent.

## Parallel work decisions
- `app/index.html` and `app/styles.css` can run in parallel once the data model is settled.
- `.vscode/launch.json` can be prepared alongside the UI work because it only depends on the app location, not the final styling.
- Data modeling and launch configuration should not conflict, so they can be assigned separately if the Orchestrator keeps the file ownership boundaries clear.

## Sequential work
- First lock the `projects` array shape in `app/project-data.json`.
- Then build the HTML structure and the CSS treatment against that shared shape.
- Finish with `.vscode/launch.json` and a preview check so the dashboard opens directly to `index.html`.

## Edge cases to handle
- Keep the JSON strict and valid so the dashboard can consume it without extra parsing rules.
- Ensure every project entry has the required fields and no missing keys.
- Make the launch configuration open the dashboard page directly, not a folder listing.
- Preserve readable spacing and card layout on narrow screens as well as desktop widths.

## Validation expectations
- `app/project-data.json` parses as valid JSON and includes a top-level `projects` array.
- `app/index.html` shows a Project Pulse dashboard with project cards and the required project fields.
- `app/styles.css` includes clear `.dashboard` and `.project-card` hooks plus responsive, readable styling.
- `.vscode/launch.json` uses strict JSON, launches from `${workspaceFolder}/app`, and opens `index.html`.
- The final preview matches the brief: polished layout, status badges, priority treatment, and contributor-friendly summaries.

## Open questions
- None. The brief and step instructions define the required files, fields, and launch behavior.