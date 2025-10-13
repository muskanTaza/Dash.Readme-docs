---
title: Collect Object
excerpt: >-
  Collects represent incoming payments to your global collection accounts. A
  collect is created whenever there is a credit in the collection accounts.
deprecated: false
hidden: false
metadata:
  robots: index
---
## Object Structure

```json Fiat Collect
{
  "amount": 12829,
  "balance_transaction": "btr_u7ftrgipu69og2qj1j1pg",
  "created_at": "2027-08-15T03:43:46.980214Z",
  "currency": "SGD",
  "destination": "cva_d2dgk0ka772psfuj1he0",
  "destination_details": {
    "type": "virtual_account",
    "virtual_account": {
      "account_holder_name": "OM Grand Limited",
      "account_number": "0109866363",
      "bank_address": {
              "address_line_1": "",
              "address_line_2": "",
              "city": "",
              "country": "Singapore",
              "postal_code": "",
              "state": ""
            },
      "bank_branch": "8 MARINA BOULEVARD, 27-01, MARINA BAY FINANCIAL CENTRE",
      "bank_codes": {
              "swift_code": "SLSGO2XXX"
            },
      "bank_name": "STANDARD BANK LIMITED",
      "currencies": [
              "SGD"
            ],
      "iban": "",
      "id": "cva_d2dgk0552psfuj1he0",
      "object": "virtual_account"
    }
  },
  "holding_currency": "SGD",
  "id": "col_d2fapsh76og2qj0ej5g",
  "metadata": {},
  "object": "collect",
  "on_behalf_of": "",
  "payer_details": {
    "additional_information": "CM Payment for Order 56",
    "name": "CMC COMPANY",
    "payer_bank": {
      "account_number": "1112019837840",
      "address": null,
      "bank_codes": {
              "swift_code": "AJUM7CHBKXXX"
            },
      "name": "C Bank"
    },
    "reference_id": ""
  },
  "status": "succeeded",
  "tracking_details": null,
  "type": "wire_transfer"
}
}
```
```json Crypto Collect
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 480000,
    "balance_transaction": "btr_d35s1lt7gtugq24427g",
    "created_at": "2025-09-18T08:20:33.090433Z",
    "currency": "USD",
    "destination": "cwa_jhrv4sad4tf55jrvp0",
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "currencies": [
          "USD"
        ],
        "deposit_address": "0x5gtj035ad25fnhioerfujhguri587y43894hfie2",
        "id": "cwa_jhrv4sad4tf55jrvp0",
        "object": "wallet",
        "type": "polygon pos"
      }
    },
    "holding_currency": "USD",
    "id": "col_24rtg5gtugq2t3h0bg",
    "metadata": {},
    "object": "collect",
    "on_behalf_of": "",
    "payer_details": {
      "additional_information": "",
      "name": "",
      "payer_bank": null,
      "payer_wallet": {
        "deposit_address": "0x48eb007deaebafmerdogn8470rjm32afa",
        "type": "ethereum"
      },
      "reference_id": ""
    },
    "status": "succeeded",
    "tracking_details": {
      "transaction_hash": "0x444b716efrg4b2a23224tf4gcedc91024f25c5bbb0530e99f09930769a"
    },
    "type": "stablecoin_usdc"
  }
}
```

<br />

# Object Parameters

## Collect

| Field               | Subfield         | Type                   | Description                                                                                                                                                                |
| ------------------- | ---------------- | ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| amount              |                  | number                 | The total amount of the collect transaction.                                                                                                                               |
| balance_transaction |                  | string                 | The ID of the balance transaction associated with this collect.                                                                                                            |
| created_at          |                  | string (ISO timestamp) | The timestamp when the collect transaction was created.                                                                                                                    |
| currency            |                  | string                 | The transaction currency (e.g., SGD).                                                                                                                                      |
| destination         |                  | string                 | The destination ID for the collected funds.                                                                                                                                |
| destination_details |                  | object                 | Details about the destination account where the funds are collected. [Destination details Object.](https://docs.tazapay.com/update/reference/destination-details-object#/) |
| holding_currency    |                  | string                 | The holding currency used for the transaction.                                                                                                                             |
| id                  |                  | string                 | The unique Tazapay identifier for the collect transaction.                                                                                                                 |
| metadata            |                  | object                 | Set of key-value pairs attached to the transaction.                                                                                                                        |
| object              |                  | string                 | The type of object, which is "collect".                                                                                                                                    |
| on_behalf_of        |                  | string                 | The party on whose behalf the funds are collected, if applicable.                                                                                                          |
| payer_details       |                  | object                 | Details about the payer who initiated the transfer. [Payer Details Object](https://docs.tazapay.com/update/reference/payer-details-object#/)                               |
| status              |                  | string                 | The current status of the collect transaction (e.g., succeeded).                                                                                                           |
| tracking_details    |                  | object                 | Tracking details for the transaction, if available.                                                                                                                        |
|                     | transaction_hash | string                 | Transaction hash for a crypto transaction                                                                                                                                  |
| type                |                  | string                 | The type of payment method used (e.g., wire_transfer).                                                                                                                     |

<br />

## Destination Details - Virtual Account

| Field               | Type   | Description                                           |
| ------------------- | ------ | ----------------------------------------------------- |
| account_holder_name | string | The name of the virtual account holder.               |
| account_number      | string | The account number for the virtual account.           |
| bank_address        | object | The bank’s address details. (See Bank Address Table). |
| bank_branch         | string | The branch address of the bank.                       |
| bank_codes          | object | The bank codes associated with the bank.              |
| bank_name           | string | The name of the bank.                                 |
| currencies          | array  | The list of currencies supported by the account.      |
| iban                | string | The IBAN of the account, if applicable.               |
| id                  | string | The unique identifier of the virtual account.         |
| object              | string | The type of object, which is "virtual_account".       |

### Bank Address

| Field          | Type   | Description                                  |
| -------------- | ------ | -------------------------------------------- |
| address_line_1 | string | The first line of the bank’s address.        |
| address_line_2 | string | The second line of the bank’s address.       |
| city           | string | The city where the bank is located.          |
| country        | string | The country where the bank is located.       |
| postal_code    | string | The postal code of the bank’s address.       |
| state          | string | The state or province of the bank’s address. |

## Destination Details - Wallet

| Field           | Type   | Description                                     |
| --------------- | ------ | ----------------------------------------------- |
| id              | string | The unique identifier of the wallet.            |
| type            | string | The blockchain or wallet type (e.g., ethereum). |
| deposit_address | string | The deposit address of the wallet.              |
| currencies      | array  | The list of currencies supported by the wallet. |

<br />

## Payer Details

| Field                  | Type   | Description                                                         |
| :--------------------- | :----- | :------------------------------------------------------------------ |
| additional_information | string | Additional information about the payment (e.g., payment reference). |
| name                   | string | Name of the payer.                                                  |
| payer_bank             | object | Payer’s bank details (See Payer Bank Table).                        |
| reference_id           | string | Reference identifier for the payer’s transaction.                   |
| payer_wallet           | object | Payer's wallet details (See Payer's wallet table)                   |

### Payer Bank

| Field          | Type        | Description                            |
| -------------- | ----------- | -------------------------------------- |
| account_number | string      | The payer’s bank account number.       |
| address        | object/null | The payer’s bank address, if provided. |
| bank_codes     | object      | The payer’s bank codes.                |
| name           | string      | The payer’s bank name.                 |

### Payer Wallet

| id              | string | The unique identifier of the wallet.            |
| --------------- | ------ | ----------------------------------------------- |
| type            | string | The blockchain or wallet type (e.g., ethereum). |
| deposit_address | string | The deposit address of the wallet.              |
