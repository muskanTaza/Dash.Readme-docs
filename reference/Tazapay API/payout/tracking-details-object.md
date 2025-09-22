---
title: Tracking Details Object
deprecated: false
hidden: false
metadata:
  robots: index
---
## Object Structure

```json
{
  "tracking_number": "7833d-34b4-478-aac8-1184beae",
  "tracking_type": "uetr"
}
```

<br />

## Object Parameters

| Field           | Type   | Description                                                    |
| --------------- | ------ | -------------------------------------------------------------- |
| tracking_number | string | The tracking number (UETR, UTR, transaction hash, etc.).       |
| tracking_type   | enum   | The tracking type. [Values: `uetr`, `utr`, `transaction_hash`] |
