---
title: Buyer-Initiated Payments
excerpt: Let buyers pay flexibly with Tazapay's buyer-initiated payment links (BIPs)
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

Buyer-Initiated Payment Links work similarly to [Co-Branded Payment Links](doc:co-branded-payment-link)  in which there is a customised/manual input for the amount paid in a transaction, except that it is initiated by a buyer.

BIPs can also be known as push payments.

This is ideal for online platforms looking to allow buyers to initiate their own payment for donations, tips, and other one-off payments to their intended seller user or to the platform itself if they are the participant of the transaction.

To create a buyer-initiated payment link as a marketplace/platform, you’ll need to:

1. Create or have the marketplace/platform and buyer’s UUID before initiating the creation of a payment link.
2. When the buyer generates a payment link, the seller’s UUID is called to complete the payment link details and an underlying transaction API is called.
3. Buyer pays with their preferred payment method and completes the transaction once the generated payment link URL is created. 

### Creating or Retrieving the Buyer and Seller

To create a buyer-initiated payment link, two user entities, a buyer and a marketplace/platform, need to exist in Tazapay’s database first. 

The buyer, who is registered under the marketplace/platform, will be able to generate payment links via the marketplace if the marketplace creates the buyer user on their behalf on Tazapay’s API.

The following API calls would need to be used:

- [Create User](ref:create-user-api)  to create the marketplace and buyer entities if they don't exist in Tazapay's database yet (requires email ID, country, ind_bus_type, and business name or first name/last name as per the ind_bus_type)
- [Get User by Email](ref:get-user-by-email-api) for existing Tazapay users and retrieving their UUID

As the marketplace/platform, your buyers would need to input their transaction amount, the seller’s details, and currency before clicking a button to generate their payment link.

On the seller’s details, the first two steps would be repeated in order to create or retrieve the user details on Tazapay. Following that, the next set of API calls needed are:

- [KYB Application](ref:kyb-application-api)  for adding the KYB of the seller or marketplace/platform if they are the beneficiary of the transaction. This is typically for new users
- [Add Bank](ref:add-bank-api) to seller users
- [Get Bank](ref:get-bank-api) if the users’ bank account details are on Tazapay already

### Generating the Underlying Transaction (Escrow)

Within the same “Generate Payment Link” interface, the transaction details can also be captured. These would include:

1. **seller_id**: seller’s UUID
2. **buyer_id**: buyer’s UUID
3. **initiated_by**: buyer’s UUID since the buyer is initiating the payment link
4. **invoice_amount**: actual amount of the transaction
5. **invoice_currency**: the currency of the transaction (can be the buyer’s local currency or USD)
6. **txn_description**: description of the transaction (why is this payment link made)

These details would be entered on the [create escrow](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTA4-create-escrow) API (our unit for creating transactions).

Once the API call is successful, you will get a txn_no that looks like this:

**2022-00000**

### Creating the Co-Branded Payment Link

Once you have completed the create escrow API call, take the txn_no and call the create_payment API.

The response message should provide a URL where the seller can collect the payment from their buyer. For more info on how the buyer can [pay any Tazapay transaction](https://support.tazapay.com/how-do-i-pay-fund-tazapay-escrow), read our FAQ.

For more info on [payment links](https://tazapay.com/payment-links/), you may refer to our website.