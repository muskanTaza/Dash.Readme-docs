---
title: qris_idr
excerpt: >-
  **QRIS (Quick Response Code Indonesian Standard) in Indonesia:** A national QR
  code standard developed and implemented by Bank Indonesia (the central bank)
  to unify all QR code payment systems across the country.
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

- **Standardization:** QRIS establishes a single QR code that can be used by all participating payment service providers (PSPs), including banks, e-wallets, and fintech companies.
- **Merchant Display:** Merchants only need to display one QRIS code, eliminating the clutter of multiple QR codes from different payment platforms.
- **User Scanning:** Consumers can use any QRIS-enabled payment application on their smartphones (e.g., GoPay, OVO, Dana, LinkAja, ShopeePay, and mobile banking apps from various banks) to scan the merchant's QRIS code.
- **Payment Initiation:** After scanning, the user enters the payment amount (for static QR codes) or the amount is pre-filled (for dynamic QR codes).
- **Confirmation and Transfer:** The user reviews the transaction details and confirms the payment within their chosen mobile payment application. Funds are then transferred in near real-time from the consumer's account to the merchant's account, regardless of the underlying payment service providers used by each party.

# Payment Method type

Users can use the below payment method type to create a transaction using QRIS in the available geography

- Indonesia: `shopeepay_vnd`

# Functionality

| Functionality               | Yes/No | Description                                                                                                    |
| --------------------------- | ------ | -------------------------------------------------------------------------------------------------------------- |
| **Refund Support**          |        |                                                                                                                |
| Full Refund                 | ✅      |                                                                                                                |
| Partial Refund              | ❌      |                                                                                                                |
| **Generally Available**     | ✅      | Means that the payment method is available by default and does not need any additional configuration/approval. |
| **Dispute and Chargebacks** | ❌      |                                                                                                                |

# Limits and Expiration

The following is the upper and lower limits for QRIS transactions:

- **Minimum Limit**: USD 0.06
- **Maximum Limit**: USD 600

The default expiration for a transaction is **2 minutes.**

# User Experience

Native Experience

For more details, please click [here](https://tazapay.com/payment-methods/qris).