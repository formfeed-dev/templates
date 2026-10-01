# Annual report with contents and bookmarks

A four-page report: a cover with a linked table of contents, KPI cards, a line chart comparing two years, regions sorted by revenue and an appendix of accounts grouped by region. `pdf.outline` turns the headings into bookmarks, and no region is split across a page.

![Annual report with contents and bookmarks, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `sum`, `sortBy`, `first`, `groupBy`, `length`, `pluck`, `chart`, `round`, `number`, `money`, `date`

[See it on formfeed.dev](https://formfeed.dev/examples/annual-report?utm_source=github-templates&utm_content=annual-report) · [example.pdf](example.pdf)

## What this shows

- The contents on the cover link to the chapters, and `pdf.outline` turns the headings into PDF bookmarks. Chromium 153 does not support `target-counter()`, so the contents give no page numbers; links and bookmarks do the navigating.
- `regions | sortBy('revenue', 'desc')` puts the largest region first, and each share is computed in its row: the United Kingdom is `36.3%` of `£591,000`.
- One line chart compares two years from the same rows: `pluck('previous')` and `pluck('revenue')` become two series, and `devicePixelRatio: 3` in the Chart.js options keeps it sharp when the PDF is zoomed.
- In the appendix each region is its own `tbody` with `break-inside: avoid`, so a region never splits across pages and the column headings repeat. The [page-break measurements](https://formfeed.dev/blog/page-breaks-in-tables?utm_source=github-templates&utm_content=annual-report) show why that works.
- The footer prints the document title from `pdf.metadata.title` through Chromium’s `title` class, beside the page number.

## Files

| File | What it is |
| --- | --- |
| [`template.html`](template.html) | the template |
| [`style.css`](style.css) | its stylesheet |
| [`head.html`](head.html) | extra `<head>` content, such as a font link |
| [`footer.html`](footer.html) | the running footer of every PDF page |
| [`settings.json`](settings.json) | paper, margins and output settings |
| [`data/default.json`](data/default.json) | the sample data it was designed with |
| [`template.json`](template.json) | name, kind and engine, which `formfeed templates push` needs |

## Use it

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/annual-report?utm_source=github-templates&utm_content=annual-report) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`sum`, `sortBy`, `first`, `groupBy`, `length`, `pluck`, `chart`, `round`, `number`, `money`, `date`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push annual-report`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render annual-report`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=annual-report) is a PDF and image generation API with a free plan: 100 units a month, no card.
