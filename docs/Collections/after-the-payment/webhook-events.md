---
title: Webhook events
excerpt: Use webhooks to get notified of offline/asynchronous events
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
A <a href="https://docs.tazapay.com/reference/webhooks-intro" target="_blank">webhook</a> is an HTTP endpoint on your server that receives information from Tazapay.

Webhooks allow you to get notified of any updates that happen for a transaction outside the payment flow. For example, if a customer successfully completes the payment on the hosted payment page, webhooks instantly notify you of the receiving of funds. Upon receiving the information from Tazapay, you can accordingly proceed for order fulfilment. Currently, Tazapay supports webhooks for any updates related to:

1. <a href="https://docs.tazapay.com/docs/checkout-webhook" target="_blank">The state of the checkout session.</a>
2. The payment attempts for a checkout session.
3. Refund Status.

Webhooks are also very useful when a customer chooses an asynchronous mode of payment like Local Bank Transfer. Rather than deploying your resources to constantly poll the Status API, Tazapay will itself send a webhook as soon as the funds are received.

> 👍 
> 
> Tazapay recommends use of dashboard and GET APIs only for an one-off transaction. For a faster and more-scalable approach, use webhooks.