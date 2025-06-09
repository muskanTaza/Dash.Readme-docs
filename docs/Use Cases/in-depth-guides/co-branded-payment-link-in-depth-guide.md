---
title: Co-Branded Payment Links In-Depth Guide
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

You are a marketplace wanting to provide your sellers with the facility of creating payment links. This integration guide will help you integrate with Tazapay’s developer tools and APIs to leverage Tazapay’s payments platform.

You can collect on a screen on your marketplace (let us name this screen X) the following information and pass it onto Tazapay via an API to create a payment link:

* Buyer’s country
* E-mail ID
* Name
* Payment currency (e.g. USD, INR, EUR, etc.)
* Amount
* Transaction description

## STEP 1: Creating entities

For a transaction to happen, two entities need to exist in Tazapay’s database - a seller entity and a buyer entity. Marketplaces need to create an additional marketplace entity.

To create entities: **Use POST /v1/user**.

For example, Marketplace Minekart, based in Singapore, wants to register itself as an entity at Tazapay. 

Minekart submits the following payload for the body.

```
{
    "email": "business@minekart.com",
    "country": "SG",
    "ind_bus_type": "Business",
    "business_name":"Minekart Pvt. Ltd."
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

The account id acts as the UUID for Minekart. Minekart stores it in its records.Now, Minekart onboards an Indian seller Spec Sales on its platform. 

To enable the seller to use Tazapay’s services, Spec Sales is required to be a Tazapay registered entity. 

As soon as Spec Sales is onboarded on Minekart, Minekart creates a Tazapay entity by submitting the following payload for the body while using **POST /v1/user**:

```
{
    "email": "cool@specsales.com",
    "country": "IN",
    "ind_bus_type": "Business",
    "business_name":"Spec Sales Awesome"
}
```

A Tazapay entity is created for Spec Sales and the following response is returned.

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "0ed3ab19-f6f2-479a-9467-c241561f393d",
       "customer_id": ""
   }
}
```

The account id acts as the `UUID` for Spec Sales. Minekart stores it in its records.

Spec Sales wants to collect USD $128 from a buyer Alice Dawkins from the United States of America and enters her details on screen X hosted on Minekart. Spec Sales enters the following information:

* **Buyer’s country** - United States of America
* **E-mail ID** - [alice.dawkins@me.com](mailto:alice.dawkins@me.com)
* **Name** - Alice Dawkins
* **Payment currency** - USD
* **Amount** - $128
* **Transaction description** - Cool Lenses #12

As soon as Spec Sales clicks on ‘**Generate Payment Link**’, Minekart creates a Tazapay entity for Alice by submitting the following payload for the body while using **POST /v1/user**:

```
{
    "email": “alice.dawkins@me.com",
    "country": "US",
    "ind_bus_type": "Individual",
    "first_name":"Alice",
    "last_name":"Dawkins"	
}
```

A Tazapay entity is created for Alice and the following response is returned:

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "3c9e0055-eb27-46d9-b773-fe35592186fe",
       "customer_id": ""
   }
}
```

The account id acts as the UUID for Alice. Minekart stores it in its records.

For more details about how to manage entities using Tazapay’s endpoints, please click [here](https://developer.tazapay.com/docs/tazapay-API-documentation/f1e6a64cb9051-users) to get redirected to the relevant part of our documentation.

## Step 2: Create a unit of transaction (escrow in Tazapay’s parlance)

For a unit of transaction to be created, Minekart uses **POST /v1/escrow**. Minekart can customise the transaction (in terms of fee collection, transaction costs, etc.) in this step. For details on how to do this, click [here](https://developer.tazapay.com/docs/tazapay-API-documentation/4qe3kuym-escrow) to get redirected to the relevant section of our documentation.

Minekaft submits the following payload to **POST /v1/escrow**.

```
{
   "txn_type": "goods",
   "initiated_by": "0ed3ab19-f6f2-479a-9467-c241561f393d",
   "buyer_id": "3c9e0055-eb27-46d9-b773-fe35592186fe",
   "seller_id": "0ed3ab19-f6f2-479a-9467-c241561f393d",
   "txn_description": "Cool Lenses #12",
   "invoice_currency": "USD",
   "invoice_amount": 128
}
```

The ‘**inititated\_by**’ field takes the UUID of Specs Sales since it is the seller who has initiated the transaction, ‘**buyer\_id**’ takes the UUID of Alice, the ‘**seller\_id**’ takes the UUID of Specs Sales, ‘**txn\_description**’ has Cool Lenses #12 which is the transaction description. Invoice currency and invoice amount are also entered in the payload.

A Tazapay transaction is created and the following response  is returned.

```
{
   "status": "success",
   "message": "escrow created successfully",
   "data": {
       "txn_no": "2205-171521",
       "state": "Escrow_Awaiting_Funds",
       "sub_state": "na",
       "txn_type": "goods",
       "invoice_currency": "USD",
       "invoice_amount": 128,
       "fee_tier": "standard",
       "fee_paid_by": "buyer",
       "fee_tier_percentage": 1.8,
       "fee_amount": 2.3,
       "collect_amount": 128,
       "disburse_amount": 125.7
   }
}
```

The ‘**txn\_no**’ is a unique number representing this particular transaction, which will be used to generate the payment link. Minekart stores this in its database.\
The fee\_amount of $2.3 will be deducted by Tazapay before disbursing the funds. 

## Step 3: Generating the payment Link

To generate the payment link, Minekart uses v1/session/payment API by submitting the following payload.

```
{
   "txn_no": "2205-171521"
}
```

The txn\_no is the same as the txn\_no in the response of the Create Escrow API.\
The following response is returned.

```
{
   "status": "success",
   "message": "payment session created successfully",
   "data": {
       "redirect_url": "https://sandbox.tazapay.com/marketplace/paymentdetails/_exsXsnvB1OPQ4wqD1hlnB2rpaBGExbUG_uBAKS41jgMVgvB6Wc0GbLIBgdXURai"
   }
}
```

The ‘redirect\_url’ is the payment link that is generated. Specs Sales can use this link to collect payment from Alice.

For more details about Tazapay’s Create Payment API, please click [here](https://developer.tazapay.com/docs/tazapay-API-documentation/13bd5163ce44c-payments). When Alice clicks on the link, she has to go through the below steps in order to complete the payment.

![co branded payment link1.png](https://stoplight.io/api/v1/projects/cHJqOjk1NTE1/images/vlJW3CalTcU)

* Alice wants to pay with her credit card, she selects Card and then clicks on Confirm Payment.

![co branded payment link2.png](https://stoplight.io/api/v1/projects/cHJqOjk1NTE1/images/7FwUtzi42A0)

* Alice then enters her card details and clicks on ‘Pay Now’ to complete the payment.

![co branded payment link3.png](https://stoplight.io/api/v1/projects/cHJqOjk1NTE1/images/j4vScvghMr8)

* She gets confirmation that her payment has been successful and she can close the tab.

![co branded payment link4.png](https://stoplight.io/api/v1/projects/cHJqOjk1NTE1/images/as4bBCXI90Y)

## Step 4: Releasing the payment to Spec Sales

Minekart can authorise the release of the payment to Spec Sales by submitting the following payload in /v1/session/release.

```
{
   "txn_no": "2205-171521"
}
```

The payment ($125.7) gets credited in Spec Sales’ account after deduction of the transaction fees. This is the response from the above API.

```
{
   "status": "success",
   "message": "release session created successfully",
   "data": {
       "reference_id": "59ecefae-14d4-4c7b-968e-c6d5fe6c35f4"
   }
}
```

For more details about the [Release API](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTEy-release), please click on the link.

Apart from the above APIs, you will also need to use the following APIs at some point during the integration process:

**1.Post KYB:** 

KYB stands for Know Your Business, To disburse funds into the seller’s account (in this case, Spec Sales’), the seller will have to undergo an one-time verification exercise before the first disbursal by Tazapay. It is a standard risk management practice aimed at eliminating money laundering. 

**POST/v2/kyb** can be used to add the required documents on Tazapay’s server for KYB verification of the sellers. For more information about the KYB facilities provided by Tazapay, please click [here](https://developer.tazapay.com/docs/tazapay-API-documentation/27k7of4hztyff-kyb).

**2.Get Escrow Status**:

To know the status of a particular transaction, marketplaces can use **GET /v1/escrow/\{txn\_no}**. It will return the state and substate of a particular transaction (in this case, the transaction between Spec Sales and Alice). 

> This will keep all the stakeholders (marketplace, seller and buyer) always informed of the stage of the transaction. 

For more information about the **Get Escrow Status API**, please click [here](https://developer.tazapay.com/docs/tazapay-API-documentation/feb5f2440b7f2-get-escrow-status).

**3.Refund:** 

To refund a buyer for a particular transaction, marketplaces can use **POST v1/payment/refund/request**. 

For more information about the payload, please click [here](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjQ0OTY4NDMw-refund).

If you'd like to know more about our [payment link](https://tazapay.com/payment-links/) feature, head over to our website.
