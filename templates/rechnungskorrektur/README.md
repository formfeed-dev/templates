# German invoice correction (Rechnungskorrektur)

What is commonly called a “Gutschrift”: a correction that refers to the original invoice by number and date and shows the amounts as negatives. The data holds the positive values of the corrected lines; the template turns the sign with `multiply(-1)` and computes VAT on the result.

![German invoice correction (Rechnungskorrektur), as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `money`, `number`, `date`, `sum`, `multiply`

[See it on formfeed.dev](https://formfeed.dev/examples/rechnungskorrektur?utm_source=github-templates&utm_content=rechnungskorrektur) · [example.pdf](example.pdf)

## What this shows

- The data holds the corrected lines as positive values; `multiply(-1)` turns the sign for display, so the same line objects serve invoice and correction.
- `sum('total') | multiply(-1)` is the net correction of `-480,00 €`; VAT follows from it, which gives `-571,20 €`.
- The document names the original invoice by number and date, which is what makes it a correction of that invoice.
- The closing sentence prints the amount positive again, `571,20 €`, and takes the settlement wording from the data.
- It shares the letter layout and the legal footer with the quote and the reminder: one `style.css`, several templates.

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

- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`money`, `number`, `date`, `sum`, `multiply`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push rechnungskorrektur`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render rechnungskorrektur`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=rechnungskorrektur) is a PDF and image generation API with a free plan: 100 units a month, no card.
