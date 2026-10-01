# German donation receipt (Spendenbescheinigung)

A receipt for a monetary donation laid out after the wording of the official German sample: the amount in figures and, through `numToWords`, in capital letters as the form asks, the exemption notice of the tax office, and the liability note. It shows the mechanics; have your tax adviser check the wording for your organisation.

![German donation receipt (Spendenbescheinigung), as rendered](preview.webp)

**Engine:** Liquid · **Output:** PDF · **Helpers:** `money`, `numToWords`, `date`, `upper`

[See it on formfeed.dev](https://formfeed.dev/examples/spendenbescheinigung?utm_source=github-templates&utm_content=spendenbescheinigung) · [example.pdf](example.pdf)

## What this shows

- `donation.amount | numToWords: "de" | upper` writes the amount as `ZWEIHUNDERTFÜNFZIG`, the spelled-out form the receipt asks for beside the figures.
- The yes/no boxes for the waiver of reimbursement are one Liquid `{% if donation.waiver %}`.
- Tax office, tax number, date and period of the exemption notice come from the data, so one template serves several organisations.
- The year’s receipts are one batch: an item per donation, a zip at the end.
- The wording follows the official sample for monetary donations to corporations; it is an example of the mechanics, not tax advice.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/spendenbescheinigung?utm_source=github-templates&utm_content=spendenbescheinigung) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`money`, `numToWords`, `date`, `upper`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push spendenbescheinigung`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render spendenbescheinigung`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=spendenbescheinigung) is a PDF and image generation API with a free plan: 100 units a month, no card.
