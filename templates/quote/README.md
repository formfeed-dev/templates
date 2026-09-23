# Quote marked as a draft

The template knows nothing about the mark: `post.watermark` stamps DRAFT across every page after the render, so the reviewed draft and the final quote come from the same template and data. The text is sized to the page diagonal and runs from bottom left to top right. Half a unit on top of the render; `/pdf/watermark` marks a PDF you rendered earlier.

![Quote marked as a draft, as rendered](preview.webp)

**Engine:** Liquid · **Output:** PDF · **Helpers:** `money`, `date`, `dateAdd`, `sum`

[See it on formfeed.dev](https://formfeed.dev/examples/draft-watermark?utm_source=github-templates&utm_content=quote) · [example.pdf](example.pdf)

## What this shows

- The template contains no watermark: `post.watermark` stamps the text across every page after the render, and leaving it out gives the clean quote.
- The text is sized to the page diagonal and runs from bottom left to top right; `color`, `opacity` and `rotation` change that.
- Liquid passes helper arguments after a colon: `dateAdd: 30, "days"` sets the validity, and `money` prints pounds because the template’s currency is `GBP`.
- A PDF that was rendered earlier is marked through `/pdf/watermark` without rendering it again.
- A post-processing step costs half a unit on top of the render.

The rendered example carries the watermark from the request's `post` block ([PDF post-processing](https://docs.formfeed.dev/api/pdf-tools), Starter plan and above), not from the template.

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

- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`money`, `date`, `dateAdd`, `sum`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push quote`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render quote`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=quote) is a PDF and image generation API with a free plan: 100 units a month, no card.
