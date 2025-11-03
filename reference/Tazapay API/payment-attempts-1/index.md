---
title: Payment Attempts
excerpt: ''
deprecated: false
hidden: false
icon: far fa-money-check-dollar-pen
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Tazapay API object that tracks each payment attempt, including successful and failed ones. It provides valuable insights into the payment process, helping businesses optimize their revenue streams.

## Object

```json
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 9899,
        "balance_transaction": "btr_d679f6dqd9ne66lsngb0",
        "charge_currency": "PLN",
        "created_at": "2023-07-23T08:03:29.718275Z",
        "customer": "cus_d209e84kspu2df5phfm0",
        "customer_details": {
            "country": "PL",
            "email": "sowajan1010@gmail.com",
            "name": "Jan",
            "phone": {
                "calling_code": "48",
                "number": "1234369"
            }
        },
        "fx_transaction": {
            "exchange_rate": 0.219768,
            "final": {
                "amount": 2173,
                "currency": "EUR"
            },
            "id": "fx_d209ek2fhufa9pkp5c4g",
            "initial": {
                "amount": 9888,
                "currency": "PLN"
            },
            "object": "fx_transaction"
        },
        "id": "pat_d209ek5qd9ne66lsn6gg",
        "metadata": null,
        "object": "payment_attempt",
        "payin": "chk_d209e85qd65u66lsn1g0",
        "payment_method_details": {
            "card": {
                "cardholder_name": "jan cebella",
                "checks": {
                    "cvc_check": "pass"
                },
                "expiry": {
                    "month": 7,
                    "year": 2031
                },
                "first6": "428771",
                "funding": "debit",
                "issuer": "ing bank slaski sa",
                "issuing_country": "pl",
                "last4": "6095",
                "scheme": "visa",
                "three_d_secure": {
                    "eci": "05",
                    "result": "attempt_acknowledged",
                    "version": "2.2.0"
                }
            },
            "type": "card"
        },
        "reference_id": "TR000001385673188",
        "refunded": "true",
        "status": "succeeded",
        "status_description": ""
    }

```

## Parameters

### Payment Attempt

| Parameter              | Type              | Description                                                                                                                                              |
| ---------------------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                     | string            | The Tazapay ID of the payment attempt.                                                                                                                   |
| object                 | string            | The object type, which is "payment_attempt".                                                                                                             |
| created_at             | string (ISO Date) | The date and time when the payment attempt was created.                                                                                                  |
| amount                 | number            | The amount attempted to be paid in the charge currency.                                                                                                  |
| balance_transaction    | string            | The balance transaction id associated with the payment attempt.                                                                                          |
| customer               | string            | The unique Tazapay customer id.                                                                                                                          |
| customer_details       | object            | Customer Details.                                                                                                                                        |
| reference_id           | string            | Reference id attached to the payment attempt.                                                                                                            |
| charge_currency        | string            | The currency in which the payment was attempted (e.g., SGD).                                                                                             |
| payin                  | string            | The reference to the payin object related to the checkout transaction.                                                                                   |
| payment_method_details | string            | The payment method details used in this attempt                                                                                                          |
| refunded               | boolean           | Indicates whether the payment attempt has been refunded.                                                                                                 |
| status                 | string            | The status of the payment attempt (e.g., succeeded, failed).                                                                                             |
| status_description     | string            | A description providing more information about the payment attempt status                                                                                |
| final_currency         | string            | The final currency after the payment is converted, if applicable (e.g., USD).                                                                            |
| fx_transaction         | object            | Details about the foreign exchange transaction, if any. Check [FX transaction](https://docs.tazapay.com/update/reference/fx-transaction-object#/) object |
| metadata               | json              | Additional key value pairs related to the payment attempt (optional).                                                                                    |
