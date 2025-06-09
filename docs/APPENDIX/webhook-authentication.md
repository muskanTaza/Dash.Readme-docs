---
title: Webhook Authentication
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
At Tazapay, we want to ensure that every webhook sent to our merchants is authentic and unaltered. Each webhook request header includes a signature generated using the event ID, payload, and timestamp.

Because the signature is tied to the payload, any tampering invalidates the signature, preventing malicious modifications. Additionally, the timestamp in the signature helps mitigate [replay attacks](https://docs.tazapay.com/docs/webhook-authentication#avoiding-replay-attacks).

Use this mechanism to confirm that incoming webhooks originate from Tazapay and have not been compromised in transit.

***

## Steps to Generate the Webhook Signature

### 1. Extract the `event_id`

The `event_id` is a unique identifier for each webhook event. It is part of the webhook request payload.

Example of how `event_id` is structured:

```json
{
  "id": "evt_cv82n92p51c5jo1f5vfg",
  "data":{}
}
```

### 2. Extract the Timestamp

The time when the webhook request was received. Extract the created\_at field from the webhook response. Please note that we need to extract the `created_at` field that is outside the data json block. The timestamp will be in RFC3339Nano format.

```Text json
{
  "created_at": "2025-03-11T12:25:08.284979602Z",
  "data":{}
}
```

### 3. Concatenate Data for Signing

Once you have the event\_id and the timestamp, you need to concatenate them with the payload into a single string. This concatenated string will be used to generate the signature.

```Text json
<event_id><payload><timestamp>
```

Example - 

```
evt_cv82n92p51c5jo1f5vfg{"type":"payout.created","id":"evt_cv82n92p51c5jo1f5vfg","object":"event","created_at":"2025-03-11T12:25:08.284979602Z","data":{"created_at":"2025-03-11T12:25:05.960717Z","beneficiary_details":{"address":{"line1":"test","line2":"test","postal_code":"10038","city":"test","state":"test","country":""},"destination_details":{"bank":{"bank_codes":{"aba_code":"test","swift_code":"test"},"account_number":"test","bank_name":"test","country":"US","currency":"USD"},"type":"bank"},"phone":{"calling_code":"1","number":"12312312312"},"name":"test","email":"test@examplee.com","type":"individual","tax_id":"test"},"payout_fx_transaction":{"initial":{"currency":"USD","amount":100},"final":{"currency":"USD","amount":100},"id":"fx_cv82n89445nl3tkns2ug","object":"fx_transaction","exchange_rate":1},"type":"local","status":"processing","purpose":"PYR001","id":"pot_cv82n88epb2o04b90t9g","holding_currency":"USD","currency":"USD","beneficiary":"bnf_crv7poph1l071n2fkcmg","object":"payout","balance_transaction":"btr_cv82n8gepb2o04b90tdg","amount":100}}2025-03-11T12:25:08.284979602Z
```

<br />

### Generate HMAC-SHA256 Signature

Once you have concatenated the data, you will use HMAC-SHA256 to generate the signature. HMAC (Hash-based Message Authentication Code) is a cryptographic function that ensures data integrity and authenticity by using a secret key and a hashing algorithm.

To generate the signature:

1. Concatenate the event\_id, payload, and timestamp into a single string.
2. Use HMAC-SHA256 to hash the concatenated string using your secret key.
3. You can find the secret key on the merchant dashboard on the Settings > Webhooks > secret token. Click on reveal to view the secret token

   <Image align="center" src="https://files.readme.io/03c439acea7152575a001bfa423830050182ab0be3a170dfc628ee14614224b0-Screenshot_2025-03-12_at_6.03.25_PM.png" />
4. Generate the signature in Base64 format.

Example of how the signature will look like for the above concatenated string for secret key  `YKzhhJM4gd8s5MS1LVvWbqSyJqLPvr7j` - 

```
T2tZvRcMuZWVyDZrorBlPd7u8XKBx8RTWUSGuTakZqQ=
```

## Verify the signature

Once you have generated the signature on your end, you can match it with the signature sent by Tazapay in the webhook header in the field name - `signature`. If both of the signatures match , that means that the webhook is sent by Tazapay and has not been tampered with while transmission.

<Image align="center" src="https://files.readme.io/f15829643fb1f7c1e59a1510c0a20d9259a5fa891437644fc2f2cf18d25f05c1-Screenshot_2025-03-12_at_1.27.02_PM.png" />

<br />

## Avoiding Replay Attacks

A replay attack occurs when an attacker intercepts a valid payload and its signature, then retransmits them. To mitigate such attacks, Tazapay includes a timestamp in the `signature` header. Since this timestamp is part of the signed payload, it is also verified through the signature. This ensures that an attacker cannot modify the timestamp without invalidating the signature.

If the signature is valid but the timestamp is too old, your application should reject the payload. You can allow a tolerance of 10 minutes between the timestamp and the current time to avoid replay attacks.
