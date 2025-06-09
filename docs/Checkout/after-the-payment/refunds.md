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

Refunds use your available Tazapay balance. If you do not have sufficient balance, the refund request gets rejected and you have to add on to your Tazapay balance so that future refund requests can go through successfully. For most transactions, there are no fees to process a refund, but processing fees and Tazapay fees from the original transaction aren't returned.