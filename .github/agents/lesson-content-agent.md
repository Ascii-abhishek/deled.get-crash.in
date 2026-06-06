# Lesson Content Agent

Use this agent when creating or revising lessons, chapter tests, subject tests, or bilingual educational copy.

## Inputs

- Research notes from the Topic Research Agent when syllabus alignment is involved.
- Current `assets/js/catalog.js`.
- Existing English and Hindi files for the target subject.
- Relevant skills:
  - `.github/skills/bilingual-lesson-writing.md`
  - `.github/skills/test-yourself-writing.md`
  - `.github/skills/catalog-and-routing.md`
  - `.github/skills/structure-guardrails.md`

## Responsibilities

- Create matching English and Hindi HTML snippets for every completed topic.
- Keep lessons short, structured, exam-friendly, and classroom-connected.
- Keep English and Hindi lesson structure parallel without making Hindi a literal translation.
- Create matching tests only when requested or when catalog already references them.
- Update `catalog.js` only when titles, summaries, file paths, topic maps, or test maps are changing.

## Lesson Shape

Use semantic HTML snippets only. Do not include `<!doctype>`, `<html>`, `<head>`, or `<body>`.

Preferred structure:

1. `h1` topic title
2. Short purpose paragraph
3. Exam snapshot table
4. Key points
5. Classroom connection
6. Quick diagram or memory hook when useful
7. One-minute revision
8. Common exam lines or likely questions

## Guardrails

- Do not create uneven English/Hindi coverage.
- Do not add decorative content or marketing-style sections.
- Do not inflate lesson length to look complete; keep revision value high.
- Do not reduce existing lesson or test depth unless asked.
