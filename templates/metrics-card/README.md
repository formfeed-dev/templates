# Metrics card with a chart, 1200×675

A 16:9 card for Slack, LinkedIn or X from thirty days of orders: totals, the change on the month before, the busiest day found with `sortBy` and `first`, and a Chart.js bar chart styled for a dark background, all computed in the template.

![Metrics card with a chart, 1200×675, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** image · **Helpers:** `sum`, `round`, `sortBy`, `first`, `number`, `money`, `date`, `chart`, `range`, `length`, `pluck`

[See it on formfeed.dev](https://formfeed.dev/examples/metrics-card?utm_source=github-templates&utm_content=metrics-card) · [example.png](example.png)

## What this shows

- Thirty rows of daily orders go in; the template sums them to `2,524` orders and `£214,791.00` and divides for the average order, `£85.10`.
- The change on August is computed and rounded in the template, `▲ 13.1%`, and turns red with a downward arrow when the month was weaker.
- `days | sortBy('orders', 'desc') | first` finds the busiest day, `Sun 27 Sep` with 126 orders.
- The chart is Chart.js with its `options` passed through, tick and grid colours for the dark card, and `range(1, (days | length) + 1)` numbers the days.
- `access: "public"` gives a link Slack can fetch for an image block in the team channel.

## Files

| File | What it is |
| --- | --- |
| [`template.html`](template.html) | the template |
| [`style.css`](style.css) | its stylesheet |
| [`head.html`](head.html) | extra `<head>` content, such as a font link |
| [`settings.json`](settings.json) | paper, margins and output settings |
| [`data/default.json`](data/default.json) | the sample data it was designed with |
| [`template.json`](template.json) | name, kind and engine, which `formfeed templates push` needs |

## Use it

- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`sum`, `round`, `sortBy`, `first`, `number`, `money`, `date`, `chart`, `range`, `length`, `pluck`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push metrics-card`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render metrics-card`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=metrics-card) is a PDF and image generation API with a free plan: 100 units a month, no card.
