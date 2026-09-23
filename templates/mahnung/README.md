# German payment reminder (Mahnung) with GiroCode

A dunning letter in Handlebars: the wording changes with the final notice, open invoices are summed with interest and the reminder fee through nested helpers, and a GiroCode carries the total and the payment reference. The dunning run for all customers is one batch.

![German payment reminder (Mahnung) with GiroCode, as rendered](preview.webp)

**Engine:** Handlebars · **Output:** PDF · **Helpers:** `money`, `date`, `dateAdd`, `sum`, `add`, `epcQr`

[See it on formfeed.dev](https://formfeed.dev/examples/mahnung?utm_source=github-templates&utm_content=mahnung) · [example.pdf](example.pdf)

## What this shows

- `{{#if reminder.final}}` switches between the friendly reminder and the final notice; both share the new deadline from `dateAdd reminder.date reminder.days_to_pay "days"`.
- Handlebars nests helpers in brackets: `(add (add (sum invoices "amount") reminder.interest) reminder.fee)` is the `4.676,54 €` to pay.
- The same expression feeds `epcQr`, so the GiroCode carries exactly the amount printed above it, with the payment reference from the data.
- The days overdue come from your system as data. A template formats and adds up; it should not decide what is overdue.
- A dunning run is one batch: an item per customer, `zip: true`, and one job to wait for.

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

- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`money`, `date`, `dateAdd`, `sum`, `add`, `epcQr`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push mahnung`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render mahnung`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=mahnung) is a PDF and image generation API with a free plan: 100 units a month, no card.
