---
title: pix_brl
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
PIX in Brazil is a single use payment method. It allows users to make payments instantly, 24/7 including weekends and holidays. To make a payment, the payer accesses their bank's app or website and selects the PIX option. They then enter the recipient's PIX key or scan a QR code provided by the recipient.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from PIX QR creation to payment completion.  
Create a payin on your server with an amount, invoice_currency `BRL` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "invoice_currency": "BRL",
  "amount": 10000,
  "transaction_description": "1 X Good",
	"webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a QR code is generated to display to your customer. The status of the payin moves to `requires_action`

The following sub-fields can be passed in payment_method_details

| Field   | Subfield | type   | Mandatory (Y/N) | Description                                                                                                      |
| ------- | :------- | ------ | --------------- | ---------------------------------------------------------------------------------------------------------------- |
| type    |          | enum   | Y               | The type of the payment method. In this case, the value is `pix_brl`                                             |
| pix_brl |          | json   | Y               | Details of the PIX payment method                                                                                |
|         | tax_id   | string | Y               | Tax ID (CPF / CPNJ number) entered by the customer, This should be alphanumeric, without any special characters. |

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
    "email": "andrea.lark@tazapay.com",
    "country": "BR"
  },
  "payment_method_details": {
    "type": "pix_brl",
    "pix_brl": {
      "tax_id": "50444710000189"
    }
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
  "invoice_currency": "BRL",
  "amount": 10000,
  "transaction_description": "1 X Good",
  "webhook_url": "https://webhook.site/ref8y92937922",
  "confirm":true,
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea.lark@tazapay.com",
    "country": "BR"
  },
  "payment_method_details": {
    "type": "pix_brl",
    "pix_brl": {
      "tax_id": "9876543210"
    }
  }
}'
```

> In case, the tax_id entered by the customer is invalid, you will receive an error message which you can display to your customer
>
> "code": 19628,  
> "message": "Tax ID entered is invalid. Please enter a valid tax ID",  
> "remarks": "tax_id"

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
    "client_token": "9wC-vSEYwhgjm3ofZzufG6xdNF0B35iJima5cqLazW4=",
    "confirm": true,
    "created_at": "2024-01-15T12:29:33.308983510Z",
    "customer": "cus_cmiiaajkhi7uqjkfjb50",
    "customer_details": {
      "country": "BR",
      "email": "andrea.lark@tazapay.com",
      "name": "Andrea Lark",
      "phone": null
    },
    "id": "pay_cmiiaamaq0pbt3fkadm0",
    "invoice_currency": "BRL",
    "latest_payment_attempt": "pat_cmiiaauaq0pbt3fkadng",
    "latest_payment_attempt_data": {
      "qr_code": "MDAwMjAxMDEwMjExMjY4NDAwMDlTRy5QQVlOT1cwMTAxMjAyMTMyMDExMjA3OTdSUkRQMDMwMTAwNDE0MjAyNDAxMTUyMDM0MzEwNTIyUkQyMDI0MDExNTEyMjkzMVRUVzgyNjUxODAwMDA3U0cuU0dRUjAxMTIyMDEyMjgzMEY2RTgwMjA3MDEuMDAwMTAzMDYwNjk1NDIwNDAyMjEwNTAyMDEwNjA0MDAwMDA3MDgyMDIwMTIyODUyMDQwMDAwNTMwMzcwMjU0MDYxMDAuMDA1ODAyU0c1OTIzUkVEIERPVCBQQVlNRU5UIFBURSBMVEQ2MDA5U2luZ2Fwb3JlNjIyNjAxMjJSRDIwMjQwMTE1MTIyOTMxVFRXODI2NjMwNDhhNmQ="
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "pix_brl",
      "pix_brl": {
        "tax_id": "9876543210"
      }
    },
    "payment_method_options": {
      "pix_brl": {
        "expires_at": "2024-07-21T14:01:04.576356Z"
      }
    },
    "reference_id": "",
    "shipping_details": null,
    "statement_descriptor": "",
    "status": "requires_action",
    "status_description": "",
    "success_url": "",
    "transaction_data": [],
    "transaction_description": "1 X Good",
    "transaction_documents": [],
    "webhook_url": "https://webhook.site/ref8y92937922"
  }
}
```

> You can use [this library](https://www.npmjs.com/package/qrcode) to convert the QR string to an image to display to your customers.

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Use the `webhook_url` field in the payin API to receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer within the stipulated active time of the QR and the QR expires, Tazapay sends a `payment_attempt.failed` event. Display a CTA on your screen beside the QR to allow the customer to generate a new QR. To generate a new QR, confirm the payin again using Step 2.

| Event                  | Description                                       | Next Steps                                                                                 |
| ---------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| payin.succeeded        | The customer paid before the expiration of the QR | Fulfill the goods or services that the customer purchased                                  |
| payment_attempt.failed | The customer did not pay and the QR expired       | Allow the customer to generate a new QR or complete the payment via another payment method |

# Test the Integration (Work in Progress | Not live yet)

In test mode (sandbox), set the tax_id as 07341712503 so that it bypasses the tax_id validation.

1. All the pix_brl payment attempts will succeed 3 minutes after creation by default. You will receive a `payin.succeeded` event.
2. All the pix_brl payment attempts created with value 100 BRL (invoice_currency - BRL, amount - 10000) will fail 3 minutes after creation by default. You will receive a `payment_attempt.failed` event and the status of the payin will move to `requires_payment_method`.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

PIX supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

### Refunding using dashboard

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
  "amount": 9000,
  "currency": "BRL",
  "reason": "Customer Return",
  "webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.