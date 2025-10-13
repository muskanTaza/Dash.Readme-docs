---
title: Create a quote
excerpt: This is available on request.
api:
  file: sandbox.json
  operationId: create-a-quote
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Either `initial_amount` or `converted_amount` is mandatory.

* Passing the initial\_amount returns the converted\_amount based on the prevailing exchange rate.
* Passing the converted\_amount returns the initial\_amount based on the prevailing exchange rate.