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
* For invoice amount of exactly 100000, the payout stays in `processing` forever
* For invoice amount between 200000 and 250000, payouts will move to `failed`
* For invoice amount between 300000 and 350000, payouts will move to `compliance_hold` and then `succeeded`
* For invoice amount between 400000 and 450000, payouts will move to `compliance_hold` and then `failed`
* For invoice amount of exactly 500000, the payout stays in `compliance_hold` forever
* For invoice amount between 500000 and 600000, payouts will move to `succeeded` and then `reversed`
  * 500000 - 549999: balance impact, payout fee impact, no fx impact, no third party fee impact
  * 550000 - 600000: balance impact, payout fee impact, fx impact, third party fee impact