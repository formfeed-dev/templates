# Course certificate in Handlebars

A landscape certificate with a verification QR code, rendered one at a time as PNG or for a whole course as a batch that ends in a zip. Handlebars takes options as hash arguments: `{{qrcode verify_url size=96}}`.

![Course certificate in Handlebars, as rendered](preview.webp)

**Engine:** Handlebars · **Output:** PDF · **Helpers:** `date`, `qrcode`, `upper`

[See it on formfeed.dev](https://formfeed.dev/examples/certificate?utm_source=github-templates&utm_content=certificate) · [example.pdf](example.pdf)

## What this shows

- A4 landscape with zero margins: the frame is plain CSS on a box exactly as tall as the page (`210mm`), so it prints to the edge.
- `{{qrcode verify_url size=96}}` turns the verification link into a QR code; `{{upper id}}` prints the certificate number as `CERT-8841`.
- `head.html` loads Inter and Playfair Display from Google Fonts; the render-worker fetches them once and serves them from its cache afterwards.
- `output: "png"` renders the same template as an image for sharing; without it the answer is the PDF.
- A whole course goes through `renders.batch` with `zip: true`: one job, one archive at the end.

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

- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`date`, `qrcode`, `upper`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push certificate`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render certificate`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=certificate) is a PDF and image generation API with a free plan: 100 units a month, no card.
