# Skill: Static Site Verification

Use this skill after code, catalog, content, or route changes.

## Syntax Checks

For changed JavaScript files, run:

```sh
node --check assets/js/file-name.js
```

For `catalog.js`, also verify it still defines `window.COURSE_CATALOG`.

## Catalog Path Check

When `catalog.js` changes, ensure every referenced content path exists:

- topic `file.en`
- topic `file.hi`
- topic `test.en`
- topic `test.hi`
- subject test `file.en`
- subject test `file.hi`

## Browser Preview

Lesson files are fetched by the browser, so preview with:

```sh
python3 -m http.server 8000
```

Check the changed routes in both languages.

## Minimum Manual Checks

- Home route loads.
- Sidebar opens and navigates.
- Selected topic content renders.
- Language toggle loads the matching content file.
- Test answer checks work when tests were touched.
- Mobile layout remains usable when layout or CSS changed.
