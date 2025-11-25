---
title: bank_push_idr
deprecated: false
hidden: false
metadata:
  robots: index
---
Online Banking enables secure real-time payments directly from Indonesia bank accounts, offering a convenient option for e-commerce and bill payments.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a payin object to represent your intent to collect a payment from your customer. The payin object tracks state changes from bank_push transaction creation to payment completion.  
Create a payin on your server with an amount, invoice_currency IDR and a transaction_description using the create payin API

A payin is created with the status requires_payment_method.

### Sample cURL

```
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '{
  "invoice_currency": "IDR",
  "amount": 100000,
  "transaction_description": "1 X Goods",
  "webhook_url": "https://webhook.site/ref8y92937922"
}'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the [confirm payin API.](https://docs.tazapay.com/reference/confirm-payin) Upon confirmation of the payin, a redirection URL is generated. The status of the payin moves to requires_action

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
    "name": "Andrea Lark",
    "email": "andrea.lark@tazapay.com",
    "country": "ID"
  },
  "payment_method_details": {
    "type": "bank_push_idr"
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
  "invoice_currency": "IDR",
  "amount": 10000000,
  "transaction_description": "1 X Good",
  "webhook_url": "https://webhook.site/ref8y92937922",
  "confirm":true,
	"success_url":"https://mypage.success",
  "cancel_url":"https://mypage.failure",
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea.lark@tazapay.com",
    "country": "ID"
  },
  "payment_method_details": {
    "type": "bank_push_idr",
    "bank_push_idr": {
        "bank_name":"BNI"
    }
    }
  }
'
```

## Step 3: Redirect the customer to the payment URL

After confirming the payin, you will receive the following response. You will receive a redirect_url where you can redirect your customer to. You must redirect the customer to `latest_payment_attempt_data.redirect_url` in order to enable them to complete the payment.

```
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 10000000,
        "amount_paid": 0,
        "billing_details": null,
        "cancel_url": "https://mypage.failure",
        "cancelled_at": null,
        "client_token": "FVRgT8_kJGtt3MYj3J5zoben-wl4_mJJkNcmse_ykHU=",
        "confirm": true,
        "created_at": "2025-11-25T06:27:17.633557362Z",
        "customer": "cus_d4fd90np3mil5glh0fh0",
        "customer_details": {
            "country": "ID",
            "email": "andrea.lark@tazapay.com",
            "name": "Andrea Lark",
            "phone": null
        },
        "form": "",
        "holding_currency": "IDR",
        "id": "pay_d4ikoh03f4q3iicmm2a0",
        "invoice_currency": "IDR",
        "items": [],
        "latest_payment_attempt": "pat_d4ikoh03f4q3iicmm2c0",
        "latest_payment_attempt_data": {
            "bank": {
                "account_number": "9882917230376055",
                "bank_name": "BNI",
                "reference_id": "2511-cmm2a0"
            }
        },
        "metadata": null,
        "object": "payin",
        "paid_in_excess": false,
        "partially_paid": false,
        "payment_attempts": [],
        "payment_method_details": {
            "bank_push_idr": {
                "bank_name": "BNI"
            },
            "type": "bank_push_idr"
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

| Event                  | Description                                             | Next Steps                                                                     |
| ---------------------- | ------------------------------------------------------- | ------------------------------------------------------------------------------ |
| payin.succeeded        | The customer successfully completed the payment request | Fulfill the goods or services that the customer purchased                      |
| payment_attempt.failed | The customer payment attempt failed                     | Allow the customer to do the payment again with same or another payment method |

## Expiration and cancellation

There is no expiration for this payment method.

# Test the Integration

You can simulate the following scenarios on the `redirect_url`

1. Successful Payment - Click on `Simulate Success` CTA. A `payin.succeeded` event will be triggered. The status of the payin will change to `succeeded`.
2. Failed Payment - Click on `Simulate Failure` CTA. A `payment_attempt.failed` event will be triggered. The status of the payin will change to `requires_payment_method`.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

This method does not supports partial refunds, that is, only refunds with amount equal to the invoice amount are supported.

### Refunding using dashboard

Refer to this guide: [https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard](https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard)

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
  "currency": "IDR",
  "reason": "Customer Return",
  "webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.
