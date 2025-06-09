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

<Image className="border" border={true} src="https://files.readme.io/8492cc9-yj1XeiukBos.jpg" />

For payment states, we'll pass on payment failed, received, and 'reported' (i.e., user completes an offline transfers and confirms payment is made) as sub-states under Awaiting Payment.

For release, we'll pass on Release Authorized once we get confirmation for release of escrow, and payout completed once the amount is settled to the seller (failed if there was a failure in doing transfer).

### All Possible Escrow States

| Name                | Type  | Description                                                     |
| ------------------- | ----- | --------------------------------------------------------------- |
| Awaiting\_Payment   | state | Awaiting Payment from Buyer                                     |
| Payment\_Received   | state | Received Payment from Buyer                                     |
| Payment\_NoResponse | state | Not received Payment from Buyer before due date                 |
| Release\_Authorized | state | Buyer or Marketplace requested to release the payment to seller |
| Payout\_Completed   | state | Seller received the payment (final stage)                       |

### All Possible Escrow Sub States

| Name                       | Type     | State               | Description                                                                                                                               |
| -------------------------- | -------- | ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Generic                    | subState | Generic             | A generic state when the transaction is created                                                                                           |
| Payment\_Failed            | subState | Awaiting\_Payment   | Payment failed                                                                                                                            |
| Payment\_Reported          | subState | Awaiting\_Payment   | user completes an offline transfer and confirms payment is made                                                                           |
| Payment\_Shortfall         | subState | Awaiting\_Payment   | Total payment is not done. Full amount is not received.                                                                                   |
| under\_review              | subState | Awaiting\_Payment   | Payment under review. Will be resolved within 1 business day.                                                                             |
| Doc\_Verification\_Failed  | subState | Release\_Authorized | The KYB document verification has failed. Drop an email to [support@tazapay.com](mailto:support@tazapay.com) to find out more information |
| Requested\_Additional\_Doc | subState | Release\_Authorized | Additional documents are required to complete the KYB                                                                                     |
