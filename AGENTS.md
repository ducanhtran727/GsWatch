# GsWatch — project agents

## Project context

- Communicate with the user in Vietnamese unless requested otherwise.
- This repository is a Vietnamese watch sales landing page. `index.html` contains HTML, CSS and vanilla JavaScript; product images live at the repository root. `backup.html` is a reference backup, not the default implementation target.
- Inspect the current files before each task. Preserve existing user changes. Do not introduce a framework, build system or dependencies unless the task needs them.
- Preserve verified product facts, prices, contact details and integrations unless changing them is part of the user's request. Never invent reviews, purchases, scarcity, affiliation or research results.

## Specialist delegation

For substantive UI/UX and frontend tasks, delegate bounded work to the specialists below. Small isolated fixes can be handled directly. The primary agent owns scope, integration and the final response.

- `ui_ux_designer`: user journeys, usability, information hierarchy, visual design, mobile behavior, accessibility and design review. Instructions: `.codex/agents/ui_ux_designer.toml`.
- `frontend_dev`: HTML/CSS/JavaScript implementation, responsive layouts, interactions, performance and functional verification. Instructions: `.codex/agents/frontend_dev.toml`.
- If the runtime cannot select custom roles directly, read the matching TOML and include its role instructions in the delegated task. Do not claim a role is loaded or running without evidence.

## Collaboration workflow

1. Define the user outcome, affected sections and acceptance criteria. Separate observed behavior from assumptions about shoppers.
2. Let the designer inspect the relevant flow and provide an actionable design brief. FE can independently inspect technical constraints while this happens.
3. Pass the brief and relevant existing decisions to FE. Assign one writer per file; this is especially important for `index.html`. Designer does not edit production code unless explicitly assigned.
4. FE implements the scoped change and checks it. Designer reviews the resulting rendered interface against the brief when browser tools are available. Resolve material issues before delivery.
5. Report what changed, validation performed and any remaining limitations. Do not claim visual or browser testing when only source inspection was possible.

## Verification

- For layout changes, inspect representative widths such as 360, 390, 768 and 1440 CSS pixels. Check overflow, image cropping, reading order and fixed elements covering content or controls.
- For interaction changes, check affected CTA links, galleries and order controls, plus keyboard access and visible focus.
- For order-form changes, verify quantity/total consistency, validation, submission progress, duplicate-submit prevention, errors and success using mocked requests or an authorized test endpoint.
- During local tests, intercept production order submissions and analytics so tests do not create real orders or conversion events.
- Use checks proportionate to the change. Do not add a test framework for documentation-only or trivial cosmetic changes.
