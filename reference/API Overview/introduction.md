---
title: Introduction
excerpt: How Tazapay's API works to create a payment gateway
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
The Tazapay API is organised around <a href="https://en.wikipedia.org/wiki/Representational_state_transfer" target="_blank">REST</a>. Our API has predictable resource-oriented URLs, accepts form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

You can use the Tazapay API in test mode, which doesn't affect your live data or interact with the payment rails. The API key you use in combination with the endpoint URL determine whether the request is in live mode or test mode.
