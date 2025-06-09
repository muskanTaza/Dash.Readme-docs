---
title: Settlements
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Settlements refer to the process by which Tazapay transfers (or "sweeps") all collected customer payments into your  added bank account. It involves consolidating payments processed over a specific period and moving these funds , typically on a weekly or scheduled basis.

# The Settlement Object

| Field               | Subfield        | type      | Description                                           |
| ------------------- | --------------- | --------- | ----------------------------------------------------- |
| id                  |                 | string    | ID of the settlement object                           |
| object              |                 | enum      | This is `settlement` here                             |
| created_at          |                 | timestamp | Timestamp at which the settlement was created         |
| count               |                 | json      | Count of various transactions for the settlement      |
|                     | payins          | integer   | Count of payins in the settlement                     |
|                     | refunds         | integer   | Count of refunds in the settlement                    |
|                     | adjustments     | integer   | Count of adjustments in the transaction               |
|                     | collects        | integer   | Count of collects in the transaction                  |
|                     | payouts         | integer   | Count of payouts in the transaction                   |
| tracking_details    |                 |           |                                                       |
|                     | tracking_type   | enum      | `uetr` or `utr`                                       |
|                     | tracking_number | string    | Tracking number for the settlement                    |
| amount              |                 | integer   | Gross Amount for the settlement                       |
| type                |                 | enum      | Transfer type                                         |
| mt103               |                 | string    | MT103 in case the transfer_type is `swift`            |
| fee                 |                 | integer   | Fee for the settlement                                |
| net_amount          |                 | integer   | Net Amount for the settlement after deducting fees    |
| balance_transaction |                 | string    | Balance Transaction ID associated with the settlement |
| status              |                 | enum      | Status of the settement                               |
| status_description  |                 | string    | Additional description about the status               |
| currency            |                 | string    | Three-letter ISO currency code                        |
| updated_at          |                 | timestamp | Timestamp at which the settlement was last updated    |

```Text JSON
{
    "id": "stl_ahfafooi7ibakbfahoan",
    "object": "settlement",
    "created_at": "2025-02-20T00:00:00Z",
    "count": {
        "payins": 100,
        "refunds": 10,
        "adjustments": 25,
        "collects": 30,
        "payouts": 10
    },
    "tracking_details": {
        "tracking_number": "8937589hfoiha98h",
        "tracking_type": "uetr"
    },
    "amount": 100123,
    "type": "wire_transfer",
    "mt103": "{1:F01BANKUS33AXXX0000000000}\n{2:O1031205050425BANKGB2LXXXX22221234560504251205N}\n{3:{108:20250408ABC12345}}\n{4:\n:20:ABC1234567890\n:23B:CRED\n:32A:250408USD123456,78\n:33B:USD123456,78\n:50K:/1234567890\nJOHN DOE\n123 MAIN STREET\nNEW YORK NY 10001\nUSA\n:59:/0987654321\nJANE SMITH\n456 ELM STREET\nLONDON SW1A 1AA\nUNITED KINGDOM\n:70:INVOICE PAYMENT REF 2025-04-INV12345\n:71A:OUR\n-}\n",
    "net_amount": 100000,
    "fee": 123,
    "balance_transaction": "btr_1234",
    "status": "succeeded",
    "status_description": "",
    "currency": "USD",
    "updated_at": "2025-02-20T00:00:00Z"
}
```

### Suggested Links:

- [Settlement API](https://docs.tazapay.com/reference/fetch-payins)
- Webhook Events for Settlements
- [Settlement State Machine](https://docs.tazapay.com/docs/settlement-state-machine)
- [Fetching the list of payins for a settlement](https://docs.tazapay.com/reference/fetch-payins)
- [Fetching the list of payouts for a settlement](https://docs.tazapay.com/reference/fetch-payouts)
- [Fetching the list of refunds for a settlement](https://docs.tazapay.com/reference/fetch-refunds)
- [Fetching the list of collects for a settlement](https://docs.tazapay.com/reference/fetch-collects)
- [Fetching the list of adjustments for a settlement](https://docs.tazapay.com/reference/fetch-adjustments)