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
```json Local Bank Payout
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
```json Local Payment Network Payout
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 144,
    "balance_transaction": "btr_d35v6ddendp1ul1p0",
    "beneficiary": "bnf_d2pkuchg06m8tvjg",
    "beneficiary_details": {
      "address": null,
      "date_of_birth": "",
      "destination": "",
      "destination_details": {
        "local_payment_network": {
          "currency": "BRL",
          "deposit_key": "fep@gmail.com",
          "type": "pix_brl"
        },
        "type": "local_payment_network"
      },
      "documents": [],
      "email": "fep@gmail.com",
      "name": "Feete Pereira",
      "name_local": "",
      "national_identification_number": "",
      "party_classification": "",
      "phone": null,
      "registration_number": "",
      "tax_id": "3879876743",
      "type": "individual"
    },
    "charge_type": "",
    "confirmation_documents": [],
    "created_at": "2025-09-18T11:56:35.627500Z",
    "currency": "BRL",
    "destination_fx_quote": "fx_d35v6go4p2dt8ec0",
    "documents": [],
    "holding_currency": "USD",
    "holding_fx_quote": "fx_d35vfigo4p2dt8ecg",
    "holding_fx_transaction": {
      "exchange_rate": 5.158393,
      "final": {
        "amount": 144,
        "currency": "BRL"
      },
      "id": "fx_d35vfigo4p2dt8ecg",
      "initial": {
        "amount": 28,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "id": "pot_d35v6sp8dp1ul1m0",
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
        "amount": 144,
        "currency": "BRL"
      },
      "id": "fx_d35v6go4p2dt8ec0",
      "initial": {
        "amount": 144,
        "currency": "BRL"
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
      "tracking_number": "",
      "tracking_type": "utr"
    },
    "transaction_description": "",
    "type": "local_payment_network"
  }
}
```
```json Transfer Within Tazapay
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 44000,
    "balance_transaction": "btr_d35sqe74qcl8im850",
    "beneficiary": "bnf_d35spsnl8imrh3gv0",
    "beneficiary_details": {
      "address": {},
      "date_of_birth": "",
      "destination": "",
      "destination_details": {
        "tazapay_account": {
          "deposit_address": "ce4f51ue@tzp"
        },
        "type": "tazapay_account"
      },
      "documents": [],
      "email": "info@trading.com",
      "name": "T Co., Limited",
      "name_local": "",
      "national_identification_number": "",
      "party_classification": "",
      "phone": {},
      "registration_number": "",
      "tax_id": "",
      "type": "business"
    },
    "charge_type": "",
    "confirmation_documents": [],
    "created_at": "2025-09-18T09:13:28.633167Z",
    "currency": "USD",
    "destination_fx_quote": "fx_d35sqe7figo4dsvt00",
    "documents": [],
    "holding_currency": "USD",
    "holding_fx_quote": "fx_d35sfigo4p2dsvsvg",
    "holding_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 44000,
        "currency": "USD"
      },
      "id": "fx_d35sqe7figo4p2dsvsvg",
      "initial": {
        "amount": 44000,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "id": "pot_d5sqe7cl8imrh4810",
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
        "amount": 44000,
        "currency": ""
      },
      "id": "fx_d35sqe7figo4psvt00",
      "initial": {
        "amount": 44000,
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
      "tracking_number": "",
      "tracking_type": ""
    },
    "transaction_description": "Payment for goods acc 001",
    "type": "tazapay_account"
  }
}
```
```json Crypto Payout
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 122225,
    "balance_transaction": "btr_dag4eup1ekl94qrlg",
    "beneficiary": "bnf_d35eag4eupl94qrig",
    "beneficiary_details": {
      "address": {
        "city": "Vrtmore",
        "country": "JM",
        "line1": "it12 3cwth",
        "postal_code": "00000",
        "state": "Vortmore"
      },
      "date_of_birth": "2003-04-04",
      "destination": "",
      "destination_details": {
        "type": "wallet",
        "wallet": {
          "currency": "USDC",
          "deposit_address": "09e53bcac0f2edxnjsui87f8bb7a9faf64789ed8",
          "type": "ethereum"
        }
      },
      "documents": [],
      "email": "",
      "name": "Scott",
      "name_local": "",
      "national_identification_number": "",
      "party_classification": "third_party",
      "phone": {},
      "registration_number": "",
      "tax_id": "",
      "type": "individual"
    },
    "charge_type": "",
    "confirmation_documents": [],
    "created_at": "2025-09-17T16:43:44.378053Z",
    "currency": "USD",
    "destination_fx_quote": "fx_d35igo4p2drbeu0",
    "documents": [],
    "holding_currency": "USD",
    "holding_fx_quote": "fx_d35eag74p2drbeug",
    "holding_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 122225,
        "currency": "USD"
      },
      "id": "fx_d35eag74p2drbeug",
      "initial": {
        "amount": 122225,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "id": "pot_d35eag4ekl94qri0",
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
        "amount": 122225,
        "currency": "USDC"
      },
      "id": "fx_d35igo4p2drbeu0",
      "initial": {
        "amount": 122225,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "payout_quote": "",
    "purpose": "PYR030",
    "reference_id": "",
    "statement_descriptor": "",
    "status": "succeeded",
    "status_description": "",
    "tracking_details": {
      "tracking_number": "0xadef30173d3dd42333779a683c1404e50567e03fb4daef4f850f415789f559f",
      "tracking_type": "transaction_hash"
    },
    "transaction_description": "commision",
    "type": "wallet"
  }
}
```

### Payout

### Payout

| Field                       | Type   | Description                                                                                                                          |
| --------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| amount                      | number | The total amount for the payout transaction.                                                                                         |
| balance_transaction         | string | The Tazapay ID of the balance transaction associated with the payout.                                                                |
| beneficiary                 | string | The Tazapay ID of the beneficiary receiving the payout.                                                                              |
| beneficiary_details         | object | The details of the beneficiary. (See **Beneficiary Details Table**)                                                                  |
| charge_type                 | enum   | The charge type for the payout. [Values: `ours`, `shared`]                                                                           |
| confirmation_documents      | array  | The list of confirmation documents for the payout.                                                                                   |
| created_at                  | string | The timestamp when the payout was created (ISO 8601).                                                                                |
| currency                    | string | The currency of the payout amount.                                                                                                   |
| destination_fx_quote        | string | The FX quote ID used for conversion to destination currency.                                                                         |
| documents                   | array  | The list of documents related to the payout.                                                                                         |
| holding_currency            | string | The currency used for holding funds before payout.                                                                                   |
| holding_fx_quote            | string | The FX quote ID used for holding currency.                                                                                           |
| holding_fx_transaction      | object | The FX transaction details for the holding currency. (See **FX Transaction Table**)                                                  |
| id                          | string | The unique Tazapay identifier for the payout.                                                                                        |
| local.fund_transfer_network | string | The local transfer network used (if applicable).                                                                                     |
| logistics_tracking_details  | array  | The logistics tracking details if payout is linked with goods.                                                                       |
| metadata                    | object | Key-value metadata attached to the payout.                                                                                           |
| mt103                       | string | The MT103 SWIFT message reference for the payout (if applicable).                                                                    |
| object                      | string | The type of object, always `"payout"`.                                                                                               |
| on_behalf_of                | string | The account ID if the payout was made on behalf of another entity.                                                                   |
| payout_fx_transaction       | object | The FX transaction details for payout currency. (See **FX Transaction Table**)                                                       |
| payout_quote                | string | The payout quote reference (if applicable).                                                                                          |
| purpose                     | enum   | The purpose code for the payout. [Values: PYR001–PYR030]. Full list in [docs](https://docs.tazapay.com/docs/reasons-for-payout).     |
| reference_id                | string | The merchant’s reference ID for the payout.                                                                                          |
| statement_descriptor        | string | The statement descriptor that appears on the beneficiary’s bank statement.                                                           |
| status                      | enum   | The current status of the payout. [Values: `Processing`, `Requires Approval`, `Requires Action`, `Succeeded`, `Failed`, `Cancelled`] |
| status_description          | string | A description of the current payout status.                                                                                          |
| tracking_details            | object | Tracking details of the payout. (See **Tracking Details Table**)                                                                     |
| transaction_description     | string | A description of the payout transaction provided by the merchant.                                                                    |
| type                        | enum   | The type of payout. [Values: `swift`, `local`, `wallet`, `local_payment_network`, `tazapay_account`]                                 |

***

### Beneficiary Details

| Field                          | Type   | Description                                                                 |
| ------------------------------ | ------ | --------------------------------------------------------------------------- |
| address                        | object | The address of the beneficiary. (See **Address Table**)                     |
| date_of_birth                  | string | Date of birth of the beneficiary (for individuals).                         |
| destination                    | string | The destination identifier (if applicable).                                 |
| destination_details            | object | The details of the destination account. (See **Destination Details Table**) |
| documents                      | array  | The list of documents related to the beneficiary.                           |
| email                          | string | The email address of the beneficiary.                                       |
| name                           | string | The name of the beneficiary.                                                |
| name_local                     | string | The local language name of the beneficiary.                                 |
| national_identification_number | string | The national ID number of the beneficiary.                                  |
| party_classification           | string | Classification of the beneficiary (e.g., `self`, `third_party`).            |
| phone                          | object | The phone details of the beneficiary. (See **Phone Table**)                 |
| registration_number            | string | The registration number (for business beneficiaries).                       |
| tax_id                         | string | The tax identification number of the beneficiary.                           |
| type                           | enum   | The type of the beneficiary. [Values: `business`, `individual`]             |

***

### Destination Details

| Field                 | Subfield        | Type    | Description                                                                                     |
| --------------------- | --------------- | ------- | ----------------------------------------------------------------------------------------------- |
| type                  |                 | enum    | The type of destination. [Values: `bank`, `wallet`, `local_payment_network`, `tazapay_account`] |
| bank                  | account_number  | string  | The account number of the beneficiary's bank.                                                   |
|                       | account_type    | string  | The type of bank account.                                                                       |
|                       | bank_codes      | object  | The bank codes (ABA / SWIFT).                                                                   |
|                       | bank_name       | string  | The name of the beneficiary’s bank.                                                             |
|                       | branch_name     | string  | The branch name of the beneficiary’s bank.                                                      |
|                       | country         | string  | The country of the beneficiary’s bank.                                                          |
|                       | currency        | string  | The currency in which the bank account operates.                                                |
|                       | firc_required   | boolean | Whether FIRC is required.                                                                       |
|                       | purpose_code    | string  | The purpose code for the bank transfer.                                                         |
|                       | transfer_type   | string  | The transfer type (`swift`, `local`, `any`).                                                    |
|                       | iban            | string  | The IBAN of the beneficiary’s bank account.                                                     |
| wallet                | currency        | string  | The cryptocurrency type (e.g., `USDC`).                                                         |
|                       | deposit_address | string  | The wallet deposit address.                                                                     |
|                       | type            | enum    | The blockchain type. [Values: `ethereum`]                                                       |
| local_payment_network | currency        | string  | The currency used in the local payment network.                                                 |
|                       | deposit_key     | string  | The deposit key (e.g., PIX key in Brazil).                                                      |
|                       | type            | enum    | The local payment network type. [Values: `pix_brl`]                                             |
| tazapay_account       | deposit_address | string  | The Tazapay account deposit address.                                                            |

***

### Address

| Field       | Type   | Description                           |
| ----------- | ------ | ------------------------------------- |
| line1       | string | The first line of the address.        |
| line2       | string | The second line of the address.       |
| city        | string | The city of the beneficiary.          |
| state       | string | The state or province of the address. |
| postal_code | string | The postal code of the address.       |
| country     | string | The country (ISO alpha-2 format).     |

***

### Phone

| Field        | Type   | Description                           |
| ------------ | ------ | ------------------------------------- |
| calling_code | string | The country calling code of the phone |

***

### FX Transaction

| Field            | Type   | Description                              |
| ---------------- | ------ | ---------------------------------------- |
| exchange_rate    | number | The exchange rate applied for FX.        |
| final.amount     | number | The final amount after FX conversion.    |
| final.currency   | string | The currency of the final amount.        |
| initial.amount   | number | The initial amount before FX conversion. |
| initial.currency | string | The currency of the initial amount.      |
| id               | string | The FX transaction ID.                   |
| object           | string | Always `"fx_transaction"`.               |

***

### Tracking Details

| Field           | Type   | Description                                                           |
| --------------- | ------ | --------------------------------------------------------------------- |
| tracking_number | string | The tracking number (UETR, UTR, transaction hash, etc.).              |
| tracking_type   | enum   | The tracking type. [Values: `uetr`, `UTR`, `utr`, `transaction_hash`] |
