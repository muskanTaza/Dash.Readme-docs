---
title: Payout Quote
excerpt: >-
  Lock in the exact amount to be deducted a payout. The API returns the fees
  along with exchange rates which will be applicable to the payout. The payout
  quote generated will be unique to your account.
api:
  file: sandbox.json
  operationId: post_v3payoutquote
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
* Holding currency refers to the balance currency. This is the currency whose balance will fund the payout. In case it is not specified in the request to create a quote, the holding currency will be determined based on this priority order.
  * Payout Currency if the payout currency is one of the balance currencies for the account.
  * Primary Holding Currency
* Destination Currency refers to the currency in which Tazapay will transfer funds to the beneficiary. In case it is not specified in the request to create a quote, the payout currency will be considered as the destination currency.
* Payout Currency and Payout Amount are mandatory requirements to generate a quote.
* The id returned in the response can be passed in the `quote` parameter in the Create Payout request to lock the exchange rates and amount to be deducted from the balance.