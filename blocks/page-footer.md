# Footer with page numbers

Company line and “Page x of y” in the page footer.

**Group:** Page and layout · **For:** PDF templates only · **Goes in:** the footer

## Jinja2

```jinja
<div style="width:100%;display:flex;justify-content:space-between;font-size:9px;color:#666">
  <span>{{ company.name }} · {{ company.email }}</span>
  <span>{{ t('footer.page') }} <span class="pageNumber"></span> {{ t('footer.of') }} <span class="totalPages"></span></span>
</div>
```

## Liquid

```liquid
<div style="width:100%;display:flex;justify-content:space-between;font-size:9px;color:#666">
  <span>{{ company.name }} · {{ company.email }}</span>
  <span>{{ 'footer.page' | t }} <span class="pageNumber"></span> {{ 'footer.of' | t }} <span class="totalPages"></span></span>
</div>
```

## Handlebars

```handlebars
<div style="width:100%;display:flex;justify-content:space-between;font-size:9px;color:#666">
  <span>{{ company.name }} · {{ company.email }}</span>
  <span>{{t 'footer.page'}} <span class="pageNumber"></span> {{t 'footer.of'}} <span class="totalPages"></span></span>
</div>
```

## Sample data it reads

```json
{
  "company": {
    "name": "Fennlor Studio GmbH",
    "email": "hello@fennlor.example"
  }
}
```

## Labels

The texts of its `t` calls per language; a template's own dictionary wins.

```json
{
  "en": {
    "footer.page": "Page",
    "footer.of": "of"
  },
  "de": {
    "footer.page": "Seite",
    "footer.of": "von"
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
