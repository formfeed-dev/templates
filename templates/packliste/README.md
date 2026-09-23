# German packing list (Packliste) grouped by package

The request sends one flat list of items; `groupBy` turns it into a section per package with its own table and weight, and the opening line counts packages, items and kilograms. A package never splits across two pages.

![German packing list (Packliste) grouped by package, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `groupBy`, `sum`, `number`, `date`, `length`

[See it on formfeed.dev](https://formfeed.dev/examples/packliste?utm_source=github-templates&utm_content=packliste) · [example.pdf](example.pdf)

## What this shows

- `shipment.items | groupBy('package')` returns a list of `{ key, items }`, so the caller sends the items as they come out of the warehouse system and the template builds the sections.
- Each section sums its own weight with `package.items | sum('weight_kg')`; the opening line sums the whole list: 3 packages, 44 items, `19,6` kg.
- `number(1)` prints one decimal with the German comma because the locale is `de-DE`.
- `.package { break-inside: avoid }` keeps a package with its table on one page when the list grows.

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

- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`groupBy`, `sum`, `number`, `date`, `length`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push packliste`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render packliste`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=packliste) is a PDF and image generation API with a free plan: 100 units a month, no card.
