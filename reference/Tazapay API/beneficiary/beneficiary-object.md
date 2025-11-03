---
title: Beneficiary Object
excerpt: >-
  The Tazapay Beneficiary Object represents the recipient of a payment or payout
  within the Tazapay platform. This object holds all relevant information about
  the beneficiary, including personal details, bank account information, and any
  other relevant metadata required for processing payments to them.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Parameters

```json Individual
{
  "address": {
        "city": "Vijay",
        "country": "IN",
        "line1": "street 30th",
        "postal_code": "110018",
        "state": "Delhi"
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
  "email": "abc@gmail.com",
  "name": "Scott",
  "name_local": "",
  "national_identification_number": "",
  "party_classification": "third_party",
  "phone": {
    "calling_code": "91",
    "number": "9231231231"
  },
  "registration_number": "",
  "tax_id": "",
  "type": "individual"
}
```
```json Business
{
  "address": {
        "city": "Vrtmore",
        "country": "JM",
        "line1": "it12 3cwth",
        "postal_code": "00000",
        "state": "Vortmore"
  },
  "destination": "",
  "destination_details": {
        "bank": {
          "account_type": "savings",
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
    "calling_code": "49",
    "number": "9231231231"
  },
  "registration_number": "",
  "tax_id": "",
  "type": "business"
},
```

<br />

### Beneficiary Details

| Field                          | Type                   | Description                                                                                                                                       |
| :----------------------------- | :--------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------ |
| id                             | string                 | The unique Tazapay identifier for the beneficiary.                                                                                                |
| address                        | object                 | The address of the beneficiary. **[Address Object](https://docs.tazapay.com/update/reference/address-object#/)**                                  |
| date_of_birth                  | string                 | Date of birth of the beneficiary (for individuals).                                                                                               |
| destination                    | string                 | The destination identifier (if applicable).                                                                                                       |
| destination_details            | object                 | The details of the destination account. (**[Destination Details Object](https://docs.tazapay.com/update/reference/destination-deatils-object/)**) |
| documents                      | array                  | The list of documents related to the beneficiary.                                                                                                 |
| email                          | string                 | The email address of the beneficiary.                                                                                                             |
| name                           | string                 | The name of the beneficiary.                                                                                                                      |
| name_local                     | string                 | The local language name of the beneficiary.                                                                                                       |
| national_identification_number | string                 | The national ID number of the beneficiary.                                                                                                        |
| party_classification           | enum                   | Classification of the beneficiary (Possible values -  `self`, `third_party`).                                                                     |
| phone                          | object                 | The phone details of the beneficiary. (**[Phone Object](https://docs.tazapay.com/update/reference/phone-object/)**)                               |
| registration_number            | string                 | The registration number (for business beneficiaries).                                                                                             |
| tax_id                         | string                 | The tax identification number of the beneficiary.                                                                                                 |
| created_at                     | string (ISO timestamp) | The date and time when the beneficiary was created.                                                                                               |
| metadata                       | json                   | Additional  key-value pairs associated with the beneficiary (optional).                                                                           |

# Destination Details

## Object Structure

```json Wallet
{
  "type": "wallet",
    "wallet": {
            "currency": "USDC",
            "deposit_address": "09e53bcac0f2edxnjsui87f8bb7a9faf64789ed8",
             "type": "ethereum"
    }
}
```
```json Bank
{
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
}
```
```json Local Payment Network
{
  "local_payment_network": {
          "currency": "BRL",
          "deposit_key": "fep@gmail.com",
          "type": "pix_brl"
  },
  "type": "local_payment_network"
}
```
```json Tazapay Account
{
  "tazapay_account": {
    "deposit_address": "ce4f51ue@tzp"
  },
    "type": "tazapay_account"
}
```

## Object Parameters

### Bank

| Subfield       | Type    | Description                                                             |
| -------------- | ------- | ----------------------------------------------------------------------- |
| account_number | string  | The account number of the beneficiary's bank.                           |
| account_type   | enum    | The type of bank account. Enum value - `savings`, `checking`, `payment` |
| bank_codes     | object  | The bank codes (ABA / SWIFT).                                           |
| bank_name      | string  | The name of the beneficiary’s bank.                                     |
| branch_name    | string  | The branch name of the beneficiary’s bank.                              |
| country        | string  | The country of the beneficiary’s bank.                                  |
| currency       | string  | The currency in which the bank account operates.                        |
| firc_required  | boolean | Whether FIRC is required.                                               |
| purpose_code   | string  | The purpose code for the bank transfer.                                 |
| transfer_type  | enum    | The transfer type (values - `swift`, `local`, `any`).                   |
| iban           | string  | The IBAN of the beneficiary’s bank account.                             |

### Wallet

| Subfield        | Type   | Description                                                            |
| :-------------- | :----- | :--------------------------------------------------------------------- |
| currency        | string | The cryptocurrency type (e.g., `USDC`).                                |
| deposit_address | string | The wallet deposit address.                                            |
| type            | enum   | The blockchain type. [Values: `ethereum`, `tron`, `polygon`, `solana`] |

### Local Payment Network

| Subfield    | Type   | Description                                         |
| :---------- | :----- | :-------------------------------------------------- |
| currency    | string | The currency used in the local payment network.     |
| deposit_key | string | The deposit key (e.g., PIX key in Brazil).          |
| type        | enum   | The local payment network type. [Values: `pix_brl`] |

### Tazapay Account

| Subfield        | Type   | Description                          |
| :-------------- | :----- | :----------------------------------- |
| deposit_address | string | The Tazapay account deposit address. |
