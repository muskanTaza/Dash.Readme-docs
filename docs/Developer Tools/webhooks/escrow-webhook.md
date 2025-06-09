---
title: Escrow
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
```json Sample response for escrow webhook
{
  "txn_no": "2207-117037",
  "state": "Awaiting_Payment",
  "sub_state": "Generic",
  "invoice_currency": "USD",
  "invoice_amount": 1000,
  "milestone": {
    "code": "Scheme 2",
    "short_description": "30% advance; 70% on delivery",
    "long_description": "Pay 30% advance to the seller and 70% when the shipment gets delivered",
    "breakdowns": [
      {
        "milestone_no": 1,
        "category": "payment",
        "type": "passthrough",
        "percentage": 30,
        "milestone_amount": 300,
        "status": "new",
        "txn_status": "new",
        "doc_status": "na"
      },
      {
        "milestone_no": 2,
        "category": "payout",
        "type": "passthrough",
        "percentage": 30,
        "milestone_amount": 294.6,
        "status": "new",
        "txn_status": "new",
        "doc_status": "na"
      },
      {
        "milestone_no": 3,
        "category": "payment",
        "type": "hold",
        "percentage": 70,
        "milestone_amount": 700,
        "status": "new",
        "txn_status": "new",
        "doc_status": "na"
      },
      {
        "milestone_no": 4,
        "category": "payout",
        "type": "hold",
        "percentage": 70,
        "milestone_amount": 687.4,
        "status": "new",
        "txn_status": "new",
        "doc_status": "na"
      }
    ]
  },
  "partner_reference_id": "uid1"
}
```

## Response Parameters

| Parameter         | Description                                         |
| ----------------- | --------------------------------------------------- |
| txn\_no           | `string` Year and 5 digit escrow transcation number |
| state             | `string` State / status of escrow                   |
| sub\_state        | `string` Sub state / status of escrow               |
| invoice\_currency | `string`  Invoice currency                          |
| invoice\_amount   | `float` Invoice amount                              |
