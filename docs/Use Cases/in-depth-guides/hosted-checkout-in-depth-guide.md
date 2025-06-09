---
title: Hosted Checkout In-Depth Guide
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
### Scenario:

You are a marketplace looking to integrate Tazapay’s checkout for a fixed cart amount. This in-depth guide will help you set up with Tazapay for a hosted checkout experience where you enable your buyers with multiple localised payment methods. 

You can pass the following information to Tazapay’s API to orchestrate payouts:

- Buyer’s and seller’s country
- E-mail ID of the buyer and seller
- Name
- Invoice currency (e.g. USD, INR, EUR, etc.)
- Amount
- Transaction description

## Step 1: Creating User entities

For a transaction to happen, two entities need to exist in Tazapay’s database - a seller entity and a buyer entity. Marketplaces need to create an additional marketplace entity.  
To create entities: Use `POST /v1/user.`

For example, Marketplace Minekart, based in Singapore, wants to register itself as an entity at Tazapay.

Minekart submits the following payload for the body:

```
{
    "email": "business@minekart.com",
    "country": "SG",
    "ind_bus_type": "Business",
    "business_name":"Minekart Pte. Ltd."
}
```



Tazapay creates an entity for Minekart and returns the following response. 

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "8a012414-99a6-4a1e-9dca-91529c0b4093",
       "customer_id": ""
   }
}
```



The account id acts as the UUID for Minekart. Minekart stores it in its records.

Spec Rayes, a seller based in Indonesia, wants to sign up on Minekart. To enable Spec Rayes to use Tazapay’s services, they need to be a Tazapay registered entity. 

As soon as Spec Rayes is onboarded on Minekart, Minekart creates a Tazapay entity on Spec Rayes’ behalf by submitting the following payload for the body while using `POST /v1/user`:

```
{
    "email": "info@specrayes.com",
    "country": "IN",
    "ind_bus_type": "Business",
    "business_name":"PT Spec Rayes"
}
```



A Tazapay entity is created for Spec Rayes and the following response is returned.

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "29b47654-7457-4f7e-a00c-e70bf78f3008",
       "customer_id": ""
   }
}
```



The account_id acts as the `UUID` for Spec Rayes. Minekart stores it in its records.

Arnold from the US wants to buy a pair of branded sunglasses from Spec Rayes. He registers for an account on Minekart to buy from Spec Rayes, and the following user information is also captured during signup using `POST /v1/user`:

```
{
    "email": "arnold.darwin@me.com",
    "country": "US",
    "ind_bus_type": "Individual",
    "first_name":"Arnold",
    "last_name":"Darwin"
}
```



A Tazapay entity is created for Arnold and the following response is returned.

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "7eec2b41-5db0-4430-a8df-374b6c0722a2",
       "customer_id": ""
   }
}
```



Arnold’s account_id acts as his `UUID`. Minekart stores this info in their database.

To learn more about creating & managing entities on Tazapay’s endpoints, we have a section on [Users](ref:user-intro) here. 

## Step 2: Creating the Unit of Transaction (Escrow in Tazapay’s Lexicon)

To create a transaction unit, Minekart uses `POST /v1/escrow`. 

Fee collection, transaction costs, flat fees, and other customisations can be edited here. More details on how to do this can be found on our [create escrow API](ref:create-escrow-api) documentation.

Once Minekart has the details of the buyer captured on checkout, the `POST /v1/escrow` is fired as such:

```
{
   "txn_type": "goods",
   "initiated_by": "29b47654-7457-4f7e-a00c-e70bf78f3008",
   "buyer_id": "7eec2b41-5db0-4430-a8df-374b6c0722a2",
   "seller_id": "29b47654-7457-4f7e-a00c-e70bf78f3008",
   "txn_description": "Branded Sunglasses",
   "invoice_currency": "USD",
   "invoice_amount": 98
}
```



A Tazapay transaction is created and the following response is returned:

```
{
   "status": "success",
   "message": "escrow created successfully",
   "data": {
       "txn_no": "2207-105500",
       "state": "Escrow_Awaiting_Funds",
       "sub_state": "na",
       "txn_type": "goods",
       "invoice_currency": "USD",
       "invoice_amount": 98,
       "fee_tier": "standard",
       "fee_paid_by": "buyer",
       "fee_tier_percentage": 1.8,
       "fee_amount": 1.76,
       "collect_amount": 98,
       "disburse_amount": 96.24,
       "transcation_source": "api"
   }
}
```



The `txn_no` is a unique number representing this particular transaction. Minekart stores this info in their database and would refer to the transaction number if need be.

Tazapay will deduct USD 1.76 from the transaction before disbursing the remaining amount.

## Step 3: Generating the Checkout Page (Payment in Tazapay’s Lexicon)

Minekart needs to use `v1/session/payment API` to generate a checkout page. The marketplace submits the following payload:

```
{
   "txn_no": "2207-105500"
}
```



This is the same txn_no from the response for the Create Escrow API.

The URL for checkout is generated in the following response:

```
{
   "status": "success",
   "message": "payment session created successfully",
   "data": {
       "redirect_url": "https://sandbox.tazapay.com/marketplace/paymentdetails/kUss2rNJfYFL84R1d3oeigcK5a_fdlmnqBZzv1M7vYc-oviVkBQaXMkKG4BSqUXu"
   }
}
```



Minekart can redirect Arnold to the hosted checkout page where he can select his preferred payment method for his purchase. In this instance, he is presented with two options: local bank transfer or card.

![](https://files.readme.io/3e19156-checkout1.png "checkout1.png")

Arnold chooses to pay via bank transfer so he selects “Local Bank Transfer” and clicks “Proceed to Pay”

![](https://files.readme.io/43e5172-checkout2.png "checkout2.png")

He then copies the details to make his payment to Tazapay’s account

![](https://files.readme.io/d4e3bba-checkout3.png "checkout3.png")

Once he’s completed his payment, he clicks “I’ve completed payment” and he will be redirected to this page:

![](https://files.readme.io/541ee28-checkout4.png "checkout4.png")

Once Tazapay is able to verify that he has paid for the transaction, the transaction status would be updated and the payment is ready to be released. 

For more details about Tazapay’s [Create Payment API](https://developer.tazapay.com/docs/tazapay-API-documentation/13bd5163ce44c-payments), please refer to our documentation.

## Step 4: Releasing the Payment

Arnold must first complete his payment before Minekart is able to release the payment to Spec Rayes. To release the payout, Minekart can call the following API using `/v1/session/release`.

```
{
   "txn_no": "2207-105500"
}
```



This is the response from the above API.

```
{
   "status": "success",
   "message": "release session created successfully",
   "data": {
       "reference_id": "59ecefae-14d4-4c7b-968e-c6d5fe6c35f4"
   }
}
```



At this point, the transaction is now complete.

We have more details about the [Release API](ref:release-intro) on our documentation here. 

You may need to use the following APIs at some point during the integration process apart from the steps listed above:

**Post KYB:** KYB stands for Know Your Business, To disburse funds into the seller’s account (in this case, Spec Rayes), the seller will have to undergo a one-time verification exercise before the first disbursal by Tazapay. It is a standard risk management practice aimed at eliminating money laundering. The [KYB](ref:kyb-intro)  
`POST/v2/kyb` can be used to add the required documents on Tazapay’s server for KYB verification of the sellers. 

**Get Escrow Status:** To know the status of a particular underlying transaction, marketplaces can use `GET/v1/escrow/{txn_no}`. It will return the state and substate of a particular transaction (in this case, the payout between Slydeshow and the freelancers). This will keep all the stakeholders (marketplace and seller) always informed of the stage of the transaction. For more information about the [Get Escrow Status API](ref:escrow-status-api), please refer to the link.

To find out how this will help with [eCommerce platform payments](https://tazapay.com/marketplaces-and-platforms/), check out our website URL.