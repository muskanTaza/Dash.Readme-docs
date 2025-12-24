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

***

### Third-party fees and FX rate visibility

TazaPay provides full visibility into fees and exchange rates applied during a payout reversal.

For each `payout_reversal` balance transaction, merchants can view:

* **Third-party fees**

  Returned under `fee_details`, representing bank, PSP, or network fees incurred during the payout or reversal process.

  These fees may be reported in currencies different from the payout currency and are transparently itemized.

* **Applied FX rates**

  Returned under `fx_conversions`, showing:

  * The exchange rates applied at the time of reversal
  * Converted amounts across currencies
  * Any third-party or holding-currency FX movements

***

## Using the balance transaction object for reconciliation

The balance transaction object provides all required reconciliation inputs:

* `amount` and `currency`: Gross credited or debited amount
* `operation_type`: `debit` or `credit`
* `fee_details`: Any applied fixed or variable fees
* `fx_conversions`: FX rates used and converted amounts
* `net`: Final net balance impact
* `created_at`: Timestamp for ledger ordering
* `type`: `payout` or `payout_reversal`

For reconciliation systems, TazaPay recommends using the **`net.amount`** field as the authoritative value for ledger posting.
