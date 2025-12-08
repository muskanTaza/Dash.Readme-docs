---
title: Webhook Retry Policy
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
If Tazapay does not receive a 2xx status from your endpoint as an acknowledgement of successful webhook delivery, it keeps retrying.

Tazapay keeps retrying for the below error codes:

* StatusBadRequest - 400
* StatusNotFound - 404
* StatusRequestTimeout - 408
* StatusConflict - 409
* StatusPreconditionFailed - 412
* StatusInternalServerError - 500

The time between each retry increases exponentially by a power of 2 with jitter till a period of 8 hours. The first retry starts after 1 second of original webhook delivery. 

This process is repeated 3 times. You can receive a retried webhook upto 24 hours from the delivery of the first webhook.