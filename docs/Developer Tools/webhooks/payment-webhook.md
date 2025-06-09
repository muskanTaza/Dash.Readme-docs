---
title: Payment
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
```json Sample Webhook Response for Create Payment Endpoint
{
  "txn_no": "2207-589815",
  "state": "Payment_Received",
  "sub_state": "Generic",
  "invoice_currency": "USD",
  "invoice_amount": 1000,
  "partner_reference_id": "uid1",
  "payment": {
    "collection_method": "Card",
    "remarks": "payment received",
    "payable_amount": 1000,
    "paid_amount": 1000,
    "collection_currency": "USD",
    "fx_rate": 1,
    "transaction_id": "7979aebf-6780-4b7b-ba5c-3961ea0ae430"
  },
  "attributes": {
    "doc_url": "https://media.istockphoto.com/photos/historic-buildings-of-wall-street-in-the-financial-district-of-lower-picture-id1337246025?s=612x612"
  }
}
```

## Response parameters:

| Parameter         | Description                                                   |
| ----------------- | ------------------------------------------------------------- |
| txn\_no           | `string` The txn\_no for the request made                     |
| invoice\_currency | `string` The invoice currency of payment made for this escrow |
| invoice\_amount   | `float` Invoice amount i.e. amount paid for this escrow       |
| state             | `string` The state / status of escrow                         |
| sub\_state        | `string` The sub state / status of escrow                     |
