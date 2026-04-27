# D.El.Ed Learning

Static bilingual learning website for Diploma in Elementary Education students.

This project is intentionally simple: plain HTML, CSS, and JavaScript only. It is designed to deploy directly on Cloudflare Pages without a build step, login system, database, backend, or framework.

## LLM Handoff Summary

Use this section as context when asking another LLM to update the website.

The website is a browser-only D.El.Ed learning portal. Students first land on a home page and choose one of four semesters. After choosing a semester, they enter a course-reader interface inspired by ByteByteGo: a dark left sidebar for navigation and progress, and a large right-side reading area for the selected content.

The site supports two languages for now: English (`en`) and Hindi (`hi`). All semester names, subject names, topic names, summaries, and lesson content should exist in both languages. The language toggle changes the whole interface and loads the matching HTML content file. Student progress is stored only in the browser with `localStorage`.

## Design Intent

- Home page: clean, simple, and focused on selecting a semester.
- Reader page: two-panel learning layout.
- Left panel: semester/subject title, progress count, reset button, progress bar, and navigation list.
- Right panel: actual learning content loaded from HTML lesson snippets.
- Mobile: sidebar can collapse/expand using the round button that remains visible when collapsed.
- Top bar: must stay on every page with site logo/name on the left and controls on the right.
- Controls: language toggle, theme button, font size increase/decrease, and font style selector.
- Visual style: quiet educational interface, readable typography, minimal decoration, clear spacing.

## Structure

- `index.html` - single page app shell.
- `assets/css/` - global and reader layout styles.
- `assets/js/catalog.js` - semester, subject, topic, and content file mapping.
- `assets/js/app.js` - hash routing, sidebar navigation, progress marking.
- `assets/js/settings.js` - language, theme, and font controls saved in browser storage.
- `assets/js/i18n.js` - interface labels in English and Hindi.
- `assets/js/test-yourself.js` - self-check behavior for chapter and subject tests.
- `assets/templates/test-yourself.html` - copyable HTML skeleton for new tests.
- `content/semester-*/<subject>/en|hi|media/` - HTML lesson files and shared subject media.

## Important Files

### `index.html`

Contains the app shell and top bar. Avoid putting semester, subject, or lesson content here. Content should be added through `catalog.js` and HTML lesson files.

### `assets/js/catalog.js`

This is the main content map. It defines:

- semesters
- subjects inside each semester
- topics inside each subject
- English and Hindi display text
- English and Hindi HTML file paths

When adding any new content, update this file first so the app knows where the content lives.

### `content/semester-*/...`

These folders contain the actual lesson files. Each topic should have one English HTML file and one Hindi HTML file. Chapter-level tests live beside the chapter HTML files. Subject-level tests live under `tests/en` and `tests/hi`. Media shared by both languages for a subject lives in the subject's `media` folder.

Recommended path pattern:

```txt
content/semester-1/subject-slug/en/topic-slug.html
content/semester-1/subject-slug/hi/topic-slug.html
content/semester-1/subject-slug/en/test_topic-slug.html
content/semester-1/subject-slug/hi/test_topic-slug.html
content/semester-1/subject-slug/tests/en/test_subject-slug_1.html
content/semester-1/subject-slug/tests/hi/test_subject-slug_1.html
content/semester-1/subject-slug/media/example-image.png
```

Example:

```txt
content/semester-1/childhood-and-development/en/meaning-of-childhood.html
content/semester-1/childhood-and-development/hi/meaning-of-childhood.html
```

## How Routing Works

The app uses hash routing so it works on static hosting.

Examples:

```txt
#/
#/semester/1
#/semester/1/subject/childhood-and-development
#/semester/1/subject/childhood-and-development/topic/meaning-of-childhood
```

No server-side routing is required.

## How To Add A New Topic

1. Create the English HTML file:

```txt
content/semester-1/example-subject/en/example-topic.html
```

2. Create the Hindi HTML file:

```txt
content/semester-1/example-subject/hi/example-topic.html
```

3. Add the topic entry inside the correct subject in `assets/js/catalog.js`:

```js
{
  id: "example-topic",
  title: {
    en: "Example Topic",
    hi: "उदाहरण टॉपिक"
  },
  summary: {
    en: "Short one-line summary for the topic.",
    hi: "टॉपिक का छोटा एक-पंक्ति सारांश।"
  },
  file: {
    en: "content/semester-1/example-subject/en/example-topic.html",
    hi: "content/semester-1/example-subject/hi/example-topic.html"
  },
  test: {
    en: "content/semester-1/example-subject/en/test_example-topic.html",
    hi: "content/semester-1/example-subject/hi/test_example-topic.html"
  }
}
```

## How To Add A New Subject

Add a new subject object inside the correct semester in `assets/js/catalog.js`.

Subject shape:

```js
{
  id: "subject-slug",
  title: {
    en: "Subject Name",
    hi: "विषय का नाम"
  },
  summary: {
    en: "Short description of what the subject contains.",
    hi: "विषय में क्या शामिल है इसका छोटा विवरण।"
  },
  topics: [
    // topic objects go here
  ],
  tests: [
    {
      id: "example-subject-1",
      title: {
        en: "Test 1",
        hi: "टेस्ट 1"
      },
      summary: {
        en: "Mixed subject-level practice.",
        hi: "मिश्रित विषय-स्तरीय अभ्यास।"
      },
      file: {
        en: "content/semester-x/subject-slug/tests/en/test_subject-slug_1.html",
        hi: "content/semester-x/subject-slug/tests/hi/test_subject-slug_1.html"
      }
    }
  ]
}
```

Then create matching HTML files under:

```txt
content/semester-x/subject-slug/en/
content/semester-x/subject-slug/hi/
content/semester-x/subject-slug/tests/en/
content/semester-x/subject-slug/tests/hi/
content/semester-x/subject-slug/media/
```

## How To Add Or Edit A Semester

Semesters are listed in `assets/js/catalog.js` under `window.COURSE_CATALOG.semesters`.

Each semester has:

- `id`
- bilingual `title`
- bilingual `summary`
- `subjects`

There are currently four semesters. If the real D.El.Ed structure changes by state/board/university, update the semester and subject list in `catalog.js`.

## HTML Content Guidelines

Use simple semantic HTML inside lesson files. The app loads these files into the reader shell, so do not include `<!doctype>`, `<html>`, `<head>`, or `<body>` tags.

For media shared by English and Hindi pages, place files in the subject's `media` folder and reference them relatively:

```html
<img src="../media/example-image.png" alt="Short useful description">
```

Recommended lesson shape:

```html
<h1>Topic Title</h1>

<p>Short introduction paragraph.</p>

<h2>Key Points</h2>

<ul>
  <li>Point one.</li>
  <li>Point two.</li>
  <li>Point three.</li>
</ul>

<h2>Classroom Connection</h2>

<p>Explain how this topic applies to elementary classrooms.</p>

<h2>Reflect</h2>

<p>Add one question or activity for the student.</p>
```

Keep language simple and useful for D.El.Ed students. Prefer examples from elementary classrooms, school internships, child observation, lesson planning, assessment, and local/community context.

## Test Yourself Template

Each chapter can include a chapter-level test, and each subject can include multiple subject-level tests. In the reader, chapter tests are opened by the bottom `Test Yourself` button beside `Mark as Complete`. Subject tests appear in the left pane after chapter links under a separate `Test Yourself` heading.

Use three sections: multiple choice, short answer, and long answer. Copy the starter file from `assets/templates/test-yourself.html` when creating a new test.

```html
<section class="test-yourself">
  <h2>Test Yourself</h2>
  <h3>Test 1</h3>

  <p class="test-section-title">Section 1: Multiple Choice</p>

  <div class="test-card">
    <fieldset class="test-mcq" data-answer="C">
      <legend>1. Question text?</legend>
      <div class="mcq-options">
        <label class="mcq-option"><input type="radio" name="test1-q1" value="A"><span class="option-text">Option A</span></label>
        <label class="mcq-option"><input type="radio" name="test1-q1" value="B"><span class="option-text">Option B</span></label>
        <label class="mcq-option"><input type="radio" name="test1-q1" value="C"><span class="option-text">Option C</span></label>
        <label class="mcq-option"><input type="radio" name="test1-q1" value="D"><span class="option-text">Option D</span></label>
      </div>
      <button class="test-check-answer" type="button">Check answer</button>
      <p class="test-feedback" aria-live="polite"></p>
    </fieldset>
  </div>

  <details class="test-answer-key">
    <summary>Section 1 Answers</summary>
    <div class="answer-body">
      <ol>
        <li><strong>C: "Option C"</strong> One or two sentences explaining why this answer is correct.</li>
      </ol>
    </div>
  </details>

  <p class="test-section-title">Section 2: Short Answer Questions</p>
  <details class="qa-card">
    <summary>1. Short answer question?</summary>
    <div class="answer-body">
      <p>Concise model answer.</p>
    </div>
  </details>

  <p class="test-section-title">Section 3: Long Answer Questions</p>
  <details class="qa-card">
    <summary>1. Long answer question?</summary>
    <div class="answer-body">
      <p>Structured model answer with points, examples, or a small table.</p>
    </div>
  </details>
</section>
```

## Browser Storage

The site uses `localStorage` for:

- selected language
- selected theme
- font size
- font style
- completed topic progress

There is no login. Progress is device/browser specific.

## Styling Notes

- Global layout and top bar styles live in `assets/css/base.css`.
- Reader/sidebar/content styles live in `assets/css/reader.css`.
- Use CSS variables in `:root` for colors and typography.
- Keep the reader layout close to the current two-panel design.
- Do not add a heavy landing page; the home page should stay practical and semester-focused.
- Make sure mobile layout remains usable after any sidebar or content changes.

## Deployment

Deploy the repository root directly to Cloudflare Pages as a static site. No build step is required.

## Local Preview

Because lesson files are loaded with `fetch`, preview with a small local server:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

## Current Placeholder Content

The current subject/topic list is sample placeholder content. In the next iteration, replace or expand it with researched D.El.Ed syllabus-aligned content. When researching, keep the `catalog.js` structure stable and update HTML files topic by topic.
