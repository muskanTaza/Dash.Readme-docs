---
title: promptpay_thb
excerpt: >-
  PromptPay is an interbank real-time near-instant payment system that enables
  users to easily receive and transfer funds using either their Citizen ID or
  mobile phone number.  #
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

- Users register for PromptPay with their bank, linking their mobile phone number or citizen ID to their bank account.
- Payments can be made by:
  - Scanning a QR code displayed by the merchant.
  - Entering the recipient's mobile phone number or citizen ID.
- Funds are transferred instantly between bank accounts.

# Payment Method type

Users can use the below payment method type to create a transaction using PromptPay in the available geography

- Thailand: `promptpay_thb`

# Functionality

| Functionality               | Yes/No | Description                                                                                                    |
| --------------------------- | ------ | -------------------------------------------------------------------------------------------------------------- |
| **Refund Support**          |        |                                                                                                                |
| Full Refund                 | ✅      | Only if mobile number is provided                                                                              |
| Partial Refund              | ✅      | Only if mobile number is provided                                                                              |
| **Generally Available**     | ✅      | Means that the payment method is available by default and does not need any additional configuration/approval. |
| **Dispute and Chargebacks** | ✅      |                                                                                                                |

# Limits and Expiration

The following is the upper and lower limits for PromptPay transactions:

- **Minimum Limit**: USD 0.5
- **Maximum Limit**: USD 19000

The default expiration for a transaction is **20 minutes.** This is further configurable within the default time of expiration.

# User Experience

Native Experience

For more details, please click [here](https://tazapay.com/payment-methods/promptpay).