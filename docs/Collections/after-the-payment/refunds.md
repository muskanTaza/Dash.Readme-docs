---
title: Refunds
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
You can make refunds to your customers against a particular transaction using the <a href="https://docs.tazapay.com/reference/refund-api" target="_blank">refund endpoint</a>. You can either make a full refund or a partial refund of the initial transaction. You can also make multiple requests for partial refunds provided the sum of these partial refunds does not exceed the transaction amount.

Refunds use your funds available with Tazapay. If you do not have sufficient funds with Tazapay, the refund request gets rejected. It is necessary to ensure that you have sufficient funds with Tazapay to process refunds.