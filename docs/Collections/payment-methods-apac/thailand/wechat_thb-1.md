---
title: wechat_thb
excerpt: '  A popular mobile wallet and payment service particularly favored by Chinese tourists and residents, as well as businesses that cater to them.'
deprecated: false
hidden: false
metadata:
  robots: index
---
# How It Works

* **For Chinese Users:** Users with a Chinese ID and bank account can use the cross-border payment feature of the WeChat app. The user's account is linked to their Chinese bank account, and the app automatically handles the currency conversion from Thai Baht (THB) to Chinese Yuan (CNY) at the real-time exchange rate.
* **For Merchants:** Merchants in Thailand that accept WeChat Pay display a QR code. The customer simply scans this QR code with their WeChat app to make the payment. The merchant's system receives an instant confirmation of the payment, and the funds are settled in Thai Baht (THB) to their local bank account, often with a slight delay for processing.
* **Payment Types:** WeChat Pay supports various payment flows in Thailand, including QR code payments, in-app payments, and mini-program payments. The most common method is the QR code-based transaction.

# Payment Method type

Users can use the below payment method type to create a transaction using WechatPay in the available geography

* Thailand: `wechat_thb`

# Functionality

| Functionality           | Yes/No | Description                                                                                                    |
| ----------------------- | ------ | -------------------------------------------------------------------------------------------------------------- |
| **Refund Support**      |        |                                                                                                                |
| Full Refund             | ✅      |                                                                                                                |
| Partial Refund          | ✅      |                                                                                                                |
| **Generally Available** | ✅      | Means that the payment method is available by default and does not need any additional configuration/approval. |
| Dispute and Chargebacks | ❌      |                                                                                                                |

# Limits and Expiration

The following is the upper and lower limits for ShopeePay transactions:

* **Minimum Limit**: USD 0.02
* **Maximum Limit**: USD 200000

The default expiration for a transaction is **2 hours.**

# User Experience

Redirect Experience
