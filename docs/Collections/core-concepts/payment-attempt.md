---
title: Payment Attempt
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
A payment attempt is an attempt by your customer to make a payment using a particular <a href = "https://docs.tazapay.com/v3/docs/payin-1" target="_blank"> payment method</a>. The payment attempt contains the customer specific information for a payment. For example, in case of a card payment, it is cardholder name, issuing bank, issuing country, etc.

Each checkout session can have multiple payment attempts. In case the previous payment attempt fails, the customer can go ahead using the same or a different payment method.

```Text payment_attempt
{
  "id": "pat_ahfafooi7ibakbfahoan",
  "object": "payment_attempt",
  "payin": "pay_bfiuafuiafianifnao",
  "created_at": "2023-08-31 16:58:59",
  "charge_currency": "INR",
  "amount": 123450,
  "payment_method_details": {
    "type": "card",
    "card": {
      "scheme": "visa",
      "checks": {
        "address_line1_check": "unavailable",
        "address_postal_code_check": "unavailable",
        "cvc_check": "pass"
      },
      "issuing_country": "IN",
      "expiry": {
        "month": "05",
        "year": "2028"
      },
      "funding": "credit",
      "last4": "3131",
      "first6": "459115",
      "issuer": "Axis Bank of India",
      "cardholder_name": "John Doe",
      "three_d_secure": {
        "authentication_flow": "challenge",
        "result": "authenticated",
        "result_reason": "successfully_authenticated",
        "version": "2.2.0"
      }
    }
  },
  "refunded": false,
  "status": "succeeded",
  "status_description": null,
  "final_currency": "USD",
  "fx_transaction": {
    "initial": {
      "currency": "INR",
      "amount": 123450
    },
    "final": {
      "currency": "USD",
      "amount": 148735
    },
    "exchange_rate": 83
  },
  "metadata": null
}
```