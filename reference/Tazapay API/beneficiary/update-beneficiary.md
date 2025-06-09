---
title: Update Beneficiary
excerpt: This lets you update an existing beneficiary
api:
  file: sandbox.json
  operationId: update-beneficiary
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
### For beneficiaries having successful payouts, the following information cannot be updated

- Type (business or individual)
- Beneficiary Name
- Account Number / IBAN
- Country
- Existing Bank Codes (SWIFT, IFSC, BSB_CODE, ABA_CODE, etc.). Additional bank codes can be added.

In these scenarios, you can create a new beneficiary with the updated details.