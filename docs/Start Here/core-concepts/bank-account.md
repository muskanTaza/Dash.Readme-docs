---
title: Bank Account
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Bank Account details for a user can be added by logging in to <a href="https://app.tazapay.com" target="_blank">Tazapay Dashboard</a> or passing the information using the [Add Bank](ref:add-bank-api) endpoint. 

Tazapay can help disburse the funds directly to the seller’s preferred bank account (or initiate a refund to a buyer’s bank account). To do that, we would need to collect the user’s bank details.

We provide payouts in both local currency and USD. Check the currencies we carry in the [Invoice Currency API](ref:invoice-currency-api) or the <a href="https://tazapay.com/" target="_blank">interactive widget on the homepage</a>.

Depending on the geography, we would need the following information:

* Account ID of user `UUID`
* Name on the Bank Account `legal_name`
* Account Number `account_number`
* <a href="https://tazapay-api-developer.readme.io/reference/bank-codes" target="_blank">Bank Codes</a>`bank_codes`
* Bank Name `bank_name`
* Country code `country_code`
* Contact number `contact_number`
* Currency `currency`

> 🚧 Your legal business name should be same as the bank account name in order for us to release the money to your account.
