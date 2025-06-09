---
title: Payout Orchestration In-Depth Guide
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

You are a marketplace looking to pay your beneficiaries (sellers, freelancers, service providers, etc.) on a regular basis via seamless cross-border payment rails. This in-depth guide will help you integrate with Tazapay’s developer tools and APIs to leverage Tazapay’s payments system.

You can pass the following information to Tazapay’s API to orchestrate payouts:

- Beneficiary’s country
- E-mail ID of the beneficiary
- Beneficiary Name
- Payment currency (e.g. USD, INR, EUR, etc.)
- Amount
- Transaction description

## Step 1: Creating User Entities

For a payout transaction to happen, two user entities need to exist within Tazapay’s database - a seller entity and a buyer entity. Marketplaces need to create an additional marketplace entity. In this instance, the beneficiary for payouts will be set as the seller. 

To create entities: Use **POST /v1/user**.

For example, Slydeshow, a freelancer platform based in Singapore, wants to register itself as an entity at Tazapay.

Slydeshow submits the following payload for the body.

```
{
    "email": "info@slydeshow.com",
    "country": "SG",
    "ind_bus_type": "Business",
    "business_name":"Slydeshow Pte. Ltd."
}
```

Tazapay creates a user entity for Slydeshow and returns the following response. 

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "dbf835e1-be96-497a-b57e-91bb2cfc3aae",
       "customer_id": ""
   }
}
```

**Account_id** in this instance will also be the unique user identifier (**UUID**), which will be used in any form of transactions including payout. 

Slydeshow wants to execute payout to their freelancers, known as sellers in Tazapay’s parlance, on their platform. They are Alice, Bob, and Charlie. All of these freelancers would need to be in Tazapay’s database, so user entities are created for them using **POST /v1/user**. 

**The payload for the request looks like this:**

This is for Alice, who is based in Malaysia:

```
{
    "email": "alice@hmail.com",
    "country": "MY",
    "ind_bus_type": "Individual",
    "first_name":"Alice",
    "last_name":"Lorem"
}
```

This is for Bob, who is based in India:

```
{
    "email": "bob@bladesong.com",
    "country": "IN",
    "ind_bus_type": "Individual",
    "first_name":"Bob",
    "last_name":"Bladesong"
}
```

This is for Charlie, who is based in the Philippines:

```
{
    "email": "charlie@popmail.com",
    "country": "PH",
    "ind_bus_type": "Individual",
    "first_name":"Charlie",
    "last_name":"Ipsum"
}
```

Tazapay would individually return responses that would look like this for all 3 users.

This is for Alice

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "221fd398-cba8-45d0-ae6a-f89960c5eee4",
       "customer_id": ""
   }
}
```

This is for Bob

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "8114d7ba-7ee1-430b-8979-af28bf05d7d4",
       "customer_id": ""
   }
}
```

This is for Charlie

```
{
   "status": "success",
   "message": "User created successfully",
   "data": {
       "account_id": "2099935e-3ce4-4aa7-af84-230f0df663d8",
       "customer_id": ""
   }
}
```

The account_id acts as the UUID for Alice, Bob, and Charlie. Slydeshow stores these IDs in its database.

For more details about how to manage entities using Tazapay’s endpoints, please [click](https://developer.tazapay.com/docs/tazapay-API-documentation/f1e6a64cb9051-users) here to get redirected to the relevant part of our documentation.

## Step 2: Creating the units of transaction (escrow in Tazapay’s parlance)

For a unit of transaction to be created, Slydeshow would need to use POST /v1/escrow. 

Slydeshow can customise the transaction (in terms of fee collection, transaction costs, etc.) in this step. To pay for all 3 freelancers, Slydeshow must create 3 units of transactions

Slydeshow submits the following payload to POST /v1/escrow for Alice:

```
{
   "Txn_type": "service",
   "initiated_by": "dbf835e1-be96-497a-b57e-91bb2cfc3aae",
   "buyer_id": "dbf835e1-be96-497a-b57e-91bb2cfc3aae",
   "seller_id": "221fd398-cba8-45d0-ae6a-f89960c5eee4",
   "txn_description": "Monthly Payout",
   "transaction_category": "payout",
   "invoice_currency": "MYR",
   "invoice_amount": 2500
}
```

This is the payload for Bob:

```
{
   "Txn_type": "service",
   "initiated_by": "dbf835e1-be96-497a-b57e-91bb2cfc3aae",
   "buyer_id": "dbf835e1-be96-497a-b57e-91bb2cfc3aae",
   "seller_id": "8114d7ba-7ee1-430b-8979-af28bf05d7d4",
   "txn_description": "Monthly Payout",
   "transaction_category": "payout",
   "invoice_currency": "INR",
   "invoice_amount": 44000
}
```

This is the payload for Charlie:

```
{
   "Txn_type": "service",
   "initiated_by": "dbf835e1-be96-497a-b57e-91bb2cfc3aae",
   "buyer_id": "dbf835e1-be96-497a-b57e-91bb2cfc3aae",
   "seller_id": "2099935e-3ce4-4aa7-af84-230f0df663d8",
   "txn_description": "Monthly Payout",
   "transaction_category": "payout",
   "invoice_currency": "PHP",
   "invoice_amount": 30000
}
```

The initiated_by field is Slydeshow’s UUID because the platform is paying out to their users, in this case Alice, Bob, and Charlie. 

Buyer_id is Slydeshow’s UUID since they are the account paying out to the user, and seller_id is Alice, Bob, and Charlie’s UUID because they are the beneficiary/recipient of the payout. 

Transaction_category is set to payout to indicate that it is a payout and not a sale of goods or services. Invoice currency and invoice amount are also entered in the payload. 

The Tazapay transactions will be created and the following responses are returned.

This is the response for Alice:

```
{
   "status": "success",
   "message": "escrow created successfully",
   "data": {
       "txn_no": "2206-082912",
       "state": "Escrow_Funds_Received",
       "sub_state": "na",
       "txn_type": "service",
       "invoice_currency": "MYR",
       "invoice_amount": 2500,
       "fee_tier": "standard",
       "fee_paid_by": "buyer",
       "fee_tier_percentage": 1.8,
       "fee_amount": 45,
       "collect_amount": 2500,
       "disburse_amount": 2455,
       "transcation_source": "api"
   }
}
```

This is the response for Bob:

```
{
   "status": "success",
   "message": "escrow created successfully",
   "data": {
       "txn_no": "2206-447487",
       "state": "Escrow_Funds_Received",
       "sub_state": "na",
       "txn_type": "service",
       "invoice_currency": "INR",
       "invoice_amount": 44000,
       "fee_tier": "standard",
       "fee_paid_by": "buyer",
       "fee_tier_percentage": 1.8,
       "fee_amount": 45,
       "collect_amount": 44000,
       "disburse_amount": 43208,
       "transcation_source": "api"
   }
}
```

This is the response for Charlie:

```
{
   "status": "success",
   "message": "escrow created successfully",
   "data": {
       "txn_no": "2206-687869",
       "state": "Escrow_Funds_Received",
       "sub_state": "na",
       "txn_type": "service",
       "invoice_currency": "PHP",
       "invoice_amount": 30000,
       "fee_tier": "standard",
       "fee_paid_by": "buyer",
       "fee_tier_percentage": 1.8,
       "fee_amount": 45,
       "collect_amount": 30000,
       "disburse_amount": 29460,
       "transcation_source": "api"
   }
}
```

The ‘txn_no’ is a unique number representing this particular transaction. Slydeshow stores this in its database.

> 📘 Currency and Amount in the Request Body:
> 
> The currency and amount that you enter in the request body is the amount and currency that the beneficiary will receive. In case, a bank account is not added in that currency for the beneficiary, there will be an FX conversion before the transfer.

The fee_amount of 45 MYR, 792 INR, and 540 PHP will be deducted by Tazapay respectively before disbursing the funds.

> NOTE: You can also customise for the transaction fees to be borne by Slydeshow. For more details, read more in our [Create Escrow](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTA4-create-escrow#body-parameters) part of the documentation.

## Step 3: Releasing the Payout

Slydeshow can authorise the release of the payout to their freelancers by submitting the following payload in /v1/session/release. Each transaction unit requires an individual release session.

This is the submission for Alice

```
{
   "txn_no": "2206-082912"
}
```

This is the submission for Bob

```
{
   "txn_no": "2206-447487"
}
```

This is the submission for Charlie

```
{
   "txn_no": "2206-687869"
}
```

The payment (MYR 2455) gets credited in Alice’s account after deduction of the transaction fees. This is the response from the release API.

```
{
   "status": "success",
   "message": "release session created successfully",
   "data": {
       "reference_id": "f166f9f5-1ed4-4d2a-85cb-07bb14575b9e"
   }
}
```

The payment (INR 43208) gets credited in Bob’s account after deduction of the transaction fees. This is the response from the release API.

```
{
   "status": "success",
   "message": "release session created successfully",
   "data": {
       "reference_id": "2b83c172-6f57-4219-93c4-714c451757e4"
   }
}
```

The payment (PHP 29460) gets credited in Charlie’s account after deduction of the transaction fees. This is the response from the release API.

```
{
   "status": "success",
   "message": "release session created successfully",
   "data": {
       "reference_id": "3596b851-5e38-4718-944b-17e0b7eccb6e"
   }
}
```

We have more details about the Release API [here](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTEy-release).

Apart from the above APIs, you will also need to use the following APIs at some point during the integration process:

1\.**Post KYB**: KYB stands for Know Your Business, To disburse funds into the seller’s account (in this case, Alice, Bob, and Charlie), the seller will have to undergo a one-time verification exercise before the first disbursal by Tazapay. It is a standard risk management practice aimed at eliminating money laundering. POST/v2/kyb can be used to add the required documents on Tazapay’s server for KYB verification of the sellers. For more information about the KYB facilities provided by Tazapay, please click [here](https://developer.tazapay.com/docs/tazapay-API-documentation/27k7of4hztyff-kyb).

2. **Get Escrow Status:** To know the status of a particular underlying transaction, marketplaces can use GET /v1/escrow/{txn_no}. It will return the state and substate of a particular transaction (in this case, the payout between Slydeshow and the freelancers). This will keep all the stakeholders (marketplace and seller) always informed of the stage of the transaction. For more information about the Get Escrow Status API, please click [here](https://developer.tazapay.com/docs/tazapay-API-documentation/feb5f2440b7f2-get-escrow-status).

For more details about Tazapay’s pre-built solutions and developer tools, please visit our [documentation](https://developer.tazapay.com).