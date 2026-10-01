# Trade price list with EAN barcodes

A product feed goes in unsorted. `groupBy` makes a section per category, `sortBy` orders each by name, `min` and `max` give the price range in the heading, and every row carries its EAN-13 barcode. A category never breaks across a page.

![Trade price list with EAN barcodes, as rendered](preview.webp)

**Engine:** Liquid · **Output:** PDF · **Helpers:** `groupBy`, `sortBy`, `min`, `max`, `length`, `money`, `multiply`, `barcode`, `date`

[See it on formfeed.dev](https://formfeed.dev/examples/price-list?utm_source=github-templates&utm_content=price-list) · [example.pdf](example.pdf)

## What this shows

- `products | groupBy: 'category'` makes a section per category in the order the feed names them, and `sortBy: 'name'` sorts each section.
- `min: 'price'` and `max: 'price'` put each category’s price range into its heading: desk lamps run from `£49.50` to `£118.00`.
- Every row carries its EAN-13 code as a barcode, `barcode: type: 'ean13'`, with the digits in their usual groups. The sample codes start with 20, a prefix GS1 keeps for numbers that are only used inside one company.
- `multiply: product.pack` gives the price per pack beside the unit price: ten bulbs at `£3.20` make `£32.00`.
- A category has `break-inside: avoid`, and the footer repeats the validity date from the data on every page.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/price-list?utm_source=github-templates&utm_content=price-list) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`groupBy`, `sortBy`, `min`, `max`, `length`, `money`, `multiply`, `barcode`, `date`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push price-list`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render price-list`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=price-list) is a PDF and image generation API with a free plan: 100 units a month, no card.
