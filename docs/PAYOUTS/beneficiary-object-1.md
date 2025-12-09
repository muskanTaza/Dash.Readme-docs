---
title: Beneficiary Object
excerpt: ''
deprecated: false
hidden: true
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

| **Field**           | **type**  | **Description**                                                                                                                                               |
| ------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                  | string    | Unique ID for the beneficiary. Begins with 'bnf_'                                                                                                             |
| object              | string    | This is 'beneficiary' here                                                                                                                                    |
| created_at          | timestamp | Timestamp at which the beneficiary object is created. (ISO 8601 format - YYYY-MM-DDTHH:MM:SS±hh:mm)                                                           |
| beneficiary_details | json      | Details of the beneficiary. Refer here for beneficiary_details sub-fields                                                                                     |
| purpose             | enum      | The reason for payout. Refer \<[https://docs.tazapay.com/docs/reasons-for-payout](https://docs.tazapay.com/docs/reasons-for-payout)> for the possible values. |
| firc_required       | boolean   | Whether FIRC is required for the payout made for this beneficiary. Only applicable when the destination currency is INR.                                      |
| metadata                       | json      | Set of key-value pairs to attach to the payout                                                                                                                |
| is_doc_verification_required   | boolean   | Indicates if document verification is required for this beneficiary. Applicable for wallet beneficiaries.                                                     |
| status                         | enum      | Current status of the beneficiary. Possible values: active, inactive                                                                                          |
| verification_status            | enum      | Document verification status for wallet beneficiaries. Possible values: processing, requires_action, succeeded, failed                                       |

### **beneficiary_details**

| **Field**                        | **Sub-fields**                        | **type** | **Description**                                                                                                                                             |
| -------------------------------- | ------------------------------------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| type                             |                                       | enum     | Beneficiary type - business or individual                                                                                                                   |
| name                             |                                       | string   | Name of the beneficiary                                                                                                                                     |
| name_local                       |                                       | string   | Name of the beneficiary in local language/script (e.g., Chinese, Arabic characters)                                                                         |
| email                            |                                       | string   | Email of the beneficiary                                                                                                                                    |
| national_identification_number   |                                       | string   | National identification number of the individual beneficiary (e.g., SSN, National ID)                                                                       |
| party_classification             |                                       | enum     | Type of relationship between beneficiary and creator of beneficiary Possible values - self, third_party (Mandatory if destination_details.type is a wallet) |
| registration_number              |                                       | string   | Registration number of the business (Mandatory if destination_details.type is a wallet and type is business)                                                |
| date_of_birth                    |                                       | string   | Date of birth of individual, Format DD-MM-YYYY (Mandatory if destination_details.type is a wallet and type is individual                                    |
| address                          |                                       | json     | Address of the beneficiary                                                                                                                                  |
|                                  | line1                                 | string   | Address line 1                                                                                                                                              |
|                                  | line2                                 | string   | Address Line 2                                                                                                                                              |
|                                  | city                                  | string   | City                                                                                                                                                        |
|                                  | state                                 | string   | State                                                                                                                                                       |
|                                  | country                               | string   | ISO 3166-1 alpha-2 country code, in uppercase                                                                                                               |
|                                  | postal_code                           | string   | Postal Code                                                                                                                                                 |
| destination_details              |                                       |          |                                                                                                                                                             |
|                                  | type                                  | enum     | Type of the destination - bank, wallet or local_payment_network                                                                                             |
|                                  | bank / wallet / local_payment_network | json     | A JSON containing the destination details                                                                                                                   |

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

<Table>
  <thead>
    <tr>
      <th>
        **Field**
      </th>

      <th>
        **type**
      </th>

      <th>
        **Description**
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        deposit_address
      </td>

      <td>
        string
      </td>

      <td>
        Deposit Address
      </td>
    </tr>

    <tr>
      <td>
        type
      </td>

      <td>
        enum
      </td>

      <td>
        Blockchain of the wallet. Possible values include - Ethereum, Tron, Polygon, Solana
      </td>
    </tr>

    <tr>
      <td>
        currency
      </td>

      <td>
        string
      </td>

      <td>
        currency
      </td>
    </tr>

    <tr>
      <td>
        hosted
      </td>

      <td>
        enum
      </td>

      <td>
        Indicates whether the wallet is custodial (hosted) or non-custodial (unhosted).
        Possible values:  
        yes – The wallet is hosted by a Virtual Asset Service Provider (VASP) or exchange.  
        no – The wallet is non-custodial and controlled directly by the user (e.g., MetaMask, Ledger)  

        Mandatory if `party_classification` is 'self' and `destination_details.type` is 'wallet'.
      </td>
    </tr>

    <tr>
      <td>
        vasp_name
      </td>

      <td>
        string
      </td>

      <td>
        The registered name of the Virtual Asset Service Provider (VASP) or exchange that hosts or manages the wallet  
        Mandatory if `party_classification` is 'self', `destination_details.type` is 'wallet'  and `hosted` is 'yes'
      </td>
    </tr>

    <tr>
      <td>
        vasp_website
      </td>

      <td>
        string
      </td>

      <td>
        The official website URL of the VASP or exchange that manages the wallet. Used for VASP identification and due diligence under Travel Rule requirements  
        Mandatory if `party_classification` is 'self', `destination_details.type` is 'wallet'  and `hosted` is 'yes'
      </td>
    </tr>
  </tbody>
</Table>

### **local_payment_method**

| **Field**        | **type** | **Description**                                                                                                     |
| ---------------- | -------- | ------------------------------------------------------------------------------------------------------------------- |
| type             | string   | Type of the local_payment_network (example - pix_brl, upi_inr, promptpay_thb)                                       |
| deposit_key_type | enum     | Type of the deposit key. Conditionally Mandatory depending on the value of type                                     |
| deposit_key      | string   | Deposit key corresponding to the type of local payment network (Example, PIX key for PIX, UPI handle for UPI, etc.) |