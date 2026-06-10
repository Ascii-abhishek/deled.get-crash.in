# Skill: Test Yourself Writing

Use this skill for chapter-level and subject-level tests.

## Structure

Copy the shape from `assets/templates/test-yourself.html`.

Use three sections:

1. Multiple choice
2. Short answer
3. Long answer

Use these required counts:

- Chapter-level test: 10 MCQs, 5 short-answer questions, and 4 or 5 long-answer questions.
- Subject-level test: 20 MCQs, 10 short-answer questions, and 5 to 7 long-answer questions.

## Rules

- Create matching English and Hindi test files.
- Keep question counts consistent between languages.
- Keep answer keys consistent between languages.
- Use unique radio `name` values per question.
- Use `data-answer` on every MCQ fieldset.
- Prefer `data-explanation` on MCQ fieldsets, following the Semester 4 Science tests.
- Keep explanations concise and student-friendly.

## Catalog Placement

- Chapter-level tests belong in topic entries as `test.en` and `test.hi`.
- Subject-level tests belong in the subject `tests` array.
- Do not add a test path to `catalog.js` until the matching files exist.
- A `content-chapter` task is not complete until the topic entry has chapter test paths and both test files exist.
- A `content-test` task is not complete until the subject `tests` array references the subject test files.

## Quality Bar

- MCQs should test core recall and common confusion points.
- Short answers should be useful for 2-3 mark exam preparation.
- Long answers should model structured 5-8 mark responses.
- Subject-level tests should mix chapters across the whole subject instead of repeating one chapter.
