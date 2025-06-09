---
title: Beneficiary Object
excerpt: >-
  The Tazapay Beneficiary Object represents the recipient of a payment or payout
  within the Tazapay platform. This object holds all relevant information about
  the beneficiary, including personal details, bank account information, and any
  other relevant metadata required for processing payments to them.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Parameters

```json
{
        "address": {
            "city": "Test",
            "country": "IN",
            "line1": "Test",
            "line2": "Test",
            "postal_code": "110017",
            "state": "Test"
        },
        "created_at": "2024-10-03T11:03:40.326462Z",
        "destination": "bnk_crv7k337eoqgk10pqp40",
        "destination_details": {
            "bank": {
                "account_number": "Test",
                "account_type": "",
                "bank_codes": {
                    "ifsc_code": "Test",
                    "swift_code": "Test"
                },
                "bank_name": "hdfc",
                "branch_name": "",
                "country": "IN",
                "currency": "INR",
                "firc_required": true,
                "purpose_code": "Test"
            },
            "type": "bank"
        },
        "documents": [],
        "email": "test@example.com",
        "id": "bnf_crv7k31h1l071n2fkbjg",
        "metadata": {},
        "name": "test",
        "object": "beneficiary",
        "phone": {
            "calling_code": "91",
            "number": "9231231231"
        },
        "tax_id": "",
        "type": "individual"
    }
```

### Beneficiary

| Parameter           | Sub Field | Type                   | Description                                                             |
| ------------------- | :-------- | ---------------------- | ----------------------------------------------------------------------- |
| id                  |           | string                 | The unique Tazapay identifier for the beneficiary.                      |
| object              |           | string                 | The type of object, which is "beneficiary".                             |
| name                |           | string                 | The name of the beneficiary.                                            |
| type                |           | enum                   | The type of the beneficiary [Values -  individual, business].           |
| address             |           | object                 | The address details of the beneficiary (see Address Table).             |
| email               |           | string                 | The email address of the beneficiary.                                   |
| phone               |           | object                 | The phone details of the beneficiary (see Phone Table).                 |
| tax_id              |           | string                 | The tax ID of the beneficiary.                                          |
| destination         |           | string                 | The Tazapay ID of the destination related to the payout.                |
| destination_details |           | object                 | The details of the destination for the payout.                          |
|                     | bank      | object                 | The bank details for the beneficiary's destination (see Bank Table).    |
|                     | type      | string                 | The type of destination (e.g., bank).                                   |
| documents           |           | array                  | List of documents related to the beneficiary.                           |
| created_at          |           | string (ISO timestamp) | The date and time when the beneficiary was created.                     |
| metadata            |           | json                   | Additional  key-value pairs associated with the beneficiary (optional). |

<br />

### Address

| Field       | Type   | Description                                          |
| ----------- | ------ | ---------------------------------------------------- |
| city        | string | The city of the beneficiary.                         |
| country     | string | The country of the beneficiary (e.g., IN for India). |
| line1       | string | The first line of the address.                       |
| line2       | string | The second line of the address (optional).           |
| postal_code | string | The postal code of the beneficiary's address.        |
| state       | string | The state of the beneficiary's address.              |

<br />

### Phone

| Field        | Type   | Description                                                     |
| ------------ | ------ | --------------------------------------------------------------- |
| calling_code | string | The international calling code for the customer's phone number. |
| number       | string | The phone number of the customer.                               |

<br />

### Bank

| Field                 | Type    | Description                                                                           |
| --------------------- | ------- | ------------------------------------------------------------------------------------- |
| account_number        | string  | The account number of the beneficiary's bank.                                         |
| account_type          | string  | The type of the bank account (optional).                                              |
| bank_codes.ifsc_code  | string  | The IFSC code of the beneficiary's bank.                                              |
| bank_codes.swift_code | string  | The SWIFT code of the beneficiary's bank.                                             |
| bank_name             | string  | The name of the beneficiary's bank.                                                   |
| branch_name           | string  | The branch name of the beneficiary's bank.                                            |
| country               | string  | The country where the beneficiary's bank is located.                                  |
| currency              | string  | The currency of the beneficiary's bank account (e.g., INR for Indian Rupee).          |
| firc_required         | boolean | Whether FIRC (Foreign Inward Remittance Certificate) is required for the transaction. |
| purpose_code          | string  | The purpose code for the transaction .                                                |