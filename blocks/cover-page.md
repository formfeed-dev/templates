# Cover page

Title, subtitle and date on a page of its own.

**Group:** Report · **For:** PDF templates only

## Jinja2

```jinja
<section class="ff-cover">
  <h1>{{ report.title }}</h1>
  <p class="subtitle">{{ report.subtitle }}</p>
  <p class="date">{{ report.date | date('PPP') }}</p>
</section>
<div class="page-break"></div>
```

## Liquid

```liquid
<section class="ff-cover">
  <h1>{{ report.title }}</h1>
  <p class="subtitle">{{ report.subtitle }}</p>
  <p class="date">{{ report.date | date: 'PPP' }}</p>
</section>
<div class="page-break"></div>
```

## Handlebars

```handlebars
<section class="ff-cover">
  <h1>{{ report.title }}</h1>
  <p class="subtitle">{{ report.subtitle }}</p>
  <p class="date">{{date report.date 'PPP'}}</p>
</section>
<div class="page-break"></div>
```

## Sample data it reads

```json
{
  "report": {
    "title": "Quarterly report",
    "subtitle": "Q3 2026",
    "date": "2026-09-30"
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-cover { min-height: 60vh; display: flex; flex-direction: column; justify-content: center; }
.ff-cover h1 { font-family: var(--brand-font-heading, inherit); font-size: 32pt; color: var(--brand-color-primary, inherit); margin: 0 0 8px; }
.ff-cover .subtitle { font-size: 16pt; color: #444; margin: 0; }
.ff-cover .date { margin-top: 24px; color: #666; }
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
