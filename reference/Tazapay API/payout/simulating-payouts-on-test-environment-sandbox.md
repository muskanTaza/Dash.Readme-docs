---
title: Simulating Payouts on Test Environment (Sandbox)
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
* Payouts created on sandbox will automatically move to `succeeded` triggering relevant webhook events in the process.
* For invoice amount between 200000 and 250000, payouts will move to `failed`
* For invoice amount between 300000 and 350000, payouts will move to `compliance_hold` and then `succeeded`
* For invoice amount between 400000 and 450000, payouts will move to `compliance_hold` and then `failed`