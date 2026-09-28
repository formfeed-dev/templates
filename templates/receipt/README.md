# Till receipt on an 80 mm roll

A receipt for thermal printers whose page is exactly as long as the receipt: the template writes its own `@page` size from the number of items and VAT rates. Prices include VAT, and the VAT analysis per rate is worked out in the template with `where` and `sum`.

![Till receipt on an 80 mm roll, as rendered](preview.webp)

**Engine:** Liquid · **Output:** PDF · **Helpers:** `sum`, `where`, `money`, `number`, `barcode`, `qrcode`, `date`, `dateAdd`

[See it on formfeed.dev](https://formfeed.dev/examples/receipt?utm_source=github-templates&utm_content=receipt) · [example.pdf](example.pdf)

## What this shows

- The paper is 80 mm wide and as long as the receipt: the template writes `@page { size: 80mm {{ length }}mm; }` from the number of items and VAT rates, and `preferCssPageSize: true` lets that rule decide. Four items and two rates give 160 mm on one page.
- Every row has a fixed height, and an item name too long for its line ends in an ellipsis instead of wrapping, which is what makes the length computable.
- Prices include VAT, so the analysis works backwards: `where: 'vat', rate.code | sum: 'total'` collects the gross amount of a rate, and `times: rate.rate | divided_by: divisor` takes the VAT out of it, `3.13` of `18.80` at 20%.
- `barcode: type: 'code128'` prints the receipt number for the returns desk, `qrcode` links to the digital copy, and `dateAdd: 30, 'days'` gives the last day for returns.
- Times are shown in the template’s time zone `Europe/London`: `07:41:00Z` in the data prints as `08:41`.

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

- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`sum`, `where`, `money`, `number`, `barcode`, `qrcode`, `date`, `dateAdd`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push receipt`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render receipt`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=receipt) is a PDF and image generation API with a free plan: 100 units a month, no card.
