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

<Table>
  <thead>
    <tr>
      <th>
        Parameter
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        state
      </td>

      <td>
        `string` State / status of escrow
      </td>
    </tr>

    <tr>
      <td>
        sub\_state
      </td>

      <td>
        `string` Sub state / status of escrow
      </td>
    </tr>

    <tr>
      <td>
        invoice\_currency
      </td>

      <td>
        `string`  Invoice currency
      </td>
    </tr>

    <tr>
      <td>
        invoice\_amount
      </td>

      <td>
        `float` Invoice amount
      </td>
    </tr>

    <tr>
      <td>
        fee\_tier
      </td>

      <td>
        `string` Applicable fee tier
      </td>
    </tr>

    <tr>
      <td>
        fee\_paid\_by
      </td>

      <td>
        `string` Party that bears the fee for the transaction. Can be: `buyer` or `seller`
      </td>
    </tr>

    <tr>
      <td>
        txn\_type
      </td>

      <td>
        `string`  Type of transaction. Can be: `goods`, `service`
      </td>
    </tr>

    <tr>
      <td>
        txn\_no
      </td>

      <td>
        `string` Year and 5 digit escrow transcation number
      </td>
    </tr>

    <tr>
      <td>
        txn\_description
      </td>

      <td>
        `string` A short description of the underlying transaction or trade
      </td>
    </tr>

    <tr>
      <td>
        release\_mechanism
      </td>

      <td>
        `string`  Party responsible for verifying the release documents. Can be: `marketplace`, `tazapay`, If empty; contracted MP level value will get applied
      </td>
    </tr>

    <tr>
      <td>
        reference\_id
      </td>

      <td>
        `string` Marketplace identifier value. Example, marketplace escrow number, auto generated value, etc.
      </td>
    </tr>

    <tr>
      <td>
        initiated\_by
      </td>

      <td>
        `string` Tazapay account UUID of the party who has initiated the transaction
      </td>
    </tr>

    <tr>
      <td>
        buyer\_id
      </td>

      <td>
        `string`  Tazapay account UUID of the buyer
      </td>
    </tr>

    <tr>
      <td>
        seller\_id
      </td>

      <td>
        `string` Tazapay account UUID of the seller
      </td>
    </tr>

    <tr>
      <td>
        invoice\_amount
      </td>

      <td>
        `float` Invoice amount
      </td>
    </tr>

    <tr>
      <td>
        collect\_amount
      </td>

      <td>
        `float` Collection amount in invoice currency
      </td>
    </tr>

    <tr>
      <td>
        disburse\_amount
      </td>

      <td>
        `float` Disburse amount in invoice currency
      </td>
    </tr>

    <tr>
      <td>
        fee\_tier\_percentage
      </td>

      <td>
        `string` Fee percentage to be paid by the party that bears the fee for the transaction.
      </td>
    </tr>

    <tr>
      <td>
        release\_docs
      </td>

      <td>
        `[] release_docs` The list of documents to be provided as completion proof for the verification.  <br> Please check <a href="/index.html#release_docs">release\_docs</a>
      </td>
    </tr>

    <tr>
      <td>
        txn\_docs
      </td>

      <td>
        `[] txn_doc` Supporting documents for transaction. <br>Please check <a href="/index.html#txn_doc">txn\_doc</a>
      </td>
    </tr>

    <tr>
      <td>
        buyer
      </td>

      <td>
        `buyer` Buyer deatils <br>Please check <a href="/index.html#buyer">buyer</a>
      </td>
    </tr>

    <tr>
      <td>
        seller
      </td>

      <td>
        `seller` Seller deatils <br>Please check <a href="/index.html#seller">seller</a>
      </td>
    </tr>

    <tr>
      <td>
        attributes
      </td>

      <td>
        `json` Tunnelled add-on fields
      </td>
    </tr>

    <tr>
      <td>
        initiator\_role
      </td>

      <td>
        `string` Party that initites the transaction. Can be `buyer` or `seller`
      </td>
    </tr>

    <tr>
      <td>
        fee\_amount
      </td>

      <td>
        `float` Fee in invoice currency
      </td>
    </tr>
  </tbody>
</Table>

#### release\_docs:

| Parameter | Description                                                                                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| type      | `string` one of Bill of lading, Commercial Invoice, Packing List, Certificate of Origin, Airway Bill, Inspection Certificate, Others |
| name      | `string`  Name of the doc if user has selected type as others                                                                        |
| url       | `string`  Direct download link                                                                                                       |

#### txn\_doc:

| Parameter | Description                                                         |
| --------- | ------------------------------------------------------------------- |
| type      | `string` One of Proforma Invoice , PO, Contract, Order Form, Others |
| name      | `string`  Name of the doc if user has selected type as others       |
| url       | `string`  Direct download link                                      |

#### buyer:

| Parameter     | Description                                  |
| ------------- | -------------------------------------------- |
| contact\_name | `string` Buyer's first and last name         |
| email         | `string`  Buyer's email address              |
| country       | `string`  Buyer's country                    |
| company\_name | `string`  Buyer's company name. Can be empty |

#### seller:

| Parameter     | Description                                   |
| ------------- | --------------------------------------------- |
| contact\_name | `string` Seller's first and last name         |
| email         | `string`  Seller's email address              |
| country       | `string` Seller's country                     |
| company\_name | `string`  Seller's company name. Can be empty |
