---
title: FX Transaction Object
deprecated: false
hidden: false
metadata:
  robots: index
---
## Object Structure

```json FX Transaction
{
  "exchange_rate": 1,
  "final": {
    "amount": 10000000,
    "currency": "USD"
  },
  "id": "fx_d35tfigo4p2dt2hh0",
  "initial": {
    "amount": 10000000,
    "currency": "USD"
  },
  "object": "fx_transaction"
},
```

<br />

## Object Parameters

| Field            | Type   | Description                              |
| ---------------- | ------ | ---------------------------------------- |
| exchange_rate    | number | The exchange rate applied for FX.        |
| final.amount     | number | The final amount after FX conversion.    |
| final.currency   | string | The currency of the final amount.        |
| initial.amount   | number | The initial amount before FX conversion. |
| initial.currency | string | The currency of the initial amount.      |
| id               | string | The FX transaction ID.                   |
