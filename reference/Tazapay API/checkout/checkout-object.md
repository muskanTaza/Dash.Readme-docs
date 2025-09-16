---
title: Checkout Object
excerpt: >-
  Checkout API object enables businesses to create and manage seamless online
  payment experiences. It lets you integrate a Tazapay-hosted payment page so
  that you can quickly collect cross-border payments on mobile and desktop
  devices.
deprecated: false
hidden: false
icon: far fa-sack-dollar
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Object Structure

```json
{
  "id": "chk_cirsp2sl4ar024j0akj0",
  "object": "checkout",
  "invoice_currency": "USD",
  "amount": 100000,
  "amount_paid": 100000,
  "customer_details": {
      "country": "SG",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": {
        "calling_code": "65",
        "number": "87654321"
      }
    },
  "customer": "cus_afobaifawnf",
  "billing_details": {
      "address": {
        "city": "Singapore",
        "country": "SG",
        "line1": "1st Street",
        "line2": "2nd Avenue",
        "postal_code": "43004",
        "state": "Singapore"
      },
      "label": "Home",
      "name": "Andrea Lark",
      "phone": {
        "calling_code": "65",
        "number": "87654321"
      }
    },
  "customer_fee_percentage" : 0,
  "shipping_details": {
      "address": {
        "city": "Singapore",
        "country": "SG",
        "line1": "1st Street",
        "line2": "2nd Avenue",
        "postal_code": "43004",
        "state": "Singapore"
      },
      "label": "Home",
      "name": "Andrea Lark",
      "phone": {
        "calling_code": "65",
        "number": "87654321"
      }
    },
  "success_url": "https://mystore.com/success_page",
  "cancel_url": "https://mystore.com/try_again",
  "webhook_url": "https://mystore.com/internal/webhook",
  "payment_methods": [
      "paynow_sgd", "card"
    ],
  "transaction_description": "1 x trousers",
  "expires_at": "2023-07-21T14:01:04.576356Z",
  "created_at": "2023-07-19T11:44:11.722049185Z",
  "url": "https://checkout.tazapay.com/transaction=ajfuibfainfaonfa",
  "payment_status": "paid",
  "payment_status_description": null,
  "status": "expired",
  "payin": "chk_cirsp2sl4ar024j0akj0",
  "payment_attempts": [{
      "id": "pat_ahbfiuahfiuaiofnioain",
      "object": "payment_attempt",
      "created_at": "2023-07-21T14:00:02.576356Z",
      "amount": 148000,
      "charge_currency": "SGD",
      "payin": "chk_cirsp2sl4ar024j0akj0",
      "payment_method_details": {
        "type": "paynow_sgd",
        "paynow_sgd": {}
      },
      "refunded": false,
      "status": "succeeded",
      "status_description": null,
      "final_currency": "USD",
      "fx_transaction": {
        "initial": {
          "currency": "SGD",
          "amount": 148000
        },
        "final": {
          "currency": "USD",
          "amount": 100000
        },
        "exchange_rate": 1.48
      },
      "metadata": null
    }],
  "latest_payment_attempt": "pat_ahbfiuahfiuaiofnioain",
  "partially_paid": false,
  "paid_in_excess": false,
  "transaction_documents": [],
  "reference_id": "mystore_order_00001",
  "metadata": {
      "key1": "value1",
      "key2": "value2",
      "key3": "value3"
    }
	}

```

<br />

## Object Parameters

### Checkout

| Field                      | Subfield               | Type                   | Description                                                                      |
| -------------------------- | ---------------------- | ---------------------- | -------------------------------------------------------------------------------- |
| id                         |                        | string                 | The Tazapay unique identifier for the checkout transaction.                      |
| object                     |                        | string                 | The type of object, which is "checkout".                                         |
| invoice_currency           |                        | string                 | The currency of the invoice (e.g., USD).                                         |
| amount                     |                        | number                 | The total amount to be paid.                                                     |
| amount_paid                |                        | number                 | The amount that has already been paid.                                           |
| customer_details           |                        | object                 | The details of the customer.                                                     |
|                            | country                | string                 | The country of the customer (e.g., SG for Singapore).                            |
|                            | email                  | string                 | The email address of the customer.                                               |
|                            | name                   | string                 | The name of the customer.                                                        |
|                            | phone                  | object                 | The phone details of the customer. (See Phone Table)                             |
| customer                   |                        | string                 | The customer ID related to the checkout.                                         |
| billing_details            |                        | object                 | The billing details of the customer.                                             |
|                            | address                | object                 | The address details of the billing information. (See Address Table)              |
|                            | label                  | string                 | The label for the billing address (e.g., Home, Office).                          |
|                            | name                   | string                 | The name of the person being billed.                                             |
|                            | phone                  | object                 | The phone details for billing. (See Phone Table)                                 |
| shipping_details           |                        | object                 | The shipping details of the customer.                                            |
|                            | address                | object                 | The address details of the shipping information. (See Address Table)             |
|                            | label                  | string                 | The label for the shipping address (e.g., Home, Office).                         |
|                            | name                   | string                 | The name of the person receiving the shipment.                                   |
|                            | phone                  | object                 | The phone details for shipping. (See Phone Table)                                |
| success_url                |                        | string                 | The URL where the user is redirected after a successful transaction.             |
| cancel_url                 |                        | string                 | The URL where the user is redirected after a cancelled transaction.              |
| webhook_url                |                        | string                 | The URL for webhook notifications regarding this transaction.                    |
| payment_methods            |                        | array                  | The list of payment methods available (e.g., paynow_sgd, card).                  |
| transaction_description    |                        | string                 | A description of the transaction (e.g., "1 x trousers").                         |
| expires_at                 |                        | string (ISO Timestamp) | The expiry date and time of the checkout session.                                |
| created_at                 |                        | string (ISO Timestamp) | The creation date and time of the checkout session.                              |
| url                        |                        | string                 | The URL for the checkout page.                                                   |
| payment_status             |                        | string                 | The payment status of the transaction (e.g., paid, pending).                     |
| payment_status_description |                        | string                 | Additional details on the payment status                                         |
| status                     |                        | string                 | The status of the checkout session (e.g., expired, active).                      |
| payin                      |                        | string                 | The unique Tazapay ID of the related payin transaction.                          |
| payment_attempts           |                        | array                  | The list of payment attempts.                                                    |
|                            | id                     | string                 | The unique Tazapay identifier for the payment attempt.                           |
|                            | object                 | string                 | The type of object, which is "payment_attempt".                                  |
|                            | created_at             | string                 | The creation date and time of the payment attempt (ISO format).                  |
|                            | amount                 | number                 | The amount attempted to be paid.                                                 |
|                            | charge_currency        | string                 | The currency in which the charge was made (e.g., SGD).                           |
|                            | payin                  | string                 | The ID of the related payin transaction.                                         |
|                            | payment_method_details | object                 | The payment method used for the attempt. (See Payment Method Details Table)      |
|                            | refunded               | boolean                | Indicates if the payment attempt was refunded.                                   |
|                            | status                 | string                 | The status of the payment attempt (e.g., succeeded, failed).                     |
|                            | status_description     | string/null            | A description of the status (optional).                                          |
|                            | final_currency         | string                 | The final currency after any conversion (e.g., USD).                             |
|                            | fx_transaction         | object                 | The foreign exchange transaction details. (See FX Transaction Table)             |
| latest_payment_attempt     |                        | string                 | The ID of the latest payment attempt.                                            |
| partially_paid             |                        | boolean                | Indicates if the payment was partially paid.                                     |
| paid_in_excess             |                        | boolean                | Indicates if the payment was made in excess.                                     |
| transaction_documents      |                        | array                  | List of transaction-related documents (if any).                                  |
| reference_id               |                        | string                 | The reference ID for the transaction (e.g., "mystore_order_00001").              |
| metadata                   |                        | object                 | Set of key-value pairs attached to the checkout object.                          |
| customer_fee_percentage    |                        | integer                | Customer fees percentage incase the fees is split between customer and merchant. |

<br />

### Address

| Field       | Type   | Description                                                    |
| ----------- | ------ | -------------------------------------------------------------- |
| city        | string | The city of the billing or shipping address.                   |
| country     | string | The country of the billing or shipping address.                |
| line1       | string | The first line of the billing or shipping address.             |
| line2       | string | The second line of the billing or shipping address (optional). |
| postal_code | string | The postal code of the billing or shipping address.            |
| state       | string | The state or province of the billing or shipping address.      |

<br />

### Phone

| Field        | Type   | Description                                                        |
| ------------ | ------ | ------------------------------------------------------------------ |
| calling_code | string | The international calling code for the beneficiary's phone number. |
| number       | string | The phone number of the beneficiary.                               |

<br />

### Payment Method Details

| Field      | Type   | Description                                               |
| ---------- | ------ | --------------------------------------------------------- |
| type       | string | The type of payment method used (e.g., paynow_sgd, card). |
| paynow_sgd | object | Additional details specific to payment method             |

<br />

### FX Transaction

| Field            | Type   | Description                                                 |
| ---------------- | ------ | ----------------------------------------------------------- |
| exchange_rate    | number | The exchange rate used for the currency conversion.         |
| final.amount     | number | The final amount after conversion.                          |
| final.currency   | string | The final currency after conversion.                        |
| initial.amount   | number | The initial amount before conversion                        |
| initial.currency | string | The initial currency before conversion.                     |
| id               | string | The Tazapay ID of the holding foreign exchange transaction. |
