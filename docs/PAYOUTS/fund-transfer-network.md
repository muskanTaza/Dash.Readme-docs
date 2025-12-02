---
title: Fund Transfer Network
excerpt: >-
  Fund transfer network is the underlying payment clearing network used to
  process your local payout. FTN affects payout speed, limits, cutoffs etc.
deprecated: false
hidden: true
metadata:
  robots: index
---
To achieve our goal of making payouts more and more predictable, we now allow users to specify a fund transfer network in case of a local payout. You can do so by both API as well as the dashboard.

## Dashboard

1. Click on `Create Payout`under the Payouts tab in the merchant dashboard.
2. Select the beneficiary for the payout.
3. Enter the payout amount and currency, one you do, you will get an option to select the fund transfer network

<Image border={false} src="https://files.readme.io/d5e55f4888a3273a18f9f719d7038f869241a64de413c1dcfa25045410727c68-Screenshot_2025-12-02_at_2.03.59PM.png" />

## API

1. In the [create payout API](https://docs.tazapay.com/reference/create-payout#/) , add the below field to specify the fund transfer network -

```json
 "local": {
    "fund_transfer_network": "imps"
 }
```

Checkout the API reference for complete API request and response.

<br />
