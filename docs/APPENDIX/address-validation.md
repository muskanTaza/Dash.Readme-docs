---
title: Address Validation
excerpt: Ensure correct input from customers to increase conversion
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
It is mandatory to ensure the following validations for the billing address for customers in United States of America (US) and Canada (CA). This is applicable to:

1. /v3/checkout
2. /v3/escrow
3. /v3/payin
4. confirmPayment() (Javascript SDK)

## Validations

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Validation",
    "h-2": "Applicable for countries",
    "0-0": "billing_details.address.country",
    "0-1": "ISO 3166-1 alpha-2 country code (in uppercase)",
    "0-2": "US, CA",
    "1-0": "billing_details.address.line1",
    "1-1": "Min 4 characters, Only alphanumeric characters allowed",
    "1-2": "US, CA",
    "2-0": "billing_details.address.city",
    "2-1": "Only alphanumeric characters allowed",
    "2-2": "US, CA",
    "3-0": "billing_details.address.state",
    "3-1": "Only alphanumeric characters allowed",
    "3-2": "US, CA",
    "4-0": "billing_details.address.state",
    "4-1": "4-letter State code (ISO 3166-2), The state names and code can be accessed from <a href = \"https://www.iso.org/obp/ui/#iso:code:3166:US\" target=\"_blank\">this list for US</a> and <a href = \"https://en.wikipedia.org/wiki/ISO_3166-2:CA\" target=\"_blank\">this list for CA</a>",
    "4-2": "US, CA",
    "5-0": "billing_details.address.postal_code",
    "5-1": "For US, valid length is 5 or 9 and the format is NNNNN  \nFor CA, valid length is 6 and the format is ANA NAN (A-Alphabet, N- Number)",
    "5-2": "US, CA",
    "6-0": "billing_details.phone.calling_code",
    "6-1": "Only codes from <a href = \"https://en.wikipedia.org/wiki/List_of_country_calling_codes#Zones_3%E2%80%934:_Europe\" target = \"_blank\"> this list </a>",
    "6-2": "US, CA",
    "7-0": "billing_details.phone.number",
    "7-1": "Only numeric values allowed. Length allowed:  \nUSA: 10  \nCanada: 10",
    "7-2": "US, CA"
  },
  "cols": 3,
  "rows": 8,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]