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

| Error Code | Error Message                                                                                                                             | HTTP Status Code |
| ---------: | :---------------------------------------------------------------------------------------------------------------------------------------- | ---------------: |
|       1040 | Account Id is required. Please check whether id provided is in correct format. Example: acc\_                                             |              400 |
|       1091 | Invalid country provided in request.Please provide a valid alpha 2 country code.                                                          |              400 |
|       1092 | Invalid currency provided in request.Please provide a valid alpha 3 currency code.                                                        |              400 |
|       1093 | Invalid payout\_type provided in request.Should be one of local or swift.Please provide a valid payout\_type.                             |              400 |
|       1094 | Invalid entity\_id provided in request.Should have 'ent\_' as prefix followed by valid xid.Please provide a valid entity\_id.             |              400 |
|       1095 | Invalid source provided in request.Should be one of dashboard api or grpc.Please provide a valid source.                                  |              400 |
|       1096 | Payout creation failed for provided country.Please contact [support@tazapay.com](mailto:support@tazapay.com) for more information.        |              500 |
|       1097 | Payout methods not found for provided request data.Please contact [support@tazapay.com](mailto:support@tazapay.com) for more information. |              404 |
|       1098 | Invalid bank account number.Please check the account number and try again.                                                                |              404 |
|       1099 | Invalid or missing parameter. Please provide valid parameters.                                                                            |              400 |
|       1086 | Field tax\_id is required please provide a valid tax\_id                                                                                  |              400 |
|       1049 | Document reference is invalid. Please provide valid document reference.                                                                   |              400 |
|       1050 | Document type is missing. Please provide valid document type.                                                                             |              400 |
|       1051 | Invalid URL format. Please make sure to provide a valid URL.                                                                              |              400 |
|       1052 | Document name is missing. Please proivde valid document name.                                                                             |              400 |
|       1053 | URL you have provided could not be reached                                                                                                |              404 |
|       1054 | URL you have provided does not have a downloadable document available                                                                     |              404 |
|       1000 | country %s is not supported at this moment                                                                                                |              404 |
|       1011 | given currency %s is not supported                                                                                                        |              404 |

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