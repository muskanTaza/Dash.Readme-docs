---
title: Co-Branded Payment Links
excerpt: >-
  Enable your sellers to create their customised invoice amount using Tazapay's
  co-branded payment links.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
### Overview

A co-branded payment link is a checkout link initiated by the seller to collect a set amount of money from their buyer or client. The sellers have the flexibility to decide how much this amount is when they generate their payment link.

While individual users can [create payment links](https://support.tazapay.com/how-do-i-create-and-send-a-payment-link) via our dashboard, an online marketplace/platform can create these links on behalf of the users selling goods or providing services by using a set of Tazapay’s API calls. 

This is ideal if there isn’t an integrated checkout for buyers due to longer or more complex negotiation terms. 

**To create a co-branded payment link as a marketplace/platform, you’ll need to:**

1. Create or have the marketplace/platform and seller’s UUID before initiating the creation of a payment link. 
2. When the seller generates a payment link, the buyer user will be generated with an inputted transaction amount. When this happens, an underlying transaction API is called.
3. Create the payment link so that sellers can send it to their buyer through any secure messaging channel.

### Creating or Retrieving the Marketplace and Seller

For a payment link to be initiated, two user entities need to exist in Tazapay’s database - a seller and a marketplace. The seller, who is registered under the marketplace/platform, will be able to generate payment links via the marketplace if the marketplace creates the seller user on their behalf on Tazapay’s API.

The following API calls would need to be used:

1. [Create User](ref:create-user-api)  to create the marketplace and seller entities if they don't exist in Tazapay's database (requires email ID, country, ind_bus_type, and business name or first name/last name as per the ind_bus_type)
2. [Get User by Email](ref:get-user-by-email-api)  for existing Tazapay users and retrieving their UUID
3. [Add Bank](ref:add-bank-api)  to seller users
4. [Get Bank](ref:get-bank-api) if the users’ bank account details are on Tazapay already
5. [KYB Application](ref:kyb-application-api) for adding the KYB of the seller (in case this is needed. This is typically for new users)

As a marketplace/platform, your sellers should enter their buyer & transaction details through your interface before clicking “Generate Payment Link”. This is where you’ll also make the same [create user](ref:create-user-api) API call to create the buyer user for your seller to collect their payment. 

### Generating the Underlying Transaction (Escrow)

Within the same “Generate Payment Link” interface, the transaction details can also be captured. These would include:

1. seller_id: seller’s UUID
2. buyer_id: UUID created for the buyer after clicking “Generate Payment Link”
3. initiated_by: the seller’s UUID since this is seller initiated
4. invoice_amount: actual amount of the transaction
5. invoice_currency: the currency of the transaction (can be the seller’s local currency or USD)
6. txn_description: description of the transaction (why is this payment link made)

These details would be entered on the [create escrow](ref:create-escrow-api) API (our unit for creating transactions).

 Once the API call is successful, you will get a txn_no that looks like this:`2022-00000`

### Creating the Co-Branded Payment Link

Once you have completed the [create escrow](ref:create-escrow-api) API call, take the txn_no and call the [create payment](ref:create-payment-api) API. 

The response message should provide a URL where the seller can collect the payment from their buyer. 

For more info on how the buyer can [fund any Tazapay transaction](https://support.tazapay.com/how-do-i-pay-fund-tazapay-escrow), read our FAQ.

If you'd like to know more about our [payment link](https://tazapay.com/payment-links/) feature, head over to our website.