# Event ticket with QR code and PDF417

A print-at-home ticket on its own paper size, 210 × 80 mm without margins: a QR code for the check-in app on the stub, the ticket number again as a PDF417 strip for hand scanners, and the start time, doors and weekday formatted in German from two timestamps.

![Event ticket with QR code and PDF417, as rendered](preview.webp)

**Engine:** Jinja2 · **Output:** PDF · **Helpers:** `date`, `money`, `upper`, `qrcode`, `barcode`

[See it on formfeed.dev](https://formfeed.dev/examples/ticket?utm_source=github-templates&utm_content=ticket) · [example.pdf](example.pdf)

## What this shows

- The paper is `210mm` × `80mm` with zero margins, so the PDF is the ticket and nothing around it.
- `barcode(ticket.id, { type: 'pdf417', height: 8 })` and `qrcode(ticket.check_in_url, { size: 120 })` encode the same ticket for two kinds of scanner.
- `date('EEEE, d. MMMM yyyy')` and `date('HH:mm')` turn two ISO timestamps into `Donnerstag, 12. November 2026`, doors `08:30` and start `09:30`, in the template’s time zone `Europe/Berlin`.
- The stub is a flex column with a dashed border: plain CSS, no image of a ticket.
- Render it right after the purchase and attach the download to the confirmation mail.

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

- **Copy it.** It is plain HTML and CSS with Jinja2 tags. The helpers (`date`, `money`, `upper`, `qrcode`, `barcode`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push ticket`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render ticket`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=ticket) is a PDF and image generation API with a free plan: 100 units a month, no card.
