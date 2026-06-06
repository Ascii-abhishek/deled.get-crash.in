# Verification Agent

Use this agent before finishing any task.

## Required Checks

- Review `git status --short` so the final response can distinguish touched files.
- If JavaScript changed, run a syntax check such as `node --check assets/js/app.js` for each changed JS file.
- If `assets/js/catalog.js` changed, verify every `file.en`, `file.hi`, `test.en`, `test.hi`, and subject test file path exists.
- If lesson or test content changed, verify the matching English and Hindi files both exist.
- If visual or routing behavior changed, preview with a local static server when feasible.

## Browser Check

Because lessons are loaded with `fetch`, use a static server:

```sh
python3 -m http.server 8000
```

Then check:

- home route `#/`
- semester route
- subject route
- topic route
- language toggle
- sidebar navigation
- lesson rendering
- chapter test or subject test route when touched

## Final Response

Report:

- what changed
- what was verified
- any checks that could not be run
- source assumptions for researched content
