---
title: Escrow States
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
## Escrow States

The following flowchart details the possible states & substates for escrow transactions

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8492cc9-yj1XeiukBos.jpg",
        "yj1XeiukBos.jpg",
        3379
      ],
      "border": true
    }
  ]
}
[/block]



For payment states, we'll pass on payment failed, received, and 'reported' (i.e., user completes an offline transfers and confirms payment is made) as sub-states under Awaiting Payment.

For release, we'll pass on Release Authorized once we get confirmation for release of escrow, and payout completed once the amount is settled to the seller (failed if there was a failure in doing transfer).

### All Possible Escrow States

| Name               | Type  | Description                                                     |
| ------------------ | ----- | --------------------------------------------------------------- |
| Awaiting_Payment   | state | Awaiting Payment from Buyer                                     |
| Payment_Received   | state | Received Payment from Buyer                                     |
| Payment_NoResponse | state | Not received Payment from Buyer before due date                 |
| Release_Authorized | state | Buyer or Marketplace requested to release the payment to seller |
| Payout_Completed   | state | Seller received the payment (final stage)                       |

### All Possible Escrow Sub States

| Name                     | Type     | State              | Description                                                                                                 |
| ------------------------ | -------- | ------------------ | ----------------------------------------------------------------------------------------------------------- |
| Generic                  | subState | Generic            | A generic state when the transaction is created                                                             |
| Payment_Failed           | subState | Awaiting_Payment   | Payment failed                                                                                              |
| Payment_Reported         | subState | Awaiting_Payment   | user completes an offline transfer and confirms payment is made                                             |
| Payment_Shortfall        | subState | Awaiting_Payment   | Total payment is not done. Full amount is not received.                                                     |
| under_review             | subState | Awaiting_Payment   | Payment under review. Will be resolved within 1 business day.                                               |
| Doc_Verification_Failed  | subState | Release_Authorized | The KYB document verification has failed. Drop an email to support@tazapay.com to find out more information |
| Requested_Additional_Doc | subState | Release_Authorized | Additional documents are required to complete the KYB                                                       |