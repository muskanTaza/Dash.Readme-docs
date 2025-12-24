---
title: Reconciliation
deprecated: false
hidden: false
metadata:
  robots: index
---
Each reversed payout is represented by two explicitly linked balance transactions:

1. **Payout debit**

   Created when the payout was processed

   Type: `payout`

   Operation Type: `debit`

2. **Payout reversal credit**

   Created when the payout is reversed

   Type: `payout_reversal`

   Operation Type: `credit`

These two transactions together represent the full financial lifecycle of the payout.

***

## How to identify the correct transactions

To reconcile a reversed payout:

1. Fetch the payout using the Payout API
2. Note the payout ID (for example: `pot_xxxxx`)
3. Fetch balance transactions where:
   * `type = payout` and `source = <payout_id>`
   * `type = payout_reversal` and `description` references the same payout

***

## How to compute the net financial impact

Reconciliation should be based on the **net balance impact**, calculated as:

```
Net impact= payout_reversal.net.amount − payout.net.amount
```

Important points to note:

* The reversal credit amount may not exactly match the original payout debit
* Differences can occur due to:
  * Third-party bank or network-level return fees
  * FX rate differences between payout time and reversal time
  * Intermediary charges applied by downstream institutions
* All such differences are transparently itemized in the reversal balance transaction
