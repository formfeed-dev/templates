# Invoice heading

Invoice number as the title and the service period below it.

**Group:** Invoice and payment · **For:** PDF and image templates

## Jinja2

```jinja
<div class="ff-heading">
  <h1>{{ t('heading.title', { number: invoice.number }) }}</h1>
  <p>{{ t('heading.period') }} {{ invoice.period_start | date('P') }} – {{ invoice.period_end | date('P') }}</p>
</div>
```

## Liquid

```liquid
<div class="ff-heading">
  <h1>{{ 'heading.title' | t: number: invoice.number }}</h1>
  <p>{{ 'heading.period' | t }} {{ invoice.period_start | date: 'P' }} – {{ invoice.period_end | date: 'P' }}</p>
</div>
```

## Handlebars

```handlebars
<div class="ff-heading">
  <h1>{{t 'heading.title' number=invoice.number}}</h1>
  <p>{{t 'heading.period'}} {{date invoice.period_start 'P'}} – {{date invoice.period_end 'P'}}</p>
</div>
```

## Sample data it reads

```json
{
  "invoice": {
    "number": "2026-0042",
    "period_start": "2026-09-01",
    "period_end": "2026-09-30"
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-heading { margin: 24px 0 16px; }
.ff-heading h1 { font-family: var(--brand-font-heading, inherit); font-size: 18pt; color: var(--brand-color-primary, inherit); margin: 0 0 4px; }
.ff-heading p { margin: 0; color: #555; }
```

## Labels

The texts of its `t` calls per language; a template's own dictionary wins.

```json
{
  "en": {
    "heading.title": "Invoice {number}",
    "heading.period": "Service period:"
  },
  "de": {
    "heading.title": "Rechnung {number}",
    "heading.period": "Leistungszeitraum:"
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
