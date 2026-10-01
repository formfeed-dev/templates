# Confidential payslip with a password

Two post-processing steps in one request: a red CONFIDENTIAL mark on every page, then AES-256 encryption with the employee’s password, allowing printing but not copying or editing. The password never reaches the render log. The download opens with the password `formfeed`. One unit for the page plus half a unit per step.

![Confidential payslip with a password, as rendered](preview.webp)

**Engine:** Handlebars · **Output:** PDF · **Helpers:** `money`, `date`, `sum`

[See it on formfeed.dev](https://formfeed.dev/examples/confidential-payslip?utm_source=github-templates&utm_content=payslip) · [example.pdf](example.pdf)

## What this shows

- Two post-processing steps in one request, applied in a fixed order: the watermark first, the password last, because an encrypted PDF cannot be changed any more.
- `password.user` opens the document, and `permissions: ["print"]` allows printing while copying and editing stay locked. The example file opens with `formfeed`; in production it is the employee’s own password.
- The password never reaches the render log.
- Handlebars nests helpers in brackets: `{{money (sum earnings "amount")}}` adds the earnings and formats the result.
- One unit for the page plus half a unit per post-processing step.

The rendered example carries the watermark and the password from the request's `post` block ([PDF post-processing](https://docs.formfeed.dev/api/pdf-tools), Starter plan and above), not from the template.

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

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/confidential-payslip?utm_source=github-templates&utm_content=payslip) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Handlebars tags. The helpers (`money`, `date`, `sum`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push payslip`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render payslip`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=payslip) is a PDF and image generation API with a free plan: 100 units a month, no card.
