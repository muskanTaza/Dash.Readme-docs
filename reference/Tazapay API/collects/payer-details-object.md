---
title: Payer Details Object
deprecated: false
hidden: false
metadata:
  robots: index
---
## Object Structure

```json
{
  "additional_information": "CM Payment for Order 56",
  "name": "CMC COMPANY",
  "payer_bank": {
    "account_number": "1112019837840",
    "address": null,
    "bank_codes": {
              "swift_code": "AJUM7CHBKXXX"
            },
    "name": "C Bank"
  },
  "reference_id": ""
}
```

<br />

## Object Parameters

<br />

| Field                  | Type   | Description                                                         |
| :--------------------- | :----- | :------------------------------------------------------------------ |
| additional_information | string | Additional information about the payment (e.g., payment reference). |
| name                   | string | Name of the payer.                                                  |
| payer_bank             | object | Payer’s bank details (See Payer Bank Table).                        |
| reference_id           | string | Reference identifier for the payer’s transaction.                   |
| payer_wallet           | object | Payer's wallet details (See Payer's wallet table)                   |
