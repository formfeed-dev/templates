# German reference letter (Arbeitszeugnis) from Markdown

A text document rather than a table: the paragraphs arrive as Markdown, `markdown` turns them into HTML with lists and emphasis, and the template sets a serif face, justified text with hyphenation and a signature block for two signers that stays together on one page.

![German reference letter (Arbeitszeugnis) from Markdown, as rendered](preview.webp)

**Engine:** Liquid · **Output:** PDF · **Helpers:** `markdown`, `date`, `upper`

[See it on formfeed.dev](https://formfeed.dev/examples/arbeitszeugnis?utm_source=github-templates&utm_content=arbeitszeugnis) · [example.pdf](example.pdf)

## What this shows

- Each entry of `reference.sections` is Markdown; `markdown` renders paragraphs, the task list and the emphasis, so the text can come straight from an HR tool.
- `date: "d. MMMM yyyy"` with the locale `de-DE` writes `12. April 1990` and `30. September 2026`.
- `hyphens: auto` with `text-align: justify` gives even lines; Chromium hyphenates German because the document language follows the locale.
- The serif face loads from Google Fonts in `head.html`; nothing has to be installed anywhere.
- The place, date and both signature lines sit in one block with `break-inside: avoid`.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/arbeitszeugnis?utm_source=github-templates&utm_content=arbeitszeugnis) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`markdown`, `date`, `upper`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push arbeitszeugnis`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render arbeitszeugnis`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=arbeitszeugnis) is a PDF and image generation API with a free plan: 100 units a month, no card.
