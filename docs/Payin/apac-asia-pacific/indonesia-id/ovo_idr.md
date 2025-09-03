---
title: OVO
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
Ovo is one of the leading e-wallets of Indonesia. When a customer wants to make a payment online, they will select OVO e-wallet, select "Place Your Order," and be redirected to the OVO landing page. They will then complete the payment by clicking "Pay" and be redirected to the payment confirmation page. Once the payment is confirmed, the page redirects to the merchant's website.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from ovo payment request creation to payment completion.  
Create a payin on your server with an amount, invoice_currency `IDR` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

A payin is created with the status `requires_payment_method`.

### Sample cURL

```bash
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "invoice_currency": "IDR",
  "amount": 10000000,
  "transaction_description": "1 X Good",
	"webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a charge is requested on the customer's mobile wallet. The status of the payin moves to `requires_action`

The following sub-fields can be passed in payment_method_details

| Field   | Subfield | type | Mandatory (Y/N) | Description                                                      |
| ------- | -------- | ---- | --------------- | ---------------------------------------------------------------- |
| type    |          | enum | Y               | The type of the payment method. In this case, it is ovo_idr      |
| ovo_idr |          | json | Y               | An object containing the details of the payment method           |
|         | phone    | json | Y               | The phone number associated with the ovo wallet of the customer. |

```json
{  
"calling_code":"62",  
"number":"81234567890"  
}
```

### Sample cURL

```bash
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
    "country": "ID"
  },
  "payment_method_details": {
    "type": "ovo_idr",
		"ovo_idr":{
			"phone":{
				"calling_code":"62",
				"number":"81234567890"
			}
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

```bash
curl --location 'https://service-sandbox.tazapay.com/v3/payin' \
--header 'accept: application/json' \
--header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
--header 'content-type: application/json' \
--data-raw '{
  "invoice_currency": "IDR",
  "amount": 10000000,
  "transaction_description": "1 X Good",
  "webhook_url": "https://webhook.site/ref8y92937922",
  "confirm":true,
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea.lark@tazapay.com",
    "country": "ID"
  },
  "payment_method_details": {
    "type": "ovo_idr",
    "ovo_idr": {
      "phone": {
				"calling_code":"62",
				"number":"81234567890"
			}
    }
  }
}'
```

## Step 3: Wait for your customer to successfully make the merchant

After confirming the payin, you will receive the following response. The customer will receive a payment request on the OVO wallet on their mobile device. They can follow the prompt to complete the payment. 

```json
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 10000000,
        "amount_paid": 0,
        "billing_details": null,
        "cancel_url": "",
        "cancelled_at": null,
        "client_token": "zWJsECjWXQNPD-bZ64pV3LGIPjdpgOnsdrwLHEP4wX8=",
        "confirm": true,
        "created_at": "2024-01-29T13:05:54.270403381Z",
        "customer": "cus_cmrq5c6oui3lmrvb8tpg",
        "customer_details": {
            "country": "ID",
            "email": "andrea.lark@tazapay.com",
            "name": "Andrea Lark",
            "phone": null
        },
        "id": "pay_cmrq5c74r2tr8tu3s2gg",
        "invoice_currency": "IDR",
        "latest_payment_attempt": "pat_cmrq5cf4r2tr8tu3s2o0",
        "latest_payment_attempt_data": {
            "expires_at": "2024-02-03T13:05:54Z"
        },
        "metadata": null,
        "object": "payin",
        "paid_in_excess": false,
        "partially_paid": false,
        "payment_attempts": [],
        "payment_method_details": {
            "ovo_idr": {
                "phone": {
                    "calling_code": "62",
                    "number": "81234567890"
                }
            },
            "type": "ovo_idr"
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

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Use the `webhook_url` field in the payin API to receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer within the stipulated active time of the payment request and it expires, Tazapay sends a `payment_attempt.failed` event. Display a CTA on your screen to regenerate a payment request. To generate a new request, confirm the payin again using Step 2.

| Event                  | Description                                                    | Next Steps                                                                                      |
| ---------------------- | -------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before the expiration of the payment request | Fulfill the goods or services that the customer purchased                                       |
| payment_attempt.failed | The customer did not pay and the request expired               | Allow the customer to generate a new request or complete the payment via another payment method |

# Test the Integration (Work in Progress | Not live yet)

In test mode (sandbox), set the phone as below so that it bypasses the validation.

```json
{
  "calling_code":"62",
  "number":"0123456789"
}
```

1. All the ovo_idr payment attempts will succeed 70 seconds after creation by default. You will receive a `payin.succeeded` event.
2. All the ovo_idr payment attempts created with value 100000 IDR (invoice_currency - IDR, amount - 10000000) will fail 70 seconds after creation by default. You will receive a `payment_attempt.failed` event and the status of the payin will move to `requires_payment_method`.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

OVO does not support partial refund, that is, only refunds with amount equal to the invoice amount are supported.

### Refunding using dashboard

Refer to this guide: [How do I request a refund from my dashboard](https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard)

### Refund using API

Sample cURL

```bash
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/refund \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "payin": "pay_cmrq5c74r2tr8tu3s2gg",
  "amount": 10000000,
  "currency": "IDR",
  "reason": "Customer Return",
  "webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.