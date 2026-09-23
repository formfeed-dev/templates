# German timesheet (Stundenzettel) with balance and projects

A weekly timesheet in Handlebars: weekdays formatted in German, worked hours summed and set against the target with `subtract`, and the same entries grouped by project for the summary. Two signature lines stay together at the foot of the page.

![German timesheet (Stundenzettel) with balance and projects, as rendered](preview.webp)

**Engine:** Handlebars · **Output:** PDF · **Helpers:** `date`, `number`, `sum`, `subtract`, `groupBy`

[See it on formfeed.dev](https://formfeed.dev/examples/stundenzettel?utm_source=github-templates&utm_content=stundenzettel) · [example.pdf](example.pdf)

## What this shows

- `{{date day "EEE, dd.MM."}}` prints the weekday in German (`Mo., 14.09.`) because the template’s locale is `de-DE`.
- The balance is `(subtract (sum entries "hours") sheet.target_hours)`: 40.5 hours worked against 40 gives `0,50` h.
- `{{#each (groupBy entries "project")}}` reuses the same entries for the project summary, with `sum items "hours"` inside each group.
- Start, end and break are shown as they were recorded; the hours per day come from the time tracking system, which knows its own rounding rules.
- One batch renders the whole team’s week, with the employee number and the calendar week in each file name.

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

- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`date`, `number`, `sum`, `subtract`, `groupBy`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push stundenzettel`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render stundenzettel`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=stundenzettel) is a PDF and image generation API with a free plan: 100 units a month, no card.
