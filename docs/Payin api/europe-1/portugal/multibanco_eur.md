---
title: multibanco_eur
excerpt: >-
  A widely used payment method in Portugal. It's a network that allows customers
  to make various financial transactions through ATMs, bank branches, and online
  banking.
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

- When making a payment, the customer receives a unique reference number and an entity number.
- They can then make the payment at an ATM using their debit card and entering the provided numbers.
- Alternatively, they can pay at a bank branch or through their online banking platform.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from `multibanco_eur` transaction creation to payment completion.  
Create a payin on your server with an amount, invoice_currency `EUR` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "transaction_description": "test"
}
'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a redirect URL is generated to redirect the customer. The status of the payin moves to `requires_action`

Refer the below for the fields to be passed in `payment_method_details`

### Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin/pay_cttqsgs2ukmk385scqt0/confirm \
     --header 'accept: application/json' \
     --header 'authorization: Basic xxxxxxxXXXXxxxxxxxxxxxxxxxxx' \
     --header 'content-type: application/json' \
     --data '
{
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea@example.com",
    "country": "PT"
  },
  "payment_method_details": {
    "type": "multibanco_eur"
  }
}
'
```

### Combining Steps 1 and 2 into a single step

Instead of making 2 API calls, you can also combine steps 1 and 2 into a single API call. To do so, pass the parameters in both the create payin and confirm payin endpoints to the create payin API.

Also, pass the following field

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
    "country": "PT"
  },
  "confirm": true,
  "invoice_currency": "EUR",
  "amount": 10000,
  "transaction_description": "test",
  "payment_method_details": {
    "type": "multibanco_eur"
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
    "client_token": "vM81aywoK7aM_m8Iikp6fK7CATMirdyeSDQVPUYqvEg=",
    "confirm": true,
    "created_at": "2025-01-06T10:25:05.492177298Z",
    "customer": "cus_cttqoup70g0h95qquumg",
    "customer_details": {
      "country": "PT",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": null
    },
    "holding_currency": "EUR",
    "id": "pay_cttqv042ukmk385scuhg",
    "invoice_currency": "EUR",
    "items": [],
    "latest_payment_attempt": "pat_cttqv0c2ukmk385scuk0",
    "latest_payment_attempt_data": {
      "expires_at": "2025-01-06T10:30:05Z",
      "redirect_url": "https://checkout-sandbox.tazapay.com/single-payment.html?tzid=vM81aywoK7aM_m8Iikp6fK7CATMirdyeSDQVPUYqvEg=&spid=aHR0cHM6Ly9jaGVja291dC1zYW5kYm94LnRhemFwYXkuY29tL3NpbXVsYXRlL3ZNODFheXdvSzdhTV9tOElpa3A2Zks3Q0FUTWlyZHllU0RRVlBVWXF2RWc9L3BheV9jdHRxdjA0MnVrbWszODVzY3VoZy9tdWx0aWJhbmNvX2V1cg=="
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "multibanco_eur"
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

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer within 7 days and the URL expires, Tazapay sends a `payment_attempt.failed` event. To generate a new URL, confirm the payin again using Step 2.

| Event                  | Description                                        | Next Steps                                                                                  |
| ---------------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before the expiration of the URL | Fulfill the goods or services that the customer purchased                                   |
| payment_attempt.failed | The customer did not pay, and the URL expired      | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

- Click on the redirect URL.
- Select dummy `bank` on the redirect page
- A dummy `username` and `password` are already prefilled.
- Click on `Simulate Success` CTA on the redirect_url. You will receive a `payin.succeeded` event.

## Simulating Failure / Expiry

Click on `Simulate Failure` CTA on the redirect_url. You will receive a `payin.failed` event.

# Integrating Refunds

This payment method does not support refunds.