---
title: Release
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
| ERROR CODE | Meaning                                                                                                  |
|------------|----------------------------------------------------------------------------------------------------------|
| 2101       | Required field is missing from the request. Please check our release segment in our API docs             |
| 2102       | Value must be a valid URL                                                                                |
| 2103       |  txn_no is not found in our database                                                                     |
| 2104       | At least one document should be available                                                                |
| 2105       | Transaction/escrow is not in payment received mode. Please ensure that the transaction/escrow is funded. |
| 2106       | Unsupported verification document for release condition                                                  |
| 2109       | Funds for this transaction/escrow have already been released                                             |
| 2110       | Release request was already initiated for this transaction/escrow                                        |