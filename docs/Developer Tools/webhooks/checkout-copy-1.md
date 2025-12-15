---
title: Payin
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
## Payin Status specific events

These are the events created and triggered when the status of the payin changes. 

| Event                           | Description                                           | Default (on/off) |
| ------------------------------- | ----------------------------------------------------- | ---------------- |
| payin.requires\_payment\_method | Triggers when the status is requires\_payment\_method | On               |
| payin.requires\_action          | Triggers when the status is requires\_action          | On               |
| payin.processing                | Triggers when the status is processing                | On               |
| payin.succeeded                 | Triggers when the status is succeeded                 | On               |
| payin.cancelled                 | Triggers when the payin is cancelled                  | Off              |

## payin.requires\_payment\_method

```json json
{
  "type":"payin.requires_payment_method",
  "created_at" : "2023-12-25 21:59:59",
  "data":{
    "id":"pay_ahfafooi7fibakbfahoan",
    "object":"payin",
    "status":"requires_payment_method",
    "metadata":{},
    ......
    ...... //Entire payin object
    ........
  },
  "id":"evt_auigfiafaaaufaeoanfgohuehg",
  "object":"event"
}
```

## payin.requires\_action

```json json
{
  "type":"payin.requires_action",
  "created_at" : "2023-12-25 21:59:59",
  "data":{
    "id":"pay_ahfafooi7fibakbfahoan",
    "object":"payin",
    "status":"requires_action",
    "payment_method_details":{
      ....
      .....
    },
    "latest_payment_attempt_data":{
      ....
      ....
    },
    "metadata":{},
    ......
    ...... //Entire payin object
    ........
  },
  "id":"evt_auigfiafaaaufaeoanfgohuehg",
  "object":"event"
}
```

## payin.processing

```json json
{
  "type":"payin.processing",
  "created_at" : "2023-12-25 21:59:59",
  "data":{
    "id":"pay_ahfafooi7fibakbfahoan",
    "object":"payin",
    "status":"processing",
    "payment_method_details":{
      ....
      .....
    },
    "latest_payment_attempt_data":{
      ....
      ....
    },
    "metadata":{},
    ......
    ...... //Entire payin object
    ........
  },
  "id":"evt_auigfiafaaaufaeoanfgohuehg",
  "object":"event"
}
```

## payin.succeeded

```json json
{
  "type":"payin.succeeded",
  "created_at" : "2023-12-25 21:59:59",
  "data":{
    "id":"pay_ahfafooi7fibakbfahoan",
    "object":"payin",
    "status":"succeeded",
    "payment_method_details":{
      ....
      .....
    },
    "latest_payment_attempt_data":{
      ....
      ....
    },
    "metadata":{},
    ......
    ...... //Entire payin object
    ........
  },
  "id":"evt_auigfiafaaaufaeoanfgohuehg",
  "object":"event"
}
```

## payin.cancelled

```json json
{
  "type":"payin.cancelled",
  "created_at" : "2023-12-25 21:59:59",
  "data":{
    "id":"pay_ahfafooi7fibakbfahoan",
    "object":"payin",
    "status":"cancelled",
    "metadata":{},
    ......
    ...... //Entire payin object
    ........
  },
  "id":"evt_auigfiafaaaufaeoanfgohuehg",
  "object":"event"
}
```

## Payment\_Attempt Specific Events:

These events are created and triggered when something of interest happens for a payment attempt.

| Event                      | Description                        | Default (on/off) |
| -------------------------- | ---------------------------------- | ---------------- |
| payment\_attempt.failed    | When a payment\_attempt fails      | On               |
| payment\_attempt.succeeded | When the payment\_attempt succeeds | Off              |

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

| Event         | Description        | Default (on/off) |
| ------------- | ------------------ | ---------------- |
| payin.created | A payin is created | Off              |

### payin.created

```json json
{
  "type":"payin.created",
  "created_at" : "2023-12-25 21:59:59",
  "data":{
    "id":"pay_ahfafooi7fibakbfahoan",
    "object":"payin",
    "status":"requires_payment_method",
    "metadata":{},
    ......
    ...... //Entire payin object
    ........
  },
  "id":"evt_auigfiafaaaufaeoanfgohuehg",
  "object":"event"
}
```