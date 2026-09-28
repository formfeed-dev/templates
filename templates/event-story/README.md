# Webinar story, 1080×1920

A 9:16 story in Liquid and Tailwind that gives the start time in three cities from one timestamp: `date` takes a time zone as its second argument, so London, Berlin and New York each read their own clock, winter time included.

![Webinar story, 1080×1920, as rendered](preview.webp)

**Engine:** Liquid · **Output:** image · **Helpers:** `date`, `qrcode`, `replace`, `join`

[See it on formfeed.dev](https://formfeed.dev/examples/event-story?utm_source=github-templates&utm_content=event-story) · [example.png](example.png)

## What this shows

- The canvas is `1080` × `1920` pixels, the 9:16 format of Instagram and LinkedIn stories.
- One timestamp, three clocks: `date: 'HH:mm', zone.tz` reads `2026-11-05T16:00:00Z` as `16:00` in London, `17:00` in Berlin and `11:00` in New York, each by its own daylight-saving rules; the time zones come from the data.
- `tailwind: true` compiles the classes of the markup at render time, arbitrary values such as `text-[104px]` included.
- The QR code links to the registration page, and `replace: 'https://', ''` prints the same address without its scheme.
- `access: "public"` returns a CDN link that a scheduling tool can fetch.

## Files

| File | What it is |
| --- | --- |
| [`template.html`](template.html) | the template |
| [`head.html`](head.html) | extra `<head>` content, such as a font link |
| [`settings.json`](settings.json) | paper, margins and output settings |
| [`data/default.json`](data/default.json) | the sample data it was designed with |
| [`template.json`](template.json) | name, kind and engine, which `formfeed templates push` needs |

## Use it

- **Copy it.** It is plain HTML and CSS with Liquid tags. The helpers (`date`, `qrcode`, `replace`, `join`) are Formfeed's; the [helper reference](https://docs.formfeed.dev/templates/helpers) says what each does.
- **Push it into a Formfeed workspace** from the root of this repository, where `formfeed.json` is: `npx formfeed login`, then `npx formfeed templates push event-story`. Open it in the editor to change it with a live preview.
- **Render it** from your code with the [API](https://docs.formfeed.dev/api/overview) and your own data, or try it first with `npx formfeed render event-story`: renders with a test key are free.

MIT licensed, like the rest of this repository. [Formfeed](https://formfeed.dev/?utm_source=github-templates&utm_content=event-story) is a PDF and image generation API with a free plan: 100 units a month, no card.
