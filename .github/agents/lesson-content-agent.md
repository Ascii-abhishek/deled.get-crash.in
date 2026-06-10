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
- Keep lessons crash-course style, structured, exam-friendly, and classroom-connected while preserving full chapter coverage.
- Keep English and Hindi lesson structure parallel without making Hindi a literal translation.
- Create matching chapter-level tests for every completed `content-chapter` task.
- Create or revise matching subject-level tests for `content-test` tasks.
- Update `catalog.js` only when titles, summaries, file paths, topic maps, or test maps are changing.

## Lesson Shape

Use semantic HTML snippets only. Do not include `<!doctype>`, `<html>`, `<head>`, or `<body>`.

Preferred structure:

1. `h1` topic title
2. Short purpose paragraph
3. Exam snapshot table with key terms, definitions, and examples
4. Core concept sections in bullets, short definitions, and tables
5. Difference or comparison table when the chapter has commonly confused concepts
6. Classroom connection for elementary teaching
7. Quick diagram or memory hook when useful
8. One-minute revision
9. Common exam lines or likely questions

## Test Shape

Every completed chapter needs a matching English and Hindi chapter test:

1. 10 multiple-choice questions with four options, `data-answer`, and short explanations.
2. 5 short-answer questions with model answers.
3. 4 or 5 long-answer questions with structured model answers.

Every completed subject needs matching English and Hindi subject-level tests:

1. 20 multiple-choice questions.
2. 10 short-answer questions.
3. 5 to 7 long-answer questions.

## Guardrails

- Do not create uneven English/Hindi coverage.
- Do not add decorative content or marketing-style sections.
- Do not replace full chapter coverage with a tiny summary. Compress into crash-course form instead.
- Do not inflate lesson length with filler; keep revision value high.
- Do not reduce existing lesson or test depth unless asked.
