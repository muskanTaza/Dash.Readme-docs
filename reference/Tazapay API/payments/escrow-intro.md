---
title: Introduction to Escrow
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
Escrow allows two parties to protect funds until certain conditions or [milestones](doc:milestone-schemes) are met. The verification of completion of these funds can be either done by Tazapay or the user, which has to be communicated to Tazapay at the time of onboarding. 

To create an escrow, we need to know the Tazapay User IDs of the buyer and seller participating in the transaction, the invoice amount and currency and a free-text note on what the transaction is about. 

Documents are not required to create an escrow but can be provided to indicate additional details about the underlying trade to make the eventual release process smoother for the seller (entity getting paid).

```json Escrow object
{
    "state": "Escrow_Draft",
    "sub_state": "na",
    "invoice_currency": "USD",
    "fee_tier": "standard",
    "fee_paid_by": "buyer",
    "txn_type": "goods",
    "txn_no": "2021-71615",
    "txn_description": "",
    "release_mechanism": "",
    "reference_id": "",
    "initiated_by": "53bb481a-58bc-450a-b7ea-8e818a0edcd8",
    "buyer_id": "53bb481a-58bc-450a-b7ea-8e818a0edcd8",
    "seller_id": "6ec614d4-26af-467e-a57f-aea4b04489aa",
    "invoice_amount": 300000,
    "collect_amount": 300750,
    "disburse_amount": 300000,
    "fee_tier_percentage": 6.2,
    "release_docs": [
        {
         "type": "Proof of Work",
         "url": "https://direct.download.link" 
        },
        {
         "type" : "Others",
         "name" : "OTH - File", 
         "url" : "https://direct.download.link" 
        }
      ],
    "txn_docs":[ 
      {
       "type" : "Proforma Invoice",
       "url" : "https://direct.download.link"
      },
      {
       "type" : "Others",
       "name" : "OTH - File",
       "url" : "https://direct.download.link"
      }
    ],
    "buyer": {
      "contact_name": "Jane doe",
      "email": "janedoe@example.com",
      "country": "SG",
      "company_name": "LoremPay",
      "ind_bus_type": "Business"
    },
    "seller": {
      "contact_name": "John doe",
      "email": "johndoe@example.com",
      "country": "GB",
      "company_name": "",
      "ind_bus_type": "Individual"
    },
    "attributes": null,
    "initiator_role": "buyer",
    "fee_amount": 750,
  }
```



### Parameters:

| Parameter           | Description                                                                                                                                                             |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| state               | `string` State / status of escrow                                                                                                                                       |
| sub_state           | `string` Sub state / status of escrow                                                                                                                                   |
| invoice_currency    | `string`  Invoice currency                                                                                                                                              |
| invoice_amount      | `float` Invoice amount                                                                                                                                                  |
| fee_tier            | `string` Applicable fee tier                                                                                                                                            |
| fee_paid_by         | `string` Party that bears the fee for the transaction. Can be: `buyer` or `seller`                                                                                      |
| txn_type            | `string`  Type of transaction. Can be: `goods`, `service`                                                                                                               |
| txn_no              | `string` Year and 5 digit escrow transcation number                                                                                                                     |
| txn_description     | `string` A short description of the underlying transaction or trade                                                                                                     |
| release_mechanism   | `string`  Party responsible for verifying the release documents. Can be: `marketplace`, `tazapay`, If empty; contracted MP level value will get applied                 |
| reference_id        | `string` Marketplace identifier value. Example, marketplace escrow number, auto generated value, etc.                                                                   |
| initiated_by        | `string` Tazapay account UUID of the party who has initiated the transaction                                                                                            |
| buyer_id            | `string`  Tazapay account UUID of the buyer                                                                                                                             |
| seller_id           | `string` Tazapay account UUID of the seller                                                                                                                             |
| invoice_amount      | `float` Invoice amount                                                                                                                                                  |
| collect_amount      | `float` Collection amount in invoice currency                                                                                                                           |
| disburse_amount     | `float` Disburse amount in invoice currency                                                                                                                             |
| fee_tier_percentage | `string` Fee percentage to be paid by the party that bears the fee for the transaction.                                                                                 |
| release_docs        | `[] release_docs` The list of documents to be provided as completion proof for the verification.  <br> Please check <a href="/index.html#release_docs">release_docs</a> |
| txn_docs            | `[] txn_doc` Supporting documents for transaction. <br>Please check <a href="/index.html#txn_doc">txn_doc</a>                                                           |
| buyer               | `buyer` Buyer deatils <br>Please check <a href="/index.html#buyer">buyer</a>                                                                                            |
| seller              | `seller` Seller deatils <br>Please check <a href="/index.html#seller">seller</a>                                                                                        |
| attributes          | `json` Tunnelled add-on fields                                                                                                                                          |
| initiator_role      | `string` Party that initites the transaction. Can be `buyer` or `seller`                                                                                                |
| fee_amount          | `float` Fee in invoice currency                                                                                                                                         |

#### release_docs:

| Parameter | Description                                                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| type      | `string` one of Bill of lading, Commercial Invoice, Packing List, Certificate of Origin, Airway Bill, Inspection Certificate, Others |
| name      | `string`  Name of the doc if user has selected type as others                                                                        |
| url       | `string`  Direct download link                                                                                                       |

#### txn_doc:

| Parameter | Description                                                         |
| --------- | ------------------------------------------------------------------- |
| type      | `string` one of Proforma Invoice , PO, Contract, Order Form, Others |
| name      | `string`  Name of the doc if user has selected type as others       |
| url       | `string`  Direct download link                                      |

#### buyer:

| Parameter    | Description                                  |
| ------------ | -------------------------------------------- |
| contact_name | `string` Buyer's first and last              |
| email        | `string`  Buyer's email address              |
| country      | `string`  Buyer's country                    |
| company_name | `string`  Buyer's company name. Can be empty |

#### seller:

| Parameter    | Description                                   |
| ------------ | --------------------------------------------- |
| contact_name | `string` Seller's first and last              |
| email        | `string`  Seller's email address              |
| country      | `string` Seller's country                     |
| company_name | `string`  Seller's company name. Can be empty |