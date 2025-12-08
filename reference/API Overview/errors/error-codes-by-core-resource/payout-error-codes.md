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
### POST v3/payout

| Code  | Message                                                                                                                                                                                                     | HTTP Status |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| 20165 | Please provide either the beneficiary details or a beneficiary ID. One of these fields is mandatory for processing.                                                                                         | 422         |
| 20166 | Payout risk is not enabled to initiate payout                                                                                                                                                               | 403         |
| 20167 | Please provide a valid payout currency                                                                                                                                                                      | 400         |
| 20168 | Please provide a valid holding currency                                                                                                                                                                     | 400         |
| 20169 | Please provide a valid bank swift_code                                                                                                                                                                      | 400         |
| 20170 | Payout creation failed: The bank transfer type is swift which is incompatible with the local payout type                                                                                                    | 422         |
| 20171 | Please provide a valid purpose code to create payout                                                                                                                                                        | 400         |
| 20172 | The requested payout type does not match the beneficiary destination type                                                                                                                                   | 422         |
| 20173 | The requested beneficiary is not associated with the account                                                                                                                                                | 403         |
| 20174 | Please provide valid transaction source                                                                                                                                                                     | 400         |
| 20175 | Payout invoice document is not found. Please provide valid invoice document                                                                                                                                 | 400         |
| 20198 | Field on_behalf_of is required for creating this payout                                                                                                                                                     | 400         |
| 20199 | Please provide valid on_behalf_of should be valid xid type with prefix 'ent_'                                                                                                                               | 400         |
| 20200 | Entity doesn't match with tazapay compliance policy. Please contact us at [ops@tazapay.com](mailto:ops@tazapay.com)                                                                                         | 403         |
| 20201 | There is insufficient balance in your account to make the desired payout. Please ensure you have added sufficient funds to your account.                                                                    | 422         |
| 20296 | Requested payout config is not supported please check the payout config                                                                                                                                     | 400         |
| 20297 | Invalid or missing bank fields. Please provide a valid bank fields                                                                                                                                          | 400         |
| 20298 | The specified transaction amount does not meet the required minimum or maximum limits.                                                                                                                      | 422         |
| 20300 | Field is required and must be either one of cpf/cnpj/email/phone/random                                                                                                                                     | 400         |
| 20320 | Please provide the common bank fields to create a payout either through local or swift:%s                                                                                                                   | 400         |
| 20321 | Please provide all the valid bank local_fields to create a local payout:%s                                                                                                                                  | 400         |
| 20322 | Please provide all the valid bank swift_fields to create a swift payout:%s                                                                                                                                  | 400         |
| 20299 | Please provide a valid fx quote fx quote is expired or mismatch in from and to currency                                                                                                                     | 400         |
| 20110 | When the txn source is bfi funding interval should be configured please configure funding interval and try again later                                                                                      | 400         |
| 20035 | INR payouts purpose code validation is failing. Please check [https://docs.tazapay.com/docs/purpose-codes-valid-for-india-payouts#/](https://docs.tazapay.com/docs/purpose-codes-valid-for-india-payouts#/) | 400         |
| 20326 | Invalid fund_transfer_network provided. The specified fund transfer network is not supported for this country and currency. Please use the Payout Bank Metadata API to get the list of supported networks.  | 400         |

***

### POST v3/metadata/payout/bank

| Error Code | Error Message                                                                                                                             | HTTP Status Code |
| ---------: | :---------------------------------------------------------------------------------------------------------------------------------------- | ---------------: |
|       1040 | Account Id is required. Please check whether id provided is in correct format. Example: acc_                                              |              400 |
|       1091 | Invalid country provided in request.Please provide a valid alpha 2 country code.                                                          |              400 |
|       1092 | Invalid currency provided in request.Please provide a valid alpha 3 currency code.                                                        |              400 |
|       1093 | Invalid payout_type provided in request.Should be one of local or swift.Please provide a valid payout_type.                               |              400 |
|       1094 | Invalid entity_id provided in request.Should have 'ent_' as prefix followed by valid xid.Please provide a valid entity_id.                |              400 |
|       1095 | Invalid source provided in request.Should be one of dashboard api or grpc.Please provide a valid source.                                  |              400 |
|       1096 | Payout creation failed for provided country.Please contact [support@tazapay.com](mailto:support@tazapay.com) for more information.        |              500 |
|       1097 | Payout methods not found for provided request data.Please contact [support@tazapay.com](mailto:support@tazapay.com) for more information. |              404 |
|       1098 | Invalid bank account number.Please check the account number and try again.                                                                |              404 |
|       1099 | Invalid or missing parameter. Please provide valid parameters.                                                                            |              400 |
|       1086 | Field tax_id is required please provide a valid tax_id                                                                                    |              400 |
|       1049 | Document reference is invalid. Please provide valid document reference.                                                                   |              400 |
|       1050 | Document type is missing. Please provide valid document type.                                                                             |              400 |
|       1051 | Invalid URL format. Please make sure to provide a valid URL.                                                                              |              400 |
|       1052 | Document name is missing. Please proivde valid document name.                                                                             |              400 |
|       1053 | URL you have provided could not be reached                                                                                                |              404 |
|       1054 | URL you have provided does not have a downloadable document available                                                                     |              404 |
|       1000 | country %s is not supported at this moment                                                                                                |              404 |
|       1011 | given currency %s is not supported                                                                                                        |              404 |
|       1100 | Invalid fund_transfer_network provided. The specified fund transfer network is not supported for this country and currency combination.   |              400 |

***

### POST v3/payout/:id/fund

| Code  | Message                                                                                                                                                  | HTTP Status |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| 20290 | Field is required and must be a valid payout_id                                                                                                          | 400         |
| 20291 | Field value must be either one of validate/confirm                                                                                                       | 400         |
| 20201 | There is insufficient balance in your account to make the desired payout. Please ensure you have added sufficient funds to your account before retrying. | 422         |

***

### POST v3/payout/:id/confirm

| Code  | Message                                                                                                                                     | HTTP Status |
| :---- | :------------------------------------------------------------------------------------------------------------------------------------------ | :---------- |
| 20391 | Field cannot be empty, must be valid xid type with prefix 'col_'                                                                            | 400         |
| 20393 | Payout status is invalid to perform this action or payout has moved to higher status.                                                       | 400         |
| 20475 | The collect created is already linked to a payout. Please try with different collect id or transaction hash.                                | 400         |
| 20477 | The balance impact or the currency of the collect does not match with the payout. Please try with different transaction hash or collect id. | 400         |
| 20478 | The account ID of the payout does not match the account ID of the collect. Please ensure both transactions belong to the same account.      | 400         |
| 20479 | Collect status is invalid to perform this action                                                                                            | 400         |

<br />

### POST v3/beneficiary

| Code  | Message                                                                                                                     | HTTP Status |
| ----- | --------------------------------------------------------------------------------------------------------------------------- | ----------- |
| 20150 | Field is required please provide a valid name                                                                               | 400         |
| 20151 | PLease provide a valid email address                                                                                        | 400         |
| 20152 | Please provide a valid type                                                                                                 | 400         |
| 20153 | Please provide a valid beneficiary_details                                                                                  | 400         |
| 20154 | Please provide a valid bank_name                                                                                            | 400         |
| 20155 | Please provide a valid country. Must be alpha-2 country code. Ex: IN SG                                                     | 400         |
| 20156 | Please provide a valid currency                                                                                             | 400         |
| 20157 | Please provide a valid bank codes                                                                                           | 400         |
| 20158 | Please provide a valid payout_wallet deposit_address                                                                        | 400         |
| 20159 | Bank payout functionality is currently disabled. Please contact support for assistance.                                     | 403         |
| 20160 | Wallet payout functionality is currently disabled. Please contact support for assistance.                                   | 403         |
| 20163 | Field is required please provide a valid tax_id                                                                             | 400         |
| 20164 | Field 'url' is required and must be a valid url                                                                             | 400         |
| 20270 | Invalid or missing account type. Please provide a valid account type. Accepted values are 'savings' 'checking' or 'payment' | 400         |
| 20320 | Please provide the common bank fields to create a payout either through local or swift:%s                                   | 400         |
| 20321 | Please provide all the valid bank local_fields to create a local payout:%s                                                  | 400         |
| 20322 | Please provide all the valid bank swift_fields to create a swift payout:%s                                                  | 400         |
| 20325 | Invalid bank fields. Please provide a valid value for following fields:%s                                                   | 400         |
| 20361 | Please provide the missing required beneficiary fields:%s                                                                   | 400         |

***

### GET v3/payout/:id

| Code  | Message                                                             | HTTP Status |
| ----- | ------------------------------------------------------------------- | ----------- |
| 20197 | Field is required and must be a valid payout_id                     | 400         |
| 20180 | Payout might not exist or it is invalid please verify and try again | 404         |
| 20195 | You do not have permission to access this resource                  | 403         |

***

### GET v3/beneficiary/:id

| Code  | Message                                                                  | HTTP Status |
| ----- | ------------------------------------------------------------------------ | ----------- |
| 20161 | Field is required and must be a valid beneficiary id. Example: bnf_xid   | 400         |
| 20180 | Beneficiary might not exist or it is invalid please verify and try again | 404         |
| 20195 | You do not have permission to access this resource                       | 403         |

***

### PUT v3/beneficiary/:id

| Code  | Message                                                                | HTTP Status |
| ----- | ---------------------------------------------------------------------- | ----------- |
| 20161 | Field is required and must be a valid beneficiary id. Example: bnf_xid | 400         |
| 20323 | Please provide a valid transfer type for the selected beneficiary      | 400         |
| 20324 | Please provide a valid existing beneficiary id                         | 400         |
| 20325 | Restricted field update attempt:%s                                     | 422         |
| 20195 | You do not have permission to access this resource                     | 403         |

<br />
