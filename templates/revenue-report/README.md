# Report with a chart

A cover page, a page break and a Chart.js bar chart built from the data inside the template, with `pluck` pulling the labels and values out of the rows. Charts render without animation, so the PDF matches the preview. Long reports go async and report back through a webhook.

![Report with a chart, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `chart`, `pluck`, `sum`, `money`, `number`, `date`, `pageBreak`

[See it on formfeed.dev](https://formfeed.dev/examples/report?utm_source=github-templates&utm_content=revenue-report) · [example.pdf](example.pdf)

## What this shows

- The cover is a box 235 mm high, and `pageBreak()` starts the figures on a new page.
- `chart` takes a Chart.js configuration written in the template; `pluck('month')` and `pluck('revenue')` pull labels and values out of the rows.
- Charts render without animation, so the PDF shows the same chart as the editor preview.
- Derived figures stay in the template: the average order is `m.revenue / m.orders` per row, and the footer sums orders and revenue.
- `mode: "async"` answers at once with a queued render; `webhook_url` receives `render.completed` with the download URL when it is done.

## Files

| File | What it is |
| --- | --- |
| [`template.html`](template.html) | the template |
| [`style.css`](style.css) | its stylesheet |
| [`settings.json`](settings.json) | paper, margins and output settings |
| [`data/default.json`](data/default.json) | the sample data it was designed with |
| [`template.json`](template.json) | name, kind and engine, which `formfeed templates push` needs |

## Use it

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/report?utm_source=github-templates&utm_content=revenue-report) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`chart`, `pluck`, `sum`, `money`, `number`, `date`, `pageBreak`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push revenue-report`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render revenue-report`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=revenue-report) is a PDF and image generation API with a free plan: 100 units a month, no card.
