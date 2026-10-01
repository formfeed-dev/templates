# German invoice with GiroCode

Line items, net, VAT and gross computed in the template, dates in German format with a due date 14 days out, a SEPA QR code banking apps scan, and a running footer with page numbers. Your code sends the facts; the template owns the legal layout.

![German invoice with GiroCode, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `money`, `number`, `date`, `dateAdd`, `sum`, `epcQr`

[See it on formfeed.dev](https://formfeed.dev/examples/invoice?utm_source=github-templates&utm_content=invoice-de) · [example.pdf](example.pdf)

## What this shows

- The request carries no derived numbers: `sum('total')` adds the lines, and VAT and gross follow from `invoice.vat_rate` inside the template.
- `epcQr` draws the GiroCode (EPC QR code) from name, IBAN, BIC, amount and the payment reference as free text, so a banking app fills in the transfer from a scan. For a single one, the [GiroCode generator](https://formfeed.dev/tools/girocode?utm_source=github-templates&utm_content=invoice-de) makes the same code in your browser.
- `dateAdd(14, 'days')` sets the due date; with the locale `de-DE`, `date('dd.MM.yyyy')` and `money` print `24.09.2026` and `3.760,40 €`.
- The footer is a Chromium footer template with `pageNumber` and `totalPages`: “Seite 1 von 1” stays correct when the lines run over several pages.
- `filename` is a template as well, so the download is called `rechnung-2026-0042.pdf`.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/invoice?utm_source=github-templates&utm_content=invoice-de) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`money`, `number`, `date`, `dateAdd`, `sum`, `epcQr`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push invoice-de`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render invoice-de`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=invoice-de) is a PDF and image generation API with a free plan: 100 units a month, no card.
