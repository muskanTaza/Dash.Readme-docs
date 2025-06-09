---
title: mobile_money_ugx
excerpt: >-
  A dominant force in the country's financial landscape, offering a wide range
  of financial services to millions of Ugandans.
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

* Users register for mobile money services with their mobile phone numbers.
* They can deposit and withdraw cash through a vast network of mobile money agents.
* Send and receive money to other users instantly.
* Pay bills, purchase airtime, and even access micro-loans and savings accounts.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from transaction creation to payment completion via mobile money.\
Create a payin on your server with an amount, invoice\_currency `UGX` and a transaction\_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "invoice_currency": "UGX",
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
    "country": "UG"
  },
  "payment_method_details": {
    "type": "mobile_money_ugx"
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
    "country": "UG"
  },
  "confirm": true,
  "invoice_currency": "UGX",
  "amount": 10000,
  "transaction_description": "test",
  "payment_method_details": {
    "type": "mobile_money_ugx"
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
    "client_token": "diNZgYbkex4DDaGbkFEnHv8kNzccQ0Btr_b1wr_8biw=",
    "confirm": true,
    "created_at": "2025-01-23T07:39:58.377683520Z",
    "customer": "cus_cu8v4jklppnoaibo23gg",
    "customer_details": {
      "country": "UG",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": null
    },
    "holding_currency": "USD",
    "id": "pay_cu8v4janbet4snrlvvig",
    "invoice_currency": "UGX",
    "items": [],
    "latest_payment_attempt": "pat_cu8v4jinbet4snrlvvl0",
    "latest_payment_attempt_data": {
      "expires_at": "2025-01-23T07:44:58Z",
      "redirect_url": "https://checkout-sandbox.tazapay.com/single-payment.html?tzid=diNZgYbkex4DDaGbkFEnHv8kNzccQ0Btr_b1wr_8biw=&spid=aHR0cHM6Ly9jaGVja291dC1zYW5kYm94LnRhemFwYXkuY29tL3NpbXVsYXRlL2RpTlpnWWJrZXg0RERhR2JrRkVuSHY4a056Y2NRMEJ0cl9iMXdyXzhiaXc9L3BheV9jdTh2NGphbmJldDRzbnJsdnZpZy9tb2JpbGVfbW9uZXlfdWd4"
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "mobile_money_ugx"
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
| payin.succeeded         | The customer paid before 5 days               | Fulfill the goods or services that the customer purchased                                   |
| payment\_attempt.failed | The customer did not pay, and the URL expired | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

Click on `Simulate Success` CTA on the redirect\_url. You will receive a `payin.succeeded` event.

## Simulating Failure

Click on  `Simulate Failure` CTA on the redirect\_url. You will receive a `payment_attempt.failed` event.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Mobile Money supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

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
  "currency": "UGX",
  "reason": "Customer Return",
  }
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.
