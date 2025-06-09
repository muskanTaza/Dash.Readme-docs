---
title: Introduction to Release
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
Release API is a call made to inform Tazapay so that we can initiate the release of funds from Tazapay balance directly to the user's bank account. For Tazapay to release the payment, a seller's <a href="https://tazapay-api-developer.readme.io/reference/kyb-object" target="_blank">KYB</a> should have been completed and the seller's <a href="https://tazapay-api-developer.readme.io/reference/the-bank-object" target="_blank">bank account</a> details should have been provided to Tazapay.

Tazapay will release the payment to the seller's bank account within 48 business hours of the API call, provided prerequisites are met.

If required, the API will support the upload of all documents required for the release of payment, such as:

- Proof of service rendered
- Proof of shipment (such as Bill of Lading, Airway Bill etc)

> 📘 Uploading Documents
> 
> Depending on your use case, an upload of the release document may not be required.

```json Release object
{
    "txn_no": "2021-59991",
    "release_docs": [
        {
            "type": "Others",
            "name": "sampletest",  // required if type = Others
            "url": "https://tazapay-temp-doc-sandbox.s3.ap-southeast/",
            "file_name": "test_1634014597228917008_Screenshot_2021-10-11_at_3.01.32_PM.png"
        }
    ]
}
```

The different types of release_docs are:

1. When the txn_type is goods, the value of type can be:`Bill of Lading/ Airway Bill`, `Commercial Invoice`, `Others`
2. When the txn_type is service, the value of type can be:`Invoice`, `Proof of Service Delivery`, `Others`

The `url` refers to the url where the file is located. It should be publicly accessible so that we can download the document and verify the same.

The `name` is mandatory if the `type` is set as `Others`.



### Object Body Parameters

| Parameter                               | Description                                                                                                                                                                                                                            |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| txn_no<br><small>required</small>       | `String `  Escrow transcation number received from create_escrow API response                                                                                                                                                          |
| release_docs<br><small>optional</small> | `[] release_docs` The list of documents to be provided as completion proof for the verification.  <br> Please check [release_docs](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTEy-release#release_docs) |

#### release_docs

| Parameter | Description                                                                                                                                                                                                                                 |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type      | `string` One of the documents <br><br>If txn_type = goods <br>1. Bill of Lading/ Airway Bill <br>2. Commercial Invoice <br><br>If txn_type = service <br>1. Invoice <br>2. Proof of Service Delivery<br><br> For both txn_type<br>1. Others |
| name      | `string`  Name of the doc if user has selected type as others                                                                                                                                                                               |
| url       | `string`  Direct download link                                                                                                                                                                                                              |
| filename  | `string`  Name of the file which being uploaded in the above public link                                                                                                                                                                    |