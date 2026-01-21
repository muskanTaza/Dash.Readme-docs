---
title: Collect
excerpt: Following are the collect events for which you will receive webhooks
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Collect status specific events

| Event               | Description                                | Default (On / Off) |
| :------------------ | :----------------------------------------- | :----------------- |
| collect.succeeded   | Triggered when the status is `succeeded`   | On                 |
| collect.failed      | Triggered when the status is `failed`      | On                 |
| collect.on\_hold    | Triggered when the status is `on_hold`     | On                 |
| collect.created     | Triggered when the status is `created`     | On                 |
| collect.broadcasted | Triggered when the status is `broadcasted` | On                 |

## collect.succeeded

### Virtual Account

```Text JSON
{
  "type": "collect.succeeded",
  "id": "evt_cn1m86nnt3hkq7385qd0",
  "object": "event",
  "created_at": "2024-02-07T11:06:02.538953779Z",
  "data": {
    "metadata": {},
    "created_at": "2024-02-07T11:06:00.421853Z",
    "payer_details": {
      "name": "Hrithik Agarwal",
      "payer_bank": {
        "account_number":"9876542321",
        "name":"State Bank of Mars",
        "address":{
          "line1":"Address Line 1",
          "line2":"Address Line 2",
          "city":"City",
          "state":"state",
          "country":"country",
          "postal_code":"postal code"
        },
        "bank_codes":{
          "swift_code":"SBM001"
        }
      },
      "reference_id": "reffffff",
      "additional_information": "Additional Information for the transaction"
    },
    "id": "col_cn1m8651ed8dn2517esg",
    "object": "collect",
    "currency": "USD",
    "status": "succeeded",
    "type": "wire_transfer",
    "destination": "cca_uafanfianknon792nfak",
    "amount": 100000
  }
}
```

### Wallet

```
{
  "type": "collect.succeeded",
  "id": "evt_cus736u228ka51i3g0pg",
  "object": "event",
  "created_at": "2025-02-21T12:29:15.4554149Z",
  "data": {
    "id": "col_cus735e5ainf6ati9dlg",
    "object": "collect",
    "amount": 1000,
    "currency": "USD",
    "status": "succeeded",
    "type": "stablecoin_usdc",
    "payer_details": {
      "name": "",
      "payer_bank": null,
      "reference_id": "",
      "additional_information": "",
      "payer_wallet": {
        "type": "Ethereum",
        "deposit_address": "addrss23423423"
      }
    },
    "destination": "cwa_cuivfrvkk61qlul7c8g0",
    "metadata": {},
    "created_at": "2025-02-21T12:29:09.412049Z",
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "id": "cwa_cuivfrvkk61qlul7c8g0",
        "object": "wallet",
        "type": "ethereum",
        "deposit_address": "wead",
        "currencies": [
          "USD"
        ]
      }
    },
    "holding_currency": "USD",
    "balance_transaction": "btr_cus736u5ainf6ati9edg",
    "on_behalf_of": "",
    "tracking_details": {
      "transaction_hash": "fhjkdfi9823720@#"
    }
  }
}
```

## collect.failed

### Virtual Account

```Text JSON
{
  "type": "collect.failed",
  "id": "evt_cn1m86nnt3jbkq7385qd0",
  "object": "event",
  "created_at": "2024-02-07T11:06:02.538953779Z",
  "data": {
    "metadata": {},
    "created_at": "2024-02-07T11:06:00.421853Z",
    "payer_details": {
      "name": "Hrithik Agarwal",
      "payer_bank": {
        "account_number":"9876542321",
        "name":"State Bank of Mars",
        "address":{
          "line1":"Address Line 1",
          "line2":"Address Line 2",
          "city":"City",
          "state":"state",
          "country":"country",
          "postal_code":"postal code"
        },
        "bank_codes":{
          "swift_code":"SBM001"
        }
      },
      "reference_id": "reffffff",
      "additional_information": "Additional Information for the transaction"
    },
    "id": "col_cn1m8651ed8dn2517esg",
    "object": "collect",
    "currency": "USD",
    "status": "failed",
    "type": "wire_transfer",
    "destination": "cca_uafanfianknon792nfak",
    "amount": 100000
  }
}
```

### Wallet

```
{
  "type": "collect.failed",
  "id": "evt_cus74j6228ka51i3glog",
  "object": "event",
  "created_at": "2025-02-21T12:32:12.288984183Z",
  "data": {
    "id": "col_cus74hm5ainf6atiabs0",
    "object": "collect",
    "amount": 1000,
    "currency": "USD",
    "status": "failed",
    "type": "stablecoin_usdt",
    "payer_details": {
      "name": "",
      "payer_bank": null,
      "reference_id": "",
      "additional_information": "",
      "payer_wallet": {
        "type": "Ethereum",
        "deposit_address": "addrss23423423"
      }
    },
    "destination": "cwa_crltnagotd3175aonav0",
    "metadata": {},
    "created_at": "2025-02-21T12:32:06.212490Z",
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "id": "cwa_crltnagotd3175aonav0",
        "object": "wallet",
        "type": "ethereum",
        "deposit_address": "test",
        "currencies": [
          "USD"
        ]
      }
    },
    "holding_currency": "USD",
    "balance_transaction": "",
    "on_behalf_of": "",
    "tracking_details": {
      "transaction_hash": "fhjkdfi9823720@#"
    }
  }
}
```

## collect.on\_hold

### Virtual Account

```Text JSON
{
  "type": "collect.on_hold",
  "id": "evt_cn1m86nnt3jbkq7385qd0",
  "object": "event",
  "created_at": "2024-02-07T11:06:02.538953779Z",
  "data": {
    "metadata": {},
    "created_at": "2024-02-07T11:06:00.421853Z",
    "payer_details": {
      "name": "Hrithik Agarwal",
      "payer_bank": {
        "account_number":"9876542321",
        "name":"State Bank of Mars",
        "address":{
          "line1":"Address Line 1",
          "line2":"Address Line 2",
          "city":"City",
          "state":"state",
          "country":"country",
          "postal_code":"postal code"
        },
        "bank_codes":{
          "swift_code":"SBM001"
        }
      },
      "reference_id": "reffffff",
      "additional_information": "Additional Information for the transaction"
    },
    "id": "col_cn1m8651ed8dn2517esg",
    "object": "collect",
    "currency": "USD",
    "status": "on_hold",
    "type": "wire_transfer",
    "destination": "cca_uafanfianknon792nfak",
    "amount": 100000
  }
}
```

### Wallet

```
{
  "type": "collect.on_hold",
  "id": "evt_cus74bm228ka51i3gihg",
  "object": "event",
  "created_at": "2025-02-21T12:31:42.609555864Z",
  "data": {
    "id": "col_cus74a65ainf6atia7m0",
    "object": "collect",
    "amount": 1000,
    "currency": "USD",
    "status": "on_hold",
    "type": "stablecoin_usdc",
    "payer_details": {
      "name": "",
      "payer_bank": null,
      "reference_id": "",
      "additional_information": "",
      "payer_wallet": {
        "type": "Ethereum",
        "deposit_address": "addrss23423423"
      }
    },
    "destination": "cwa_cuivfrvkk61qlul7c8g0",
    "metadata": {},
    "created_at": "2025-02-21T12:31:36.335350Z",
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "id": "cwa_cuivfrvkk61qlul7c8g0",
        "object": "wallet",
        "type": "ethereum",
        "deposit_address": "wead",
        "currencies": [
          "USD"
        ]
      }
    },
    "holding_currency": "USD",
    "balance_transaction": "",
    "on_behalf_of": "",
    "tracking_details": {
      "transaction_hash": "fhjkdfi9823720@#"
    }
  }
}
```

# Other Events

| Event               | Description                                | Default (On / Off) |
| :------------------ | :----------------------------------------- | :----------------- |
| collect.created     | Triggered when the status is `created`     | On                 |
| collect.broadcasted | Triggered when the status is `broadcasted` | On                 |

## collect.created

### Wallet

```
{
  "type": "collect.created",
  "id": "evt_cus736u228ka51i3g0pg",
  "object": "event",
  "created_at": "2025-02-21T12:29:15.4554149Z",
  "data": {
    "id": "col_cus735e5ainf6ati9dlg",
    "object": "collect",
    "amount": 1000,
    "currency": "USD",
    "status": "created",
    "type": "stablecoin_usdc",
    "payer_details": {
      "name": "",
      "payer_bank": null,
      "reference_id": "",
      "additional_information": "",
      "payer_wallet": {
        "type": "Ethereum",
        "deposit_address": "addrss23423423"
      }
    },
    "destination": "cwa_cuivfrvkk61qlul7c8g0",
    "metadata": {},
    "created_at": "2025-02-21T12:29:09.412049Z",
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "id": "cwa_cuivfrvkk61qlul7c8g0",
        "object": "wallet",
        "type": "ethereum",
        "deposit_address": "wead",
        "currencies": [
          "USD"
        ]
      }
    },
    "holding_currency": "USD",
    "balance_transaction": "btr_cus736u5ainf6ati9edg",
    "on_behalf_of": "",
    "tracking_details": {
      "transaction_hash": "fhjkdfi9823720@#"
    }
  }
}
```

## collect.broadcasted

### Wallet

```
{
  "type": "collect.broadcasted",
  "id": "evt_cus736u228ka51i3g0pg",
  "object": "event",
  "created_at": "2025-02-21T12:29:15.4554149Z",
  "data": {
    "id": "col_cus735e5ainf6ati9dlg",
    "object": "collect",
    "amount": 1000,
    "currency": "USD",
    "status": "broadcasted",
    "type": "stablecoin_usdc",
    "payer_details": {
      "name": "",
      "payer_bank": null,
      "reference_id": "",
      "additional_information": "",
      "payer_wallet": {
        "type": "Ethereum",
        "deposit_address": "addrss23423423"
      }
    },
    "destination": "cwa_cuivfrvkk61qlul7c8g0",
    "metadata": {},
    "created_at": "2025-02-21T12:29:09.412049Z",
    "destination_details": {
      "type": "wallet",
      "wallet": {
        "id": "cwa_cuivfrvkk61qlul7c8g0",
        "object": "wallet",
        "type": "ethereum",
        "deposit_address": "wead",
        "currencies": [
          "USD"
        ]
      }
    },
    "holding_currency": "USD",
    "balance_transaction": "btr_cus736u5ainf6ati9edg",
    "on_behalf_of": "",
    "tracking_details": {
      "transaction_hash": "fhjkdfi9823720@#"
    }
  }
}
```