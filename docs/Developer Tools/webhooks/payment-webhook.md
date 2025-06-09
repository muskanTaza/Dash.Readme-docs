---
title: Payment
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
      "code": "{\n  \"txn_no\": \"2207-589815\",\n  \"state\": \"Payment_Received\",\n  \"sub_state\": \"Generic\",\n  \"invoice_currency\": \"USD\",\n  \"invoice_amount\": 1000,\n  \"partner_reference_id\": \"uid1\",\n  \"payment\": {\n    \"collection_method\": \"Card\",\n    \"remarks\": \"payment received\",\n    \"payable_amount\": 1000,\n    \"paid_amount\": 1000,\n    \"collection_currency\": \"USD\",\n    \"fx_rate\": 1,\n    \"transaction_id\": \"7979aebf-6780-4b7b-ba5c-3961ea0ae430\"\n  },\n  \"attributes\": {\n    \"doc_url\": \"https://media.istockphoto.com/photos/historic-buildings-of-wall-street-in-the-financial-district-of-lower-picture-id1337246025?s=612x612\"\n  }\n}",
      "language": "json",
      "name": "Sample Webhook Response for Create Payment Endpoint"
    }
  ]
}
[/block]
## Response parameters:
Parameter                | Description
--------                 | --------
txn_no                   | `string` The txn_no for the request made
invoice_currency         | `string` The invoice currency of payment made for this escrow
invoice_amount           | `float` Invoice amount i.e. amount paid for this escrow
state                    | `string` The state / status of escrow
sub_state                | `string` The sub state / status of escrow