---
title: shopeepay_vnd
excerpt: >-
  A popular mobile wallet and payment service in Vietnam deeply integrated
  within the Shopee e-commerce platform.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
### How It Works

* Users link their Vietnamese bank accounts or top up their ShopeePay wallets.
* Primarily used for seamless and secure transactions within the Shopee app but also accepted by a growing number of offline merchants.
* Payments are made through the app, often via QR code scanning.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from transaction creation to payment completion via shopeepay.\
Create a payin on your server with an amount, invoice\_currency `VND` and a transaction\_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

A payin is created with the status `requires_payment_method`.

### Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin \
     --header 'accept: application/json' \
     --header 'authorization: Basic xxxxxxxXXXXxxxxxxxxxxxxxxxxx' \
     --header 'content-type: application/json' \
     --data '
{
  "invoice_currency": "VND",
  "amount": 10000,
  "transaction_description": "Test",
}
'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a redirect URL is generated to redirect the customer. The status of the payin moves to `requires_action`

Refer the below for the fields to be passed in `payment_method_details`

### Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin/pay_cttprok2ukmk385sbfm0/confirm \
     --header 'accept: application/json' \
     --header 'authorization: Basic xxxxxxxXXXXxxxxxxxxxxxxxxxxx' \
     --header 'content-type: application/json' \
     --data '
{
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea@example.com",
    "country": "VN"
  },
  "payment_method_details": {
    "type": "shopeepay_vnd"
  }
}
'
```

### Combining Steps 1 and 2 into a single step

Instead of making 2 API calls, you can also combine steps 1 and 2 into a single API call. To do so, pass the parameters in both the create payin and confirm payin endpoints to the create payin API.

Also, pass the following field and set the field to ‘true’

| Field   | type    | Mandatory (Y/N) | Description                              |
| ------- | ------- | --------------- | ---------------------------------------- |
| confirm | boolean | Y               | To confirm the payin along with creation |

### Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin \
     --header 'accept: application/json' \
     --header 'authorization: Basic xxxxxxxXXXXxxxxxxxxxxxxxxxxx' \
     --header 'content-type: application/json' \
     --data '
{
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea@example.com",
    "country": "VN"
  },
  "confirm": true,
  "invoice_currency": "VND",
  "amount": 10000,
  "transaction_description": "test",
  "payment_method_details": {
    "type": "shopeepay_vnd"
  }
}
'
```

## Step 3: Redirect the customer to the redirect URL

After confirming the payin, you will receive the following response

```json
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 10000,
    "amount_paid": 0,
    "billing_details": null,
    "cancel_url": "",
    "cancelled_at": null,
    "client_token": "TRoRcFApPP6BTxVvRWHCiXo3SJ56_FSoWWh1D3qjBts=",
    "confirm": true,
    "created_at": "2025-01-23T08:02:19.895460705Z",
    "customer": "cus_cu8vc74lppnoaibo23lg",
    "customer_details": {
      "country": "VN",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": null
    },
    "holding_currency": "USD",
    "id": "pay_cu8vf2qnbet4snrm0gf0",
    "invoice_currency": "VND",
    "items": [],
    "latest_payment_attempt": "pat_cu8vf2qnbet4snrm0ghg",
    "latest_payment_attempt_data": {
      "expires_at": "2025-01-23T08:07:19Z",
      "redirect_url": "https://checkout-sandbox.tazapay.com/single-payment.html?tzid=TRoRcFApPP6BTxVvRWHCiXo3SJ56_FSoWWh1D3qjBts=&spid=aHR0cHM6Ly9jaGVja291dC1zYW5kYm94LnRhemFwYXkuY29tL3NpbXVsYXRlL1RSb1JjRkFwUFA2QlR4VnZSV0hDaVhvM1NKNTZfRlNvV1doMUQzcWpCdHM9L3BheV9jdTh2ZjJxbmJldDRzbnJtMGdmMC9zaG9wZWVwYXlfdm5k"
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "shopeepay_vnd"
    },
    "reference_id": "",
    "shipping_details": null,
    "statement_descriptor": "",
    "status": "requires_action",
    "status_description": "",
    "success_url": "",
    "transaction_data": [],
    "transaction_description": "Test",
    "transaction_documents": [],
    "webhook_url": ""
  }
}
```

> You must redirect the customer to `latest_payment_attempt_data.redirect_url` in order to enable them to complete the payment.

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer.  Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer and the URL expires, Tazapay sends a `payment_attempt.failed`  event. To generate a new URL, confirm the payin again using Step 2.

| Event                   | Description                                   | Next Steps                                                                                  |
| ----------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------- |
| payin.succeeded         | The customer paid before 25 minutes.          | Fulfill the goods or services that the customer purchased                                   |
| payment\_attempt.failed | The customer did not pay, and the URL expired | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

Click on `Simulate Success` CTA on the redirect\_url. You will receive a `payin.succeeded` event.

## Simulating Failure

Click on  `Simulate failure` CTA on the redirect\_url. You will receive a `payment_attempt.failed` event.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Shopeepay doesnt support partial refunds. 

### Refunding using dashboard

Refer to this guide: [https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard](https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard)

### Refund using API

Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/refund \
     --header 'accept: application/json' \
     --header 'authorization: Basic xxxxxxxXXXXxxxxxxxxxxxxxxxxx' \
     --header 'content-type: application/json' \
     --data '
{
  "payin": "pay_cmiiaamaq0pbt3fkadm0",
  "amount": 10000,
  "currency": "VND",
  "reason": "Customer Return",
  }
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.
