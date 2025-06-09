---
title: How Checkout works
excerpt: >-
  Add a low-code cross-border payment page to your website, online shop or
  marketplace.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
### Checkout Lifecycle

A customer's checkout experience looks like this:

1. When customers are ready with the goods/services and would like to complete their purchase, your application creates a new Checkout session.
2. Tazapay returns a 'url' as a response to your application's creation of a Checkout session.
3. Your application redirects the customers to the 'url' which is a Tazapay-hosted payment page, where the customers complete their payment.
4. After the completion of the payment process, Tazapay returns the customer back to your application.
5. Tazapay sends <a href="https://docs.tazapay.com/docs/checkout-webhook" target="_blank">webhooks</a> about the <a href="https://docs.tazapay.com/docs/checkout-object-states" target="_blank">state</a> of the transaction and payment details directly to your application so that you can handle fulfilment.

![](https://files.readme.io/a223951-Tazapay_checkout.jpeg "Tazapay checkout.jpeg")
