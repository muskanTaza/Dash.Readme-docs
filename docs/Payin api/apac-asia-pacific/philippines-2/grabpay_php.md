---
title: grabpay_php
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
GrabPay is a digital wallet payment method in the Philippines, enabling customers to make secure online and in-store transactions using their GrabPay balance. It supports instant payments and is widely accepted across local merchants.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a payin object to represent your intent to collect a payment from your customer. The payin object tracks state changes from grabpay transaction creation to payment completion.  
Create a payin on your server with an amount, invoice_currency PHP and a transaction_description using the create payin API

A payin is created with the status requires_payment_method.

### Sample cURL

```
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '{
  "invoice_currency": "PHP",
  "amount": 100000,
  "transaction_description": "1 X Goods",
  "webhook_url": "https://webhook.site/ref8y92937922"
}'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the [confirm payin API](https://docs.tazapay.com/reference/confirm-payin). Upon confirmation of the payin, a redirection URL is generated. The status of the payin moves to requires_action

### Sample cURL

```
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin/pay_uiabfuiahfanwofihwnwon/confirm \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80HFt' \
     --header 'content-type: application/json' \
     --data '
{
  "customer_details": {
    "name": "Lily",
    "email": "lily@tazapay.com",
    "country": "PH"
  },
  "payment_method_details": {
    "type": "grabpay_php"
  }
}'
```

## Combining Steps 1 and 2 into a single step

Instead of making 2 API calls, you can also combine steps 1 and 2 into a single API call. To do so, pass the parameters in both the create payin and confirm payin endpoints to the create payin API.

Also, pass the following field and set confirm equals true.

| Field   | type    | Mandatory (Y/N) | Description                              |
| ------- | ------- | --------------- | ---------------------------------------- |
| confirm | boolean | Y               | To confirm the payin along with creation |

### Sample cURL

```json
curl --location 'https://service-sandbox.tazapay.com/v3/payin' \
--header 'accept: application/json' \
--header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEMSEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
--header 'content-type: application/json' \
--data-raw '{
  "invoice_currency": "PHP",
  "amount": 100000,
  "transaction_description": "1 X Good",
  "webhook_url": "https://webhook.site/ref8y92937922",
	"success_url":"https://mypage.success",
  "cancel_url":"https://mypage.failure",
  "confirm":true,
  "customer_details": {
    "name": "Lily",
    "email": "lily@tazapay.com",
    "country": "PH"
  },
  "payment_method_details": {
    "type": "grabpay_php"
    }
  }'
```

## Step 3: Redirect the customer to the payment URL

After confirming the payin, you will receive the following response. You will receive a redirect_url where you can redirect your customer to. You must redirect the customer to `latest_payment_attempt_data.redirect_url` in order to enable them to complete the payment.

```
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 100000,
        "amount_paid": 0,
        "billing_details": null,
        "cancel_url": "https://mypage.failure",
        "cancelled_at": null,
        "client_token": "4VlAL5BwbdHTgCtNY9KuXhCl4cOWymutVwLLWhooTtU=",
        "confirm": true,
        "created_at": "2025-01-07T07:50:34.551592559Z",
        "customer": "cus_ctudcp970g0h95qqvb30",
        "customer_details": {
            "country": "PH",
            "email": "lily@tazapay.com",
            "name": "Lily",
            "phone": null
        },
        "holding_currency": "USD",
        "id": "pay_ctudpik2ukmk385t6gv0",
        "invoice_currency": "PHP",
        "items": [],
        "latest_payment_attempt": "pat_ctudpik2ukmk385t6h10",
        "latest_payment_attempt_data": {
            "expires_at": "2025-01-07T07:55:34Z",
            "redirect_url": "https://checkout-sandbox.tazapay.com/single-payment.html?tzid=4VlAL5BwbdHTgCtNY9KuXhCl4cOWymutVwLLWhooTtU=&spid=aHR0cHM6Ly9jaGVja291dC1zYW5kYm94LnRhemFwYXkuY29tL3NpbXVsYXRlLzRWbEFMNUJ3YmRIVGdDdE5ZOUt1WGhDbDRjT1d5bXV0VndMTFdob29UdFU9L3BheV9jdHVkcGlrMnVrbWszODV0Nmd2MC9ncmFicGF5X3BocA=="
        },
        "metadata": null,
        "object": "payin",
        "paid_in_excess": false,
        "partially_paid": false,
        "payment_attempts": [],
        "payment_method_details": {
            "type": "grabpay_php"
        },
        "reference_id": "",
        "shipping_details": null,
        "statement_descriptor": "",
        "status": "requires_action",
        "status_description": "",
        "success_url": "https://mypage.success",
        "transaction_data": [],
        "transaction_description": "1 X Good",
        "transaction_documents": [],
        "webhook_url": "https://webhook.site/ref8y92937922"
    }
}
```

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer within 15 mins minutes and the URL expires, Tazapay sends a `payment_attempt.failed` event. To generate a new URL, confirm the payin again using Step 2.

| Event                  | Description                                                    | Next Steps                                                                                      |
| ---------------------- | -------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before the expiration of the payment request | Fulfill the goods or services that the customer purchased                                       |
| payment_attempt.failed | The customer did not pay and the request expired               | Allow the customer to generate a new request or complete the payment via another payment method |

## Expiration and cancellation

Grabpay requests expire after 15 minutes and the customer cannot pay once the request has expired. After expiration, the status of the payin changes to `requires_payment_method.` At this point, you can confirm the payin with another payment method or cancel.

# Test the Integration

You can simulate the following scenarios on the `redirect_url`

1. Successful Payment - Click on `Simulate Success` CTA. A `payin.succeeded` event will be triggered. The status of the payin will change to `succeeded`.
2. Failed Payment - Click on `Simulate Failure` CTA. A `payment_attempt.failed` event will be triggered. The status of the payin will change to `requires_payment_method`.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Grabpay supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

### Refunding using dashboard

Refer to this guide: <https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard>

### Refund using API

Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/refund \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "payin": "pay_ctrt9l1jbc4tc23vsmdg",
  "amount":1000,
  "currency": "PHP",
  "reason": "Customer Return",
  "webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.