# Skill: Catalog And Routing

Use this skill whenever `assets/js/catalog.js` changes.

## Catalog Rules

- Semesters live in `window.COURSE_CATALOG.semesters`.
- Subjects live inside the correct semester `subjects` array.
- Topics live inside the correct subject `topics` array.
- Subject-level tests live inside the correct subject `tests` array.
- Every `title` and `summary` must include `en` and `hi`.
- Every `file` or `test` path must include `en` and `hi`.
- Completed topics must include chapter-level `test.en` and `test.hi` paths after their tests are created.
- Completed subjects must include subject-level test entries after their subject tests are created.

## Path Patterns

```txt
content/semester-1/subject-slug/en/topic-slug.html
content/semester-1/subject-slug/hi/topic-slug.html
content/semester-1/subject-slug/en/test_topic-slug.html
content/semester-1/subject-slug/hi/test_topic-slug.html
content/semester-1/subject-slug/tests/en/test_subject-slug_1.html
content/semester-1/subject-slug/tests/hi/test_subject-slug_1.html
content/semester-1/subject-slug/media/example-image.png
```

## Route Patterns

```txt
#/
#/semester/1
#/semester/1/subject/subject-slug
#/semester/1/subject/subject-slug/topic/topic-slug
#/semester/1/subject/subject-slug/topic/topic-slug/test
#/semester/1/subject/subject-slug/test/subject-test-id
```

## Verification

After editing `catalog.js`, verify:

- JavaScript syntax is valid.
- All referenced English and Hindi files exist.
- Topic IDs and subject IDs are stable lowercase slugs.
- Topic order and test counts changed only when the task required it.
- Chapter tests contain 10 MCQs, 5 short-answer questions, and 4 or 5 long-answer questions.
- Subject tests contain 20 MCQs, 10 short-answer questions, and 5 to 7 long-answer questions.

For `syllabus-map` tasks, every new topic path must have a minimal bilingual placeholder file. A placeholder may say the chapter is mapped and content is pending, but it must be valid lesson-snippet HTML and must not pretend to be a completed lesson.
