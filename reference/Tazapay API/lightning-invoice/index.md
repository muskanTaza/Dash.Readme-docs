---
title: Lightning Invoice
excerpt: This repesents a bolt11 standard invoice on the bitcoin lightning network
deprecated: false
hidden: false
icon: ⚡
metadata:
  robots: index
---
## Object structure

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
