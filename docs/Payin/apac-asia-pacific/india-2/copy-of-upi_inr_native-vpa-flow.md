---
title: Copy of upi_inr_native (VPA Flow)
excerpt: >-
  UPI (Unified Payments Interface) in India: A revolutionary real-time mobile
  payment system developed by the National Payments Corporation of India (NPCI).
deprecated: false
hidden: false
metadata:
  robots: index
---
### How It Works

* Users link their bank accounts to their UPI apps (e.g., Google Pay, PhonePe, Paytm).
* Payments are made by entering the recipient's UPI ID, mobile number, or virtual payment address (VPA).
* Funds are transferred instantly between bank accounts.

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from transaction creation to payment completion via UPI payment method.  
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

| Field          | Subfield    | type             | Mandatory (Y/N) | Description                                                                                                                                                                                           |
| -------------- | :---------- | ---------------- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type           |             | enum             | Y               | The type of the payment method. In this case, the value is `upi_inr_native`                                                                                                                           |
| upi_inr_native |             | json             | Y               | Details of the UPI payment method                                                                                                                                                                     |
|                | payer_vpa   | string           | Y               | VPA (Virtual Payment Address) entered by the customer. This must be alphanumeric and can include valid UPI separators (e.g., dot . and at-sign @). No spaces or other special characters are allowed. |
| items          |             | array of objects | Y               | List of items                                                                                                                                                                                         |
|                | name        | string           | Y               | Item name                                                                                                                                                                                             |
|                | description | string           | N               | Item description                                                                                                                                                                                      |
|                | amount      | int64            | Y               | Item unit price                                                                                                                                                                                       |
|                | quantity    | int64            | Y               | Item quantity                                                                                                                                                                                         |

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
  "items": [
    {
      "name": "Software Service for Antivirus",
      "description": "Firewall Antivirus",
      "amount": 10000,
      "quantity": 1
    }
  ],
  "payment_method_details": {
    "type": "upi_inr_native",
    "upi_inr_native": {
      "payer_vpa": "test@bank"
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
    "country": "IN"
  },
  "items": [
    {
      "name": "Software Service for Antivirus",
      "description": "Firewall Antivirus",
      "amount": 10000,
      "quantity": 1
    }
  ],
  "confirm": true,
  "invoice_currency": "INR",
  "amount": 10000,
  "transaction_description": "test",
  "payment_method_details": {
    "type": "upi_inr_native"
    "upi_inr_native": {
      "payer_vpa": "test@bank,"
    }
  }
}
'
```

> The buyer will receive a payment request in their UPI app and can authenticate the transaction by entering their UPI PIN.
>
> Note: A UPI Collect request remains valid for 5 minutes. If the buyer does not authorise it within this timeframe, the request will expire.

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer.  Tazapay sends these events to the endpoint configured from your dashboard. You can receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

If the payment is not made by the customer within the expiry and the request expires, Tazapay sends a `payment_attempt.failed`  event. To generate a new payment attempt, confirm the payin again using Step 2.

| Event                  | Description                                            | Next Steps                                                                                  |
| ---------------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before the expiration of the request | Fulfill the goods or services that the customer purchased                                   |
| payment_attempt.failed | The customer did not pay, and the URL expired          | Allow the customer to generate a new URL or complete the payment via another payment method |

# Test the Integration

## Simulating success

Click on `Simulate Success` CTA on the redirect_url. You will receive a `payin.succeeded` event.

## Simulating Failure

Click on  `Simulate failure` CTA on the redirect_url. You will receive a `payment_attempt.failed` event.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

`upi_inr_native` supports partial refunds.

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
  "amount": 10000,
  "currency": "INR",
  "reason": "Customer Return",
  }
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.