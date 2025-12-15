---
title: Beneficiary Object
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Beneficiary Object

```json
{
    "id": "bnf_d05lmjp8ddevmnvfp3a0",
    "object": "beneficiary",
    "created_at": "2025-04-25T09:52:15.739077Z",
    "beneficiary_details": {
        "address": {
            "line1": "Address line 1",
            "line2": "Address line 2",
            "city": "city",
            "state": "state",
            "country": "SG",
            "postal_code": "10090"
        },
        "date_of_birth": "15-02-1985",
        "nationality": "SG",
        "destination": "bnk_d05lmjuq59csbboqt9d0",
        "destination_details": {
            "bank": {
                "account_number": "90980778",
                "bank_codes": {
                    "ifsc_code": "IFX001"
                },
                "bank_name": "Bank of India",
                "branch_name": "",
                "country": "IN",
                "currency": "INR",
                "iban": "",
                "firc_required": true,
                "purpose_code": ""
            },
            "type": "bank"
        },
        "email": "support@tazapay.com",
        "name": "John Doe",
        "phone": null,
        "type": "business"
    }
    ,
    "documents": [],
    "metadata": null
}
```

| **Field**           | **type**  | **Description**                                                                                                          |
| ------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------ |
| id                  | string    | Unique ID for the beneficiary. Begins with 'bnf\_'                                                                       |
| object              | string    | This is 'beneficiary' here                                                                                               |
| created_at          | timestamp | Timestamp at which the beneficiary object is created. (ISO 8601 format - YYYY-MM-DDTHH:MM:SS±hh:mm)                      |
| beneficiary_details | json      | Details of the beneficiary. Refer here for beneficiary_details sub-fields                                                |
| purpose             | enum      | The reason for payout. Refer &lt;https://docs.tazapay.com/docs/reasons-for-payout&gt; for the possible values.           |
| firc_required       | boolean   | Whether FIRC is required for the payout made for this beneficiary. Only applicable when the destination currency is INR. |
| metadata            | json      | Set of key-value pairs to attach to the payout                                                                           |

### **beneficiary_details**

| **Field**           | **Sub-fields**                        | **type** | **Description**                                                 |
| ------------------- | ------------------------------------- | -------- | --------------------------------------------------------------- |
| type                |                                       | enum     | Beneficiary type - business or individual                       |
| name                |                                       | string   | Name of the beneficiary                                         |
| email               |                                       | string   | Email of the beneficiary                                        |
| date_of_birth       |                                       | string   | Date of birth of the beneficiary (Format DD-MM-YYYY)            |
| nationality         |                                       | string   | ISO 3166-1 alpha-2 country code representing beneficiary's nationality (e.g., US, GB, IN, FR) |
| address             |                                       | json     | Address of the beneficiary                                      |
|                     | line1                                 | string   | Address line 1                                                  |
|                     | line2                                 | string   | Address Line 2                                                  |
|                     | city                                  | string   | City                                                            |
|                     | state                                 | string   | State                                                           |
|                     | country                               | string   | ISO 3166-1 alpha-2 country code, in uppercase                   |
|                     | postal_code                           | string   | Postal Code                                                     |
| destination_details |                                       |          |                                                                 |
|                     | type                                  | enum     | Type of the destination - bank, wallet or local_payment_network |
|                     | bank / waleet / local_payment_network | json     | A JSON containing the destination details                       |

### **bank**

| **Field**      | **type** | **Description**                                                                     |
| -------------- | -------- | ----------------------------------------------------------------------------------- |
| bank_name      | string   | Name of the bank                                                                    |
| account_number | string   | Account Number                                                                      |
| iban           | string   | IBAN                                                                                |
| country        | string   | Two-letter country code (ISO 3166-1 alpha-2)                                        |
| currency       | string   | Three-letter ISO currency code                                                      |
| branch_name    | string   | Name of the branch                                                                  |
| purpose_code   | string   | Purpose Code in the Indian context                                                  |
| bank_codes     | json     | Bank Codes (For example - swift_code, ifsc_code). Refer here for the list of codes. |

### **wallet**

| **Field**       | **type** | **Description**                                  |
| --------------- | -------- | ------------------------------------------------ |
| deposit_address | string   | Deposit Address                                  |
| type            | enum     | Name of the wallet (Type of the deposit address) |
| currency        | string   | currency                                         |

### **local_payment_method**

| **Field**        | **type** | **Description**                                                                                                     |
| ---------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| type             | string   | Type of the local_payment_network (example - pix_brl, upi_inr, promptpay_thb)                                       |
| deposit_key_type | enum     | Type of the deposit key. Conditionally Mandatory depending on the value of type                                     |
| deposit_key      | string   | Deposit key corresponding to the type of local payment network (Example, PIX key for PIX, UPI handle for UPI, etc.) |