# Chart

Bar chart from labels and values in the data, in the brand colour.

**Group:** Report · **For:** PDF and image templates

## Jinja2

```jinja
<figure class="ff-chart-box">
  {{ chart(sales, { type: 'bar', width: 480, height: 240, color: brand.colors.primary }) }}
  <figcaption>{{ sales.caption }}</figcaption>
</figure>
```

## Liquid

```liquid
<figure class="ff-chart-box">
  {{ sales | chart: type: 'bar', width: 480, height: 240, color: brand.colors.primary }}
  <figcaption>{{ sales.caption }}</figcaption>
</figure>
```

## Handlebars

```handlebars
<figure class="ff-chart-box">
  {{chart sales type='bar' width=480 height=240 color=brand.colors.primary}}
  <figcaption>{{sales.caption}}</figcaption>
</figure>
```

## Sample data it reads

```json
{
  "sales": {
    "caption": "Revenue per quarter",
    "labels": [
      "Q1",
      "Q2",
      "Q3",
      "Q4"
    ],
    "values": [
      12000,
      15500,
      14200,
      18900
    ]
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-chart-box { margin: 16px 0; break-inside: avoid; }
.ff-chart-box figcaption { font-size: 9pt; color: #666; margin-top: 4px; }
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
