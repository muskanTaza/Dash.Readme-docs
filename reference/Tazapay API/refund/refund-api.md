---
title: Initiate Refund
excerpt: To initiate a refund of an existing paid transaction back to source
api:
  file: sandbox.json
  operationId: refund-api
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> 📘 Not all the payment methods support refunds!
>
> Depending on the payment method, Tazapay may not be able to process refunds. For more info, read our [FAQ](https://support.tazapay.com/what-payment-methods-are-unsupported-for-refunds)

* For refunding a payment made by Promptpay, WeChat, Linepay, Shopeepay and Truemoney in Thailand, the customer's phone number is required. You can choose to pass it to Tazapay in the customer\_details field of the checkout API. You can also use the Update Customer endpoint to attach the phone number to an existing customer you want to refund.