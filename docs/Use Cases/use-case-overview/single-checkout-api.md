---
title: Hosted Checkout with Tazapay
excerpt: >-
  This is the easiest integration to enable over 80+ localised payment options
  for your buyers around the world via Tazapay's payment gateway
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
> 🚧
>
> This overview covers the use of the Single API call [Create Checkout](https://docs.tazapay.com/reference/create-checkout). For Escrow transactions and more extensive customisability, refer to [Hosted Escrow Checkout](https://docs.tazapay.com/docs/hosted-escrow-checkout-with-tazapay)

To complete a checkout with Tazapay, you'll need to:

1. Ensure you have your buyer's details ready. Seller details are optional if you're the sole merchant.
2. Have the transaction details and currency ready.

### Input Buyer Details

This section of the API's body parameter requires the following details from the buyer:

* buyer `email`
* buyer `country` eg: `SG`,`US`, `IN`
* `individual`or `business`in`ind_bus_type`
* name (`first_name` and `last_name` for individuals, `business_name` for businesses

Upon sending the API, a new user will be created and their `account_id` acts as the `UUID`. You can always retrieve their info again with [Get User by ID](https://docs.tazapay.com/reference/get-user-by-id-api).

If you need to create a seller user, the above parameters are also required for them.

### Platform Fee Payment

These parameters determine who pays for the platform fees to Tazapay. 

* The `fee_percentage` parameter can be anywhere between 0-100
* `fee_paid_by` determines who pays the `fee_percentage`. This is either the `buyer` or `seller`

> 📘
>
> **Example:**
>
> If `fee_percentage` is set to 0 and `fee_paid_by` is `buyer`, then the seller will pay for 100% of Tazapay's platform fees.

### Transaction Details

The next few required parameters are where you would input the details of your transaction. 

* `invoice_currency` eg: `USD`, `EUR`
* `invoice_amount`
* `txn_description` to input your transaction details

> 📘 Currency Definitions
>
> **Invoice Currency:** The currency in which the transaction is listed or invoiced.
>
> **Collection Currency:** The currency used by the buyer to pay for the transaction. If this is different from the invoice currency, we apply our FX rates to show the invoice currency amount in the collection currency equivalent value.
>
> **Settlement Currency:** The currency used to settle to the seller. The current options are the seller’s local currency, USD, GBP, or EUR. Again, we apply our FX rates to convert to the settlement currency if it is different from the invoice currency.

### Disabling Payment Methods

If you want to limit certain payment methods during checkout, you can disable them by using the Filter parameter. For more info, read our [FAQ](https://support.tazapay.com/how-do-i-disable-payment-method).

### Return URL for a Payment Link

Once you send the API call, the Create Checkout API should return a payment link for your buyer to make their payment for your product.

To find out how this will help with [eCommerce platform payments](https://tazapay.com/marketplaces-and-platforms), check out our website.
