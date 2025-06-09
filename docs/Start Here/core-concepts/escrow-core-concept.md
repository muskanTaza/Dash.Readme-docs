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
Escrow allows two parties to protect funds until certain conditions or [milestones](doc:milestone-schemes) are met. The verification of completion of these funds can be either done by Tazapay or the user, which has to be communicated to Tazapay at the time of onboarding. 

To create an escrow, we need to know the Tazapay User IDs of the buyer and seller participating in the transaction, the invoice amount and currency and a free-text note on what the transaction is about. 

Documents are not required to create an escrow but can be provided to indicate additional details about the underlying trade to make the eventual release process smoother for the seller (entity getting paid).

Try the [Create Escrow](ref:create-escrow-api) API out yourself.

> 🚧
>
> You'll need to have a user's UUID from either [Create User](ref:create-user-api) or [Get User by ID](ref:get-user-by-id-api) and then create the [payment link](doc:payment-links-core-concept) by calling [Create Payment](ref:create-payment)
