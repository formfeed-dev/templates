# Invoice table

Line items with description, quantity, unit price and line total.

**Group:** Invoice and payment · **For:** PDF and image templates

## Jinja2

```jinja
<table class="ff-lines">
  <thead><tr><th>{{ t('lines.description') }}</th><th class="num">{{ t('lines.qty') }}</th><th class="num">{{ t('lines.price') }}</th><th class="num">{{ t('lines.total') }}</th></tr></thead>
  <tbody>
{% for line in invoice.lines %}
    <tr><td>{{ line.description }}</td><td class="num">{{ line.qty | number(0) }}</td><td class="num">{{ line.price | money }}</td><td class="num">{{ line.total | money }}</td></tr>
{% endfor %}
  </tbody>
</table>
```

## Liquid

```liquid
<table class="ff-lines">
  <thead><tr><th>{{ 'lines.description' | t }}</th><th class="num">{{ 'lines.qty' | t }}</th><th class="num">{{ 'lines.price' | t }}</th><th class="num">{{ 'lines.total' | t }}</th></tr></thead>
  <tbody>
{% for line in invoice.lines %}
    <tr><td>{{ line.description }}</td><td class="num">{{ line.qty | number: 0 }}</td><td class="num">{{ line.price | money }}</td><td class="num">{{ line.total | money }}</td></tr>
{% endfor %}
  </tbody>
</table>
```

## Handlebars

```handlebars
<table class="ff-lines">
  <thead><tr><th>{{t 'lines.description'}}</th><th class="num">{{t 'lines.qty'}}</th><th class="num">{{t 'lines.price'}}</th><th class="num">{{t 'lines.total'}}</th></tr></thead>
  <tbody>
{{#each invoice.lines}}
    <tr><td>{{ description }}</td><td class="num">{{number qty 0}}</td><td class="num">{{money price}}</td><td class="num">{{money total}}</td></tr>
{{/each}}
  </tbody>
</table>
```

## Sample data it reads

```json
{
  "invoice": {
    "lines": [
      {
        "description": "Consulting",
        "qty": 8,
        "price": 120,
        "total": 960
      },
      {
        "description": "Implementation",
        "qty": 20,
        "price": 110,
        "total": 2200
      }
    ]
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-lines { width: 100%; border-collapse: collapse; font-size: 10pt; }
.ff-lines th, .ff-lines td { padding: 6px 8px; border-bottom: 1px solid #ddd; text-align: left; }
.ff-lines .num { text-align: right; white-space: nowrap; }
.ff-lines thead th { border-bottom: 2px solid var(--brand-color-primary, #222); }
```

## Labels

The texts of its `t` calls per language; a template's own dictionary wins.

```json
{
  "en": {
    "lines.description": "Description",
    "lines.qty": "Qty",
    "lines.price": "Unit price",
    "lines.total": "Total"
  },
  "de": {
    "lines.description": "Beschreibung",
    "lines.qty": "Menge",
    "lines.price": "Einzelpreis",
    "lines.total": "Gesamt"
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
