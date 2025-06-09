---
title: Global Collection Account
excerpt: These are the events for which webhooks will be triggered
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Global Collection Account status specific events

| Event                                    | Description                             | Default (On / Off) |
| :--------------------------------------- | :-------------------------------------- | :----------------- |
| collection_account.creation_succeeded    | Triggered when the status is `enabled`  | On                 |
| collection_account.disablement_succeeded | Triggered when the status is `disabled` | On                 |

## collection_account.creation_succeeded

```json json
{
  "type": "collection_account.creation_succeeded",
  "id": "evt_crqinqs584jmicmfjbhg",
  "object": "event",
  "created_at": "2024-09-26T09:39:55.369534811Z",
  "data": {
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
    "updated_at": "2024-09-26T09:39:25.03501Z",
    "id": "cva_crqinja9chqqs7moi8rg",
    "object": "collection_account",
    "payment_method_type": "local_bank_transfer_cad",
    "status": "enabled",
    "currencies": [
      "CAD"
    ]
  }
}
```

## collection_account.disablement_succeeded

```json
{
  "type": "collection_account.disablement_succeeded",
  "id": "evt_crqiom4584jmicmfjf5g",
  "object": "event",
  "created_at": "2024-09-26T09:41:44.365564104Z",
  "data": {
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
}
```

Check the collection account object parameter details here - [Global Collection Account](https://docs.tazapay.com/reference/global-collection-account-object)