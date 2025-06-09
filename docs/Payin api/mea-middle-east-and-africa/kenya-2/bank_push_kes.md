---
title: bank_push_kes
excerpt: >-
  It is the process of initiating a bank transfer directly from a merchant's
  system to a customer's bank account widely used in Kenya. While not as
  prominent as mobile money solutions like M-Pesa, bank push payments are
  gaining traction in Kenya.
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

- Businesses initiate fund transfers directly to customers' bank accounts.
- Customers receive notifications (e.g., SMS, email) about the incoming funds.
- Some instances may require customer authorization within their online banking.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from transaction creation to payment completion via bank push.  
Create a payin on your server with an amount, invoice_currency `KES` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "invoice_currency": "KES",
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
    "country": "KE"
  },
  "payment_method_details": {
    "type": "bank_push_kes"
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
    "country": "KE"
  },
  "confirm": true,
  "invoice_currency": "KES",
  "amount": 10000,
  "transaction_description": "test",
  "payment_method_details": {
    "type": "bank_push_kes"
  }
}
'
```

## Step 3: Getting a success response for the payin created

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
    "client_token": "ZDruXQwumFeVZFmOYrHaF-yTFuMHlaLN8UjSh8XGv-Y=",
    "confirm": false,
    "created_at": "2025-01-23T07:25:14.713723030Z",
    "customer": "cus_cu8us2slppnoaibo23bg",
    "customer_details": {
      "country": "KE",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": null
    },
    "holding_currency": "USD",
    "id": "pay_cu8utminbet4snrlvl3g",
    "invoice_currency": "KES",
    "items": [],
    "latest_payment_attempt": "",
    "latest_payment_attempt_data": null,
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "bank_push_kes"
    },
    "reference_id": "",
    "shipping_details": null,
    "statement_descriptor": "",
    "status": "requires_payment_method",
    "status_description": "",
    "success_url": "",
    "transaction_data": [],
    "transaction_description": "Test",
    "transaction_documents": [],
    "webhook_url": ""
  }
}
```

> You must instruct the customer to approve the payment (if not auto complete) to complete the payment.

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer.  Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer and the URL expires, Tazapay sends a `payment_attempt.failed` after the `payin.processing` event. To generate a new URL, confirm the payin again using Step 2.

| Event                  | Description                                   | Next Steps                                                                                  |
| ---------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before 5 days               | Fulfill the goods or services that the customer purchased                                   |
| payment_attempt.failed | The customer did not pay, and the URL expired | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

Click on `Simulate Success` CTA on the redirect_url. You will receive a `payin.succeeded` event.

## Simulating Failure / Expiry

Click on `Simulate Failure` CTA on the redirect_url. You will receive a `payment_attempt.failed` event.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Bank Push in Kenya supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

### Refunding using dashboard

Refer to this guide: <https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard>

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
  "currency": "KES",
  "reason": "Customer Return",
  }
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.