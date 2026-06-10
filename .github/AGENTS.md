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

## Todo Routes

Use route names in `todo.md`; do not repeat long skill lists in every todo item.

- `syllabus-map`: Topic Research Agent -> Verification Agent.
- `content-chapter`: Topic Research Agent -> Lesson Content Agent -> Verification Agent.
- `content-test`: Lesson Content Agent -> Verification Agent.
- `code-change`: Coding Agent -> Verification Agent.
- `audit-only`: Verification Agent, with no content or code edits unless a bug is found and the user asked for fixes.

For `syllabus-map`, use these skills:

- `.github/skills/topic-research.md`
- `.github/skills/syllabus-map.md`
- `.github/skills/catalog-and-routing.md`
- `.github/skills/static-site-verification.md`
- `.github/skills/structure-guardrails.md`

For `content-chapter`, use these skills:

- `.github/skills/topic-research.md`
- `.github/skills/catalog-and-routing.md`
- `.github/skills/bilingual-lesson-writing.md`
- `.github/skills/test-yourself-writing.md`
- `.github/skills/static-site-verification.md`
- `.github/skills/structure-guardrails.md`

Each `syllabus-map` todo item must research one subject, update the full ordered chapter/topic map for that subject, and create only minimal bilingual placeholder files for newly mapped topics. Do not write full lessons or tests during `syllabus-map`.

Each `content-chapter` todo item must add or fully revise exactly one chapter/topic at a time, including the attached chapter-level test. Do not start `content-chapter` tasks for a subject until its `syllabus-map` task is done.

Each `content-test` todo item must add or fully revise subject-level tests after the subject's chapter-level content is complete.

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
- Every completed topic must include an attached chapter-level test in `catalog.js`, with matching English and Hindi test files.
- Subject-level tests must be listed under the subject `tests` array and use matching English and Hindi files.
- Hindi must be natural academic Hindi, not word-by-word translation.
- Lesson content must be original, full enough for chapter revision, scannable, and useful for last-minute D.El.Ed preparation.
- Prefer bullets, short definitions, snapshot tables, comparison tables, quick diagrams, exam lines, and elementary-school classroom examples.
- Use Semester 4 Science as the quality reference: full crash-course chapter content, one chapter test per chapter, and subject-level tests.
- Chapter tests must have 10 MCQs, 5 short-answer questions, and 4 or 5 long-answer questions.
- Subject tests must have 20 MCQs, 10 short-answer questions, and 5 to 7 long-answer questions.

## Research Contract

- Research the real course name, semester, subject, and chapter list before adding academic content.
- Prefer official SCERT, board, university, or government sources.
- If official sources are unreachable, use multiple credible syllabus or textbook sources.
- Keep chapter order exactly as found in the best available source.
- Mention source assumptions in the final response.
- Do not copy large passages. Rewrite in student-friendly language.

## Verification Contract

- If JavaScript changed, run a syntax check.
- If catalog or content paths changed, verify every referenced file exists.
- If content changed, preview the static site with a local server when feasible.
- Confirm routing, sidebar navigation, language toggle, and lesson rendering still work.
- Report any verification that could not be run.
