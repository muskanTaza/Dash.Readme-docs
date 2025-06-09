---
title: Payout Orchestration
excerpt: Pay your beneficiaries on time with just a few API calls on Tazapay
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
> 📘 Enable this beta function
> 
> This functionality is currently in beta and is available on an invite-only basis. If you're interested in participating, please send an email to [support@tazapay.com](mailto:support@tazapay.com).

### Overview

Payout orchestration refers to the process of handling the payment to beneficiaries on their behalf. This is typically done by online platforms such as eCommerce marketplaces and SaaS companies who collect payments on their users’ behalf and then disburse payments at a set time period. 

For instance, a SaaS platform for freelancers may want to pay their beneficiaries (in this case, freelancers) on the 25th of each month. By calling these sets of APIs, the freelancers will receive their payment on the 25th, or T+1 to 3 days from the completed API calls. 

To orchestrate a payout as a marketplace or platform, you’ll need to:

1. Initiate the payout by creating the beneficiary user for the transaction. The beneficiary should be mapped as the seller and the marketplace/platform or transacting party on behalf of the marketplace/platform should be mapped as the buyer
2. Create the transaction with the beneficiary and the marketplace/platform or transacting party who will be making the payout. Input the invoice amount and currency for the transaction and indicate that the transaction type is a payout.
3. Call the release API so that the beneficiary receives their payment.

### Initiating a Payout

Creating the beneficiary for the transaction will require the following APIs:

1. [Create User](ref:create-user-api) for adding the beneficiary user to the system (requires email ID, country, ind_bus_type, and business name or first name/last name as per the ind_bus_type)
2. [Get User by Email](ref:get-user-by-email-api) for an existing Tazapay user and retrieving their UUID
3. [Add Bank](ref:add-bank-api)  to the beneficiary user
4. [Get Bank](ref:get-bank-api)  if the beneficiary has bank account details on Tazapay already
5. [KYB Application](ref:kyb-application-api) for adding the KYB of the beneficiary (in case this is needed. This is typically for new users)

If you, as the marketplace or platform, don’t have an account with Tazapay yet, you’ll also need to call the create user & post KYB API calls. 

### Creating the Payout Escrow

Once you have the beneficiary and the marketplace UUID ready, you’ll need to call the [create escrow](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTA4-create-escrow) API (our unit for creating transactions). The following details will need to be specified:

1. **seller_id:** beneficiary’s user ID
2. **buyer_id:** either use
3. **Marketplace/Platform’s UUID**
4. Transacting party acting as the marketplace/platform’s sender
5. **invoice_amount:** actual amount to be paid out to the beneficiary
6. **invoice_currency:** the currency of the payout (can be the beneficiary’s local currency or USD)
7. **txn_description:** description of the underlying payout (why is this payout being made)
8. **transaction_category:** this should be set to ‘payout’
9. **transaction_source:** (Optional) can be hard-coded to API

### Releasing the Payout

Unlike other use cases such as [checkout](doc:single-checkout-api) and [co-branded payment links](doc:co-branded-payment-link), payout only requires you to call the release API once you’re ready to authorise the [release](https://docs.tazapay.com/reference/release-intro) of the payment to the beneficiary.