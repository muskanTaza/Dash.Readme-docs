---
title: KYB
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
| ERROR CODE | Meaning                                                                                                                                                                                                              |
|------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 2300       | KYB application already exists, please update existing details                                                                                                                                                       |
| 2301       | Please pass a valid representative's role. This is either Director, Shareholder, Beneficial Owner, Authorised Signatory, or Other. If Other, pass a "role_name" field.                                               |
| 2302       | You have indicated a role as "Other". Please provide a role_name                                                                                                                                                     |
| 2303       | Percentage value should be between 0 and 100                                                                                                                                                                         |
| 2304       | Invalid document selected                                                                                                                                                                                            |
| 2305       | Invalid country selected                                                                                                                                                                                             |
| 2306       | Document not available for the country                                                                                                                                                                               |
| 2307       | KYB application is not in initiated mode                                                                                                                                                                             |
| 2308       | KYB business not found                                                                                                                                                                                               |
| 2309       | KYB person not found                                                                                                                                                                                                 |
| 2310       | KYB person's document(s) not found                                                                                                                                                                                   |
| 2311       | A required field is missing, check our KYB API body parameters for required fields                                                                                                                                   |
| 2312       | Please provide business incorporation_no                                                                                                                                                                             |
| 2313       | Please provide document proof type                                                                                                                                                                                   |
| 2314       | User not found                                                                                                                                                                                                       |
| 2315       | account_id is a required field and must be a valid uuid                                                                                                                                                              |
| 2316       | Please pass a valid entity type for business. This can be: Sole Proprietorship, Partnership, Company or Other                                                                                                        |
| 2317       | Invalid business category                                                                                                                                                                                            |
| 2318       | Invalid year in business                                                                                                                                                                                             |
| 2319       | Please provide address line 1                                                                                                                                                                                        |
| 2320       | Please provide city                                                                                                                                                                                                  |
| 2321       | Please provide state                                                                                                                                                                                                 |
| 2322       | Please provide country                                                                                                                                                                                               |
| 2323       | Please provide annual turnover                                                                                                                                                                                       |
| 2324       | Ownership percent value must be greater than 25%                                                                                                                                                                     |
| 2325       | Please pass a valid owner's role. This is either Director, Shareholder, Beneficial Owner, Authorised Signatory, or Other. If Other, pass a "role_name" field.                                                        |
| 2326       | Please pass business object since the account type is business, refer to the Post KYB segment in our API docs                                                                                                        |
| 2327       | Please pass a valid document type. This is either Driver's License, National ID, Passport, or Other. If Other, pass a "name" field.                                                                                  |
| 2328       | Please pass a valid URL for download. Ensure that this is a downloadable file. We will download the file from this link and then upload internally. You can also use the Doc Upload API to generate an internal link |
| 2329       | Please pass a valid UUID for account_id. Refer to Post KYB body parameters                                                                                                                                           |
| 2330       | Unable to update since the KYB is already completed. please contact us at ops@tazapay.com if there is a change in the entity's details.                                                                              |