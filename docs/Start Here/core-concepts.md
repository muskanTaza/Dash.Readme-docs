---
title: Core Concepts
excerpt: >-
  To understand how Tazapay’s platform works, it helps to know about the core
  concepts that drive a payments platform.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
## Steps in an Online Payment Platform

A payment can happen in the online space when there’s at least 2 registered [users](doc:users-core-concept). The user receiving the payment has to have a [bank account](doc:bank-account) tied to their details, and have to have cleared [KYB (Know Your Business)](doc:kyb-know-your-business) before they can use any payment platform in order for the payment platform to comply with AML laws. 

The buyer user makes their payment on a [payment link](doc:payment-links-core-concept), which can be generated manually on the dashboard, or with the [checkout](doc:checkout-core-concept) or [escrow](doc:escrow-core-concept) API calls. 

Then the funds from the buyer are received by the payment platform, the seller or marketplace can call for the [release](doc:release-core-concept) mechanism in order for the seller user to receive their payout. 

Alternatively, if the buyer is not happy with the purchase, the marketplace can also call for a [refund](doc:refund-core-concept) on behalf of the buyer. 

If the buyer and seller require that the payment be disbursed in multiple steps, the marketplace can put a [milestone scheme](doc:milestone-schemes) in place of the escrow transaction to guarantee that their funds are secure until obligations are met.