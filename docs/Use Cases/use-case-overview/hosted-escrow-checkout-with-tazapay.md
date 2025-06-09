---
title: Hosted Escrow Checkout
excerpt: >-
  This method is a 3-step process from creating/getting user details, creating a
  transaction, and then a payment link.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
To complete a checkout with Tazapay, you'll need to:

1. Ensure users exist or are created before initiating a transaction. The users in the transaction have to be mapped as a buyer and a seller. 
2. A transaction is created between the participating users, along with the cart value and currency. If additional documents are required, it will be added here.
3. The buyer is redirected to make their payment for the transaction.

### Create/Get User

You can initiate a [Create User](ref:create-user) API call for buyers and sellers if they don't exist in Tazapay's database. To check if the user exists, you can make a [Get User by ID](ref:get-user-by-id-api) or [Get User by Email](ref:get-user-by-email-api) API call. 

> 📘
>
> This API call needs the entity type as individual or business in `ind_bus_type`, email, country, and name (`first_name` and `last_name` for individuals, `business_name` for businesses) for the purposes of user creation.

Upon creating the user, their `account_id` acts as the `UUID` of the user.

To optimize load time, you can call the Create User API anytime during checkout or when users sign up on your online platform for the first time.

### Create Transaction

Once you have the buyer's and seller's `UUID`, you can initiate a [Create Escrow](ref:create-escrow-api)  API call. 

> 📘
>
> This API call needs the `invoice_amount`, `invoice_currency`, `buyer_id` & `seller_id` in the form of their `UUID`, `initiated_by` to indicate which party initiated the transaction, and a description of the transaction in `txn_description`.

This API also allows you to add supporting documents needed for upload to turn the checkout into escrow.

### Types of Currencies

**Invoice Currency:** The currency in which the transaction is listed or invoiced.

**Collection Currency:** The currency used by the buyer to pay for the transaction. If this is different from the invoice currency, we apply our FX rates to show the invoice currency amount in the collection currency equivalent value.

**Settlement Currency:** The currency used to settle to the seller. This is currently limited to the seller’s local currency or USD. Again, we apply our FX rates to convert to the settlement currency if it is different from the invoice currency.

### Buyer Checkout

Once the buyer clicks 'Place Order and Pay', you can initiate a [Create Payment](https://docs.tazapay.com/reference/create-payment) API call. This returns a URL which you can use to redirect the buyer to the co-branded payment page.

To find out how this will help with [eCommerce platform payments](https://tazapay.com/marketplaces-and-platforms), check out our website URL.
