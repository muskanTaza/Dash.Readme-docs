---
title: Escrow
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"txn_no\": \"2207-117037\",\n  \"state\": \"Awaiting_Payment\",\n  \"sub_state\": \"Generic\",\n  \"invoice_currency\": \"USD\",\n  \"invoice_amount\": 1000,\n  \"milestone\": {\n    \"code\": \"Scheme 2\",\n    \"short_description\": \"30% advance; 70% on delivery\",\n    \"long_description\": \"Pay 30% advance to the seller and 70% when the shipment gets delivered\",\n    \"breakdowns\": [\n      {\n        \"milestone_no\": 1,\n        \"category\": \"payment\",\n        \"type\": \"passthrough\",\n        \"percentage\": 30,\n        \"milestone_amount\": 300,\n        \"status\": \"new\",\n        \"txn_status\": \"new\",\n        \"doc_status\": \"na\"\n      },\n      {\n        \"milestone_no\": 2,\n        \"category\": \"payout\",\n        \"type\": \"passthrough\",\n        \"percentage\": 30,\n        \"milestone_amount\": 294.6,\n        \"status\": \"new\",\n        \"txn_status\": \"new\",\n        \"doc_status\": \"na\"\n      },\n      {\n        \"milestone_no\": 3,\n        \"category\": \"payment\",\n        \"type\": \"hold\",\n        \"percentage\": 70,\n        \"milestone_amount\": 700,\n        \"status\": \"new\",\n        \"txn_status\": \"new\",\n        \"doc_status\": \"na\"\n      },\n      {\n        \"milestone_no\": 4,\n        \"category\": \"payout\",\n        \"type\": \"hold\",\n        \"percentage\": 70,\n        \"milestone_amount\": 687.4,\n        \"status\": \"new\",\n        \"txn_status\": \"new\",\n        \"doc_status\": \"na\"\n      }\n    ]\n  },\n  \"partner_reference_id\": \"uid1\"\n}",
      "language": "json",
      "name": "Sample response for escrow webhook"
    }
  ]
}
[/block]
## Response Parameters

Parameter                | Description
--------                 | --------
txn_no                   | `string` Year and 5 digit escrow transcation number
state                    | `string` State / status of escrow
sub_state                | `string` Sub state / status of escrow
invoice_currency         | `string`  Invoice currency
invoice_amount           | `float` Invoice amount