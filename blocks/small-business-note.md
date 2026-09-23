# Small business VAT note

States that no VAT is charged under § 19 UStG (Kleinunternehmerregelung).

**Group:** Invoice and payment · **For:** PDF and image templates

## Jinja2

```jinja
<p class="ff-note">{{ t('vat.small_business') }}</p>
```

## Liquid

```liquid
<p class="ff-note">{{ 'vat.small_business' | t }}</p>
```

## Handlebars

```handlebars
<p class="ff-note">{{t 'vat.small_business'}}</p>
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
    "vat.small_business": "No VAT is charged under the small business scheme of § 19 UStG."
  },
  "de": {
    "vat.small_business": "Gemäß § 19 UStG wird keine Umsatzsteuer berechnet."
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
