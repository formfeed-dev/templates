# German certificate of attendance (Teilnahmebescheinigung)

A certificate that lists what was taught: the course modules with their teaching units, the total as a number and spelled out in German by `numToWords`, and a QR code to verify the certificate number. Full-bleed A4 with zero margins, rendered for a whole course as one batch.

![German certificate of attendance (Teilnahmebescheinigung), as rendered](preview.webp)

**Engine:** Handlebars · **Output:** PDF · **Helpers:** `date`, `sum`, `number`, `qrcode`, `numToWords`

[See it on formfeed.dev](https://formfeed.dev/examples/teilnahmebescheinigung?utm_source=github-templates&utm_content=teilnahmebescheinigung) · [example.pdf](example.pdf)

## What this shows

- `{{#each course.modules}}` lists what was taught; `sum course.modules "units"` adds the units to 40.
- `numToWords (sum …) "de"` spells the total out as “vierzig”, which certificates of this kind usually do.
- `{{qrcode certificate.verify_url size=84}}` encodes the verification link next to the certificate number.
- Zero margins and a box exactly `297mm` high let the coloured bar run to the paper’s edge; `margin-top: auto` pins the signature to the bottom.
- Both dates share one range: `d. MMMM` for the first day, `d. MMMM yyyy` for the last.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/teilnahmebescheinigung?utm_source=github-templates&utm_content=teilnahmebescheinigung) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`date`, `sum`, `number`, `qrcode`, `numToWords`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push teilnahmebescheinigung`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render teilnahmebescheinigung`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=teilnahmebescheinigung) is a PDF and image generation API with a free plan: 100 units a month, no card.
