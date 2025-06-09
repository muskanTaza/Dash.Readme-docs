---
title: directdebit_php
excerpt: >-
  A payment method where a merchant or service provider, with the customer's
  prior authorization, directly debits funds from the customer's bank account on
  a recurring or scheduled basis.
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

- **Authorization:** The customer fills out and signs a direct debit mandate (also known as a Direct Debit Instruction or DDI), granting permission to the merchant to debit their bank account. This can be done through paper forms or increasingly through online or mobile banking platforms.
- **Bank Setup:** The merchant submits the mandate to their bank or a third-party payment processor. The customer's bank then acknowledges this instruction.
- **Payment Initiation:** On the agreed-upon date(s), the merchant (or their payment processor) initiates a debit request to the customer's bank for the specified amount.
- **Fund Transfer:** The customer's bank automatically transfers the funds from their account to the merchant's account.
- **Notification:** The customer may receive notifications from their bank or the merchant about upcoming or processed direct debit payments.
- **Key Features:**
  - **Automated Recurring Payments:** Ideal for regular bills like utilities, loan installments, subscriptions, and insurance premiums.
  - **Convenience for Customers:** Eliminates the need for manual bill payments and reduces the risk of missed payments.
  - **Efficiency for Merchants:** Ensures timely payments and can improve cash flow by automating the collection process.
  - **Potentially Lower Transaction Fees:** Compared to some other payment methods, direct debit can have lower processing fees for merchants.
  - **Security:** Transactions are processed through established banking networks, offering a secure method for recurring payments. The Direct Debit Guarantee (where applicable, though specifics in the Philippines may vary) can offer protection to customers in case of erroneous debits.

# Payment Method type

Users can use the below payment method type to create a transaction using Direct Debit in the available geography

- Philippines: `directdebit_php`

# Functionality

| Functionality               | Yes/No | Description                                                                                                    |
| --------------------------- | ------ | -------------------------------------------------------------------------------------------------------------- |
| **Refund Support**          |        |                                                                                                                |
| Full Refund                 | ❌      |                                                                                                                |
| Partial Refund              | ❌      |                                                                                                                |
| **Generally Available**     | ✅      | Means that the payment method is available by default and does not need any additional configuration/approval. |
| **Dispute and Chargebacks** | ❌      |                                                                                                                |

# Limits and Expiration

The following is the upper and lower limits for ShopeePay transactions:

- **Minimum Limit**: USD 0.01
- **Maximum Limit**: USD 860

The default expiration for a transaction is **30 minutes.**

# User Experience

Redirect Experience

For more details, please click [here](https://tazapay.com/country-list/philippines).