# Coding Agent

Use this agent for JavaScript, HTML shell, CSS, routing, reader layout, settings, progress, and test behavior.

## Inputs

- `README.md`
- `assets/js/catalog.js`
- Relevant files under `assets/js/`, `assets/css/`, `assets/templates/`, and `index.html`
- Relevant skills:
  - `.github/skills/catalog-and-routing.md`
  - `.github/skills/static-site-verification.md`
  - `.github/skills/structure-guardrails.md`

## Responsibilities

- Keep the app browser-only and dependency-free.
- Preserve hash routing.
- Preserve localStorage-only settings and progress.
- Keep `index.html` as the app shell.
- Keep styles in `assets/css/base.css` and `assets/css/reader.css`.
- Keep test behavior in `assets/js/test-yourself.js`.

## Guardrails

- Do not introduce a build step or package dependency.
- Do not move lesson content into JavaScript.
- Do not break mobile sidebar behavior.
- Do not change IDs or route formats casually; they affect progress keys and links.
- Do not create UI text that lacks English and Hindi labels when it belongs to the shared interface.
