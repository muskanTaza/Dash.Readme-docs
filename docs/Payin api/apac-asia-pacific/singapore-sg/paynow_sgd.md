---
title: paynow_sgd
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
PayNow QR payment is a convenient and popular method in Singapore that allows customers to make payments by scanning a QR code using their mobile banking app. Once the payment is completed, the business receives instant confirmation, streamlining the transaction process and enhancing customer satisfaction.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from paynow qr creation to payment completion.\
Create a payin on your server with an amount, invoice\_currency `SGD`  and a transaction\_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "invoice_currency": "SGD",
  "amount": 10000,
  "transaction_description": "1 X Goods",
	"webhook_url": "https://webhook.site/ref8y92937922"
}
,
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a QR code is generated to display to your customer. The status of the payin moves to `requires_action`

The following sub-fields can be passed in payment\_method\_details

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
    "name": "Andrea Lark",
    "email": "andrea.lark@me.com",
    "country": "SG"
  },
  "payment_method_details": {
    "type": "paynow_sgd"
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
  "invoice_currency": "SGD",
  "amount": 10000,
  "transaction_description": "1 X Goods",
  "webhook_url": "https://webhook.site/ref8y92937922",
  "confirm":true,
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea.lark@me.com",
    "country": "SG"
  },
  "payment_method_details": {
    "type": "paynow_sgd"
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
        "amount": 10000,
        "amount_paid": 0,
        "billing_details": null,
        "cancel_url": "",
        "cancelled_at": null,
        "client_token": "I2XZrhJ356-r6nHEj9jlGsL0mdCCQwP04vSF2w7B0aE=",
        "confirm": true,
        "created_at": "2024-02-06T10:25:09.333189785Z",
        "customer": "cus_cn10i0p8ukl9ae235oeg",
        "customer_details": {
            "country": "SG",
            "email": "andrea.lark@me.com",
            "name": "Andrea Lark",
            "phone": null
        },
        "id": "pay_cn10i0s6bt2fq1jlr0e0",
        "invoice_currency": "SGD",
        "latest_payment_attempt": "pat_cn10i0s6bt2fq1jlr0fg",
        "latest_payment_attempt_data": {
            "qr_code": "MDAwMjAxMjY1ODAwMDlTRy5QQVlOT1cwMTAxMjAyMTMyMDExMjA3OTdSMDAxMDMwMTAwNDE0MjAyNDAyMDYxODQwMDk1MjA0MDAwMDUzMDM3MDI1NDA2MTAwLjAwNTgwMlNHNTkyM1JFRCBET1QgUEFZTUVOVCBQVEUgTFRENjAwOVNpbmdhcG9yZTYyMjAwMTE2UVIyMDI0MDIwNlM5OTdIODYzMDQyRjA3"
        },
        "metadata": null,
        "object": "payin",
        "paid_in_excess": false,
        "partially_paid": false,
        "payment_attempts": [],
        "payment_method_details": {
            "type": "paynow_sgd"
        },
        "reference_id": "",
        "shipping_details": null,
        "statement_descriptor": "",
        "status": "requires_action",
        "status_description": "",
        "success_url": "",
        "transaction_data": [],
        "transaction_description": "1 X Goods",
        "transaction_documents": [],
        "webhook_url": "https://webhook.site/ref8y92937922"
    }
}
```

> You can use [this library](https://www.npmjs.com/package/qrcode) to convert the QR string to an image to display to your customers.

<aside>
➡️ You must also provide an option to your customers to download the QR image so that they can upload the QR on their banking application. This is useful when a customer is using a mobile device to complete the payment.

</aside>

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Use the `webhook_url` field in the payin API to receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer within the stipulated active time of the QR and the QR expires, Tazapay sends a `payment_attempt.failed` event. Display a CTA on your screen beside the QR to allow the customer to generate a new QR. To generate a new QR, confirm the payin again using Step 2.

| Event                   | Description                                       | Next Steps                                                                                 |
| ----------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| payin.succeeded         | The customer paid before the expiration of the QR | Fulfill the goods or services that the customer purchased                                  |
| payment\_attempt.failed | The customer did not pay and the QR expired       | Allow the customer to generate a new QR or complete the payment via another payment method |

# Test the Integration

In test mode (sandbox), 

1. All the paynow\_sgd payment attempts will succeed 3 minutes after creation by default. You will receive a `payin.succeeded` event.
2. All the paynow\_sgd payment attempts created with value 100 SGD (invoice\_currency - SGD, amount - 10000) will fail 3 minutes after creation by default. You will receive a `payment_attempt.failed` event and the status of the payin will move to `requires_payment_method`.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Paynow supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

### Refunding using dashboard.

Refer to this guide: [https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard](https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard)

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
  "payin": "pay_cn10i0s6bt2fq1jlr0e0",
  "amount": 1000,
  "currency": "SGD",
  "reason": "Customer Return",
  "webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

> **NOTE:** For full refund, specifying the amount and currency is not required to initiate a refund.
