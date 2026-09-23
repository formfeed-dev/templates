# Payment terms and bank details

Amount, due date and the account to transfer it to.

**Group:** Invoice and payment · **For:** PDF and image templates

## Jinja2

```jinja
<div class="ff-payment">
  <p>{{ t('payment.transfer') }} <strong>{{ payment.amount | money }}</strong> {{ t('payment.until') }} <strong>{{ invoice.due_date | date('P') }}</strong> {{ t('payment.account') }}</p>
  <table>
    <tr><th>{{ t('payment.holder') }}</th><td>{{ payment.name }}</td></tr>
    <tr><th>IBAN</th><td>{{ payment.iban }}</td></tr>
    <tr><th>BIC</th><td>{{ payment.bic }}</td></tr>
    <tr><th>{{ t('payment.reference') }}</th><td>{{ payment.reference }}</td></tr>
  </table>
</div>
```

## Liquid

```liquid
<div class="ff-payment">
  <p>{{ 'payment.transfer' | t }} <strong>{{ payment.amount | money }}</strong> {{ 'payment.until' | t }} <strong>{{ invoice.due_date | date: 'P' }}</strong> {{ 'payment.account' | t }}</p>
  <table>
    <tr><th>{{ 'payment.holder' | t }}</th><td>{{ payment.name }}</td></tr>
    <tr><th>IBAN</th><td>{{ payment.iban }}</td></tr>
    <tr><th>BIC</th><td>{{ payment.bic }}</td></tr>
    <tr><th>{{ 'payment.reference' | t }}</th><td>{{ payment.reference }}</td></tr>
  </table>
</div>
```

## Handlebars

```handlebars
<div class="ff-payment">
  <p>{{t 'payment.transfer'}} <strong>{{money payment.amount}}</strong> {{t 'payment.until'}} <strong>{{date invoice.due_date 'P'}}</strong> {{t 'payment.account'}}</p>
  <table>
    <tr><th>{{t 'payment.holder'}}</th><td>{{ payment.name }}</td></tr>
    <tr><th>IBAN</th><td>{{ payment.iban }}</td></tr>
    <tr><th>BIC</th><td>{{ payment.bic }}</td></tr>
    <tr><th>{{t 'payment.reference'}}</th><td>{{ payment.reference }}</td></tr>
  </table>
</div>
```

## Sample data it reads

```json
{
  "invoice": {
    "due_date": "2026-10-13"
  },
  "payment": {
    "name": "Fennlor Studio GmbH",
    "iban": "DE36000000000000000000",
    "bic": "XXXXDEXXXXX",
    "amount": 3760.4,
    "reference": "2026-0042"
  }
}
```

## CSS

The editor adds these rules to the stylesheet when their selectors are missing.

```css
.ff-payment { margin-top: 16px; font-size: 9.5pt; break-inside: avoid; }
.ff-payment p { margin: 0 0 6px; }
.ff-payment table { border-collapse: collapse; }
.ff-payment th { text-align: left; font-weight: normal; color: #555; padding: 1px 16px 1px 0; }
```

## Labels

The texts of its `t` calls per language; a template's own dictionary wins.

```json
{
  "en": {
    "payment.transfer": "Please transfer",
    "payment.until": "by",
    "payment.account": "to the following account:",
    "payment.holder": "Account holder",
    "payment.reference": "Reference"
  },
  "de": {
    "payment.transfer": "Bitte überweisen Sie",
    "payment.until": "bis zum",
    "payment.account": "auf folgendes Konto:",
    "payment.holder": "Kontoinhaber",
    "payment.reference": "Verwendungszweck"
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
