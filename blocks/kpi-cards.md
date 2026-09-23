# Key figures

A row of cards with label, value and change for each figure.

**Group:** Report · **For:** PDF and image templates

## Jinja2

```jinja
<div class="ff-kpis">
{% for kpi in report.kpis %}
  <div class="kpi"><span class="label">{{ kpi.label }}</span><strong>{{ kpi.value }}</strong><span class="change">{{ kpi.change }}</span></div>
{% endfor %}
</div>
```

## Liquid

```liquid
<div class="ff-kpis">
{% for kpi in report.kpis %}
  <div class="kpi"><span class="label">{{ kpi.label }}</span><strong>{{ kpi.value }}</strong><span class="change">{{ kpi.change }}</span></div>
{% endfor %}
</div>
```

## Handlebars

```handlebars
<div class="ff-kpis">
{{#each report.kpis}}
  <div class="kpi"><span class="label">{{ label }}</span><strong>{{ value }}</strong><span class="change">{{ change }}</span></div>
{{/each}}
</div>
```

## Sample data it reads

```json
{
  "report": {
    "kpis": [
      {
        "label": "Revenue",
        "value": "€ 61,600",
        "change": "+12 % on Q2"
      },
      {
        "label": "New customers",
        "value": "48",
        "change": "+9 on Q2"
      },
      {
        "label": "Churn",
        "value": "1.8 %",
        "change": "−0.4 pt on Q2"
      }
    ]
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-kpis { display: flex; gap: 12px; margin: 16px 0; break-inside: avoid; }
.ff-kpis .kpi { flex: 1 1 0; padding: 10px 12px; border: 1px solid #e5e5e5; border-top: 3px solid var(--brand-color-primary, #222); border-radius: 4px; }
.ff-kpis .label { display: block; font-size: 8pt; color: #666; text-transform: uppercase; letter-spacing: 0.04em; }
.ff-kpis strong { display: block; margin: 2px 0; font-size: 18pt; }
.ff-kpis .change { font-size: 8pt; color: #555; }
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
