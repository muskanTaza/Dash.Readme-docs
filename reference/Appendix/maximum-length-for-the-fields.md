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

first_name, last_name, contact_number, business_name

### POST /v1/checkout

first_name, last_name, contact_number, business_name, reference_id

txn\_description _(has a maximum length of 1250 characters)_

### POST /v1/escrow

reference_id

### POST /v2/kyb

address_line_1, address_line_2, city, state, zip_code, mobile_number