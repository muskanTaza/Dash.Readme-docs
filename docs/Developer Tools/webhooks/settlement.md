---
title: Settlement
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
## Related Links

* [Settlement Object](https://docs.tazapay.com/docs/settlements)

## Settlement Status Specific Events:

These are the events created and triggered when the status of the settlement object changes.

| Event                 | Description                                                                                                                         | Default (on/off) |
| :-------------------- | :---------------------------------------------------------------------------------------------------------------------------------- | :--------------- |
| settlement.created    | When the settlement is created                                                                                                      | Off              |
| settlement.processing | When the settlement is initiated from Tazapay                                                                                       | Off              |
| settlement.succeeded  | When the settlement reaches the destination bank account (using local rails) or is initiated from Tazapay (using the SWIFT network) | Off              |
| settlement.failed     | When a settlement fails                                                                                                             | Off              |

### settlement.created

```Text JSON
{
  "type":"settlement.failed",
  "created_at":"2025-04-29T12:34:56+05:30",
  "data":{
    "id":"stl_ahfafooi7ibakbfahoan",
    "object":"settlement",
    "created_at":"2025-04-29T12:34:56+05:30",
    ......
    ...... //Entire settlement object
    ........
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### settlement.processing

```Text JSON
{
  "type":"settlement.failed",
  "created_at":"2025-04-29T12:34:56+05:30",
  "data":{
    "id":"stl_ahfafooi7ibakbfahoan",
    "object":"settlement",
    "created_at":"2025-04-29T12:34:56+05:30",
    ......
    ...... //Entire settlement object
    ........
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### settlement.succeeded

```json
{
  "type":"settlement.succeeded",
  "created_at":"2025-04-29T12:34:56+05:30",
  "data":{
    "id":"stl_ahfafooi7ibakbfahoan",
    "object":"settlement",
    "created_at":"2025-04-29T12:34:56+05:30",
    ......
    ...... //Entire settlement object
    ........
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### settlement.failed

```json
{
  "type":"settlement.failed",
  "created_at":"2025-04-29T12:34:56+05:30",
  "data":{
    "id":"stl_ahfafooi7ibakbfahoan",
    "object":"settlement",
    "created_at":"2025-04-29T12:34:56+05:30",
    ......
    ...... //Entire settlement object
    ........
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```