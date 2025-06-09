---
title: internet_banking_inr
excerpt: >-
  A widely used service offered by banks that allows customers to conduct
  various banking transactions online through the bank's website or mobile app
  in India.
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

- Customers register for internet banking services with their bank.
- They can then access their accounts online and perform a range of transactions, including:
  - Checking account balances and transaction history
  - Transferring funds between their own accounts and to other bank accounts
  - Paying bills (electricity, phone, etc.)
  - Applying for loans and credit cards
  - Making investments

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from transaction creation to payment completion via internet banking payment method.  
Create a payin on your server with an amount, invoice_currency `INR` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

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
  "invoice_currency": "INR",
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
    "country": "IN"
  },
  "payment_method_details": {
    "type": "internet_banking_inr"
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
    "country": "IN"
  },
  "confirm": true,
  "invoice_currency": "INR",
  "amount": 10000,
  "transaction_description": "test",
  "payment_method_details": {
    "type": "internet_banking_inr"
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
    "client_token": "nGAt62pF3a68Gajvd0L8_YdGd_dghmApKbLYk_NHsGs=",
    "confirm": true,
    "created_at": "2025-01-23T08:40:52.094683719Z",
    "customer": "cus_cu8vnm4lppnoaibo23sg",
    "customer_details": {
      "country": "IN",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": null
    },
    "holding_currency": "USD",
    "id": "pay_cu9014qnbet4snrm1c60",
    "invoice_currency": "INR",
    "items": [],
    "latest_payment_attempt": "pat_cu9014qnbet4snrm1c8g",
    "latest_payment_attempt_data": {
      "expires_at": "2025-01-23T08:45:52Z",
      "redirect_url": "https://checkout-sandbox.tazapay.com/single-payment.html?tzid=nGAt62pF3a68Gajvd0L8_YdGd_dghmApKbLYk_NHsGs=&spid=aHR0cHM6Ly9jaGVja291dC1zYW5kYm94LnRhemFwYXkuY29tL3NpbXVsYXRlL25HQXQ2MnBGM2E2OEdhanZkMEw4X1lkR2RfZGdobUFwS2JMWWtfTkhzR3M9L3BheV9jdTkwMTRxbmJldDRzbnJtMWM2MC9pbnRlcm5ldF9iYW5raW5nX2lucg==&ref_url_req=true"
    },
    "metadata": null,
    "object": "payin",
    "paid_in_excess": false,
    "partially_paid": false,
    "payment_attempts": [],
    "payment_method_details": {
      "type": "internet_banking_inr"
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

Tazapay sends a `payin.processing` event for bank initiated transactions to the merchants. Once the payment is made by the customer and our team gets the funds sighted, they approve the payin as succeeded which triggers another event  `payin.succeeded`. Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer and the URL expires, Tazapay sends a `payment_attempt.failed` after the `payin.processing` event. To generate a new URL, confirm the payin again using Step 2.

| Event                  | Description                                   | Next Steps                                                                                  |
| ---------------------- | --------------------------------------------- | ------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before 24 hours             | Fulfill the goods or services that the customer purchased                                   |
| payment_attempt.failed | The customer did not pay, and the URL expired | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

Click on `Simulate Success` CTA on the redirect_url. You will receive a `payin.succeeded` event.

## Simulating Failure / Expiry

Click on `Simulate Failure` / `Simulate Expire` CTA on the redirect_url. You will receive a `payment_attempt.failed` event.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

Internet banking in India doesnt support partial refunds.

### Refunding using dashboard

Refer to this guide: <https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard>

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
  "amount": 10000,
  "currency": "INR",
  "reason": "Customer Return",
  }
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.