---
title: Maximum length for the fields
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
The following fields have a maximum length of 250 characters

### POST /v1/user

first\_name, last\_name, contact\_number, business\_name

### POST /v1/checkout

first\_name, last\_name, contact\_number, business\_name, reference\_id

txn\_description *(has a maximum length of 1250 characters)*

### POST /v1/escrow

reference\_id

### POST /v2/kyb

address\_line\_1, address\_line\_2, city, state, zip\_code, mobile\_number
