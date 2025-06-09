---
title: Add Bank
excerpt: Add a bank account for a user
api:
  file: sandbox.json
  operationId: add-bank-api
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Only certain <a href="https://tazapay-api-developer.readme.io/reference/bank-codes" target="_blank">bank_codes</a> can be passed for a currency-country pair.

**Note**  
The fields -  _address_, _city_, _state_ and _zip_code_ are optional for most of the countries, but they are mandatory for some specific countries and their respective currencies. Please refer the list <a href = "https://docs.tazapay.com/reference/mandatory-bank-addresses" target="_blank">here</a> where the parameters - address, city, state and zip_code are Mandatory.