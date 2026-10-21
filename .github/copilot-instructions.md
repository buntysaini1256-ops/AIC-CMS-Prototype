# Copilot instructions

## Project shape

- The application is a standalone browser UI in `AIC CMS - Minimal UI.html`. Its page markup, styles, and JavaScript are embedded in that file; there is no separate frontend or backend package.
- The script keeps the demo cases and workflow stages in `CASES` and `STAGES`, with shared interaction state in `state`. `render()` selects a page renderer for the dashboard, case explorer, QC, upload, masters, and case workspace.
- Case workspace views cover metadata/editor steps, XML and HTML previews, and a PDF viewer. Case records refer to the sample PDFs by filename, so keep those references aligned with the files at the repository root.
- The XML and PDF files at the root are sample legal-case documents. The UI uses in-memory demo data; no API or browser persistence layer is present.

## Build and checks

- No build, test, or lint scripts or package manifests are configured. There is no automated test runner or single-test command.
- To inspect UI changes, open `AIC CMS - Minimal UI.html` in a browser and exercise the affected screen or workflow.

## Code conventions

- Keep UI changes within the existing single-file structure unless a task explicitly calls for a new application structure. The CSS is in the `<style>` block and the browser-side logic is in the `<script>` block.
- Treat `state` and `CASES` as the shared demo model: update them through the existing handlers and rerender with `render()` when a view needs refreshing.
- Keep stage-dependent UI and transitions consistent with the ordered `STAGES` array; stage indexes are used throughout the dashboard and case workspace.
- View renderers build HTML strings and insert them into the page. Escape dynamic text with the existing `escapeHtml()` helper before interpolating it into markup.
