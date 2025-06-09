---
title: Required Information to create a Payout Beneficiary
excerpt: ''
deprecated: true
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Local Payout Guide

Following are the bank codes mandatory for a country-currency pair. Pass the bank codes in the `bank_codes` field in the beneficiary.destination_details object.

| Currency | Country        | Mandatory Bank Codes       | account_number / iban | Other Required Fields                                           |
| :------- | :------------- | :------------------------- | :-------------------- | :-------------------------------------------------------------- |
| AUD      | Australia      | `bsb_code`                 | account_number        |                                                                 |
| BRL      | Brazil         | `branch_code`, `bank_code` | account_number        | `tax_id`, `bank.account_type`                                   |
| CAD      | Canada         | `branch_code`, `bank_code` | account_number        |                                                                 |
| CNY      | China          | `swift_code`               | account_number        | `national_identification_number*`, `logistics_tracking_details` |
| CZK      | Czech Republic | -                          | iban                  |                                                                 |
| DKK      | Denmark        | `bank_code`                | account_number        |                                                                 |
| EEA\*\*  | EUR            | `swift_code`               | iban                  |                                                                 |
| HKD      | Hongkong       | `swift_code`               | account_number        |                                                                 |
| HUF      | Hungary        | `-`                        | iban                  |                                                                 |
| IDR      | Indonesia      | `swift_code`               | account_number        |                                                                 |
| INR      | India          | `ifsc_code`                | account_number        | `beneficiary.address_details`                                   |
| KRW      | Korea          | `swift_code`               | account_number        |                                                                 |
| MXN      | Mexico         | `swift_code`               | account_number        |                                                                 |
| MYR      | Malaysia       | `swift_code`               | account_number        | `phone`                                                         |
| NGN      | Nigeria        | `swift_code`               | account_number        |                                                                 |
| NOK      | Norway         | `bank_code`                | account_number, iban  |                                                                 |
| PHP      | Philippines    | `swift_code`               | account_number        |                                                                 |
| PKR      | Pakistan       | -                          | iban                  |                                                                 |
| PLN      | Poland         | `swift_code`               | iban                  |                                                                 |
| QAR      | Qatar          | `swift_code`               | iban                  |                                                                 |
| RON      | Romania        | -                          | iban                  |                                                                 |
| SEK      | Sweden         | `bank_code`                | account_number        |                                                                 |
| SGD      | Singapore      | `swift_code`               | account_number        |                                                                 |
| THB      | Thailand       | `swift_code`               | account_number        |                                                                 |
| TRY      | Turkey         |                            | iban                  |                                                                 |
| GBP      | United Kingdom | `sort_code`                | account_number        |                                                                 |
| EUR      | United Kingdom |                            | iban                  |                                                                 |
| USD      | United States  | `aba_code`                 | account_number        |                                                                 |
| VND      | Vietnam        | `swift_code`               | account_number        |                                                                 |

> **European Economic Area Countries Include**: Austria, Belgium, Bulgaria, Cyprus, Czech Republic, Denmark, Estonia, Finland, France, Germany, Greece, Hungary, Iceland, Ireland, Italy, Latvia, Liechtenstein, Lithuania, Luxembourg, Malta, Monaco, Netherlands, Norway, Poland, Portugal, Romania, Slovakia, Spain, Sweden, Switzerland.
>
> **\*national_identification_number**: This is a conditionally mandatory field required for doing individual local payouts in China. For payouts to businesses, it is not needed

## Swift Payout guide

Following are the bank codes mandatory for a country to do a `swift` payment. Pass the bank codes in the `bank_codes` field in the beneficiary.destination_details object.

| Countries                                                                                                                                                                                                  | Mandatory Bank Codes | account_number / iban (Either account_number or IBAN is required) | Other Required Fields         |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------- | :---------------------------------------------------------------- | :---------------------------- |
| United Arab Emirates, Switzerland, Denmark, European Economic Area (EEA), Hungary, Israel, Norway, Pakistan, Poland, Qatar, Romania, Sweden, United Kingdom                                                | `swift_code`         | `IBAN`                                                            |                               |
| Australia, Colombia, Bangladesh, Canada, China, Czech Republic, Egypt, Hong Kong, Indonesia, Japan, Kenya, South Korea, Sri Lanka, Mexico, Nigeria, New Zealand, Oman, Turkey, United States, South Africa | `swift_code`         | `account_number`                                                  |                               |
| India                                                                                                                                                                                                      | `swift_code`         | `account_number`                                                  | `beneficiary.address_details` |
| Brazil                                                                                                                                                                                                     | `swift_code`         | `account_number`                                                  | `tax_id`                      |
| Philippines, Singapore, Thailand, Vietnam                                                                                                                                                                  | `swift_code`         | `account_number`                                                  |                               |
| Malaysia                                                                                                                                                                                                   | `swift_code`         | `account_number`                                                  | `phone`                       |