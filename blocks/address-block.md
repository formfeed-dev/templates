# Address block

Recipient name and postal address lines.

**Group:** Letter · **For:** PDF and image templates

## Jinja2

```jinja
<address class="ff-address">
  <strong>{{ customer.name }}</strong><br>
  {{ customer.street }}<br>
  {{ customer.zip }} {{ customer.city }}<br>
  {{ customer.country }}
</address>
```

## Liquid

```liquid
<address class="ff-address">
  <strong>{{ customer.name }}</strong><br>
  {{ customer.street }}<br>
  {{ customer.zip }} {{ customer.city }}<br>
  {{ customer.country }}
</address>
```

## Handlebars

```handlebars
<address class="ff-address">
  <strong>{{ customer.name }}</strong><br>
  {{ customer.street }}<br>
  {{ customer.zip }} {{ customer.city }}<br>
  {{ customer.country }}
</address>
```

## Sample data it reads

```json
{
  "customer": {
    "name": "Olvarest GmbH",
    "street": "Beispielweg 2",
    "zip": "54321",
    "city": "Beispielstadt",
    "country": "Deutschland"
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-address { font-style: normal; line-height: 1.4; }
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
