---
title: LinkAja
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
# linkaja_idr

Linkaja is a popular digital wallet in Indonesia. When making a payment online, customers can select LinkAja as the payment method. On a mobile device, they get redirected to their pre-installed LinkAja application, otherwise they are redirected to the wallet’s website. The customers can then enter their mobile number, and complete the payment by entering their PIN.

> A customer can pay a minimum of 0.01 USD equivalent IDR and a maximum of 600 USD equivalent IDR using Link Aja on Tazapay

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from Link Aja transaction creation to payment completion.  
Create a payin on your server with an amount, invoice_currency `IDR` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "invoice_currency": "IDR",
  "amount": 10000000,
  "transaction_description": "1 X Good",
	"webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a redirection URL is generated. The status of the payin moves to `requires_action`

The following fields are to be passed in the request body

| Field                  | Subfield | type   | Mandatory (Y/N) | Description                                                                                           |
| ---------------------- | -------- | ------ | --------------- | ----------------------------------------------------------------------------------------------------- |
| payment_method_details |          | json   | Y               | Details specific to the payment method required to create a charge                                    |
| success_url            |          | string | Y               | URL where the customer is directed to after a successful payment                                      |
| cancel_url             |          | string | Y               | The URL the customer will be directed to if they decide to cancel payment and return to your website. |

The following sub-fields can be passed in payment_method_details

| Field | Subfield | type | Mandatory (Y/N) | Description                                                     |
| ----- | -------- | ---- | --------------- | --------------------------------------------------------------- |
| type  |          | enum | Y               | The type of the payment method. In this case, it is linkaja_idr |

### Sample cURL

```json
curl --location 'https://service-sandbox.tazapay.com/v3/payin/pay_cnfn18ne9lcetnsshe00/confirm' \
--header 'accept: application/json' \
--header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
--header 'content-type: application/json' \
--data-raw '
{
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea.lark@tazapay.com",
    "country": "ID"
  },
  "success_url":"https://mypage.success",
  "cancel_url":"https://mypage.failure",
  "payment_method_details": {
    "type": "linkaja_idr"
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
    "type": "linkaja_idr"
    }
  }
}'
```

## Step 3: Redirect the customer to LinkAja

After confirming the payin, you will receive the following response. You will receive a redirect_url where you can redirect your customer to

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
        "client_token": "lSMRSARnIHkJtaf4jkal04Fag5FWrQokejmRe-6rCno=",
        "confirm": true,
        "created_at": "2024-02-28T17:56:18.293247360Z",
        "customer": "cus_cnfn7ftk11f1q7gge7dg",
        "customer_details": {
            "country": "ID",
            "email": "andrea.lark@tazapay.com",
            "name": "Andrea Lark",
            "phone": null
        },
        "id": "pay_cnfn7fr5pbnta9her7k0",
        "invoice_currency": "IDR",
        "latest_payment_attempt": "pat_cnfn7g35pbnta9her7lg",
        "latest_payment_attempt_data": {
            "expires_at": "2024-03-04T17:56:18Z",
            "redirect_url": "https://checkout.tazapay.com/single-payment.html?tzid=lSMRSARnIHkJtaf4jkal04Fag5FWrQokejmRe-6rCno=&spid=aHR0cHM6Ly9wYXkuZGxvY2FsLmNvbS9nbWYtYXBtL3BheW1lbnRzLXJlZGlyZWN0L00tMWM4YzExZGItZjYyYi00NTRmLWE3YmUtYWY4NDBjMjQ0ZDZm"
        },
        "metadata": null,
        "object": "payin",
        "paid_in_excess": false,
        "partially_paid": false,
        "payment_attempts": [],
        "payment_method_details": {
            "type": "linkaja_idr"
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

Post a successful payment, the customer will be redirected back to the `success_url`. You will also receive a `payin.succeeded` event on your webhook_url. 

In case the customer does not complete the payment within the expiry time or the charge is not successful, the customer is redirected back to the `cancel_url` . From the cancel_url, you can display the list of payment methods again to the customer. To generate a new request, confirm the payin again using Step 2. You will also receive a `payment_attempt.failed` webhook.

| Event                  | Description                                                    | Next Steps                                                                                      |
| ---------------------- | -------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before the expiration of the payment request | Fulfill the goods or services that the customer purchased                                       |
| payment_attempt.failed | The customer did not pay and the request expired               | Allow the customer to generate a new request or complete the payment via another payment method |

## Expiration and cancellation

LinkAja charge requests expire after 5 minutes and the customer cannot pay once the charge request has expired. After expiration, the status of the payin changes to `requires_payment_method.` At this point, you can confirm the payin with another payment method or cancel.

# Test the Integration

You can simulate the following scenarios on the `redirect_url`

1. Successful Payment - Click on `Simulate Success` CTA. A `payin.succeeded` event will be triggered. The status of the payin will change to `succeeded`.
2. Failed Payment - Click on `Simulate Failure` CTA. A `payment_attempt.failed` event will be triggered. The status of the payin will change to `requires_payment_method`.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

LinkAja does not support partial refunds, the refund has to be for the full value of the transaction.

### Refunding using dashboard

Refer to this guide: \<https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard>

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
  "payin": "pay_cmrq5c74r2tr8tu3s2gg",
  "reason": "Customer Return",
  "webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.