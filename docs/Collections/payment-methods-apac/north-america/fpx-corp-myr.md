---
title: fpx_corp_myr / fpx_ind_myr
excerpt: >-
  **FPX (Financial Process Exchange) in Malaysia:** A widely adopted online
  payment gateway that facilitates real-time direct debit from a customer's bank
  account to an online merchant's account.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# How It Works

- During online checkout, customers select FPX as their payment method.
- They are then redirected to a secure FPX page where they choose their preferred bank from a list of participating Malaysian banks (which includes most major banks like Maybank, CIMB, Public Bank, and many others).
- Customers log in to their online banking portal using their existing bank credentials.
- They review the payment details (amount and payee) and authorize the transaction, often requiring a second-factor authentication method like a One-Time Password (OTP).
- Once the payment is authorized, the funds are debited from the customer's bank account in real-time, and both the customer and the merchant receive a payment confirmation.

# Payment Method type

Users can use the below payment method type to create a transaction using FPX network in the available geography

- Malaysia: `fpx_corp_myr` / `fpx_ind_myr`

# Functionality

| Functionality           | Yes/No | Description                               |
| ----------------------- | ------ | ----------------------------------------- |
| **Refund Support**      |        |                                           |
| Full Refund             | ✅      |                                           |
| Partial Refund          | ✅      |                                           |
| **Generally Available** | ❌      | Requires approval. Usual SLA is 3-4 weeks |
| Dispute and Chargebacks | ✅      |                                           |

# Limits and Expiration

The following is the upper and lower limits for FPX transactions:

- **Minimum Limit**: USD 0.5
- **Maximum Limit**: USD 20000

There is no default expiration for a FPX transaction.

# User Experience

Redirect Experience

For more details, please click [here](https://tazapay.com/payment-methods/fpx).