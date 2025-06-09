---
title: Refund
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
| ERROR CODE | Meaning                                                                                                                     |
|------------|-----------------------------------------------------------------------------------------------------------------------------|
| 2801       | Required field is missing from the request. Please check our refund segment in our API docs                                 |
| 2802       | The refund request could not be processed because the underlying transaction has not yet been funded or txn_no is not found |
| 2803       | The refund request could not be processed because the requested refund amount exceeds/lower the transaction amount.         |
| 2804       | The refund request could not be processed because the underlying transaction was already canceled                           |
| 2805       | The refund request could not be processed because a refund request already exists against the given transaction             |
| 2806       | Value must be a valid URL                                                                                                   |