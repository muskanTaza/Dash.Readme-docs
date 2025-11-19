---
title: mobilebanking_thb
excerpt: >-
  It is a widespread and convenient method for Thai residents to manage their
  finances through their mobile devices.
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

* Customers download a mobile banking app provided by their bank.
* They can then access a wide range of banking services through the app, including:
  * Checking account balances
  * Transferring funds between accounts
  * Paying bills
  * Making mobile top-ups
  * Locating ATMs and branches
  * Applying for loans and credit card

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from transaction creation to payment completion via mobile banking.  
Create a payin on your server with an amount, invoice_currency `THB` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "invoice_currency": "THB",
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
    "country": "TH"
  },
  "payment_method_details": {
    "type": "mobilebanking_thb",
		"mobilebanking_thb" : {
      "bank_name": "K-Bank",
      "phone": {
          "calling_code": "66",
          "number": "98765432"
      }		
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
    "country": "TH"
  },
  "confirm": true,
  "invoice_currency": "THB",
  "amount": 10000,
  "transaction_description": "test",
  "payment_method_details": {
    "type": "mobilebanking_thb",
		"mobilebanking_thb" : {
      "bank_name": "K-Bank",
      "phone": {
          "calling_code": "66",
          "number": "98765432"
      }
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
    "billing_details": {
      "address": null,
      "label": "",
      "name": "",
      "phone": null
    },
    "cancel_url": "",
    "cancelled_at": null,
    "client_token": "MIykUpsyrxRgjWOu1U5csBzZOqk9RaNPzDhMMDErEgc=",
    "confirm": true,
    "created_at": "2025-01-15T10:27:09.896074Z",
    "customer": "cus_cu3osb970g0h95qr5c00",
    "customer_details": {
      "country": "TH",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": {
        "calling_code": "",
        "number": ""
      }
    },
    "form": "",
    "holding_currency": "USD",
    "id": "pay_cu3oqvd3t210o3k432k0",
    "invoice_currency": "THB",
    "items": [],
    "latest_payment_attempt": "pat_cu3osbd3t210o3k434f0",
    "latest_payment_attempt_data": {
      "expires_at": "2025-01-15T10:35:05Z",
      "redirect_url": "https://checkout-sandbox.tazapay.com/single-payment.html?tzid=MIykUpsyrxRgjWOu1U5csBzZOqk9RaNPzDhMMDErEgc=&spid=aHR0cHM6Ly9jaGVja291dC1zYW5kYm94LnRhemFwYXkuY29tL3NpbXVsYXRlL01JeWtVcHN5cnhSZ2pXT3UxVTVjc0J6Wk9xazlSYU5QekRoTU1ERXJFZ2M9L3BheV9jdTNvcXZkM3QyMTBvM2s0MzJrMC9tb2JpbGViYW5raW5nX3RoYg=="
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "mobilebanking_thb": {
              "bank_name": "K-Bank",
              "phone": {
                  "calling_code": "66",
                  "number": "98765432"
                }
            },
      "type": "mobilebanking_thb"
    },
    "redirect_url": "https://checkout-sandbox.tazapay.com/simulate/MIykUpsyrxRgjWOu1U5csBzZOqk9RaNPzDhMMDErEgc=/pay_cu3oqvd3t210o3k432k0/mobilebanking_thb",
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
    "transaction_description": "test",
    "transaction_documents": [],
    "webhook_url": ""
  }
}
```

> You must redirect the customer to `latest_payment_attempt_data.redirect_url` in order to enable them to complete the payment.

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer.  Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer and the URL expires, Tazapay sends a `payment_attempt.failed`  event. To generate a new URL, confirm the payin again using Step 2.

| Event                  | Description                                   | Next Steps                                                                                  |
| ---------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before 30 days              | Fulfill the goods or services that the customer purchased                                   |
| payment_attempt.failed | The customer did not pay, and the URL expired | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

Click on `Simulate Success` CTA on the redirect_url. You will receive a `payin.succeeded` event.

## Simulating Failure / Expiry

Click on  `Simulate Expire` CTA on the redirect_url. You will receive a `payment_attempt.failed` event.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Mobile banking supports partial refunds. Specify the amount (lesser than the invoice amount of the payin) for the refund before initiating.

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
  "currency": "THB",
  "reason": "Customer Return",
  }
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.
