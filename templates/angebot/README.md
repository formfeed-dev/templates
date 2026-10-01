# German quote (Angebot) with optional items

A quote in the German letter layout: optional positions are listed but stay out of the sum, the discount and VAT are computed in the template, and the validity date follows from the quote date. The footer carries the company details German law expects on business letters.

![German quote (Angebot) with optional items, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `money`, `number`, `date`, `dateAdd`, `sum`, `where`

[See it on formfeed.dev](https://formfeed.dev/examples/angebot?utm_source=github-templates&utm_content=angebot) · [example.pdf](example.pdf)

## What this shows

- `where('optional', false)` keeps optional positions out of the sum while the table still lists them, marked as optional.
- Discount and VAT are arithmetic in the template: 5 % off `17.100,00 €`, then 19 % VAT, gives the `19.331,55 €` on the page.
- `dateAdd(quote.valid_days, 'days')` turns the quote date into “Gültig bis 15.10.2026”; the number of days comes from the data.
- The footer is a Chromium footer template with register court, managing director, VAT ID and bank details, plus `pageNumber` and `totalPages`.
- `.lines tr { break-inside: avoid }` keeps a position from being cut in half when a long quote runs onto a second page.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/angebot?utm_source=github-templates&utm_content=angebot) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`money`, `number`, `date`, `dateAdd`, `sum`, `where`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push angebot`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render angebot`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=angebot) is a PDF and image generation API with a free plan: 100 units a month, no card.
