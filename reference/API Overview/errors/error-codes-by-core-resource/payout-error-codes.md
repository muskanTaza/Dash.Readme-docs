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

| error_code | error_message                                                                                                                                            | http_status |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- |
| 20003      | Please provide a valid amount                                                                                                                            | 400         |
| 20028      | Please provide beneficiary name in Chinese                                                                                                               | 400         |
| 20029      | Please provide valid beneficiary national identification number                                                                                          | 400         |
| 20030      | Field is required and must be valid logistic tracking details                                                                                            | 400         |
| 20035      | Transaction not allowed                                                                                                                                  | 400         |
| 20036      | Account holder name is required and cannot be empty                                                                                                      | 400         |
| 20038      | Both holding_fx_quote and destination_fx_quote cannot be provided                                                                                        | 400         |
| 20039      | The amount locked in fx quote is not the same as the amount in request                                                                                   | 400         |
| 20040      | this purpose code is not supported for the Remitter and Beneficiary type combination                                                                     | 422         |
| 20041      | Invalid source for providing destination_info                                                                                                            | 400         |
| 20042      | EURC currency is not supported                                                                                                                           | 400         |
| 20043      | Mismatch detected: The provided destination currency does not align with our system records                                                              | 422         |
| 20044      | Non-fiat currency is not supported or invalid                                                                                                            | 400         |
| 20061      | Field is required and must be valid ISO 4217 alpha-3 currency code                                                                                       | 400         |
| 20067      | Holding currency not found for the specified account                                                                                                     | 400         |
| 20152      | Please provide a valid type                                                                                                                              | 400         |
| 20165      | Please provide either the beneficiary details or a beneficiary ID. One of these fields is mandatory for processing.                                      | 422         |
| 20167      | Please provide a valid payout currency                                                                                                                   | 400         |
| 20168      | Please provide a valid holding currency                                                                                                                  | 400         |
| 20170      | Payout creation failed: The bank transfer type is swift, which is incompatible with the local payout type                                                | 422         |
| 20171      | Please provide a valid purpose code to create payout                                                                                                     | 400         |
| 20172      | The requested payout type does not match the beneficiary destination type                                                                                | 422         |
| 20173      | The requested beneficiary is not associated with the account                                                                                             | 403         |
| 20174      | Please provide valid transaction source                                                                                                                  | 400         |
| 20175      | Payout invoice document is not found. Please provide valid invoice document                                                                              | 400         |
| 20196      | Field on_behalf_of is required for creating this payout                                                                                                  | 400         |
| 20197      | Please provide valid on_behalf_of, should be valid xid type with prefix ent_                                                                             | 400         |
| 20199      | There is insufficient balance in your account to make the desired payout. Please ensure you have added sufficient funds to your account before retrying. | 422         |
| 20231      | Field is required and must be a valid document type.                                                                                                     | 400         |
| 20283      | Provided document is not sufficient to create payout                                                                                                     | 400         |
| 20296      | Requested payout config is not supported, please check the payout config                                                                                 | 400         |
| 20298      | The specified transaction amount does not meet the required minimum or maximum limits.                                                                   | 422         |
| 20299      | Please provide a valid quote, payout or fx quote is expired or mismatch in from and to currency                                                          | 400         |
| 20323      | Please provide a valid transfer type for the selected beneficiary                                                                                        | 400         |
| 20380      | Mismatch detected: The provided beneficiary registration number does not align with our system records                                                   | 400         |
| 20381      | Mismatch detected: The provided beneficiary business name does not align with our system records                                                         | 400         |
| 20382      | Mismatch detected: The provided beneficiary business address country does not align with our system records                                              | 400         |
| 20383      | Beneficiary date of birth is required and can't be empty when beneficiary type is individual                                                             | 400         |
| 20385      | Beneficiary registration number is required and can't be empty                                                                                           | 400         |
| 20386      | Beneficiary address details are required and can't be empty                                                                                              | 400         |
| 20387      | Beneficiary party classification is required, please pass valid party classification                                                                     | 400         |
| 20388      | Mismatch detected: The provided individual name does not align with our system records                                                                   | 400         |
| 20389      | Individual business must be a sole proprietorship                                                                                                        | 400         |
| 20400      | Mismatch detected: The provided date of birth does not align with our system records                                                                     | 400         |
| 20401      | VASP name is required for wallet beneficiary                                                                                                             | 400         |
| 20403      | This wallet beneficiary is not yet approved, please get your beneficiary approved before creating a payout                                               | 400         |
| 20426      | Payout Quote cannot be validated if either holding_fx_quote or destination_fx_quote is present                                                           | 400         |
| 20427      | Payout quote mismatch with Create Payout request                                                                                                         | 400         |
| 20433      | Please provide a valid payout quote, payout quote is expired                                                                                             | 400         |

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

<br />

| error_code | error_message                                                                                   | http_status |
| ---------- | ----------------------------------------------------------------------------------------------- | ----------- |
| 3500       | Account id is required. Please pass a valid account id                                          | 400         |
| 3505       | Bank id is required                                                                             | 400         |
| 3509       | Bank account does not exist for requested account                                               | 400         |
| 3510       | Field is required and must be ISO 3166-1 alpha-2 country code                                   | 400         |
| 3511       | Field is required and must be ISO 4217 alpha-3 currency code                                    | 400         |
| 3513       | Bank details not found. Please pass a valid bank id                                             | 400         |
| 3519       | Not allowed to change the account holder's name                                                 | 400         |
| 3520       | KYB entity type is required. Please select valid entity type to add bank                        | 400         |
| 3521       | A bank with the currency code already exists use a different currency code                      | 400         |
| 3523       | Invalid beneficiary, should have prefix 'bnf_' and should be followed by valid xid              | 400         |
| 3524       | Invalid or missing account number. Please provide a valid account number.                       | 400         |
| 3525       | Invalid or missing account holder name. Please provide a valid account holder name.             | 400         |
| 3526       | Invalid or missing bank name. Please provide a valid bank name                                  | 400         |
| 3527       | Invalid or missing bank codes. Please provide a valid bank codes                                | 400         |
| 3528       | Invalid or missing IBAN. Please provide a valid IBAN                                            | 400         |
| 3529       | Invalid or missing Swift code. Please provide a valid Swift code                                | 400         |
| 3530       | Invalid or missing wallet address. Please provide a valid wallet address.                       | 400         |
| 3531       | Invalid or missing email. Please provide a valid email address.                                 | 400         |
| 3532       | Invalid or missing tax id. Please provide a valid tax id.                                       | 400         |
| 3533       | Invalid or missing url. Please provide a valid url.                                             | 400         |
| 3534       | Invalid or missing account type. Please provide a valid account type.                           | 400         |
| 3535       | Invalid or missing country. Please provide a valid country.                                     | 400         |
| 3536       | Field is required, please provide a valid beneficiaryID                                         | 400         |
| 3537       | Field is required, please provide a valid beneficiary type                                      | 400         |
| 3544       | Field is required, please provide a valid deposit_key                                           | 400         |
| 3545       | Field is required, please provide a valid local_payment_network type                            | 400         |
| 3546       | Field is required and value must be one of cpf/cnpj/email/phone/random                          | 400         |
| 3547       | Field is required, please provide a valid deposit_address                                       | 400         |
| 3800       | Please provide the common fields for the bank:%s                                                | 400         |
| 3801       | Please provide all the valid bank local_fields:%s                                               | 400         |
| 3802       | Please provide all the valid bank swift_fields:%s                                               | 400         |
| 3803       | Invalid bank fields. Please provide a valid value for following fields:%s                       | 400         |
| 3805       | Beneficiary details not found. Please pass a valid beneficiary id                               | 400         |
| 3806       | Field is conditionally required: please provide either a valid beneficiary ID or a bank object. | 400         |
| 3807       | Field is conditionally required: please provide either a bank object or a valid beneficiary ID. | 400         |
| 3850       | Field is required, please provide a valid vasp_id                                               | 400         |
| 3851       | Field is required, please provide a valid vasp_website                                          | 400         |

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
