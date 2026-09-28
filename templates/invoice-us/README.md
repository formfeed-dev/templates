# US invoice with sales tax

Letter paper, dollars and US dates from the template’s `en-US` locale. Sales tax applies only to the lines marked taxable, a deposit reduces the balance, the status badge and the pay-online QR code follow from what is left to pay.

![US invoice with sales tax, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `sum`, `where`, `round`, `money`, `number`, `date`, `dateAdd`, `default`, `qrcode`, `replace`

[See it on formfeed.dev](https://formfeed.dev/examples/us-invoice?utm_source=github-templates&utm_content=invoice-us) · [example.pdf](example.pdf)

## What this shows

- `paper.format` is `Letter` and the locale `en-US`, so `money` prints `$11,278.46` and `date('MMMM d, yyyy')` prints `September 28, 2026`.
- Sales tax applies only to lines with `taxable: true`: `where('taxable', true) | sum('amount')` is the `$1,565.00` the 7.25% falls on, and `round(2)` fixes the tax at `$113.46` before it is added.
- `payments` is a list, so a deposit and any later part-payment each get a line under the total, and the balance due is what is left: `$8,278.46`.
- The badge and the QR code follow from the balance: “Paid” at zero, “Partially paid” after a deposit, and no pay-online code once nothing is due.
- `dateAdd(invoice.terms_days, 'days')` turns Net 30 into the due date, `October 28, 2026`, and `default('—')` stands in for a missing PO number.

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

- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`sum`, `where`, `round`, `money`, `number`, `date`, `dateAdd`, `default`, `qrcode`, `replace`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push invoice-us`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render invoice-us`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=invoice-us) is a PDF and image generation API with a free plan: 100 units a month, no card.
