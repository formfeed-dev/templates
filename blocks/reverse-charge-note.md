# Reverse charge note

EU business customers: the recipient owes the VAT, with their VAT ID.

**Group:** Invoice and payment · **For:** PDF and image templates

## Jinja2

```jinja
<p class="ff-note">{{ t('vat.reverse_charge') }} {{ t('vat.customer_id') }} {{ customer.vat_id }}</p>
```

## Liquid

```liquid
<p class="ff-note">{{ 'vat.reverse_charge' | t }} {{ 'vat.customer_id' | t }} {{ customer.vat_id }}</p>
```

## Handlebars

```handlebars
<p class="ff-note">{{t 'vat.reverse_charge'}} {{t 'vat.customer_id'}} {{ customer.vat_id }}</p>
```

## Sample data it reads

```json
{
  "customer": {
    "vat_id": "ATU00000000"
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-note { margin-top: 12px; font-size: 9pt; color: #444; }
```

## Labels

The texts of its `t` calls per language; a template's own dictionary wins.

```json
{
  "en": {
    "vat.reverse_charge": "Reverse charge: the recipient of the service is liable for VAT.",
    "vat.customer_id": "Customer VAT ID:"
  },
  "de": {
    "vat.reverse_charge": "Steuerschuldnerschaft des Leistungsempfängers.",
    "vat.customer_id": "USt-IdNr. des Leistungsempfängers:"
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
