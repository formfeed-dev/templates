# German cancellation confirmation (Kündigungsbestätigung)

A plain business letter whose paragraphs depend on the data: with a refund it names the amount and the date, without one it says that nothing is open, and the data export paragraph appears only when there is a deadline. Dates are written out in German.

![German cancellation confirmation (Kündigungsbestätigung), as rendered](preview.webp)

**Engine:** Handlebars · **Output:** PDF · **Helpers:** `date`, `money`

[See it on formfeed.dev](https://formfeed.dev/examples/kuendigungsbestaetigung?utm_source=github-templates&utm_content=kuendigungsbestaetigung) · [example.pdf](example.pdf)

## What this shows

- `{{#if contract.refund}} … {{else}} … {{/if}}` chooses between the refund paragraph and the sentence that nothing is open; the same template serves both cases.
- The data export paragraph sits in its own `{{#if contract.export_until}}` and disappears when the contract has no such deadline.
- `{{date contract.ends "d. MMMM yyyy"}}` writes `31. Dezember 2026`; the table at the top uses the short `dd.MM.yyyy` form.
- Letter layout, address window and the legal footer are shared with the other German letters through one `style.css`.

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

- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`date`, `money`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push kuendigungsbestaetigung`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render kuendigungsbestaetigung`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=kuendigungsbestaetigung) is a PDF and image generation API with a free plan: 100 units a month, no card.
