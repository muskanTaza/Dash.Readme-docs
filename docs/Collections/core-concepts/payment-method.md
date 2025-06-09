---
title: Payment Method
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Payment Methods are the means or mechanisms by which your customer chooses to make the payment. Tazapay supports a wide variety of payment methods.

Each payment method supported by Tazapay can be identified by a string of the format: *&lt;payment\_method&gt;&lt;underscore&gt;&lt;currency&gt;*

Example, Paynow QR which is a QR based payment method in Singapore (SG) can be identified using `paynow_sgd`.

The details of the available payment methods for a particular session can be fetched by using the [Collection Methods](https://docs.tazapay.com/reference/collection-methods-api) endpoint.

For a list of all the payment methods supported, click <a href="https://tazapay.com/payment-methods/" target="_blank">here</a>.