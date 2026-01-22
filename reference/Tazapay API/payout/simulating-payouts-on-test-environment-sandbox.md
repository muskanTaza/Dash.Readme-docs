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

To test different payout scenarios, use the following invoice amounts:

| Invoice Amount    | Simulated Behavior                                                          |
| :---------------- | :-------------------------------------------------------------------------- |
| Any other amount  | Payout `succeeds` normally                                                  |
| Exactly 100,000   | Payout stays in `processing` indefinitely                                   |
| 200,000 – 250,000 | Payout `failed`                                                             |
| 300,000 – 350,000 | Payout goes to `compliance_hold`, then `succeeds`                           |
| 400,000 – 450,000 | Payout goes to `compliance_hold`, then `failed`                             |
| Exactly 500,000   | Payout stays in `compliance_hold` indefinitely                              |
| 500,000 – 550,000 | Payout `succeeds`, then gets `reversed`                                     |
| 550,000 – 600,000 | Payout `succeeds`, then gets `reversed` with fx impact and third-party fees |
