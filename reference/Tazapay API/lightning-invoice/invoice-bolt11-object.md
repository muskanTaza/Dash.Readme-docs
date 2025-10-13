---
title: Invoice (Bolt11) object
excerpt: This repesents a bolt11 standard invoice on the bitcoin lightning network
deprecated: false
hidden: false
metadata:
  robots: index
---
```json
{
  "id": "l11_abc123xyz",
  "object": "lightning_invoice_bolt11",
  "amount": 12345600,
  "d_tag_memo": "Payment for order #7890",
  "h_tag_memo": "f2ca1bb6c7e907d06dafe4687e579fce76c70fd6",
  "collect": "col_98765",
  "expiry_interval": 3600,
  "metadata": {
    "order_id": "7890",
    "customer_id": "cust_456"
  },
  "status": "active",
  "payment_status": "unpaid",
  "created_at": "2025-09-28T08:15:30Z",
  "updated_at": "2025-09-28T08:20:45Z"
}
```

| Field           | type      | Description                                                                                                 |
| :-------------- | :-------- | :---------------------------------------------------------------------------------------------------------- |
| id              | string    | Unique ID of the object                                                                                     |
| object          | enum      | This is lightning_invoice_bolt11 here                                                                       |
| amount          | integer   | Amount in BTC. The precision is 8 decimal places                                                            |
| d_tag_memo      | string    | This will be included in the d-tag. If both d_tag_memo and h_tag_memo are provided, only h_tag will be used |
| h_tag_memo      | string    | SHA-256 of the d_tag_memo. If both d_tag_memo and h_tag_memo are provided, only h_tag_memo will be used     |
| expiry_interval | integer   | The expiry of the invoice in seconds. Default value is 3600 (1 hour).                                       |
| collect         | string    | Collect ID which is created when the invoice gets funded                                                    |
| status          | enum      | active, expired                                                                                             |
| payment_status  | enum      | paid, unpaid                                                                                                |
| created_at      | timestamp | Timestamp at which this object was created                                                                  |
| updated_at      | timestamp | Timestamp at which this object was last updated                                                             |
| metadata        | json      | Set of key-value pairs attached to the object                                                               |

<br />