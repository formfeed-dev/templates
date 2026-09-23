# Window envelope address

Return address and recipient in the 85 × 45 mm field of a DIN 5008 window envelope.

**Group:** Letter · **For:** PDF templates only

## Jinja2

```jinja
<div class="ff-window">
  <div class="sender">{{ company.name }} · {{ company.street }} · {{ company.zip }} {{ company.city }}</div>
  <address>
    <strong>{{ customer.name }}</strong><br>
    {{ customer.street }}<br>
    {{ customer.zip }} {{ customer.city }}
  </address>
</div>
```

## Liquid

```liquid
<div class="ff-window">
  <div class="sender">{{ company.name }} · {{ company.street }} · {{ company.zip }} {{ company.city }}</div>
  <address>
    <strong>{{ customer.name }}</strong><br>
    {{ customer.street }}<br>
    {{ customer.zip }} {{ customer.city }}
  </address>
</div>
```

## Handlebars

```handlebars
<div class="ff-window">
  <div class="sender">{{ company.name }} · {{ company.street }} · {{ company.zip }} {{ company.city }}</div>
  <address>
    <strong>{{ customer.name }}</strong><br>
    {{ customer.street }}<br>
    {{ customer.zip }} {{ customer.city }}
  </address>
</div>
```

## Sample data it reads

```json
{
  "company": {
    "name": "Fennlor Studio GmbH",
    "street": "Musterstraße 1",
    "zip": "12345",
    "city": "Musterstadt"
  },
  "customer": {
    "name": "Olvarest GmbH",
    "street": "Beispielweg 2",
    "zip": "54321",
    "city": "Beispielstadt"
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-window { width: 85mm; height: 45mm; box-sizing: border-box; padding: 0 5mm; overflow: hidden; }
.ff-window .sender { height: 5mm; line-height: 5mm; margin-bottom: 3mm; font-size: 7pt; color: #555; border-bottom: 0.5pt solid #999; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.ff-window address { font-style: normal; font-size: 10pt; line-height: 1.35; }
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
