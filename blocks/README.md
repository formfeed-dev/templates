# Building blocks

The blocks of the Formfeed editor, each in Jinja2, Liquid and Handlebars.

### Letter

- [Letterhead](letterhead.md): Logo from the brand kit, or the organisation name when no logo is set.
- [Window envelope address](window-address.md): Return address and recipient in the 85 × 45 mm field of a DIN 5008 window envelope.
- [Reference block](reference-block.md): Customer number, invoice number and date as a right-aligned table; put it in a two-column layout to sit beside the address.
- [Address block](address-block.md): Recipient name and postal address lines.
- [Signature line](signature.md): Place, date and a signature line.

### Invoice and payment

- [Invoice heading](invoice-heading.md): Invoice number as the title and the service period below it.
- [Invoice table](invoice-table.md): Line items with description, quantity, unit price and line total.
- [Totals block](totals.md): Net, VAT and gross totals right-aligned under a table.
- [Payment terms and bank details](payment-terms.md): Amount, due date and the account to transfer it to.
- [Small business VAT note](small-business-note.md): States that no VAT is charged under § 19 UStG (Kleinunternehmerregelung).
- [Reverse charge note](reverse-charge-note.md): EU business customers: the recipient owes the VAT, with their VAT ID.
- [SEPA payment QR code](epc-qr.md): GiroCode that banking apps scan to prefill the transfer.

### Page and layout

- [Footer with page numbers](page-footer.md): Company line and “Page x of y” in the page footer.
- [Legal footer](legal-footer.md): The legal footer from the brand kit, centred in the page footer.
- [Two-column layout](two-columns.md): Two equal columns that stay side by side in print.
- [Keep together](keep-together.md): Content that is never split across two pages.
- [Page break](page-break.md): Starts a new page in the PDF.

### Report

- [Cover page](cover-page.md): Title, subtitle and date on a page of its own.
- [Chart](chart.md): Bar chart from labels and values in the data, in the brand colour.
- [Key figures](kpi-cards.md): A row of cards with label, value and change for each figure.
