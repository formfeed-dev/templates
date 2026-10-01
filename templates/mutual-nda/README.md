# Mutual NDA with numbered clauses

A two-page agreement with a running header, a footer for initials and page numbers, and clauses numbered by CSS counters, so the optional non-solicitation clause renumbers everything after it. The term is written out with `numToWords`: “two (2) years”.

![Mutual NDA with numbered clauses, as rendered](preview.webp)

**Engine:** Handlebars · **Output:** PDF · **Helpers:** `date`, `dateAdd`, `numToWords`, `join`

[See it on formfeed.dev](https://formfeed.dev/examples/nda?utm_source=github-templates&utm_content=mutual-nda) · [example.pdf](example.pdf)

## What this shows

- Clause numbers are CSS counters (`counter-increment: clause`), not text in the template: leave out the optional clause and everything after it renumbers.
- `{{#if agreement.non_solicitation_months}}` includes the non-solicitation clause only when the data gives it a period.
- `numToWords agreement.term_years "en"` writes the term the way contracts do, “two (2) years”, and `dateAdd` gives the end date, 1 October 2028.
- The header names both parties on every page and the footer has lines for initials beside “Page 1 of 2”; both are Chromium templates in the margins, where the text never runs.
- The signature block has `break-inside: avoid`, so a signature line never lands on a page without its name. The example shows the mechanics; have a lawyer check the wording before you use it.

## Files

| File | What it is |
| --- | --- |
| [`template.html`](template.html) | the template |
| [`style.css`](style.css) | its stylesheet |
| [`head.html`](head.html) | extra `<head>` content, such as a font link |
| [`header.html`](header.html) | the running header of every PDF page |
| [`footer.html`](footer.html) | the running footer of every PDF page |
| [`settings.json`](settings.json) | paper, margins and output settings |
| [`data/default.json`](data/default.json) | the sample data it was designed with |
| [`template.json`](template.json) | name, kind and engine, which `formfeed templates push` needs |

## Use it

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/nda?utm_source=github-templates&utm_content=mutual-nda) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`date`, `dateAdd`, `numToWords`, `join`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push mutual-nda`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render mutual-nda`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=mutual-nda) is a PDF and image generation API with a free plan: 100 units a month, no card.
