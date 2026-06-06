# Skill: Test Yourself Writing

Use this skill for chapter-level and subject-level tests.

## Structure

Copy the shape from `assets/templates/test-yourself.html`.

Use three sections:

1. Multiple choice
2. Short answer
3. Long answer

## Rules

- Create matching English and Hindi test files.
- Keep question counts consistent between languages.
- Keep answer keys consistent between languages.
- Use unique radio `name` values per question.
- Use `data-answer` on every MCQ fieldset.
- Keep explanations concise and student-friendly.

## Catalog Placement

- Chapter-level tests belong in topic entries as `test.en` and `test.hi`.
- Subject-level tests belong in the subject `tests` array.
- Do not add a test path to `catalog.js` until the matching files exist.

## Quality Bar

- MCQs should test core recall and common confusion points.
- Short answers should be useful for 2-3 mark exam preparation.
- Long answers should model structured 5-8 mark responses.
