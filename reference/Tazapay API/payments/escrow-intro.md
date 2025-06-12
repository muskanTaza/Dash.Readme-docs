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
       "url": "https://direct.download.link"
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
    "fee_amount": 750
  }
```

### Parameters:

| Parameter             | Description                                                                                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| state                 | `string` State / status of escrow                                                                                                                                        |
| sub\_state            | `string` Sub state / status of escrow                                                                                                                                    |
| invoice\_currency     | `string`  Invoice currency                                                                                                                                               |
| invoice\_amount       | `float` Invoice amount                                                                                                                                                   |
| fee\_tier             | `string` Applicable fee tier                                                                                                                                             |
| fee\_paid\_by         | `string` Party that bears the fee for the transaction. Can be: `buyer` or `seller`                                                                                       |
| txn\_type             | `string`  Type of transaction. Can be: `goods`, `service`                                                                                                                |
| txn\_no               | `string` Year and 5 digit escrow transcation number                                                                                                                      |
| txn\_description      | `string` A short description of the underlying transaction or trade                                                                                                      |
| release\_mechanism    | `string`  Party responsible for verifying the release documents. Can be: `marketplace`, `tazapay`, If empty; contracted MP level value will get applied                  |
| reference\_id         | `string` Marketplace identifier value. Example, marketplace escrow number, auto generated value, etc.                                                                    |
| initiated\_by         | `string` Tazapay account UUID of the party who has initiated the transaction                                                                                             |
| buyer\_id             | `string`  Tazapay account UUID of the buyer                                                                                                                              |
| seller\_id            | `string` Tazapay account UUID of the seller                                                                                                                              |
| invoice\_amount       | `float` Invoice amount                                                                                                                                                   |
| collect\_amount       | `float` Collection amount in invoice currency                                                                                                                            |
| disburse\_amount      | `float` Disburse amount in invoice currency                                                                                                                              |
| fee\_tier\_percentage | `string` Fee percentage to be paid by the party that bears the fee for the transaction.                                                                                  |
| release\_docs         | `[] release_docs` The list of documents to be provided as completion proof for the verification.  <br/> Please check <a href="/index.html#release_docs">release\_docs</a> |
| txn\_docs             | `[] txn_doc` Supporting documents for transaction. <br/>Please check <a href="/index.html#txn_doc">txn\_doc</a>                                                           |
| buyer                 | `buyer` Buyer deatils <br/>Please check <a href="/index.html#buyer">buyer</a>                                                                                             |
| seller                | `seller` Seller deatils <br/>Please check <a href="/index.html#seller">seller</a>                                                                                         |
| attributes            | `json` Tunnelled add-on fields                                                                                                                                           |
| initiator\_role       | `string` Party that initites the transaction. Can be `buyer` or `seller`                                                                                                 |
| fee\_amount           | `float` Fee in invoice currency                                                                                                                                          |

#### release\_docs:

| Parameter | Description                                                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| type      | `string` one of Bill of lading, Commercial Invoice, Packing List, Certificate of Origin, Airway Bill, Inspection Certificate, Others |
| name      | `string`  Name of the doc if user has selected type as others                                                                        |
| url       | `string`  Direct download link                                                                                                       |

#### txn\_doc:

| Parameter | Description                                                         |
| --------- | ------------------------------------------------------------------- |
| type      | `string` one of Proforma Invoice , PO, Contract, Order Form, Others |
| name      | `string`  Name of the doc if user has selected type as others       |
| url       | `string`  Direct download link                                      |

#### buyer:

| Parameter     | Description                                  |
| ------------- | -------------------------------------------- |
| contact\_name | `string` Buyer's first and last              |
| email         | `string`  Buyer's email address              |
| country       | `string`  Buyer's country                    |
| company\_name | `string`  Buyer's company name. Can be empty |

#### seller:

| Parameter     | Description                                   |
| ------------- | --------------------------------------------- |
| contact\_name | `string` Seller's first and last              |
| email         | `string`  Seller's email address              |
| country       | `string` Seller's country                     |
| company\_name | `string`  Seller's company name. Can be empty |