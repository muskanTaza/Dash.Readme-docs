---
title: Generic
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
| ERROR CODE | Meaning                                                                                                                                                                                                       |
|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1000       | Failure on decoding the json request. The format for Json is not correct, please check the syntax & case sensitivity for any missing brackets, semi-colons, capitalizations, or any other formatting errors.  |
| 1001       | Database operations failure. One of the queries for this operation has failed                                                                                                                                 |
| 1002       | Something went wrong with this API                                                                                                                                                                            |
| 1003       | "Invalid parameter in the URL path. Example : /xyz/my_value/abc Here my_value is invalid"                                                                                                                     |
| 1004       | "Invalid parameter in the URL path. Example : /xyz/&sort=my_value/abc Here my_value is invalid"                                                                                                               |
| 1005       | The resource you are trying to retrieve is not present. This error code happens when trying to Get or Read a data point (eg: transaction number, user, KYB, etc) that does not exist.                         |