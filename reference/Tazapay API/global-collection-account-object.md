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
      "account_holder_name": "testacc",
      "account_number": "testacc1234-56-1234",
      "bank_address": {
        "address_line_1": "testAdd",
        "address_line_2": "testAdd1",
        "country": "United States of America"
      },
     "bank_codes": {
        "ach_routing_number": "testRoutingNumber",
        "bank_code": "testBankCode",
        "bsb_code": "testBsbCode",
        "fedwire_routing_number": "TestFedWire",
        "routing_code": "testRoutingCode",
        "sort_code": "testSortCode",
        "swift_code": "testSwift"
      },
      "bank_branch": "testBankBranch",
      "bank_name": "testBank",
      "iban": "testIban"
    },
    "created_at": "2024-09-26T09:39:25.03501Z",
    "updated_at": "2024-09-26T09:41:43.349835Z",
    "id": "cva_crqinja9chqqs7moi8rg",
    "object": "collection_account",
    "payment_method_type": "local_bank_transfer_cad",
    "status": "disabled",
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

### collection_account

| Parameter              | Type              | Description                                                                                                                                                                                                                                                |
| ---------------------- | :---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| metadata               | json              | Set of key-value pairs attached to the collection_account object                                                                                                                                                                                           |
| virtual_account/wallet | object            | Consists of all the bank account/wallet details. Please check [virtual_account](https://docs.tazapay.com/reference/global-collection-account-object#virtual_account), [wallet](https://docs.tazapay.com/reference/global-collection-account-object#wallet) |
| created_at             | string (ISO Date) | Collection Account creation timestamp                                                                                                                                                                                                                      |
| updated_at             | string (ISO Date) | Collection account last updated timestamp                                                                                                                                                                                                                  |
| id                     | string            | Unique identifier (ID) associated with the collection_account                                                                                                                                                                                              |
| object                 | string            | Object structure name - collection_account in this case.                                                                                                                                                                                                   |
| payment_method_type    | string            | Transfer type supported for the collection account                                                                                                                                                                                                         |
| status                 | enum              | Current status of the collection account. It can either be enabled or disabled.                                                                                                                                                                            |
| currencies             | array             | List of supported currencies the collection account can receive funds in                                                                                                                                                                                   |

<br />

### virtual_account

| Parameter           | Type   | Description                                 |
| ------------------- | :----- | ------------------------------------------- |
| account_holder_name | string | Name of the account holder                  |
| account_number      | string | Account number of the collection account    |
| bank_address        | json   | Bank address of the collection account bank |
| bank_codes          | json   | Bank codes of the collection account bank   |
| bank_branch         | string | Bank branch of the collection account bank  |
| bank_name           | string | Bank name of the collection account bank    |
| iban                | string | IBAN of the collection account bank         |

<br />

### wallet

| Parameter       | Type   | Description               |
| --------------- | :----- | ------------------------- |
| type            | string | Type of wallet            |
| deposit address | string | Deposit address of wallet |