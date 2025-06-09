---
title: KYB
excerpt: 'These are the events for which webhooks will be triggered:'
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
| Event                | Description                                             | Default (on/off) |
| -------------------- | ------------------------------------------------------- | ---------------- |
| kyb.initiated        | Status of the KYB object when the KYB object is created | On               |
| kyb.submitted        | Status of the KYB object changes to submitted.          | On               |
| kyb.requires\_action | Status of the KYB object changes to requires\_action    | On               |
| kyb.approved         | Status of the KYB object changes to approved            | On               |
| kyb.rejected         | Status of the KYB object changes to rejected            | On               |

> 👍 📧 For a specific KYB object, each of the above events can be created multiple times

For KYB, the events and subsequent webhooks are based on the status updation for KYB.

### kyb.initiated

```json
{
  "type":"kyb.initiated",
  "created_at":958793503,
  "data":{
    "id":"kyb_ahfafooi7ibakbfahoan",
    "object":"kyb",
    "account":"acc_aoofhanoahgnaogoihganoagogab",
    "status":"initiated",
		......
		......//Entire KYB object
		......
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### kyb.submitted

```json
{
  "type":"kyb.submitted",
  "created_at":958793503,
  "data":{
    "id":"kyb_ahfafooi7ibakbfahoan",
    "object":"kyb",
    "status":"submitted",
    ...........
    ..........   //Entire KYB object
    ...........
  },
  "id":"evt_auigfianfdoangohuehg",
  "object":"event"
}
```

### kyb.requires\_action

```json
{
  "type":"kyb.requires_action",
  "created_at":958793503,
  "data":{
    "id":"kyb_ahfafooi7ibakbfahoan",
    "object":"kyb",
    "account":"acc_aoofhanoahgnaogoihganoagogab",
    "status":"requires_action",
    ............
    ............. //Entire KYB object
    ............
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### kyb.approved

```json
{
  "type":"kyb.approved",
  "created_at":958793503,
  "data":{
    "id":"kyb_ahfafooi7ibakbfahoan",
    "object":"kyb",
    "account":"acc_aoofhanoahgnaogoihganoagogab",
    "status":"approved",
		.............
		..........//entire KYB object
		........
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```

### kyb.rejected

```json
{
  "type":"kyb.rejected",
  "created_at":958793503,
  "data":{
    "id":"kyb_ahfafooi7ibakbfahoan",
    "object":"kyb",
    "account":"acc_aoofhanoahgnaogoihganoagogab",
    "status":"rejected",
    ............
    ............. //Entire KYB object
    ............
  },
  "id":"evt_auigfianfoangohuehg",
  "object":"event"
}
```
