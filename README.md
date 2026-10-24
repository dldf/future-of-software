# Markdown → HTML → Print

Write and revise the article in Markdown. Convert it to HTML for page layout, then use the browser's print preview to check and print it.

## Files

| File | Purpose |
| --- | --- |
| [future_software.md](future_software.md) | Authoritative article content. Edit the prose here. |
| [future_software.html](future_software.html) | Maintained HTML edition with page sections, figures, captions, and quotation credits. |
| [css/main.css](css/main.css) | Shared screen and print typography, margins, columns, and quote styling. |
| [img/](img/) | Local images used by both editions. |
| [AGENTS.md](AGENTS.md) | Instructions for future editing and conversion work. |

## Workflow

1. Edit `future_software.md`.
2. Ask the agent to bring the Markdown into `future_software.html`. Preserve the existing HTML/CSS layout while replacing its content with the current Markdown.
3. Review the browser's page view. Move content between page sections if necessary.
4. Check print preview using Letter, portrait, one page per sheet, Default margins, and 100% scale. CSS supplies the document's margins. Custom print-dialog margins can override them.
5. Print or export a PDF. Put temporary PDFs and screenshots in `output/`, which Git ignores.

The HTML is not automatically synchronized with Markdown. A conversion is a deliberate update. There is currently no saved conversion script or build command; Pandoc can help parse Markdown, but a plain conversion does not restore the page layout by itself.

## Conversion and layout

Keep the wording, punctuation, headings, emphasis, images, captions, and credits from Markdown. Do not silently copyedit or fact-check during conversion.

- The title, subtitle, and byline become the HTML header.
- An image and its following caption become a `figure` with an `img` and `figcaption`.
- A quotation becomes a `blockquote` containing a paragraph. Its attribution belongs in a `footer`. The opening paragraph is required for the decorative quote mark.
- Keep the Hamilton photo and its quote together in the existing `.row`, with `.half` on each column and the caption beneath the photo.
- Keep relative image paths so both editions use the same assets.

## Choosing page breaks

Each `<section class="page">` is a manually composed page. These sections are siblings inside the article. The stylesheet shows them as separate sheets in the browser and forces a printed page break between them. There is no JavaScript pagination.

Choose breaks deliberately when converting. Keep headings with the text they introduce, images with their captions, and quotations with their credits. Prefer topic transitions over filling every last line. Add a page when the content needs it; do not shrink the type just to retain the previous page count.

An explicit page instruction takes priority. In this workflow, a standalone Markdown horizontal separator can mark a requested page boundary. When there are no markers, use editorial judgment and report the chosen grouping. The current HTML groups Hamilton on page one, Moore and Good on page two, and Kurzweil and the chart on page three. That grouping can change as the article develops.

Pages are Letter size. `--page-margin-y` and `--page-margin-x` in `css/main.css` control both screen padding and printed margins. Print removes the page element's padding because `@page` supplies the margins there. Keep these dimensions and the typography aligned between screen and print.

Overflow is intentionally visible. If content runs into a margin or the next page, move it to another section. A `.page` section can still spill onto additional printed sheets if it contains too much content. Browser-added headers and footers appear only in print; disable them if you want the output to match the article view more closely.

## Before calling a conversion complete

Check that all Markdown content appears once, in order, and that both images and their captions survive. Check quotation credits, balanced HTML, relative asset paths, and page boundaries. When a browser is available, review screen and print layouts for overflow, clipped content, and unexpected blank pages. State clearly when visual verification was unavailable.

The Markdown, maintained HTML, stylesheet, images, and workflow documentation belong in the repository. Temporary conversions, backups, PDFs, and screenshots do not. No publication or remote repository is required for this workflow.
