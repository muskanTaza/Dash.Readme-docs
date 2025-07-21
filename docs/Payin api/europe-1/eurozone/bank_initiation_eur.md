---
title: bank_initiation_eur
excerpt: >-
  It is an online payment method that allow customers to directly initiate
  payments from their bank accounts within an online environment.
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

* The customer has to select their bank.
* They are then redirected to their online banking environment (or a secure third-party platform).
* Within their banking environment, they authenticate the payment (e.g., with a password, fingerprint, or one-time code).
* Once authenticated, the payment is instantly transferred to the merchant.

### Where It Works

**Europe (28 EU countries)**

Austria, Belgium, Bulgaria, Cyprus, Czech Republic, Germany, Estonia, Spain, Finland, France, Greece, Hungary, Ireland, Italy, Lithuania, Luxembourg, Latvia, Malta, Netherlands, Poland, Portugal, Romania, Sweden, Slovakia.

`💡The above set of countries are available subject to Tazapay AML Policies`

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from transaction creation to payment completion via bank initiation.\
Create a payin on your server with an amount, invoice\_currency `EUR` and a transaction\_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "invoice_currency": "EUR",
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
    "country": "AT"
  },
  "payment_method_details": {
    "type": "bank_initiation_eur"
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
    "country": "AT"
  },
  "confirm": true,
  "invoice_currency": "EUR",
  "amount": 10000,
  "transaction_description": "test",
  "payment_method_details": {
    "type": "bank_initiation_eur"
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
    "client_token": "lb8Xhsb8UpMRJfGI7Up9CziXB88qjUGy1_nnUqg-UGs=",
    "confirm": true,
    "created_at": "2025-01-06T09:33:10.839403476Z",
    "customer": "cus_cttpk0970g0h95qqusfg",
    "customer_details": {
      "country": "AT",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": null
    },
    "holding_currency": "EUR",
    "id": "pay_cttq6lk2ukmk385sbpo0",
    "invoice_currency": "EUR",
    "items": [],
    "latest_payment_attempt": "pat_cttq6lk2ukmk385sbpq0",
    "latest_payment_attempt_data": {
      "expires_at": "2025-01-06T09:38:10Z",
      "redirect_url": "https://checkout-sandbox.tazapay.com/single-payment.html?tzid=lb8Xhsb8UpMRJfGI7Up9CziXB88qjUGy1_nnUqg-UGs=&spid=aHR0cHM6Ly9jaGVja291dC1zYW5kYm94LnRhemFwYXkuY29tL3NpbXVsYXRlL2xiOFhoc2I4VXBNUkpmR0k3VXA5Q3ppWEI4OHFqVUd5MV9ublVxZy1VR3M9L3BheV9jdHRxNmxrMnVrbWszODVzYnBvMC9iYW5rX2luaXRpYXRpb25fZXVy"
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "bank_initiation_eur"
    },
    "reference_id": "",
    "shipping_details": null,
    "statement_descriptor": "",
    "status": "requires_action",
    "status_description": "",
    "success_url": "",
    "transaction_data": [],
    "transaction_description": "test",
    "transaction_documents": [],
    "webhook_url": ""
  }
}
```

> You must redirect the customer to `latest_payment_attempt_data.redirect_url` in order to enable them to complete the payment.

## Step 4: Handle post-payment events

Tazapay sends a `payin.processing` event for bank initiated transactions to the merchants. Once the payment is made by the customer and our team gets the funds sighted, they approve the payin as succeeded which triggers another event  `payin.succeeded`. Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer and the URL expires, Tazapay sends a `payment_attempt.failed` after the `payin.processing` event. To generate a new URL, confirm the payin again using Step 2.

| Event                   | Description                                   | Next Steps                                                                                  |
| ----------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------- |
| payin.succeeded         | The customer paid before 30 days              | Fulfill the goods or services that the customer purchased                                   |
| payment\_attempt.failed | The customer did not pay, and the URL expired | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

Click on `Simulate Success` CTA on the redirect\_url. You will receive a `payin.succeeded` event.

## Simulating Failure / Expiry

Click on `Simulate Failure` / `Simulate Expire` CTA on the redirect\_url. You will receive a `payment_attempt.failed` event.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Bank Initiation supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

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
  "amount": 5000,
  "currency": "EUR",
  "reason": "Customer Return",
  }
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.