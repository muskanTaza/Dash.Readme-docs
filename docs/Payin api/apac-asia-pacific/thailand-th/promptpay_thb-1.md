---
title: promptpay_thb
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
PromptPay is an interbank real-time near-instant payment system that enables users to easily receive and transfer funds using either their Citizen ID or mobile phone number.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from promptpay creation to payment completion.  
Create a payin on your server with an amount, invoice_currency `THB` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

A payin is created with the status `requires_payment_method`.

### Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "invoice_currency": "THB",
  "amount": 10000,
  "transaction_description": "1 X Goods",
	"webhook_url": "https://webhook.site/ref8y92937922"
}
,
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a QR code is generated to display to your customer. The status of the payin moves to `requires_action`

### Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin/pay_uiabfuiahfanwofihwnwon/confirm \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "customer_details": {
    "name": "Lily",
    "email": "lily@tazapay.com",
    "country": "TH"
  },
  "payment_method_details": {
    "type": "promptpay_thb"
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
curl --location 'https://service-sandbox.tazapay.com/v3/payin' \
--header 'accept: application/json' \
--header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
--header 'content-type: application/json' \
--data-raw '{
  "invoice_currency": "THB",
  "amount": 10000,
  "transaction_description": "1 X Goods",
  "webhook_url": "https://webhook.site/ref8y92937922",
  "confirm":true,
  "customer_details": {
    "name": "Lily",
    "email": "lily@tazapay.com",
    "country": "TH"
  },
  "payment_method_details": {
    "type": "promptpay_thb"
  }
}'
```

## Step 3: Display the QR code on your screen

After confirming the payin, you will receive the following response

```json
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 100,
    "amount_paid": 0,
    "billing_details": {
      "address": null,
      "label": "",
      "name": "",
      "phone": null
    },
    "cancel_url": "",
    "cancelled_at": null,
    "client_token": "_ddC0efg7UT2i2HplSvX0dOVegh3oGsKdSlJamNkdzU=",
    "confirm": true,
    "created_at": "2024-01-24T05:29:41.867869Z",
    "customer": "cus_cmoa8147e7ph7pbi7tug",
    "customer_details": {
      "country": "TH",
      "email": "lily@tazapay.com",
      "name": "Lily",
      "phone": {
        "calling_code": "",
        "number": ""
      }
    },
    "id": "pay_cmoa0hcjslcv0qnkjufg",
    "invoice_currency": "THB",
    "latest_payment_attempt": "pat_cmoa81cjslcv0qnkjv8g",
    "latest_payment_attempt_data": {
      "expires_at": "2024-01-24T06:05:41Z",
      "qr_code": "c29tZS1yYW5kb20tcXItc3RyaW5n"
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "promptpay_thb"
    },
    "reference_id": "",
    "shipping_details": {
      "address": null,
      "label": "",
      "name": "",
      "phone": null
    },
    "statement_descriptor": "",
    "status": "requires_action",
    "status_description": "",
    "success_url": "",
    "transaction_data": [],
    "transaction_description": "1xGoods",
    "transaction_documents": [],
    "webhook_url": "https://webhook.site/ref8y92937922"
  }
}
```

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Use the `webhook_url` field in the payin API to receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer within the stipulated active time of the QR and the QR expires, Tazapay sends a `payment_attempt.failed` event. Display a CTA on your screen beside the QR to allow the customer to generate a new QR. To generate a new QR, confirm the payin again using Step 2.

| Event                  | Description                                       | Next Steps                                                                                 |
| ---------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| payin.succeeded        | The customer paid before the expiration of the QR | Fulfill the goods or services that the customer purchased                                  |
| payment_attempt.failed | The customer did not pay and the QR expired       | Allow the customer to generate a new QR or complete the payment via another payment method |

# Test the Integration

In test mode (sandbox), 

1. All the promptpay_thb payment attempts will succeed 3 minutes after creation by default. You will receive a `payin.succeeded` event.
2. All the promptpay_thb payment attempts created with value 100 THB (invoice_currency - THB, amount - 10000) will fail 3 minutes after creation by default. You will receive a `payment_attempt.failed` event and the status of the payin will move to `requires_payment_method`.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Promptpay supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

### **Prerequisite:**

Promptpay mandatorily requires customers phone number to initiate a refund.

### Refunding using dashboard.

Refer to this guide: <https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard>

### Refund using API

Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/refund \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "payin": "pay_cmiiaamaq0pbt3fkadm0",
  "amount": 1000,
  "currency": "THB",
  "reason": "Customer Return",
  "webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

> **NOTE:** For full refund, specifying the amount and currency is not required to initiate a refund.