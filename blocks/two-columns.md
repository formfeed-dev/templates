# Two-column layout

Two equal columns that stay side by side in print.

**Group:** Page and layout · **For:** PDF and image templates

## Jinja2

```jinja
<div class="ff-columns">
  <div></div>
  <div></div>
</div>
```

## Liquid

```liquid
<div class="ff-columns">
  <div></div>
  <div></div>
</div>
```

## Handlebars

```handlebars
<div class="ff-columns">
  <div></div>
  <div></div>
</div>
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-columns { display: flex; gap: 24px; }
.ff-columns > div { flex: 1 1 0; min-width: 0; }
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
