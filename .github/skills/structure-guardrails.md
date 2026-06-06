# Skill: Structure Guardrails

Use this skill to prevent future agent runs from damaging the learning-site shape.

## Do Not Change Casually

- Number of semesters.
- Topic IDs.
- Subject IDs.
- Topic order.
- Test counts.
- Route formats.
- Progress key behavior.
- Existing bilingual coverage.

## Safe Change Rules

- Change IDs only when the task explicitly asks or research proves a correction is necessary.
- If an ID changes, update paths, routes, catalog references, and mention progress impact.
- If topic count changes, explain why in the final response.
- If test count changes, keep English and Hindi counts aligned.
- If content is shortened, preserve the same learning outcomes.
- If content is expanded, keep the revision style and avoid long theory blocks.

## Static Boundaries

- No framework.
- No build step.
- No backend.
- No login.
- No database.
- No heavy dependency.

## Consistency Checklist

- Bilingual catalog fields are complete.
- English and Hindi content files both exist.
- Tests are symmetrical across languages.
- Paths match actual folders.
- Final response names any intentional structure change.
