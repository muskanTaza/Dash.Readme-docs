---
title: Release
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Once a buyer has made their payment into a Tazapay checkout or escrow, the funds are ready to be released. Tazapay will hold onto the funds and will wait for the [Release](ref:release-intro) API to be called before the funds are disbursed to the seller or counterparty in the transaction.

Tazapay will release the payment to the seller's bank account within 48 business hours of the API call, provided the payment prerequisites are met
 
If required, the API will support the upload of all documents required for the release of payment, such as:
- Proof of service rendered
- Proof of shipment (such as Bill of Lading, Airway Bill etc)
[block:callout]
{
  "type": "info",
  "body": "Depending on your use case, an upload of the release document may not be required."
}
[/block]