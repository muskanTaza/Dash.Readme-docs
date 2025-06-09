---
title: Introduction to Refund
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
[Refund](ref:refund-api) initiates a refund of an existing paid transaction back to source. 

If the refund request is approved, Tazapay will refund the amount to the source used by the buyer to make the payment.

> 📘 
> 
> Depending on the payment method, Tazapay may not be able to process refunds. For more info, read our [FAQ](https://support.tazapay.com/what-payment-methods-are-unsupported-for-refunds)

```json Refund body
{
  "txn_no": "2021-20053",
  "amount": 200,
  "remarks": "refund"
  "documents": [ 
    {
      "file_name": "file_name",
      "url": "https://direct.download.link"
    }
  ]
}
```



### Object body Parameters

| Parameter                            | Description                                                                                                                                                                                             |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| txn_no<br><small>required</small>    | `String `  Transcation number received from create_escrow API response                                                                                                                                  |
| Amount<br><small>optional</small>    | `INT` Amount to be refunded. If omitted, the request will be registered for a refund of the full escrow (refund_amount cannot be greater than the  invoice_amount of the underlying transaction/escrow) |
| remarks<br><small>optional</small>   | `string` free text to add any additional details concerning the refund request                                                                                                                          |
| documents<br><small>optional</small> | `[] release_docs` Any document to support the refund request  <br> Please check [documents](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTEy-release#release_docs)         |

#### documents

| Parameter | Description                                                              |
| --------- | ------------------------------------------------------------------------ |
| url       | `string`  Direct download link                                           |
| file_name | `string`  Name of the file which being uploaded in the above public link |