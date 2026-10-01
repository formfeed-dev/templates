# German delivery note (Lieferschein)

A delivery note without prices: ordered against delivered quantities, a note on lines with a remainder to follow, the number as a Code 128 barcode for goods receipt, and a signature block that never splits across pages. Written in Liquid.

![German delivery note (Lieferschein), as rendered](preview.webp)

**Engine:** Liquid · **Output:** PDF · **Helpers:** `barcode`, `date`, `number`, `sum`, `default`

[See it on formfeed.dev](https://formfeed.dev/examples/lieferschein?utm_source=github-templates&utm_content=lieferschein) · [example.pdf](example.pdf)

## What this shows

- No prices anywhere: the table compares `ordered` and `delivered`, and a Liquid `{% if line.delivered < line.ordered %}` adds “Restmenge folgt” to short lines.
- `barcode: type: 'code128', height: 12` draws the delivery note number, so goods receipt books it with a scanner.
- `sum: "delivered"` and `sum: "ordered"` give the closing line “44 von 48 Einheiten geliefert”.
- `default: customer.contact` falls back to the contact person when the delivery names no recipient of its own.
- The acknowledgement of receipt has `break-inside: avoid`, so the signature line never lands alone on a new page.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/lieferschein?utm_source=github-templates&utm_content=lieferschein) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`barcode`, `date`, `number`, `sum`, `default`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push lieferschein`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render lieferschein`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=lieferschein) is a PDF and image generation API with a free plan: 100 units a month, no card.
