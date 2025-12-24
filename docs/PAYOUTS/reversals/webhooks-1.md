---
title: Webhooks
excerpt: >-
  You can programmatically detect, track, and reconcile payout reversals using
  webhooks and APIs.
deprecated: false
hidden: false
metadata:
  robots: index
---
## Step 1: Detect a payout reversal

When a payout is reversed, TazaPay transitions the payout to a new terminal state: `reversed`.

You can detect this in the following ways:

* **Webhook event**: `payout.reversed`
* **Payout API**: Fetching a payout shows `status = reversed`
* **Dashboard**: Payout appears under the _Reversed_ filter
* **Reports**: Reversal reflected as a separate balance transaction

## Step 2: Consume the `payout.reversed` webhook

When a payout is reversed, TazaPay emits a webhook event with the updated payout object.

Key characteristics:

* Event type: `payout.reversed`
* Triggered once per payout
* Contains:
  * Payout ID
  * Final status (`reversed`)
  * Reversal reason code
  * Reversal balance transaction ID

Merchants should:

* Treat `reversed` as a **terminal state**
* Update internal payout records accordingly

<br />
