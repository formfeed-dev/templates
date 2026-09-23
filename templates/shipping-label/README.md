# Shipping label, 100×150 mm

A custom paper size for thermal printers, a Code 128 tracking barcode, a QR code built from a URL and the tracking number, and the package contents summed in the template. `barcode` also does EAN-13, ITF-14, DataMatrix and PDF417.

![Shipping label, 100×150 mm, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `barcode`, `qrcode`, `number`, `sum`, `upper`

[See it on formfeed.dev](https://formfeed.dev/examples/shipping-label?utm_source=github-templates&utm_content=shipping-label) · [example.pdf](example.pdf)

## What this shows

- The paper is a custom size, `100mm` × `150mm` with 4 mm margins, the common format of thermal label printers.
- `barcode(shipment.tracking, { type: 'code128', height: 18 })` draws the tracking code; the same helper does EAN-13, ITF-14, DataMatrix and PDF417.
- The QR code is built in the template: `~` joins the tracking URL and the number before `qrcode` encodes it.
- `sum('qty')` counts the items, so the label says “3 items” without the caller adding anything up.
- The PDF goes straight to the printer: no browser and no print dialogue in between.

## Files

| File | What it is |
| --- | --- |
| [`template.html`](template.html) | the template |
| [`style.css`](style.css) | its stylesheet |
| [`settings.json`](settings.json) | paper, margins and output settings |
| [`data/default.json`](data/default.json) | the sample data it was designed with |
| [`template.json`](template.json) | name, kind and engine, which `formfeed templates push` needs |

## Use it

- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`barcode`, `qrcode`, `number`, `sum`, `upper`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push shipping-label`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render shipping-label`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=shipping-label) is a PDF and image generation API with a free plan: 100 units a month, no card.
