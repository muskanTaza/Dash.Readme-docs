---
title: Escrow states
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
## Payment Status

The following flowchart details the possible payment status for an escrow status:

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/2adc953-image.png",
        null,
        ""
      ],
      "align": "center",
      "border": true
    }
  ]
}
[/block]


| Name       | Description                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| unpaid     | The customer has not made the payment and further action is required from the customer                                                                                                                                                                                                                                                                                                                                                  |
| processing | The customer has performed all the actions but Tazapay is yet to receive the payment. It is very rare that an escrow session stays in this state unless the payment method chosen is not an instant one. For example, an escrow session stays in the processing state when the payment method chosen is local bank transfer / wire transfer. Offline payments take some time for the intermediary banking institutions to process them. |
| paid       | The payment is successful                                                                                                                                                                                                                                                                                                                                                                                                               |

## Document verification Status

The following flowchart details the possible verification status for an escrow.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/3b72409-image.png",
        null,
        ""
      ],
      "align": "center",
      "border": true
    }
  ]
}
[/block]


| Name          | Description                                                                              |
| ------------- | ---------------------------------------------------------------------------------------- |
| not_submitted | The required documents are not submitted for the KYB.                                    |
| processing    | Tazapay is reviewing the documents submitted                                             |
| succeeded     | The verification is successful. You can expect to receive a payout for this transaction. |
| failed        | The document verification has failed.                                                    |