# Signature line

Place, date and a signature line.

**Group:** Letter · **For:** PDF and image templates

## Jinja2

```jinja
<div class="ff-signature">
  <div class="line"></div>
  <div>{{ signature.place }}, {{ signature.date | date('PP') }} · {{ signature.name }}</div>
</div>
```

## Liquid

```liquid
<div class="ff-signature">
  <div class="line"></div>
  <div>{{ signature.place }}, {{ signature.date | date: 'PP' }} · {{ signature.name }}</div>
</div>
```

## Handlebars

```handlebars
<div class="ff-signature">
  <div class="line"></div>
  <div>{{ signature.place }}, {{date signature.date 'PP'}} · {{ signature.name }}</div>
</div>
```

## Sample data it reads

```json
{
  "signature": {
    "place": "Berlin",
    "date": "2026-09-07",
    "name": "Erika Mustermann"
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-signature { margin-top: 48px; width: 260px; font-size: 9pt; color: #444; }
.ff-signature .line { border-top: 1px solid #222; margin-bottom: 6px; }
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
