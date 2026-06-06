# Agent Playbook

This repository is a plain static D.El.Ed learning website. The agentic workflow must protect the site structure first, then add content or code.

## Start Here

1. Read `README.md`.
2. Read `todo.md` unless the user gave a more specific task in chat.
3. Read `assets/js/catalog.js` before adding, removing, renaming, or reordering semesters, subjects, topics, or tests.
4. Read existing lesson and test files in the target `content/semester-*` folder before writing new material.
5. Choose the smallest relevant agent file from `.github/agents/` and skill files from `.github/skills/`.

## Operating Rules

- Keep the site static: HTML, CSS, and JavaScript only.
- Do not add a framework, package manager, build step, backend, login, database, or heavy dependency.
- Preserve user changes. Do not revert unrelated edits.
- Keep `index.html` as the app shell only.
- Keep course structure in `assets/js/catalog.js`.
- Keep lesson and test content in `content/semester-*/<subject>/en|hi|tests|media/`.
- Do not point catalog entries to missing files.
- Do not silently change topic order, topic counts, test counts, IDs, or paths.
- When a task is taken from `todo.md`, complete it, verify it, then mark only that task as done.

## Agent Routing

- Topic or syllabus research: use `.github/agents/topic-research-agent.md`.
- Lesson or test content: use `.github/agents/lesson-content-agent.md`.
- App shell, routing, styling, or JavaScript: use `.github/agents/coding-agent.md`.
- Final checks: use `.github/agents/verification-agent.md`.

For content work, run the agents in this order:

1. Topic Research Agent
2. Lesson Content Agent
3. Verification Agent

For code work, run the agents in this order:

1. Coding Agent
2. Verification Agent

## Content Contract

- Every visible title and summary in `catalog.js` must have both `en` and `hi`.
- Every completed topic must have matching English and Hindi HTML files.
- Every completed chapter-level test must have matching English and Hindi HTML files.
- Subject-level tests must be listed under the subject `tests` array and use matching English and Hindi files.
- Hindi must be natural academic Hindi, not word-by-word translation.
- Lesson content must be original, short, scannable, and useful for last-minute D.El.Ed revision.
- Prefer bullets, short tables, quick diagrams, exam lines, and elementary-school classroom examples.

## Research Contract

- Research the real course name, semester, subject, and chapter list before adding academic content.
- Prefer official SCERT, board, university, or government sources.
- If official sources are unreachable, use multiple credible syllabus or textbook sources.
- Mention source assumptions in the final response.
- Do not copy large passages. Rewrite in student-friendly language.

## Verification Contract

- If JavaScript changed, run a syntax check.
- If catalog or content paths changed, verify every referenced file exists.
- If content changed, preview the static site with a local server when feasible.
- Confirm routing, sidebar navigation, language toggle, and lesson rendering still work.
- Report any verification that could not be run.
