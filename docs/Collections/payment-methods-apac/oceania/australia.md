---
title: paynow_sgd
excerpt: >-
  PayNow QR payment is a convenient and popular method in Singapore that allows
  customers to make payments by scanning a QR code using their mobile banking
  app. Once the payment is completed, the business receives instant
  confirmation, streamlining the transaction process and enhancing customer
  satisfaction.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# How it Works?

- Users register for PayNow by linking their mobile phone number or NRIC/FIN (National Registration Identity Card/Foreign Identification Number) to their bank account.
- Payments can be made by:
  - Entering the recipient's mobile phone number or NRIC/FIN.
  - Scanning a QR code (PayNow QR).
  - Using a proxy (e.g., Virtual PayNow Account).
- Funds are transferred instantly between bank accounts.

# Payment Method type

Users can use the below payment method type to create a transaction using PayNow in the available geography

- Singapore: `paynow_sgd`

# Functionality

| Functionality               | Yes/No | Description                                                 |
| --------------------------- | ------ | ----------------------------------------------------------- |
| **Refund Support**          |        |                                                             |
| Full Refund                 | ✅      | Made to phone number if provided, else with account details |
| Partial Refund              | ✅      | Made to phone number if provided, else with account details |
| **Generally Available**     | ❌      | Requires enablement which is almost instant.                |
| **Dispute and Chargebacks** | ✅      |                                                             |

# Limits and Expiration

The following is the upper and lower limits for PayNow transactions:

- **Minimum Limit**: USD 0.01
- **Maximum Limit**: USD 20000

The default expiration for a transaction is **20 minutes.** This is further configurable within the default time of expiration.

# User Experience

Native Experience

For more details, please click [here](https://tazapay.com/payment-methods/paynow).