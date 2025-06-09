---
title: Collection Methods Fields
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
| Field            | Subfield          | type            | Description                                                                                                                                                                                      |
| :--------------- | :---------------- | :-------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| amount           |                   | integer         | Amount in invoice currency                                                                                                                                                                       |
| customer_country |                   | string          | ISO 3166 standard alpha-2 code. eg: SG, IN, US, etc.                                                                                                                                             |
| invoice_currency |                   | string          | Invoice currency (in uppercase, iso-4217 standard)                                                                                                                                               |
| payment_methods  |                   | array of json   | List of payment methods available for the country-currency combination                                                                                                                           |
|                  | amount            | integer         | Amount in charge currency                                                                                                                                                                        |
|                  | banks             | array of string | Banks if any for the customer to select. This is specific to a payment method                                                                                                                    |
|                  | currency          | string          | Charge currency (the currency in which the customer is charged)                                                                                                                                  |
|                  | exchange_rate     | float           | Exchange rate from invoice currency to charge currency                                                                                                                                           |
|                  | experience_type   | enum            | `native`, `redirect_with_input`, `redirect`                                                                                                                                                      |
|                  | family            | enum            | Family in which the payment method is characterised (`real_time_payment`, `card`, `payment_initiation_service`, `wallet`, `local_bank_transfer`, `wire_transfer`, `internet_banking`, `voucher`) |
|                  | group             | enum            | `card`, `apm`, `lbt`, `wire`                                                                                                                                                                     |
|                  | logo_url          | array of string | Logos for the payment method                                                                                                                                                                     |
|                  | type              | enum            | Payment Method type. Unique identifier representing a payment method. This is the string that you can use to specify payment methods for a checkout / escrow session.                            |
|                  | name              | string          | Customer display name for the payment method. Useful to call the payment method with this name on your checkout screen.                                                                          |
|                  | notification_type | enum            | Whether the payment is confirmed instantaneously with the customer in the payment flow. `synchronous` or `asynchronous`                                                                          |
|                  | transaction_fee   | integer         | Fees applicable for the payment method                                                                                                                                                           |