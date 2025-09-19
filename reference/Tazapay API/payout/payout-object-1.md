---
title: Payout Object
excerpt: >-
  Payout allows businesses to disburse payments to individuals or other
  businesses globally. It facilitates cross-border payouts by enabling transfers
  to local bank accounts, ensuring compliance with international regulations,
  and offering multiple payout options such as bank transfers, digital wallets,
  or local payment methods
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Payout Object

## Object Parameters

```json Swift Bank Payout
{
  "status": "success",
  "message": "",
  "data": {
      "amount": 100000,
      "balance_transaction": "btr_d35pv4qcl8imrv60",
      "beneficiary": "bnf_d3inm6ami8u10oqfg",
      "beneficiary_details": {
          "address": {
              "country": "CN"
              "line1": "Zhen Rui Yun Lu 66",
              "postal_code": "311011"
            },
          "date_of_birth": "",
          "destination": "",
          "destination_details": {
              "bank": {
                  "account_number": "33050167624000001030",
                  "account_type": "",
                  "bank_codes": {
                      "swift_code": "PCBCCNBJZJX"
                    },
                  "bank_name": "CHINA CONSTRUCTION BANK, ZHEJIANG BRANCH",
                  "branch_name": "",
                  "country": "CN",
                  "currency": "USD",
                  "firc_required": false,
                  "purpose_code": "",
                  "transfer_type": "swift"
                },
              "type": "bank"
            },
          "documents": [],
          "email": "",
          "name": "IMPORT AND EXPORT CO., LTD",
          "name_local": "",
          "national_identification_number": "",
          "party_classification": "",
          "phone": {
              "calling_code": "86"
            },
          "registration_number": "",
          "tax_id": "",
          "type": "business"
        },
      "charge_type": "ours",
      "confirmation_documents": [],
      "created_at": "2025-09-18T10:07:35.101708Z",
      "currency": "USD",
      "destination_fx_quote": "fx_d35tjpnfi4p2dt2hh0",
      "documents": [],
      "holding_currency": "USD",
      "holding_fx_quote": "fx_d35tjpnfigp2dt2hgg",
      "holding_fx_transaction": {
          "exchange_rate": 1,
          "final": {
              "amount": 10000000,
              "currency": "USD"
            },
          "id": "fx_d35tjpnfigp2dt2hgg",
          "initial": {
              "amount": 10000000,
              "currency": "USD"
            },
          "object": "fx_transaction"
        },
      "id": "pot_d35tjpn4qcl8iv30",
      "logistics_tracking_details": [],
      "metadata": null,
      "mt103": "",
      "object": "payout",
      "on_behalf_of": "",
      "payout_fx_transaction": {
          "exchange_rate": 1,
          "final": {
              "amount": 10000000,
              "currency": "USD"
            },
          "id": "fx_d35tfigo4p2dt2hh0",
          "initial": {
              "amount": 10000000,
              "currency": "USD"
            },
          "object": "fx_transaction"
        },
      "payout_quote": "",
      "purpose": "PYR003",
      "reference_id": "",
      "statement_descriptor": "",
      "status": "succeeded",
      "status_description": "",
      "tracking_details": {
          "tracking_number": "7833d-34b4-478-aac8-1184beae",
          "tracking_type": "uetr"
        },
      "transaction_description": "Payment for goods acc 125",
      "type": "swift"
    }
}
```
```
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 3000000,
    "balance_transaction": "btr_dhuvflvi5frlneafr0",
    "beneficiary": "bnf_d0dla9u8dpp4edio0",
    "beneficiary_details": {
      "address": null,
      "date_of_birth": "",
      "destination": "",
      "destination_details": {
        "bank": {
          "account_type": "",
          "bank_codes": {
            "swift_code": "FBDEFF"
          },
          "bank_name": "ER VOLKSBANK EG",
          "branch_name": "",
          "country": "DE",
          "currency": "EUR",
          "firc_required": false,
          "iban": "DE535019045650474185",
          "purpose_code": "",
          "transfer_type": "any"
        },
        "type": "bank"
      },
      "documents": [],
      "email": "",
      "name": "GMBH",
      "name_local": "",
      "national_identification_number": "",
      "party_classification": "",
      "phone": {
        "calling_code": "49"
      },
      "registration_number": "",
      "tax_id": "",
      "type": "business"
    },
    "charge_type": "",
    "confirmation_documents": [],
    "created_at": "2025-09-16T08:27:41.832790Z",
    "currency": "EUR",
    "destination_fx_quote": "fx_d34hc7loipp34fm0",
    "documents": [],
    "holding_currency": "USD",
    "holding_fx_quote": "fx_d34hc7loipp34fmg",
    "holding_fx_transaction": {
      "exchange_rate": 0.846438,
      "final": {
        "amount": 3000000,
        "currency": "EUR"
      },
      "id": "fx_d34flc7loipp34fmg",
      "initial": {
        "amount": 3544266,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "id": "pot_d34hlvi5frlneafo0",
    "local": {
      "fund_transfer_network": ""
    },
    "logistics_tracking_details": [],
    "metadata": null,
    "mt103": "",
    "object": "payout",
    "on_behalf_of": "",
    "payout_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 3000000,
        "currency": "EUR"
      },
      "id": "fx_d34huvflc7pp34fm0",
      "initial": {
        "amount": 3000000,
        "currency": "EUR"
      },
      "object": "fx_transaction"
    },
    "payout_quote": "",
    "purpose": "PYR001",
    "reference_id": "",
    "statement_descriptor": "",
    "status": "succeeded",
    "status_description": "",
    "tracking_details": {
      "tracking_number": "098771252590P9A",
      "tracking_type": "UTR"
    },
    "transaction_description": "Payment for logistic services 9-09",
    "type": "local"
  }
}
```

### Payout

| Field                   | Subfield                       | Type                   | Description                                                                                                                                                                                                                                                                                                                                        |
| ----------------------- | ------------------------------ | ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| amount                  |                                | number                 | The total amount for the payout transaction.                                                                                                                                                                                                                                                                                                       |
| balance_transaction     |                                | string                 | The Tazapay ID of the balance transaction associated with the payout.                                                                                                                                                                                                                                                                              |
| beneficiary             |                                | string                 | The Tazapay ID of the beneficiary receiving the payout.                                                                                                                                                                                                                                                                                            |
| beneficiary_details     |                                | object                 | The details of the beneficiary.                                                                                                                                                                                                                                                                                                                    |
|                         | address                        | object                 | The address of the beneficiary. (See Address Table)                                                                                                                                                                                                                                                                                                |
|                         | destination                    | string                 | The ID of the destination account for the payout.                                                                                                                                                                                                                                                                                                  |
|                         | destination_details            | object                 | The details of the destination account. (See Destination Details Table)                                                                                                                                                                                                                                                                            |
|                         | documents                      | array                  | The list of documents related to the beneficiary.                                                                                                                                                                                                                                                                                                  |
|                         | email                          | string                 | The email address of the beneficiary.                                                                                                                                                                                                                                                                                                              |
|                         | name                           | string                 | The name of the beneficiary.                                                                                                                                                                                                                                                                                                                       |
|                         | phone                          | object                 | The phone details of the beneficiary. (See Phone Table)                                                                                                                                                                                                                                                                                            |
|                         | tax_id                         | string                 | The tax identification number of the beneficiary.                                                                                                                                                                                                                                                                                                  |
|                         | type                           | enum                   | The type of the beneficiary [Values - individual, business].                                                                                                                                                                                                                                                                                       |
|                         | date_of_birth                  |                        |                                                                                                                                                                                                                                                                                                                                                    |
|                         | name_local                     |                        |                                                                                                                                                                                                                                                                                                                                                    |
|                         | national_identification_number |                        |                                                                                                                                                                                                                                                                                                                                                    |
|                         | party_classification           |                        |                                                                                                                                                                                                                                                                                                                                                    |
|                         | registration_number            |                        |                                                                                                                                                                                                                                                                                                                                                    |
| charge_type             |                                | enum                   | The charge type for the payout. [Value - shared, ours]                                                                                                                                                                                                                                                                                             |
| created_at              |                                | string (ISO Timespamp) | The timestamp when the payout was created.                                                                                                                                                                                                                                                                                                         |
| currency                |                                | string                 | The currency of the payout amount.                                                                                                                                                                                                                                                                                                                 |
| documents               |                                | array                  | The list of documents related to the payout.                                                                                                                                                                                                                                                                                                       |
| holding_currency        |                                | string                 | The currency used for holding funds before payout (e.g., EUR).                                                                                                                                                                                                                                                                                     |
| holding_fx_transaction  |                                | object                 | The details of the FX transaction for holding currency. (See FX Transaction Table)                                                                                                                                                                                                                                                                 |
| id                      |                                | string                 | The unique Tazapay identifier for the payout.                                                                                                                                                                                                                                                                                                      |
| metadata                |                                | json                   | Set of key-value pairs attached to the payout.                                                                                                                                                                                                                                                                                                     |
| mt103                   |                                | string                 | The MT103 SWIFT message reference for the payout (if applicable).                                                                                                                                                                                                                                                                                  |
| object                  |                                | string                 | The type of object, which is "payout".                                                                                                                                                                                                                                                                                                             |
| payout_fx_transaction   |                                | object                 | The details of the FX transaction for payout currency. (See FX Transaction Table)                                                                                                                                                                                                                                                                  |
| purpose                 |                                | enum                   | Reason for payout. Click [here](https://docs.tazapay.com/docs/reasons-for-payout) for the detailed list. [Values - PYR001, PYR002, PYR003, PYR004, PYR005, PYR006, PYR007, PYR008, PYR009, PYR010, PYR011, PYR012, PYR013, PYR014, PYR015, PYR016, PYR017, PYR018, PYR019, PYR020, PYR021, PYR022, PYR023, PYR024, PYR025, PYR026, PYR027, PYR028] |
| reference_id            |                                | string                 | The reference ID for the payout.                                                                                                                                                                                                                                                                                                                   |
| statement_descriptor    |                                | string                 | The statement descriptor for the payout, to appear on the beneficiary’s statement.                                                                                                                                                                                                                                                                 |
| status                  |                                | enum                   | The current status of the payout [Values - Processing, Requires Approval, Requires Action, Succeeded, Failed, Cancelled]                                                                                                                                                                                                                           |
| status_description      |                                | string                 | A description of the current payout status (optional).                                                                                                                                                                                                                                                                                             |
| tracking_details        |                                | object                 | Tracking details of the payout, if applicable.                                                                                                                                                                                                                                                                                                     |
| transaction_description |                                | string                 | A description of the payout transaction.                                                                                                                                                                                                                                                                                                           |
| type                    |                                | enum                   | The type of payout [Values - local, swift, wallet]                                                                                                                                                                                                                                                                                                 |

<br />

### Destination Details

| Field                                          | Type    | Description                                                                                |
| ---------------------------------------------- | ------- | ------------------------------------------------------------------------------------------ |
| destination_details.bank.account_number        | string  | The account number of the beneficiary's bank.                                              |
| destination_details.bank.account_type          | string  | The type of bank account (optional).                                                       |
| destination_details.bank.bank_codes.aba_code   | string  | The ABA routing code of the beneficiary's bank.                                            |
| destination_details.bank.bank_codes.swift_code | string  | The SWIFT code of the beneficiary's bank.                                                  |
| destination_details.bank.bank_name             | string  | The name of the beneficiary's bank.                                                        |
| destination_details.bank.branch_name           | string  | The branch name of the beneficiary's bank (optional).                                      |
| destination_details.bank.country               | string  | The country of the beneficiary's bank.                                                     |
| destination_details.bank.currency              | string  | The currency in which the bank account operates.                                           |
| destination_details.bank.firc_required         | boolean | Indicates if FIRC (Foreign Inward Remittance Certificate) is required for the transaction. |
| destination_details.bank.purpose_code          | string  | The purpose code for the transaction (optional).                                           |
| destination_details.type                       | string  | The type of destination (e.g., bank).                                                      |

<br />

### Address

| Field               | Type   | Description                                              |
| ------------------- | ------ | -------------------------------------------------------- |
| address             | object | The address of the beneficiary.                          |
| address.city        | string | The city of the beneficiary.                             |
| address.country     | string | The country of the beneficiary.                          |
| address.line1       | string | The first line of the beneficiary's address.             |
| address.line2       | string | The second line of the beneficiary's address (optional). |
| address.postal_code | string | The postal code of the beneficiary's address.            |
| address.state       | string | The state or province of the beneficiary's address.      |

<br />

### Phone

| Field              | Type   | Description                                                        |
| ------------------ | ------ | ------------------------------------------------------------------ |
| phone              | object | Phone details of the beneficiary.                                  |
| phone.calling_code | string | The international calling code for the beneficiary's phone number. |
| phone.number       | string | The phone number of the beneficiary.                               |

<br />

### FX Transaction

| Field            | Type   | Description                                                 |
| ---------------- | ------ | ----------------------------------------------------------- |
| exchange_rate    | number | The exchange rate used for the currency conversion.         |
| final.amount     | number | The final amount after conversion.                          |
| final.currency   | string | The final currency after conversion.                        |
| initial.amount   | number | The initial amount before conversion                        |
| initial.currency | string | The initial currency before conversion.                     |
| id               | string | The Tazapay ID of the holding foreign exchange transaction. |
