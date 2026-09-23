# Reference block

Customer number, invoice number and date as a right-aligned table; put it in a two-column layout to sit beside the address.

**Group:** Letter · **For:** PDF and image templates

## Jinja2

```jinja
<table class="ff-reference">
  <tr><th>{{ t('reference.customer') }}</th><td>{{ customer.number }}</td></tr>
  <tr><th>{{ t('reference.invoice') }}</th><td>{{ invoice.number }}</td></tr>
  <tr><th>{{ t('reference.date') }}</th><td>{{ invoice.date | date('P') }}</td></tr>
</table>
```

## Liquid

```liquid
<table class="ff-reference">
  <tr><th>{{ 'reference.customer' | t }}</th><td>{{ customer.number }}</td></tr>
  <tr><th>{{ 'reference.invoice' | t }}</th><td>{{ invoice.number }}</td></tr>
  <tr><th>{{ 'reference.date' | t }}</th><td>{{ invoice.date | date: 'P' }}</td></tr>
</table>
```

## Handlebars

```handlebars
<table class="ff-reference">
  <tr><th>{{t 'reference.customer'}}</th><td>{{ customer.number }}</td></tr>
  <tr><th>{{t 'reference.invoice'}}</th><td>{{ invoice.number }}</td></tr>
  <tr><th>{{t 'reference.date'}}</th><td>{{date invoice.date 'P'}}</td></tr>
</table>
```

## Sample data it reads

```json
{
  "customer": {
    "number": "K-1042"
  },
  "invoice": {
    "number": "2026-0042",
    "date": "2026-09-13"
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-reference { margin-left: auto; border-collapse: collapse; font-size: 9pt; }
.ff-reference th { text-align: left; font-weight: normal; color: #555; padding: 1px 12px 1px 0; }
.ff-reference td { text-align: right; padding: 1px 0; }
```

## Labels

The texts of its `t` calls per language; a template's own dictionary wins.

```json
{
  "en": {
    "reference.customer": "Customer no.",
    "reference.invoice": "Invoice no.",
    "reference.date": "Date"
  },
  "de": {
    "reference.customer": "Kundennummer",
    "reference.invoice": "Rechnungsnummer",
    "reference.date": "Datum"
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
