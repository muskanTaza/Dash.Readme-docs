---
title: eps_eur
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
EPS (Electronic Payment Standard) is a popular online payment method in Austria, designed for secure and seamless transactions.

### How It Works

1. Customers are redirected to their online banking portal.
2. After logging in, they review and authorize the payment, which is processed instantly.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from EPS transaction creation to payment completion.

Create a payin on your server with an amount, invoice_currency `EUR` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

A payin is created with the status `requires_payment_method`.

### Sample cURL

```bash
curl --request POST \
  --url https://service-sandbox.tazapay.com/v3/payin \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "invoice_currency": "EUR",
  "amount": 10000,
  "transaction_description": "1 X Good"
}'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a redirect URL is generated to redirect the customer. The status of the payin moves to `requires_action`

Refer the below for the fields to be passed in `payment_method_details`

### Sample cURL

```bash
curl --request POST \
  --url https://service-sandbox.tazapay.com/v3/payin/pay_ctrtfvpjbc4tc23vt0kg/confirm \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "customer_details":{
    "name":"Andrea Lark",
    "email":"andrea.lark@me.com",
    "country":"AT"
  },
  "payment_method_details":{
    "type":"eps_eur"
  }
}'
```

### Combining Steps 1 and 2 into a single step

Instead of making 2 API calls, you can also combine steps 1 and 2 into a single API call. To do so, pass the mandatory parameters in both the create payin and confirm payin endpoints to the create payin API.

Also set the confirm field to `true`

| Field   | type    | Mandatory (Y/N) | Description                              |
| ------- | ------- | --------------- | ---------------------------------------- |
| confirm | boolean | Y               | To confirm the payin along with creation |

### Sample cURL

```bash
curl --request POST \
  --url https://service-sandbox.tazapay.com/v3/payin \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "invoice_currency":"EUR",
  "amount":10000,
  "transaction_description":"1 x Good",
  "confirm":true,
  "customer_details":{
    "name":"Andrea Lark",
    "email":"andrea.lark@me.com",
    "country":"AT"
  },
  "payment_method_details":{
    "type":"eps_eur"
  }
}'
```

## Step 3: Redirect the customer to their bank payment URL

After confirming the payin, you will receive the following response

```bash
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 10000,
    "amount_paid": 0,
    "billing_details": null,
    "cancel_url": "",
    "cancelled_at": null,
    "client_token": "Un_MYNEgrcJt9lZ7IhV7jQxl5Jq03_lvO__SU_P_pp4=",
    "confirm": true,
    "created_at": "2025-01-03T12:56:12.465664211Z",
    "customer": "cus_ctrtj91th2io13jiascg",
    "customer_details": {
      "country": "AT",
      "email": "andrea.lark@me.com",
      "name": "Andrea Lark",
      "phone": null
    },
    "holding_currency": "EUR",
    "id": "pay_ctrtsqpjbc4tc23vti20",
    "invoice_currency": "EUR",
    "items": [],
    "latest_payment_attempt": "pat_ctrtsr1jbc4tc23vti4g",
    "latest_payment_attempt_data": {
      "expires_at": "2025-01-03T13:01:12Z",
      "redirect_url": "https://checkout-sandbox.tazapay.com/single-payment.html?tzid=Un_MYNEgrcJt9lZ7IhV7jQxl5Jq03_lvO__SU_P_pp4=&spid=aHR0cHM6Ly9jaGVja291dC1zYW5kYm94LnRhemFwYXkuY29tL3NpbXVsYXRlL1VuX01ZTkVncmNKdDlsWjdJaFY3alF4bDVKcTAzX2x2T19fU1VfUF9wcDQ9L3BheV9jdHJ0c3FwamJjNHRjMjN2dGkyMC9lcHNfZXVy"
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "eps_eur"
    },
    "reference_id": "",
    "shipping_details": null,
    "statement_descriptor": "",
    "status": "requires_action",
    "status_description": "",
    "success_url": "",
    "transaction_data": [],
    "transaction_description": "1 x Good",
    "transaction_documents": [],
    "webhook_url": ""
  }
}
```

You must redirect the customer to `latest_payment_attempt_data.redirect_url` in order to enable them to complete the payment.

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer within 60 minutes and the URL expires, Tazapay sends a `payment_attempt.failed` event. To generate a new URL, confirm the payin again using Step 2.

| Event                  | Description                                  | Next Steps                                                                                  |
| ---------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before 60 minutes          | Fulfill the goods or services that the customer purchased                                   |
| payment_attempt.failed | The customer did not pay and the URL expired | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

Click on `Simulate Success` CTA on the redirect_url. You will receive a `payin.succeeded` event.

## Simulating Failure / Expiry

Click on `Simulate Failure` CTA on the redirect_url. You will receive a `payin.failed` event.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com/) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

EPS supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

### Refunding using dashboard.

Refer to this guide: <https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard>

### Refund using API

Sample cURL

```json
curl --request POST \\
     --url <https://service-sandbox.tazapay.com/v3/refund> \\
     --header 'accept: application/json' \\
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \\
     --header 'content-type: application/json' \\
     --data '
{
  "payin": "pay_cn10i0s6bt2fq1jlr0e0",
  "amount": 1000,
  "currency": "EUR",
  "reason": "Customer Return"
}
'

```

> NOTE: For full refund, specifying the amount and currency is not required to initiate a refund.