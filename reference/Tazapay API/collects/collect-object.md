---
title: Collect Object
excerpt: >-
  Collects represent incoming payments to your global collection accounts. A
  collect is created whenever there is a credit in the collection accounts.
deprecated: false
hidden: true
icon: far fa-envelope-open-dollar
metadata:
  robots: index
---
## Object Structure

```json
{
  "amount": 12829,
  "balance_transaction": "btr_u7ftrgipu69og2qj1j1pg",
  "created_at": "2027-08-15T03:43:46.980214Z",
  "currency": "SGD",
  "destination": "cva_d2dgk0ka772psfuj1he0",
  "destination_details": {
          "type": "virtual_account",
          "virtual_account": {
              "account_holder_name": "OM Grand Limited",
              "account_number": "0109866363",
              "bank_address": {
                  "address_line_1": "",
                  "address_line_2": "",
                  "city": "",
                  "country": "Singapore",
                  "postal_code": "",
                  "state": ""
                },
              "bank_branch": "8 MARINA BOULEVARD, 27-01, MARINA BAY FINANCIAL CENTRE",
              "bank_codes": {
                  "swift_code": "SLSGO2XXX"
                },
              "bank_name": "STANDARD BANK LIMITED",
              "currencies": [
                  "SGD"
                ],
              "iban": "",
              "id": "cva_d2dgk0552psfuj1he0",
              "object": "virtual_account"
            }
        },
  "holding_currency": "SGD",
  "id": "col_d2fapsh76og2qj0ej5g",
  "metadata": {},
  "object": "collect",
  "on_behalf_of": "",
  "payer_details": {
          "additional_information": "CM Payment for Order 56",
          "name": "CMC COMPANY",
          "payer_bank": {
              "account_number": "1112019837840",
              "address": null,
              "bank_codes": {
                  "swift_code": "AJUM7CHBKXXX"
                },
              "name": "C Bank"
            },
          "reference_id": ""
        },
  "status": "succeeded",
  "tracking_details": null,
  "type": "wire_transfer"
}
}
```

<br />

## Object Parameters

<br />
