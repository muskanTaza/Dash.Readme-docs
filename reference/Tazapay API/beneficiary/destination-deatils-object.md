---
title: Destination Details Object
deprecated: false
hidden: false
metadata:
  robots: index
---
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

<br />

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

<br />

### Wallet

| Subfield        | Type   | Description                                                            |
| :-------------- | :----- | :--------------------------------------------------------------------- |
| currency        | string | The cryptocurrency type (e.g., `USDC`).                                |
| deposit_address | string | The wallet deposit address.                                            |
| type            | enum   | The blockchain type. [Values: `ethereum`, `tron`, `polygon`, `solana`] |

<br />

### Local Payment Network

| Subfield    | Type   | Description                                         |
| :---------- | :----- | :-------------------------------------------------- |
| currency    | string | The currency used in the local payment network.     |
| deposit_key | string | The deposit key (e.g., PIX key in Brazil).          |
| type        | enum   | The local payment network type. [Values: `pix_brl`] |

<br />

### Tazapay Account

| Subfield        | Type   | Description                          |
| :-------------- | :----- | :----------------------------------- |
| deposit_address | string | The Tazapay account deposit address. |

<br />
