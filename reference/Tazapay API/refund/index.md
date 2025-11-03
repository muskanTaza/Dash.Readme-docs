---
title: Refund
excerpt: ''
deprecated: false
hidden: false
icon: far fa-money-bill-transfer
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
A Tazapay API object that is used to return money to a customer after a payment has been made. It simplifies the process of issuing refunds for products or services, helping businesses maintain customer satisfaction.

### Refund

| Field              | Subfield | Type                   | Description                                                                                            |
| ------------------ | -------- | ---------------------- | ------------------------------------------------------------------------------------------------------ |
| id                 |          | string                 | The unique Tazapay identifier for the refund.                                                          |
| object             |          | string                 | The type of object, which is "refund".                                                                 |
| payin              |          | string                 | The unique Tazapay ID of the related payin transaction.                                                |
| amount             |          | number                 | The total amount being refunded.                                                                       |
| currency           |          | string                 | The currency in which the refund was made (e.g., USD).                                                 |
| customer_receives  |          | object                 | The amount and currency received by the customer after the refund.                                     |
|                    | currency | string                 | The currency in which the customer receives the refund.                                                |
|                    | amount   | number                 | The amount the customer receives after the refund.                                                     |
| payment_attempt    |          | string                 | The unique Tazapay ID of the payment attempt associated with the refund.                               |
| reason             |          | string                 | The reason for the refund (e.g., "Damaged Goods").                                                     |
| metadata           |          | json                   | Set of key-value pairs attached to the refund object.                                                  |
| status             |          | enum                   | The current status of the refund [Values - Requested, Pending, Initiated, Succeeded, Failed, Rejected] |
| status_description |          | string                 | A description of the current refund status.                                                            |
| webhook_url        |          | string                 | The URL for webhook notifications related to the refund.                                               |
| created_at         |          | string (ISO timestamp) | The timestamp when the refund was created.                                                             |
