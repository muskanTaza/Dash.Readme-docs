---
title: Milestone schemes
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
We’ll help you set up ‘Milestone Schemes’ as a configuration linked to your profile. A ‘scheme’ is a pre-defined order of collect and release milestones that can specify multiple payments into and payouts from the escrow.
[block:callout]
{
  "type": "info",
  "body": "💡 By default, there wouldn't be any milestone schemes set up for users. To request for milestone schemes set up for your account, please contact support@tazapay.com"
}
[/block]
**For instance:**

 **Milestone scheme 1:** 20% advance, 80% on shipment.

**Milestone scheme 2:** 30% advance, 40% on shipment and 30% on delivery can be setup as ‘schemes’.

At checkout, you can pick a scheme from the set configured for you and ‘attach’ it to the escrow by passing it in create escrow endpoint. On the UI, you can either give the users an option to choose an available scheme or select one on their behalf depending on the transaction. 

### Collect/ release:

Depending on the scheme attached to the escrow, you can orchestrate the create payment and release APIs. 

Each call to the create payment API will initiate a payment session to collect the corresponding milestone amount and each call to release will initiate the release of the milestone amount.