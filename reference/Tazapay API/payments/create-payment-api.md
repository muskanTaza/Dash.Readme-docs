---
title: Create Payment
excerpt: >-
  Generates payment links corresponding to an escrow for collection from the
  buyer
api:
  file: sandbox.json
  operationId: create-payment-api
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
> ❗ Filter Errors
>
> When you want to include a payment method in a payment URL, do *not* include this under the filter parameter. The filter function is meant to disable payment methods.

> 📘
>
> Tazapay has a [per transaction limit](https://support.tazapay.com/is-there-a-per-transaction-limit) depending on the payment method and currency. To avoid any errors, please refer to our FAQ.
