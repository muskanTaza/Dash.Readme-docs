---
title: Global Collection Account
excerpt: >-
  Tazapay provides you with global collection accounts which you can share with
  your customers to receive payments in local currencies or using the SWIFT
  network. You can then withdraw the collected funds from the global collection
  accounts into the currency and bank account of your choice.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Object

### Virtual account

```
{
  "metadata": {},
  "virtual_account": {
    "account_holder_name": "John Doe",
    "account_number": "1234567890-56-7890",
    "bank_address": {
      "address_line_1": "123 Main Street",
      "address_line_2": "Suite 500",
      "country": "United States of America"
    },
    "bank_codes": {
      "ach_routing_number": "021000021",
      "bank_code": "001",
      "bsb_code": "033-001",
      "fedwire_routing_number": "021000021",
      "routing_code": "021000021",
      "sort_code": "12-34-56",
      "swift_code": "BOFAUS3N"
    },
    "bank_branch": "Downtown Branch",
    "bank_name": "Bank of America",
    "iban": "US12345678901234567890"
  },
  "created_at": "2025-06-17T10:39:25.03501Z",
  "updated_at": "2025-06-17T10:41:43.349835Z",
  "id": "cva_crqinja9chqqs7moi8rg",
  "object": "collection_account",
  "payment_method_type": "local_bank_transfer_cad",
  "status": "enabled",
  "currencies": [
    "CAD"
  ]
}

```

<br />

### Wallet

```
{
    "metadata": {},
    "wallet": {
      "type": "ethereum",
      "deposit_address": "test"
    },
    "created_at": "2024-09-19T08:07:06.576777Z",
    "updated_at": "2024-09-19T08:07:06.576777Z",
    "id": "cwa_crltnagotd3175aonav0",
    "object": "collection_account",
    "payment_method_type": "stablecoin_usdt",
    "status": "enabled",
    "currencies": [
      "USD"
    ]
  }
```

<br />

## Object Paramaters

### collection\_account

| Parameter               | Type              | Description                                                                                                                                                                                                                                                 |
| :---------------------- | :---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| metadata                | json              | Set of key-value pairs attached to the collection\_account object                                                                                                                                                                                           |
| virtual\_account/wallet | object            | Consists of all the bank account/wallet details. Please check [virtual\_account](https://docs.tazapay.com/reference/global-collection-account-object#virtual_account), [wallet](https://docs.tazapay.com/reference/global-collection-account-object#wallet) |
| created\_at             | string (ISO Date) | Collection Account creation timestamp                                                                                                                                                                                                                       |
| updated\_at             | string (ISO Date) | Collection account last updated timestamp                                                                                                                                                                                                                   |
| id                      | string            | Unique identifier (ID) associated with the collection\_account                                                                                                                                                                                              |
| object                  | string            | Object structure name - collection\_account in this case.                                                                                                                                                                                                   |
| payment\_method\_type   | enum              | Payment Method Type used for the account. Refer - [https://docs.tazapay.com/update/docs/collection-accounts-payment-method-type#/](https://docs.tazapay.com/update/docs/collection-accounts-payment-method-type#/)                                          |
| status                  | enum              | Current status of the collection account. It can either be enabled or disabled, enablement\_requested, disablement\_requested, enablement\_rejected.                                                                                                        |
| currencies              | array             | List of supported currencies the collection account can receive funds in                                                                                                                                                                                    |

<br />

### virtual\_account

| Parameter             | Type   | Description                                 |
| --------------------- | :----- | ------------------------------------------- |
| account\_holder\_name | string | Name of the account holder                  |
| account\_number       | string | Account number of the collection account    |
| bank\_address         | json   | Bank address of the collection account bank |
| bank\_codes           | json   | Bank codes of the collection account bank   |
| bank\_branch          | string | Bank branch of the collection account bank  |
| bank\_name            | string | Bank name of the collection account bank    |
| iban                  | string | IBAN of the collection account bank         |

<br />

### wallet

| Parameter       | Type   | Description               |
| --------------- | :----- | ------------------------- |
| type            | string | Type of wallet            |
| deposit address | string | Deposit address of wallet |