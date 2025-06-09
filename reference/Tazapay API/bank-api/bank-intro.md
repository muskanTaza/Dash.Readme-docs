---
title: Introduction to Banks
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
This denotes the bank account associated with a user. Multiple bank accounts in multiple currencies can be added for a user. Separate requests need to be sent for adding separate bank accounts. You can set a preferred (primary) bank account for the user which Tazapay will disburse funds to.

```json Bank
{
    "bank_id":"2c339a9e-0035-4089-9f00-e494dda0ffc1",
    "account_id": "c1be8807-3975-45cf-aeba-fb17d0e536c9",
    "currency": "USD",
    "bank_name": "State Bank of Hind",
    "legal_name": "Radium Construction",
    "account_number": "98252414561758563",
    "is_primary_account":"true",
    "bank_codes": {
        "SWIFT Code": "BKIDFDD5102"
    },
  	"country_code":"+1",
    "contact_number":"7484961949",
    "address":"Connaught Place, New Delhi, India - 110015"
}
```

Only certain [Bank Codes](ref:bank-codes) can be passed for a currency-country pair.
