# Contributing

Thank you for helping. Two things to know first.

**This repository is generated.** The templates and blocks are exported from the repository where
Formfeed's examples and editor blocks are made, and every export replaces what is here. A pull
request is read here; when it is taken, it is carried over by hand and comes back with the next
export, so it can take a few days to appear.

**What a template needs:**

- A folder under `templates/` in the layout `formfeed templates pull` writes: `template.html`,
  `settings.json`, `template.json` and `data/default.json`, plus `style.css`, `head.html`,
  `footer.html` or `i18n.json` where it uses them.
- Sample data that cannot be mistaken for a real person or company: Max or Erika Mustermann and
  John or Jane Doe as people, Fennlor Studio and Olvarest as companies, Musterstraße 1 · 12345
  Musterstadt as an address, IBANs with an all-zero account number and valid check digits
  (`DE36 0000 0000 0000 0000 00`), all-zero tax IDs, and domains under `.example` or `.test`.
- `npx formfeed validate` passes. The Validate workflow runs it on every pull request.
- Your agreement that it is published under the MIT license.

A template that renders wrongly: open an issue with its name and what you expected to see.
