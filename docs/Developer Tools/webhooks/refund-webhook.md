---
title: Refund
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
```json Sample webhook for Refund
{
  "reference_id": "e431ac5f-8055-451f-b819-7d0c043a61d0",
  "txn_no": "2207-693901",
  "status": "approved",
  "updated_at": "2022-07-29T07:58:40.026684Z",
  "reason": "Refund processed successfully"
}
```

### Response parameters:

| Parameter     | Description                                                           |
| ------------- | --------------------------------------------------------------------- |
| reference\_id | `string` A unique ID to track each refund request                     |
| txn\_no       | `string` The transaction number to which this refund is associated to |
| status        | `string` The status of the refund request                             |
| updated\_at   | `string` Timestamp at which the status of the refund was last updated |
| reason        | `string` Additional message about the refund for better comprehension |
