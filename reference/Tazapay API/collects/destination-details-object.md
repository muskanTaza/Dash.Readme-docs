---
title: Destination Details Object
deprecated: false
hidden: false
metadata:
  robots: index
---
## Object Structure

```json Virtual Account
{
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
}
```
```json Wallet
{
  "currencies": [
    "USD"
  ],
  "deposit_address": "0x5gtj035ad25fnhioerfujhguri587y43894hfie2",
  "id": "cwa_jhrv4sad4tf55jrvp0",
  "object": "wallet",
  "type": "polygon pos"
}
```

<br />

## Virtual Account

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

<br />

### Bank Address

| Field          | Type   | Description                                  |
| -------------- | ------ | -------------------------------------------- |
| address_line_1 | string | The first line of the bank’s address.        |
| address_line_2 | string | The second line of the bank’s address.       |
| city           | string | The city where the bank is located.          |
| country        | string | The country where the bank is located.       |
| postal_code    | string | The postal code of the bank’s address.       |
| state          | string | The state or province of the bank’s address. |

<br />

## Wallet

| Field           | Type   | Description                                     |
| --------------- | ------ | ----------------------------------------------- |
| id              | string | The unique identifier of the wallet.            |
| type            | string | The blockchain or wallet type (e.g., ethereum). |
| deposit_address | string | The deposit address of the wallet.              |
| currencies      | array  | The list of currencies supported by the wallet. |

<br />

<br />
