---
title: Checkout
excerpt: These are the events for which webhooks will be triggered
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Payment\_Status-specific events:

These are the events created and triggered when the payment\_status of the checkout object changes. 

| Event         | Description                                             | Default (on/off) |
| ------------- | ------------------------------------------------------- | ---------------- |
| checkout.paid | payment\_status of the checkout object changes to paid. | On               |

## checkout.paid

```json json
{
  "type":"checkout.paid",
  "created_at":958793503,
  "data":{
    "id":"chk_ahfafooi7ibakbfahoan",
    "object":"checkout",
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
    "reference_id":"55679-7657",
    "metadata":{},
    ......
    ...... //Entire checkout object
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
| payment\_attempt.processing | When the payment\_attempt moves to the processing state | Off              |
| payment\_attempt.succeeded  | When the payment\_attempt succeeds                      | On               |

### payment\_attempt.created

```Text JSON
{
  "type":"payment_attempt.requires_action",
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

```json json
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

```json json
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

```json json
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

These events are created and triggered when something interesting happens with the checkout object not related to a status change.

| Event                            | Description                                    | Default (on/off) |
| -------------------------------- | ---------------------------------------------- | ---------------- |
| checkout.created                 | A checkout object is created                   | Off              |
| checkout.expired                 | An active checkout object gets expired         | On               |
| checkout.tax\_invoice\_generated | Triggered when Tazapay generates a tax invoice | On               |

### checkout.created

```json json
{
  "type":"checkout.created",
  "created_at":958793503,
  "data":{
    "id":"chk_ahfafooi7ibakbfahoan",
    "object":"checkout",
    "payin":"pay_aohfoahnofanofna",
    .....
    ..... //Entire Checkout object
    .....
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### checkout.expired

```json json
{
  "type":"checkout.expired",
  "created_at":958793503,
  "data":{
    "id":"chk_ahfafooi7ibakbfahoan",
    "object":"checkout",
    "payin" : "pay_aofnoianfoanfnafn",
    ....
    .... //Entire checkout object
    ....
  }  
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### checkout.tax\_invoice\_generated

```Text json
{
  "type":"checkout.tax_invoice_generated",
  "created_at":"2024-04-01T08:04:47.649905272Z",
  "data":{
    "id":"chk_ahfafooi7ibakbfahoan",
    "object":"checkout",
    "payin" : "pay_aofnoianfoanfnafn",
    "payment_status":"paid",
    "transaction_documents":[
 		 {
    	"type":"tax_invoice",
   	  "url": "https://transacion.tazapay.com/invoice/download/invoiceDownload?U2FsdGVkX1/TvmUkxGLBYS/vAmk7l7wuzs2poo/pLQjjbITj8mVX0siR7guU3zA7goWnX3hLmWc2gtNdCoQv0g=="
  	 }
		],
    ....
    .... //Entire checkout object
    ....
  }  
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```