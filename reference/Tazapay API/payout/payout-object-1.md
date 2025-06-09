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

```json
{
    "amount": 100000,
    "balance_transaction": "btr_crv5u81h1l071n2fk1o0",
    "beneficiary": "bnf_crv5r71h1l071n2fjvog",
    "beneficiary_details": {
        "address": {
            "city": "test",
            "country": "US",
            "line1": "test",
            "line2": "test",
            "postal_code": "10038",
            "state": "test"
        },
        "destination": "",
        "destination_details": {
            "bank": {
                "account_number": "test",
                "account_type": "",
                "bank_codes": {
                    "aba_code": "test",
                    "swift_code": "test"
                },
                "bank_name": "city bank",
                "branch_name": "",
                "country": "US",
                "currency": "USD",
                "firc_required": false,
                "purpose_code": ""
            },
            "type": "bank"
        },
        "documents": [],
        "email": "test@example.com",
        "name": "test",
        "phone": {
            "calling_code": "1",
            "number": "12312312345"
        },
        "tax_id": "test",
        "type": "individual"
    },
    "charge_type": "ours",
    "created_at": "2024-10-03T09:08:48.467222Z",
    "currency": "USD",
    "documents": [],
    "holding_currency": "EUR",
    "holding_fx_transaction": {
        "exchange_rate": 1.059191,
        "final": {
            "amount": 100000,
            "currency": "USD"
        },
        "id": "fx_crv5u80dj96g452dfr2g",
        "initial": {
            "amount": 94411,
            "currency": "EUR"
        },
        "object": "fx_transaction"
    },
    "id": "pot_crv5u81h1l071n2fk1ng",
    "metadata": null,
    "mt103": "",
    "object": "payout",
    "payout_fx_transaction": {
        "exchange_rate": 1,
        "final": {
            "amount": 100000,
            "currency": "USD"
        },
        "id": "fx_crv5u80dj96g452dfr20",
        "initial": {
            "amount": 100000,
            "currency": "USD"
        },
        "object": "fx_transaction"
    },
    "purpose": "PYR001",
    "reference_id": "Test_Ref",
    "statement_descriptor": "tzp*Test",
    "status": "processing",
    "status_description": "",
    "tracking_details": null,
    "transaction_description": "Test Payout",
    "type": "swift"
}
```

### Payout

| Field                   | Subfield            | Type                   | Description                                                                                                                                                                                                                                                                                                                                        |
| ----------------------- | ------------------- | ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| amount                  |                     | number                 | The total amount for the payout transaction.                                                                                                                                                                                                                                                                                                       |
| balance_transaction     |                     | string                 | The Tazapay ID of the balance transaction associated with the payout.                                                                                                                                                                                                                                                                              |
| beneficiary             |                     | string                 | The Tazapay ID of the beneficiary receiving the payout.                                                                                                                                                                                                                                                                                            |
| beneficiary_details     |                     | object                 | The details of the beneficiary.                                                                                                                                                                                                                                                                                                                    |
|                         | address             | object                 | The address of the beneficiary. (See Address Table)                                                                                                                                                                                                                                                                                                |
|                         | destination         | string                 | The ID of the destination account for the payout.                                                                                                                                                                                                                                                                                                  |
|                         | destination_details | object                 | The details of the destination account. (See Destination Details Table)                                                                                                                                                                                                                                                                            |
|                         | documents           | array                  | The list of documents related to the beneficiary.                                                                                                                                                                                                                                                                                                  |
|                         | email               | string                 | The email address of the beneficiary.                                                                                                                                                                                                                                                                                                              |
|                         | name                | string                 | The name of the beneficiary.                                                                                                                                                                                                                                                                                                                       |
|                         | phone               | object                 | The phone details of the beneficiary. (See Phone Table)                                                                                                                                                                                                                                                                                            |
|                         | tax_id              | string                 | The tax identification number of the beneficiary.                                                                                                                                                                                                                                                                                                  |
|                         | type                | enum                   | The type of the beneficiary \[Values - individual, business].                                                                                                                                                                                                                                                                                      |
| charge_type             |                     | enum                   | The charge type for the payout. [Value - shared, ours]                                                                                                                                                                                                                                                                                             |
| created_at              |                     | string (ISO Timespamp) | The timestamp when the payout was created.                                                                                                                                                                                                                                                                                                         |
| currency                |                     | string                 | The currency of the payout amount.                                                                                                                                                                                                                                                                                                                 |
| documents               |                     | array                  | The list of documents related to the payout.                                                                                                                                                                                                                                                                                                       |
| holding_currency        |                     | string                 | The currency used for holding funds before payout (e.g., EUR).                                                                                                                                                                                                                                                                                     |
| holding_fx_transaction  |                     | object                 | The details of the FX transaction for holding currency. (See FX Transaction Table)                                                                                                                                                                                                                                                                 |
| id                      |                     | string                 | The unique Tazapay identifier for the payout.                                                                                                                                                                                                                                                                                                      |
| metadata                |                     | json                   | Set of key-value pairs attached to the payout.                                                                                                                                                                                                                                                                                                     |
| mt103                   |                     | string                 | The MT103 SWIFT message reference for the payout (if applicable).                                                                                                                                                                                                                                                                                  |
| object                  |                     | string                 | The type of object, which is "payout".                                                                                                                                                                                                                                                                                                             |
| payout_fx_transaction   |                     | object                 | The details of the FX transaction for payout currency. (See FX Transaction Table)                                                                                                                                                                                                                                                                  |
| purpose                 |                     | enum                   | Reason for payout. Click [here](https://docs.tazapay.com/docs/reasons-for-payout) for the detailed list. [Values - PYR001, PYR002, PYR003, PYR004, PYR005, PYR006, PYR007, PYR008, PYR009, PYR010, PYR011, PYR012, PYR013, PYR014, PYR015, PYR016, PYR017, PYR018, PYR019, PYR020, PYR021, PYR022, PYR023, PYR024, PYR025, PYR026, PYR027, PYR028] |
| reference_id            |                     | string                 | The reference ID for the payout.                                                                                                                                                                                                                                                                                                                   |
| statement_descriptor    |                     | string                 | The statement descriptor for the payout, to appear on the beneficiary’s statement.                                                                                                                                                                                                                                                                 |
| status                  |                     | enum                   | The current status of the payout [Values - Processing, Requires Approval, Requires Action, Succeeded, Failed, Cancelled]                                                                                                                                                                                                                           |
| status_description      |                     | string                 | A description of the current payout status (optional).                                                                                                                                                                                                                                                                                             |
| tracking_details        |                     | object                 | Tracking details of the payout, if applicable.                                                                                                                                                                                                                                                                                                     |
| transaction_description |                     | string                 | A description of the payout transaction.                                                                                                                                                                                                                                                                                                           |
| type                    |                     | enum                   | The type of payout [Values - local, swift, wallet]                                                                                                                                                                                                                                                                                                 |

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