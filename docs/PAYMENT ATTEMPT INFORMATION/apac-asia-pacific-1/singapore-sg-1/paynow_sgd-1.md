---
title: paynow_sgd
excerpt: >-
  This is the transaction-specific data you will receive as part of a payment
  attempt for PayNow QR
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
| Field         | type   | Description                                         |
| :------------ | :----- | :-------------------------------------------------- |
| payer\_name   | string | Verified Name of the payer                          |
| reference\_id | string | Reference number associated with the paynow payment |

```Text JSON
"payment_method_details":{
  "type":"paynow_sgd",
  "paynow_sgd":{
    "payer_name":"Andrea Lark",
    "reference_id":"0000000000000"
  }
}
```
