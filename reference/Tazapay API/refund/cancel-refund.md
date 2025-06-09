---
title: Cancel Refund
excerpt: This endpoint cancels an already existing refund object
api:
  file: sandbox.json
  operationId: cancel-refund
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
> ❗️ 
> 
> A request to cancel the refund can only be made if the refund object is in the `initiated` state. If the refund is in any other state, the API call will result in an error.