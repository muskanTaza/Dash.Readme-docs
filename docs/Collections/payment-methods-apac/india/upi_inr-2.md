---
title: upi_inr
excerpt: >-
  A revolutionary real-time mobile payment system developed and managed by the
  National Payments Corporation of India (NPCI).
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

- UPI enables seamless and instant fund transfers between two bank accounts using a virtual payment address (VPA), mobile number, or QR code.
- Users link their bank accounts to one or more UPI-enabled mobile applications (provided by banks or third-party providers like Google Pay, PhonePe, Paytm).
- A user initiates a payment request through their UPI app by entering the recipient's VPA, mobile number (linked to a bank account via UPI), or by scanning a UPI QR code.
- The payment is authenticated using a secure PIN (UPI PIN) set by the user for their linked bank account.
- Once authenticated, the funds are instantly debited from the sender's account and credited to the recipient's account in real-time.

# Payment Method type

Users can use the below payment method type to create a transaction using UPI in the available geography:

- India: `upi_inr`

# Functionality

| Functionality                | Yes/No | Description                                        |
| ---------------------------- | ------ | -------------------------------------------------- |
| **Refund Support**           |        |                                                    |
| Full Refund                  | ✅      |                                                    |
| Partial Refund               | ❌      |                                                    |
| **Generally Available**      | ❌      | Onboarding approval required. Usual SLA is 1 week. |
| **Disputes and Chargebacks** | ✅      |                                                    |

# Limits and Expiration

The following is the upper and lower limits for UPI transactions:

- **Minimum Limit**: USD 0.02
- **Maximum Limit**: USD 1000

The default expiration for a transaction is **24 hour.**

# User Experience

Redirect Experience

For more details, please click [here](https://tazapay.com/payment-methods/upi).