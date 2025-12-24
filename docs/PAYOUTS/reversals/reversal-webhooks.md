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

## Step 3: Fetch the reversal balance transaction

Each payout reversal creates a **dedicated balance transaction** of type `payout_reversal`.

You can fetch this using the **Fetch Balance Transaction API**.

### Sample cURL

```bash
curl --location'https://api-brown.tazapay.com/v3/balance_transaction/btr_d52hd93k90bi91v2493g' \
--header'accept: application/json' \
--header'authorization: Bearer <your_api_key>' \
--header'tz-account-id: <account_id>'

```

## Sample Response

```json
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 140847,
        "created_at": "2025-12-19T09:11:00.604Z",
        "currency": "USD",
        "description": "pot_d52grubk90bi91v246s0",
        "fee_details": [
            {
                "amount": 1000000,
                "currency": "INR",
                "type": "fixed_fee"
            }
        ],
        "fx_conversions": [
            {
                "exchange_rate": 8.4682,
                "final": {
                    "amount": 140847,
                    "currency": "HKD"
                },
                "initial": {
                    "amount": 16632,
                    "currency": "USD"
                }
            },
            {
                "exchange_rate": 0.012007,
                "final": {
                    "amount": 12007,
                    "currency": "USD"
                },
                "initial": {
                    "amount": 1000000,
                    "currency": "INR"
                }
            }
        ],
        "id": "btr_d52hd93k90bi91v2493g",
        "metadata": {},
        "net": {
            "amount": 4625,
            "currency": "USD"
        },
        "object": "balance_transaction",
        "operation_type": "credit",
        "source": "btr_d52grubk90bi91v246vg",
        "type": "payout_reversal"
    }
}
```
