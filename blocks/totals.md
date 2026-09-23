# Totals block

Net, VAT and gross totals right-aligned under a table.

**Group:** Invoice and payment · **For:** PDF and image templates

## Jinja2

```jinja
<table class="ff-totals">
  <tr><td>{{ t('totals.net') }}</td><td class="num">{{ invoice.net | money }}</td></tr>
  <tr><td>{{ t('totals.vat', { rate: invoice.vat_rate }) }}</td><td class="num">{{ invoice.vat | money }}</td></tr>
  <tr class="grand"><td>{{ t('totals.total') }}</td><td class="num">{{ invoice.total | money }}</td></tr>
</table>
```

## Liquid

```liquid
<table class="ff-totals">
  <tr><td>{{ 'totals.net' | t }}</td><td class="num">{{ invoice.net | money }}</td></tr>
  <tr><td>{{ 'totals.vat' | t: rate: invoice.vat_rate }}</td><td class="num">{{ invoice.vat | money }}</td></tr>
  <tr class="grand"><td>{{ 'totals.total' | t }}</td><td class="num">{{ invoice.total | money }}</td></tr>
</table>
```

## Handlebars

```handlebars
<table class="ff-totals">
  <tr><td>{{t 'totals.net'}}</td><td class="num">{{money invoice.net}}</td></tr>
  <tr><td>{{t 'totals.vat' rate=invoice.vat_rate}}</td><td class="num">{{money invoice.vat}}</td></tr>
  <tr class="grand"><td>{{t 'totals.total'}}</td><td class="num">{{money invoice.total}}</td></tr>
</table>
```

## Sample data it reads

```json
{
  "invoice": {
    "net": 3160,
    "vat_rate": 19,
    "vat": 600.4,
    "total": 3760.4
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-totals { margin-left: auto; margin-top: 12px; border-collapse: collapse; font-size: 10pt; }
.ff-totals td { padding: 4px 8px; }
.ff-totals .num { text-align: right; min-width: 90px; }
.ff-totals .grand td { border-top: 2px solid var(--brand-color-primary, #222); font-weight: 600; }
```

## Labels

The texts of its `t` calls per language; a template's own dictionary wins.

```json
{
  "en": {
    "totals.net": "Net",
    "totals.vat": "VAT {rate} %",
    "totals.total": "Total"
  },
  "de": {
    "totals.net": "Netto",
    "totals.vat": "USt. {rate} %",
    "totals.total": "Gesamtbetrag"
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
