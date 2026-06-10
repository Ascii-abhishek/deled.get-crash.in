# Skill: Syllabus Map

Use this skill before writing chapter content for any subject whose correct chapter list is not already proven in the catalog.

## Goal

Create the correct basic subject structure first:

- official or best-available chapter order
- stable topic IDs
- bilingual topic titles
- bilingual one-sentence summaries
- valid English and Hindi placeholder files for every mapped topic

## Process

1. Read `README.md`, `.github/AGENTS.md`, `todo.md`, and `assets/js/catalog.js`.
2. Research the exact subject chapter list in order.
3. Prefer official SCERT, board, government, university, or official textbook sources.
4. If official sources are unavailable, compare multiple credible syllabus or book sources.
5. Update only the target subject in `assets/js/catalog.js`.
6. Keep the source order. Do not alphabetize chapters.
7. Create minimal placeholder files for newly referenced English and Hindi topic paths.
8. Do not create chapter tests unless the syllabus source explicitly requires a structural test entry and files are created.

## Placeholder HTML

Use short placeholder snippets like:

```html
<h1>Chapter Title</h1>
<p>This chapter has been added to the syllabus map. Full revision content will be added in a later content task.</p>
```

Hindi placeholders should be natural:

```html
<h1>अध्याय शीर्षक</h1>
<p>यह अध्याय पाठ्यक्रम संरचना में जोड़ दिया गया है। पूरा पुनरावृत्ति पाठ बाद के कंटेंट कार्य में जोड़ा जाएगा।</p>
```

## Guardrails

- Do not write full lesson content in this phase.
- Do not change other subjects.
- Do not remove existing completed content unless the project owner explicitly asks.
- Do not point catalog entries to missing files.
- Mention sources and assumptions in the final response.
