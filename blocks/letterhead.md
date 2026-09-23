# Letterhead

Logo from the brand kit, or the organisation name when no logo is set.

**Group:** Letter · **For:** PDF and image templates

## Jinja2

```jinja
<header class="ff-letterhead">
  {% if brand.logo.primary %}<img class="logo" src="{{ brand.logo.primary }}" alt="{{ brand.name }}">{% else %}<strong class="name">{{ brand.name }}</strong>{% endif %}
</header>
```

## Liquid

```liquid
<header class="ff-letterhead">
  {% if brand.logo.primary %}<img class="logo" src="{{ brand.logo.primary }}" alt="{{ brand.name }}">{% else %}<strong class="name">{{ brand.name }}</strong>{% endif %}
</header>
```

## Handlebars

```handlebars
<header class="ff-letterhead">
  {{#if brand.logo.primary}}<img class="logo" src="{{ brand.logo.primary }}" alt="{{ brand.name }}">{{else}}<strong class="name">{{ brand.name }}</strong>{{/if}}
</header>
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-letterhead { display: flex; justify-content: flex-end; align-items: center; min-height: 48px; margin-bottom: 24px; padding-bottom: 8px; border-bottom: 2px solid var(--brand-color-primary, #222); }
.ff-letterhead .logo { max-height: 56px; max-width: 200px; }
.ff-letterhead .name { font-family: var(--brand-font-heading, inherit); font-size: 18pt; color: var(--brand-color-primary, inherit); }
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
