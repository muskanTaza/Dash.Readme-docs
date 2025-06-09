---
title: Introduction to Escrow
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
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

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "state",
    "0-1": "`string` State / status of escrow",
    "1-0": "sub_state",
    "1-1": "`string` Sub state / status of escrow",
    "2-0": "invoice_currency",
    "2-1": "`string`  Invoice currency",
    "3-0": "invoice_amount",
    "3-1": "`float` Invoice amount",
    "4-0": "fee_tier",
    "4-1": "`string` Applicable fee tier",
    "5-0": "fee_paid_by",
    "5-1": "`string` Party that bears the fee for the transaction. Can be: `buyer` or `seller`",
    "6-0": "txn_type",
    "6-1": "`string`  Type of transaction. Can be: `goods`, `service`",
    "7-0": "txn_no",
    "7-1": "`string` Year and 5 digit escrow transcation number",
    "8-0": "txn_description",
    "8-1": "`string` A short description of the underlying transaction or trade",
    "9-0": "release_mechanism",
    "9-1": "`string`  Party responsible for verifying the release documents. Can be: `marketplace`, `tazapay`, If empty; contracted MP level value will get applied",
    "10-0": "reference_id",
    "10-1": "`string` Marketplace identifier value. Example, marketplace escrow number, auto generated value, etc.",
    "11-0": "initiated_by",
    "11-1": "`string` Tazapay account UUID of the party who has initiated the transaction",
    "12-0": "buyer_id",
    "12-1": "`string`  Tazapay account UUID of the buyer",
    "13-0": "seller_id",
    "13-1": "`string` Tazapay account UUID of the seller",
    "14-0": "invoice_amount",
    "14-1": "`float` Invoice amount",
    "15-0": "collect_amount",
    "15-1": "`float` Collection amount in invoice currency",
    "16-0": "disburse_amount",
    "16-1": "`float` Disburse amount in invoice currency",
    "17-0": "fee_tier_percentage",
    "17-1": "`string` Fee percentage to be paid by the party that bears the fee for the transaction.",
    "18-0": "release_docs",
    "18-1": "`[] release_docs` The list of documents to be provided as completion proof for the verification.  <br> Please check <a href=\"/index.html#release_docs\">release_docs</a>",
    "19-0": "txn_docs",
    "19-1": "`[] txn_doc` Supporting documents for transaction. <br>Please check <a href=\"/index.html#txn_doc\">txn_doc</a>",
    "20-0": "buyer",
    "20-1": "`buyer` Buyer deatils <br>Please check <a href=\"/index.html#buyer\">buyer</a>",
    "21-0": "seller",
    "21-1": "`seller` Seller deatils <br>Please check <a href=\"/index.html#seller\">seller</a>",
    "22-0": "attributes",
    "22-1": "`json` Tunnelled add-on fields",
    "23-0": "initiator_role",
    "23-1": "`string` Party that initites the transaction. Can be `buyer` or `seller`",
    "24-0": "fee_amount",
    "24-1": "`float` Fee in invoice currency"
  },
  "cols": 2,
  "rows": 25,
  "align": [
    null,
    null
  ]
}
[/block]


#### release_docs:

| Parameter | Description                                                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| type      | `string` one of Bill of lading, Commercial Invoice, Packing List, Certificate of Origin, Airway Bill, Inspection Certificate, Others |
| name      | `string`  Name of the doc if user has selected type as others                                                                        |
| url       | `string`  Direct download link                                                                                                       |

#### txn_doc:

| Parameter | Description                                                         |
| --------- | ------------------------------------------------------------------- |
| type      | `string` One of Proforma Invoice , PO, Contract, Order Form, Others |
| name      | `string`  Name of the doc if user has selected type as others       |
| url       | `string`  Direct download link                                      |

#### buyer:

| Parameter    | Description                                  |
| ------------ | -------------------------------------------- |
| contact_name | `string` Buyer's first and last name         |
| email        | `string`  Buyer's email address              |
| country      | `string`  Buyer's country                    |
| company_name | `string`  Buyer's company name. Can be empty |

#### seller:

| Parameter    | Description                                   |
| ------------ | --------------------------------------------- |
| contact_name | `string` Seller's first and last name         |
| email        | `string`  Seller's email address              |
| country      | `string` Seller's country                     |
| company_name | `string`  Seller's company name. Can be empty |