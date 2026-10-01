# Gift voucher with Tailwind, as PDF and PNG

A voucher in the DIN long format, styled with Tailwind classes that are compiled at render time, arbitrary values such as `h-[99mm]` included. The expiry date is three years after the issue date through `dateAdd`, the message appears only when there is one, and the same template renders as a PNG for the mail.

![Gift voucher with Tailwind, as PDF and PNG, as rendered](preview.webp)

**Engine:** Liquid · **Output:** PDF · **Helpers:** `money`, `date`, `dateAdd`, `qrcode`, `default`

[See it on formfeed.dev](https://formfeed.dev/examples/gutschein?utm_source=github-templates&utm_content=gutschein) · [example.pdf](example.pdf)

## What this shows

- `tailwind: true` compiles the classes the markup uses at render time, arbitrary values such as `h-[99mm]` and `text-[40pt]` included; there is no stylesheet.
- The page is `210mm` × `99mm` (DIN long) with zero margins, so the gradient runs to the edge.
- `voucher.issued | dateAdd: 3, "years" | date: "dd.MM.yyyy"` prints the expiry date `18.09.2029`.
- `{% if voucher.message %}` leaves the message line out when there is none, and `default: "Sie"` addresses a voucher without a recipient.
- `output: "png"` renders the same template as an image for the mail; without it the answer is the PDF for printing.

## Files

| File | What it is |
| --- | --- |
| [`template.html`](template.html) | the template |
| [`settings.json`](settings.json) | paper, margins and output settings |
| [`data/default.json`](data/default.json) | the sample data it was designed with |
| [`template.json`](template.json) | name, kind and engine, which `formfeed templates push` needs |

## Use it

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/gutschein?utm_source=github-templates&utm_content=gutschein) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`money`, `date`, `dateAdd`, `qrcode`, `default`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push gutschein`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render gutschein`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=gutschein) is a PDF and image generation API with a free plan: 100 units a month, no card.
