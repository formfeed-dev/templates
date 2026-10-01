# Résumé with a sidebar and skill ratings

A one-page CV in two columns, full bleed. The template sorts the positions by start date, so the data can arrive in any order, writes “present” for a job without an end date, and draws each skill rating as five dots with `range` and `lt`.

![Résumé with a sidebar and skill ratings, as rendered](preview.webp)

**Engine:** Handlebars · **Output:** PDF · **Helpers:** `sortBy`, `date`, `range`, `lt`, `join`

[See it on formfeed.dev](https://formfeed.dev/examples/resume?utm_source=github-templates&utm_content=resume) · [example.pdf](example.pdf)

## What this shows

- The data lists the positions in any order; `sortBy experience "start" "desc"` puts the current one first, and the same helper sorts the degrees.
- A position without an end date prints “present”: `{{#if end}}` chooses between the formatted date and the word.
- `{{#each (range 0 5)}}` draws five dots per skill, and `(lt this ../level)` fills as many as the level; `../` reaches the skill from inside the inner loop.
- `join stack " · "` turns each position’s list of technologies into one line.
- Zero margins let the sidebar run to the paper’s edge, and `min-height: 297mm` stretches it over the whole page.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/resume?utm_source=github-templates&utm_content=resume) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`sortBy`, `date`, `range`, `lt`, `join`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push resume`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render resume`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=resume) is a PDF and image generation API with a free plan: 100 units a month, no card.
