# SEPA payment QR code

GiroCode that banking apps scan to prefill the transfer.

**Group:** Invoice and payment · **For:** PDF and image templates

## Jinja2

```jinja
<figure class="ff-qr">
  <img src="{{ epcQr(payment, { size: 120 }) }}" alt="{{ t('qr.alt') }}">
  <figcaption>{{ t('qr.caption') }}</figcaption>
</figure>
```

## Liquid

```liquid
<figure class="ff-qr">
  <img src="{{ payment | epcQr: size: 120 }}" alt="{{ 'qr.alt' | t }}">
  <figcaption>{{ 'qr.caption' | t }}</figcaption>
</figure>
```

## Handlebars

```handlebars
<figure class="ff-qr">
  <img src="{{epcQr payment size=120}}" alt="{{t 'qr.alt'}}">
  <figcaption>{{t 'qr.caption'}}</figcaption>
</figure>
```

## Sample data it reads

```json
{
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
.ff-qr { margin: 16px 0; text-align: center; width: 140px; }
.ff-qr figcaption { font-size: 8pt; color: #666; }
```

## Labels

The texts of its `t` calls per language; a template's own dictionary wins.

```json
{
  "en": {
    "qr.alt": "Payment QR code",
    "qr.caption": "Scan to pay"
  },
  "de": {
    "qr.alt": "QR-Code zur Zahlung",
    "qr.caption": "Zum Bezahlen scannen"
  }
}
```

In the Formfeed editor this block is one click in the blocks panel; see [Building blocks](https://docs.formfeed.dev/templates/building-blocks).
