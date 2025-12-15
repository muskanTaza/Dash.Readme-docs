---
title: Beneficiary
excerpt: ''
deprecated: false
hidden: false
icon: far fa-hospital-user
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Beneficiary

## Object Structure

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
  "nationality": "IN",
  "destination": "wal_d3inm6ami8u10oqfk",
  "destination_details": {
        "type": "wallet",
        "wallet": {
          "currency": "USDC",
          "deposit_address": "09e53bcac0f2edxnjsui87f8bb7a9faf64789ed8",
          "type": "ethereum",
          "hosted": "no"
        }
      },
  "documents": [],
  "email": "abc@gmail.com",
  "name": "Scott",
  "name_local": "स्कॉट",
  "national_identification_number": "AIDPK1234M",
  "party_classification": "third_party",
  "phone": {
    "calling_code": "91",
    "number": "9231231231"
  },
  "registration_number": "",
  "tax_id": "29ABCDE1234F1Z5",
  "type": "individual",
  "is_doc_verification_required": true,
  "status": "active",
  "verification_status": "succeeded"
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
  "destination": "bnk_d05lmjuq59csbboqt9d0",
  "destination_details": {
        "bank": {
          "account_number": "DE535019045650474185",
          "account_type": "savings",
          "bank_codes": {
            "swift_code": "FBDEFF"
          },
          "bank_name": "ER VOLKSBANK EG",
          "branch_name": "Frankfurt am Main",
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
  "email": "finance@gmbh-company.de",
  "nationality": "DE",
  "name": "GMBH",
  "name_local": "",
  "national_identification_number": "",
  "party_classification": "third_party",
  "phone": {
    "calling_code": "49",
    "number": "9231231231"
  },
  "registration_number": "HRB 123456",
  "tax_id": "DE123456789",
  "type": "business",
  "is_doc_verification_required": false,
  "status": "active",
  "verification_status": "succeeded"
}
```

### Beneficiary Details

| Field                          | Type                   | Description                                                                                                                                       |
| :----------------------------- | :--------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------ |
| id                             | string                 | The unique Tazapay identifier for the beneficiary.                                                                                                |
| address                        | object                 | The address of the beneficiary. **[Address Object](https://docs.tazapay.com/update/reference/address-object#/)**                                  |
| date_of_birth                  | string                 | Date of birth of the beneficiary (for individuals).                                                                                               |
| nationality                    | string                 | ISO 3166-1 alpha-2 country code representing the beneficiary's nationality (e.g., US, GB, IN, FR). Optional field used for enhanced compliance screening. |
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
| is_doc_verification_required   | boolean                | Indicates if document verification is required for this beneficiary. Applicable for wallet beneficiaries.                                         |
| status                         | enum                   | Current status of the beneficiary. Possible values: `active`, `inactive`                                                                          |
| verification_status            | enum                   | Document verification status for wallet beneficiaries. Possible values: `processing`, `requires_action`, `succeeded`, `failed`                   |

<br />

# Destination Details

## Object Structure

```json Wallet
{
  "type": "wallet",
    "wallet": {
            "currency": "USDC",
            "deposit_address": "09e53bcac0f2edxnjsui87f8bb7a9faf64789ed8",
             "type": "ethereum",
             "hosted": "yes",
             "vasp_name": "Binance",
             "vasp_website": "https://www.binance.com"
    }
}
```
```json Bank
{
  "bank": {
    "account_number": "DE535019045650474185",
    "account_type": "savings",
    "bank_codes": {
            "swift_code": "FBDEFF"
          },
    "bank_name": "ER VOLKSBANK EG",
    "branch_name": "Frankfurt am Main",
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
          "deposit_key_type": "email",
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

| Subfield        | Type   | Description                                                                                                                                                                                                                                                                                           |
| :-------------- | :----- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| currency        | string | The cryptocurrency type (e.g., `USDC`).                                                                                                                                                                                                                                                               |
| deposit_address | string | The wallet deposit address.                                                                                                                                                                                                                                                                           |
| type            | enum   | The blockchain type. [Values: `ethereum`, `tron`, `polygon`, `solana`]                                                                                                                                                                                                                                |
| hosted          | enum   | Indicates whether the wallet is custodial (hosted) or non-custodial (unhosted). Possible values: `yes` – The wallet is hosted by a Virtual Asset Service Provider (VASP) or exchange. `no` – The wallet is non-custodial and controlled directly by the user (e.g., MetaMask, Ledger). Mandatory if `party_classification` is 'self' and `destination_details.type` is 'wallet'. |
| vasp_name       | string | The registered name of the Virtual Asset Service Provider (VASP) or exchange that hosts or manages the wallet. Mandatory if `party_classification` is 'self', `destination_details.type` is 'wallet' and `hosted` is 'yes'                                                                            |
| vasp_website    | string | The official website URL of the VASP or exchange that manages the wallet. Used for VASP identification and due diligence under Travel Rule requirements. Mandatory if `party_classification` is 'self', `destination_details.type` is 'wallet' and `hosted` is 'yes'                                  |

### Local Payment Network

| Subfield         | Type   | Description                                                                                  |
| :--------------- | :----- | :------------------------------------------------------------------------------------------- |
| currency         | string | The currency used in the local payment network.                                              |
| deposit_key      | string | The deposit key corresponding to the type of local payment network (e.g., PIX key, UPI handle). |
| deposit_key_type | enum   | Type of the deposit key. Conditionally mandatory depending on the value of type              |
| type             | enum   | The local payment network type. [Values: `pix_brl`, `upi_inr`, `promptpay_thb`]             |

### Tazapay Account

| Subfield        | Type   | Description                          |
| :-------------- | :----- | :----------------------------------- |
| deposit_address | string | The Tazapay account deposit address. |
