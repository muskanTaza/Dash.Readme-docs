---
title: Create a payin
excerpt: Creates a payin object.
api:
  file: sandbox.json
  operationId: create-payin
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
After the payin is created, provide payment method details and confirm the payin. 

When you use `confirm = true` during creation, you create and confirm the payin in the same API call. You MUST use the parameters in confirm API when you supply `confirm = true`