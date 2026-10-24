# Agent Instructions

## Explain before editing

Inspect the current files and Git status first. Explain the cause, evidence, and proposed change in plain language before editing. Be direct, state uncertainty, and preserve unrelated user changes. Ask before destructive or difficult-to-reverse actions.

## Markdown → HTML → Print

This workspace is an article-writing and print-layout workflow. Read `README.md` for the file map and layout conventions.

- `future_software.md` is the content source. The user edits it between conversions; always reread it rather than relying on conversation history.
- `future_software.html` is the maintained print edition and layout template. Preserve its useful structure while updating content from Markdown.
- `css/main.css` owns the shared typography and screen/print layout. Preserve user changes to margins, sizing, colors, and quote styling unless the task requires changing them.
- `img/` holds shared image assets. Preserve paths and alt text.
- Do not update article content merely because you are working on documentation, CSS, or repository setup.

## Converting Markdown to HTML

Treat requests such as “bring the md to the html” as a content synchronization plus layout task, not a bare Markdown export.

1. Compare the current Markdown, HTML, and CSS. Preserve the Markdown file during conversion.
2. Carry over all current Markdown wording, punctuation, headings, emphasis, quotations, credits, images, and captions. Do not silently fix typos, factual claims, or incomplete sentences. Mention material issues separately when useful.
3. Restore the header, subtitle, byline, semantic figures, visible captions, and quotation footers. Do not invent dates or attribution details. Use only the date precision present in the source.
4. Keep quote text in a first-child paragraph inside `blockquote` so the CSS opening quote mark appears. Keep the credit outside that paragraph in a `footer`.
5. Preserve the Hamilton image/quote columns where appropriate, with the caption inside the figure. Apply `.half`, `.third`, and other width utilities to the element whose whole contents should share that width.
6. Organize the result into sibling `<section class="page">` containers inside `article`. Never nest pages.
7. Verify content fidelity, structure, and asset paths. Review the diff before reporting completion.

Pandoc is available in the current environment as a conversion aid. No persistent conversion script exists. Do not present a plain Pandoc export as a finished layout or claim an automated build is available.

## Page-break judgment

The user explicitly values thoughtful page breaks. Make routine pagination decisions without asking for confirmation at every break.

- Honor explicit user page instructions and intentional standalone Markdown separators used as page markers.
- When markers are absent, choose breaks at coherent topic transitions. The last conversion used Hamilton; Moore and Good; then Kurzweil and the chart. This is a starting point, not a fixed three-page requirement.
- Keep headings with following content, figures with captions, and quotes with credits. Keep related image/text columns together where they fit.
- Add pages or move whole blocks when needed. Do not shorten prose, omit content, change margins, or reduce font size to force a fit without authorization.
- Preserve the fixed Letter page view and shared margin variables. Screen padding represents the printed margins; print must remove that padding to avoid applying margins twice.
- Keep overflow visible for editing. Do not hide excess content to make a page look finished.
- Use CSS and manual page sections. Do not introduce JavaScript pagination unless requested.

## Converting HTML back to Markdown

Preserve the article content, heading hierarchy, emphasis, image paths, visible captions, and quotation credits. Replace presentation wrappers with Markdown structure. When preserving explicit page boundaries, use standalone horizontal separators. Explain that columns, decorative quotes, and physical page dimensions are restored in HTML, not in ordinary Markdown preview.

## Verification and reporting

- Check that visible content matches the current Markdown in order, with no missing or duplicated paragraphs, captions, or credits.
- Check balanced HTML, existing local assets, page structure, and preservation of unrelated CSS changes.
- When browser access is available, inspect both the browser layout and print preview. Check for overflow, orphaned headings, detached credits, unexpected page counts, and blank pages.
- Do not claim page fit or visual equivalence based only on source checks. Report unverified layout honestly when no browser is available.
- Use checks appropriate to the change. Do not add a test framework for routine document conversions.
- In the final response, link the updated artifact, briefly describe pagination decisions, and report verification limits.

## Git and files

- Use a focused branch for each task. Never commit directly to the default branch unless explicitly instructed.
- Review the diff and appropriate checks before committing. Do not merge, rewrite history, or change Git identity or credentials.
- Do not publish, push, or create a remote merely because this is a Git repository.
- The Markdown, maintained HTML edition, stylesheet, images, and documentation are intentional repository artifacts. Keep temporary exports and screenshots under ignored `output/`, and keep backups and conversion scratch files outside the repository.
- Follow more specific instructions in subdirectories. Do not modify files outside the task's scope.
