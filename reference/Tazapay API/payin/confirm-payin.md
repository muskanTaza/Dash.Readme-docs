---
title: Confirm Payin
excerpt: Attach a payment method to the payin and create an attempt
api:
  file: sandbox.json
  operationId: confirm-payin
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Confirms that your customer intends to pay with the provided payment method. Upon confirmation, a new payment attempt will be created. You can guide your customer through the next steps using the fields `status_description` and `latest_payment_attempt_data`