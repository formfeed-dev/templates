# Review card, 1080×1080

A square card for Instagram and LinkedIn from one customer review: `range` and `lt` draw the rating as five stars, `truncate` keeps a long quote inside the square, and the date of the review is written out as month and year.

![Review card, 1080×1080, as rendered](preview.webp)

**Engine:** Handlebars · **Output:** image · **Helpers:** `range`, `lt`, `truncate`, `date`

[See it on formfeed.dev](https://formfeed.dev/examples/review-card?utm_source=github-templates&utm_content=review-card) · [example.png](example.png)

## What this shows

- `settings.image` fixes the square: `1080` × `1080` pixels at a device scale factor of `1`, which Instagram and LinkedIn show without cropping.
- `{{#each (range 0 5)}}` draws five stars and `(lt this ../review.rating)` colours as many as the rating: four amber stars and one grey.
- `{{truncate review.quote 240}}` cuts a quote that would not fit after 240 characters and ends it with an ellipsis.
- The large quotation mark is CSS, `blockquote::before`, so the data carries the plain text of the review.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/review-card?utm_source=github-templates&utm_content=review-card) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`range`, `lt`, `truncate`, `date`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push review-card`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render review-card`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=review-card) is a PDF and image generation API with a free plan: 100 units a month, no card.
