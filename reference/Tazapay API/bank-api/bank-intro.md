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
[block:code]
{
  "codes": [
    {
      "code": "{\n    \"bank_id\":\"2c339a9e-0035-4089-9f00-e494dda0ffc1\",\n    \"account_id\": \"c1be8807-3975-45cf-aeba-fb17d0e536c9\",\n    \"currency\": \"USD\",\n    \"bank_name\": \"State Bank of Hind\",\n    \"legal_name\": \"Radium Construction\",\n    \"account_number\": \"98252414561758563\",\n    \"is_primary_account\":\"true\",\n    \"bank_codes\": {\n        \"SWIFT Code\": \"BKIDFDD5102\"\n    },\n  \t\"country_code\":\"+1\",\n    \"contact_number\":\"7484961949\",\n    \"address\":\"Connaught Place, New Delhi, India - 110015\"\n}",
      "language": "json",
      "name": "Bank"
    }
  ]
}
[/block]
Only certain [Bank Codes](ref:bank-codes) can be passed for a currency-country pair.