---
title: Refund
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
      "code": "{\n  \"reference_id\": \"e431ac5f-8055-451f-b819-7d0c043a61d0\",\n  \"txn_no\": \"2207-693901\",\n  \"status\": \"approved\",\n  \"updated_at\": \"2022-07-29T07:58:40.026684Z\",\n  \"reason\": \"Refund processed successfully\"\n}",
      "language": "json",
      "name": "Sample webhook for Refund"
    }
  ]
}
[/block]
### Response parameters:
Parameter                | Description
--------                 | --------
reference_id                 | `string` A unique ID to track each refund request
txn_no            | `string` The transaction number to which this refund is associated to
status           | `string` The status of the refund request
updated_at                    | `string` Timestamp at which the status of the refund was last updated
reason                | `string` Additional message about the refund for better comprehension