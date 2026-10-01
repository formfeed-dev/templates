# Open Graph image with Tailwind

A 1200×630 social image in Liquid with Tailwind classes, compiled at render time. Liquid passes options as keyword arguments (`| image: width: 72`), and identical requests are served from the dedup cache at zero units.

![Open Graph image with Tailwind, as rendered](preview.webp)

**Engine:** Liquid · **Output:** image · **Helpers:** `image`, `date`, `truncate`, `default`

[See it on formfeed.dev](https://formfeed.dev/examples/og-image?utm_source=github-templates&utm_content=og-image) · [example.png](example.png)

## What this shows

- The settings fix the canvas: `image` with 1200×630 pixels, PNG and a device scale factor of 1, which is what social networks expect.
- `tailwind: true` compiles the classes the markup uses at render time; there is no stylesheet to maintain.
- `truncate: 70` keeps a long headline inside the card, `default: "Blog"` fills a missing category, and `image` crops the avatar with `fit: "cover"`.
- `access: "public"` returns a CDN URL you can put straight into `<meta property="og:image">`.
- An identical request is answered from the deduplication cache and costs no units, so rendering on every deploy is fine.

## Files

| File | What it is |
| --- | --- |
| [`template.html`](template.html) | the template |
| [`settings.json`](settings.json) | paper, margins and output settings |
| [`data/default.json`](data/default.json) | the sample data it was designed with |
| [`template.json`](template.json) | name, kind and engine, which `formfeed templates push` needs |

## Use it

- **Open it in a workspace.** [Use this template](https://app.formfeed.dev/en/examples/og-image?utm_source=github-templates&utm_content=og-image) puts a copy into your Formfeed workspace, published and ready for the API. A free account is enough, and it needs no CLI.
- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`image`, `date`, `truncate`, `default`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push og-image`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render og-image`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=og-image) is a PDF and image generation API with a free plan: 100 units a month, no card.
