---
title: Payout
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
### Endpoint: POST v3/payout

| Parameter            | Error Code | Error Message                                                                                                       |
| -------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------- |
| amount               | 20003      | Please provide a valid amount                                                                                       |
| currency             | 20061      | Field is required and must be valid ISO 4217 alpha-3 currency code                                                  |
| holding\_currency    | 20061      | Field is required and must be valid ISO 4217 alpha-3 currency code                                                  |
| beneficiary          | 20165      | Please provide either the beneficiary details or a beneficiary ID. One of these fields is mandatory for processing. |
| beneficiary\_details | 20165      | Please provide either the beneficiary details or a beneficiary ID. One of these fields is mandatory for processing. |
| txn\_source          | 20174      | Please provide a valid transaction source                                                                           |
| on\_behalf\_of       | 20197      | Please provide valid on\_behalf\_of, should be valid id type with prefix 'ent\_'                                    |

***

### Endpoint: POST v3/beneficiary

| Parameter            | Error Code | Error Message                                                                                                                   |
| -------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------- |
| name                 | 20150      | Field is required, please provide a valid name                                                                                  |
| email                | 20151      | Please provide a valid email address                                                                                            |
| type                 | 20152      | Please provide a valid type                                                                                                     |
| destination\_details | 20153      | Please provide a valid beneficiary\_details                                                                                     |
| bank\_name           | 20154      | Please provide a valid bank\_name                                                                                               |
| country              | 20155      | Please provide a valid country. Must be alpha-2 country code. Ex: IN, SG                                                        |
| currency             | 20156      | Please provide a valid currency                                                                                                 |
| bank\_codes          | 20157      | Please provide a valid bank codes                                                                                               |
| deposit\_address     | 20158      | Please provide a valid payout\_wallet deposit\_address                                                                          |
| documents.url        | 20164      | Field 'url' is required and must be a valid url                                                                                 |
| account\_type        | 20270      | "Invalid or missing account type. Please provide a valid account type. Accepted values are 'savings', 'checking', or 'payment'" |

***

### Endpoint: GET v3/payout/:id

| Parameter | Error Code | Error Message                                    |
| --------- | ---------- | ------------------------------------------------ |
| id        | 20195      | Field is required and must be a valid payout\_id |

***

### Endpoint: GET v3/beneficiary/:id

| Parameter | Error Code | Error Message                                                           |
| --------- | ---------- | ----------------------------------------------------------------------- |
| id        | 20161      | Field is required and must be a valid beneficiary id. Example: bnf\_xid |
