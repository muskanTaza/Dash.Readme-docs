---
title: API Types and Headers
excerpt: >-
  Learn more about the API types Tazapay has and the required headers for
  authentication
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Tazapay has 2 types of APIs: Hosted Page & Native

* Native  API: This is a pure back-end API interaction between your platform and Tazapay
* Hosted page API: When you make a call to a Tazapay hosted API, Tazapay will return a URL, to which the user can be redirected. Once the task is completed, the user will be directed back to your platform.

## API Headers

For each and every API call, you need to include the following in the header section:

| Key       | Value                                                    |
| --------- | -------------------------------------------------------- |
| accesskey | see: [Getting Started with Tazapay](doc:getting-started) |
| salt      | salt used in signature computation                       |
| signature | see: [Signature Calculation](doc:signature-calculation)  |
| timestamp | timestamp used in signature computation                  |
