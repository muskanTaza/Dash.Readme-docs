---
title: Create a quote
excerpt: ''
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

- Passing the initial_amount returns the converted_amount based on the prevailing exchange rate.
- Passing the converted_amount returns the initial_amount based on the prevailing exchange rate.