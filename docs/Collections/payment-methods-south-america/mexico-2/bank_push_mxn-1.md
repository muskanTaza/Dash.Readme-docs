---
title: bank_push_mxn
excerpt: >-
  Refers to payment systems where a sender (payer) initiates a payment directly
  to a recipient's bank account.
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

- The sender uses their online banking platform or a dedicated payment gateway integrated with their systems.
- They initiate a payment by providing the recipient's bank account details (CLABE - Clave Bancaria Estandarizada, the standard bank account number in Mexico - and bank name).
- The transaction is authenticated using the sender's banking security protocols (e.g., passwords, tokens, mobile app verification).
- The funds are then directly credited to the recipient's bank account.

# Payment Method type

Users can use the below payment method type to create a transaction using Bank Push in the available geography

- Mexico: `bank_push_mxn`

# Functionality

| Functionality           | Yes/No | Description                                                       |
| ----------------------- | ------ | ----------------------------------------------------------------- |
| **Refund Support**      |        |                                                                   |
| Full Refund             | ✅      |                                                                   |
| Partial Refund          | ✅      |                                                                   |
| **Generally Available** | ❌      | Requires a signed declaration. Usual SLA for activation is 1 week |
| Dispute and Chargebacks | ❌      |                                                                   |

# Limits and Expiration

The following is the upper and lower limits for Bank Push transactions:

- **Minimum Limit**: USD 0.5
- **Maximum Limit**: USD 20000

There is no default expiration for a transaction**.**

# User Experience

Native Experience

For more details, click [here](https://tazapay.com/country-list/mexico)