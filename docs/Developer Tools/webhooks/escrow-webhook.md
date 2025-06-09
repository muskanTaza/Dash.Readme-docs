---
title: Escrow
excerpt: 'These are the events for which webhooks will be triggered:'
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Payment\_Status-specific events:

These are the events created and triggered when the status of the escrow object is impacted.

| Event        | Description                                           | Default (on/off) |
| ------------ | ----------------------------------------------------- | ---------------- |
| escrow\.paid | payment\_status of the escrow object changes to paid. | On               |

### escrow\.paid

```json JSON
{
  "type":"escrow.paid",
  "created_at":958793503,
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin":"pay_bfiuafuiafianifnao",
    "created_at":7942792,
    "expiry_at":7967893,
    "status":"expired",
    "payment_status":"paid",
    "invoice_currency":"usd",
    "amount":"6700",
    "customer_details":{
      "country":"US",
      "email":"singapore@tazapay.com",
      "name":"Adam Smith",
      "phone":{
        "country_code":"65",
        "number":"67894321"
      }
    },
    "transaction_description":"1 x Item",
    "partner_reference":"55679-7657",
    "metadata":{},
    ......
    ...... //Entire escrow object
    ........
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### escrow\.unpaid

```json
{
  "type":"escrow.unpaid",
  "created_at":95879350,
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin":"pay_bfiuafuiafianifnao",
    "created_at":7942792,
    "expiry_at":7967893,
    "status":"expired",
    "payment_status":"unpaid",
    "invoice_currency":"usd",
    "amount":"6700",
    "customer_details":{
      "country":"US",
      "email":"singapore@tazapay.com",
      "name":"Adam Smith",
      "phone":{
        "country_code":"65",
        "number":"67894321"
      }
    },
    "transaction_description":"1 x Item",
    "partner_reference":"55679-7657",
    "metadata":{},
    ......
    ...... //Entire escrow object
    ........
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

## Payment\_Attempt Specific Events:

These events are created and triggered when something of interest happens for a payment attempt of a checkout.

| Event                       | Description                                             | Default (on/off) |
| --------------------------- | ------------------------------------------------------- | ---------------- |
| payment\_attempt.created    | When a payment\_attempt is created for the checkout     | On               |
| payment\_attempt.failed     | When a payment\_attempt fails for the checkout          | On               |
| payment\_attempt.processing | When the payment\_attempt moves to the processing state | On               |
| payment\_attempt.succeeded  | When the payment\_attempt succeeds                      | On               |

### payment\_attempt.created

```json
{
  "type":"payment_attempt.created",
  "created_at":958793503,
  "data":{
    "id":"pat_ahfafooi7ibakbfahoan",
    "object":"payment_attempt",
    "payin":"pay_bfiuafuiafianifnao",
    "created_at":7942792,
    ....
    .... ///Entire payment_attempt object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### payment\_attempt.failed

```json
{
  "type":"payment_attempt.failed",
  "created_at":958793503,
  "data":{
    "id":"pat_ahfafooi7ibakbfahoan",
    "object":"payment_attempt",
    "payin":"pay_bfiuafuiafianifnao",
    "created_at":7942792,
    ....
    .... ///Entire payment_attempt object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### payment\_attempt.processing

```json
{
  "type":"payment_attempt.processing",
  "created_at":958793503,
  "data":{
    "id":"pat_ahfafooi7ibakbfahoan",
    "object":"payment_attempt",
    "payin":"pay_bfiuafuiafianifnao",
    "created_at":7942792,
    ....
    .... ///Entire payment_attempt object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### payment\_attempt.succeeded

```json
{
  "type":"payment_attempt.succeeded",
  "created_at":958793503,
  "data":{
    "id":"pat_ahfafooi7ibakbfahoan",
    "object":"payment_attempt",
    "payin":"pay_bfiuafuiafianifnao",
    "created_at":7942792,
    ....
    .... ///Entire payment_attempt object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

## Other Events:

These events are created and triggered when something interesting happens with the escrow object not related to a status change.

| Event                           | Description                                 | Default (on/off) |
| ------------------------------- | ------------------------------------------- | ---------------- |
| escrow\.created                 | A escrow object is created                  | Off              |
| escrow\.expired                 | An active escrow object gets expired        | On               |
| escrow\.tax\_invoice\_generated | Triggered when Tazapay generates an invoice | On               |

### escrow\.created

```json
{
  "type":"escrow.created",
  "created_at":958793503,
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin":"pay_aohfoahnofanofna",
    .....
    ..... //Entire escrow object
    .....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### escrow\.expired

```json
{
  "type":"escrow.expired",
  "created_at":958793503,
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin" : "pay_aofnoianfoanfnafn",
    ....
    .... //Entire escrow object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### escrow\.tax\_invoice\_generated

```Text json
{
  "type":"escrow.tax_invoice_generated",
  "created_at":"2024-04-01T08:04:47.649905272Z",
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin" : "esc_ahfafooi7ibakbfahoan",
    "payment_status":"paid",
    "transaction_documents":[
 		 {
    	"type":"tax_invoice",
   	  "url": "https://transacion.tazapay.com/invoice/download/invoiceDownload?U2FsdGVkX1/TvmUkxGLBYS/vAmk7l7wuzs2poo/pLQjjbITj8mVX0siR7guU3zA7goWnX3hLmWc2gtNdCoQv0g=="
  	 }
		],
    ....
    .... //Entire escrow object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

<br>

## Document Verification Events:

These are the events created and triggered when documents for the escrow needs to be uploaded by the merchant. The merchant uploads the document(s) either through the document API or from the dashboard.

| Event                                 | Description (Triggered when)                                                                                                         | Default (on/off) |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ---------------- |
| escrow\.verification.processing       | The verification\_status of the release document changes to processing                                                               | On               |
| escrow\.verification.requires\_action | The verification\_status of the release document changes to requires\_action. This also contains the details of the action required. | On               |
| escrow\.verification.succeeded        | The verification\_status of the release document changes to verified                                                                 | On               |
| escrow\.verification.failed           | The verification\_status of the release document changes to failed                                                                   | On               |

### escrow\.verification.requires\_action

```json
{
  "type":"escrow.verification.requires_action",
  "created_at":958793503,
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin" : "pay_aofnoianfoanfnafn",
    ....
    .... //Entire escrow object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### escrow\.verification.processing

```json
{
  "type":"escrow.verification.processing",
  "created_at":958793503,
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin" : "pay_aofnoianfoanfnafn",
    ....
    .... //Entire escrow object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### escrow\.verification.succeeded

```json
{
  "type":"escrow.verification.succeeded",
  "created_at":958793503,
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin" : "pay_aofnoianfoanfnafn",
    ....
    .... //Entire escrow object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### escrow\.verification.failed

```json
{
  "type":"escrow.verification.failed",
  "created_at":958793503,
  "data":{
    "id":"esc_ahfafooi7ibakbfahoan",
    "object":"escrow",
    "payin" : "pay_aofnoianfoanfnafn",
    ....
    .... //Entire escrow object
    ....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```