---
title: How the SDK Works
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
1. Your customer initiates a checkout.
2. When your customer chooses to checkout, your server sends a request to the checkout API to create a new checkout session. A checkout session is created and it returns a token.
3. The UI component is instantiated in your customer’s browser using Tazapay.js library and the token of the checkout session.
4. The customer selects their preferred payment method. They then fill out the payment details and click on `Pay`. This completes the checkout experience.
5. Tazapay notifies your server when the payment is successfully received using webhooks. The webhook data contains the successful payment state as well as the unique transaction number for you to reconcile and perform further necessary actions.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/e45b177-Tazapay_Js_native.jpg",
        null,
        "How Tazapay's Javascript SDK works"
      ],
      "align": "center",
      "border": true,
      "caption": "How Tazapay's Javascript SDK works"
    }
  ]
}
[/block]