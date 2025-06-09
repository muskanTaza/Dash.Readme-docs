---
title: payeasy_jpy / payeasy_cash_jpy
excerpt: >-
  Payeasy is a unique and widely used payment method in Japan that bridges the
  gap between online transactions and physical payment at ATMs or convenience
  stores.
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

While both PayEasy and PayEasy Cash are payment options in Japan, they refer to slightly different ways a consumer can use the PayEasy system to complete a transaction:

**PayEasy (General)**

- This is the overarching payment service that allows consumers to pay for online purchases, bills, and other services conveniently through various channels.
- **Payment Channels:** PayEasy offers two main ways for consumers to pay:
  - **ATM Payment:** Using a payment number provided by the merchant, the consumer can go to a participating bank ATM and pay using cash or their ATM card.
  - **Online Banking Payment:** The consumer can select PayEasy during online checkout, choose their bank, and complete the payment directly through their online banking interface.

**PayEasy Cash**

- This specifically refers to the **ATM payment method within the broader PayEasy system where the consumer uses cash to make the payment.**
- **How it Works:**
  - The consumer receives a unique payment number (including a recipient number, customer number, and confirmation number) from the online merchant or biller.
  - They visit a participating bank ATM that displays the PayEasy logo.
  - They select the "Pay-easy" or "Tax & Fee Payment" option on the ATM.
  - They enter the required numbers (recipient number, customer number, confirmation number).
  - They confirm the payment details displayed on the screen.
  - They select "Cash" as the payment method and insert the required amount into the ATM.
  - The ATM issues a receipt as proof of payment.

# Payment Method type

Users can use the below payment method type to create a transaction using Payeasy in the available geography

- Japan: `payeasy_jpy` / `payeasy_cash_jpy`

# Functionality

| Functionality               | Yes/No | Description                                                                             |
| --------------------------- | ------ | --------------------------------------------------------------------------------------- |
| **Refund Support**          |        |                                                                                         |
| Full Refund                 | ❌      |                                                                                         |
| Partial Refund              | ❌      |                                                                                         |
| **Generally Available**     | ❌      | Requires website localization & local support in JP. Usual SLA on onboarding is 1 week. |
| **Dispute and Chargebacks** | ✅      | via police complaints / bank recalls, etc.                                              |

# Limits and Expiration

The following is the upper and lower limits for Payeasy transactions:

- **Minimum Limit**: USD 0.01
- **Maximum Limit**: USD 7636

The default expiration for a transaction is 8 days and 10 **minutes**.

# User Experience

Redirect Experience

For more details, please click [here](https://tazapay.com/payment-methods/payeasy).