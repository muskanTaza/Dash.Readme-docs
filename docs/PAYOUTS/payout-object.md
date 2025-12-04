---
title: Payout Object
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
# Payout Object

```json
{
  "id": "pot_coka64uof3laaslak1ag",
  "object": "payout",
  "created_at": "2024-04-24T06:13:39.274974Z",
  "amount": 908750,
  "currency": "USD",
  "beneficiary_details": {
    "address": {
      "line1": "Address line 1",
      "line2": "Address line 2",
      "city": "city",
      "state": "state",
      "country": "SG",
      "postal_code": "10090"
    },
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
        "iban":"",
        "purpose_code": ""
      },
      "type": "bank"
    },
    "email": "support@tazapay.com",
    "name": "John Doe",
    "phone": null,
    "type": "business"
  },
  "beneficiary": "bnf_coka5m22t0herlgcuvjg",
  "purpose": "PYR002",
  "statement_descriptor": "Invoice 20080",
  "status": "processing",
  "status_description": "",
  "tracking_details": {
    "reference": {
      "type": "UTR",
      "number": "afnafon-24i0-abfoan"
    }
  },
  "type": "local",
  "charge_type": "",
  "holding_currency": "EUR",
  "payout_fx_transaction": {
    "exchange_rate": 82.397282,
    "final": {
      "amount": 74878529,
      "currency": "INR"
    },
    "id": "fx_coka64uof3laaslak1ag",
    "initial": {
      "amount": 908750,
      "currency": "USD"
    },
    "object": "fxt_transaction"
  },
  "firc_required": false,
  "metadata": {
    "key1": "value1",
    "key2": "value2"
  },
  "mt103": "Test MT103",
  "local": {
    "fund_transfer_network": ""
  },
  "logistics_tracking_details": [],
  "confirmation_documents": [],
  "destination_fx_quote": "fx_coka64uof3laaslak1ah",
  "quote": "",
  "available_balance": 5000000,
  "is_balance_sufficient": true
}
```

| Field                       | type      | Description                                                                                                                                                  |
| --------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| id                          | string    | Unique ID for the payout. Begins with 'pot\_'                                                                                                                |
| object                      | string    | This is 'payout' here                                                                                                                                        |
| created_at                  | timestamp | Timestamp at which the payout object is created. (ISO 8601 format - YYYY-MM-DDTHH:MM:SS±hh:mm)                                                               |
| amount                      | integer   | Amount for the payout in cents in the payout currency. Refer \<https://docs.tazapay.com/docs/decimal-currencies> for decimal handling for various currencies. |
| currency                    | string    | ISO 4217 standard, in uppercase. This is the payout currency. The amount will be in the payout currency                                                      |
| beneficiary_details         | json      | Details of the beneficiary. Refer here for beneficiary_details sub-fields                                                                                    |
| beneficiary                 | string    | Unique ID representing the beneficiary for the payout                                                                                                        |
| purpose                     | enum      | The reason for payout. Refer \<https://docs.tazapay.com/docs/reasons-for-payout> for the possible values.                                                     |
| statement_descriptor        | string    | Brief text descriptor that will appear on the beneficiary's bank statement to identify the transaction                                                       |
| status                      | enum      | Status of the payout. Refer \<https://docs.tazapay.com/docs/payout-1> for possible values.                                                                    |
| status_description          | string    | This provides additional description about the status, if applicable                                                                                         |
| tracking_details            | json      | This helps track the payout                                                                                                                                  |
| type                        | enum      | Type of payout - local, swift, wallet, local_payment_network, or tazapay_account                                                                             |
| charge_type                 | enum      | Applicable only for wire transfers, shared or ours                                                                                                           |
| holding_currency            | string    | ISO 4217 standard, in uppercase. This represents the currency whose balance will be used to fund the payout                                                  |
| payout_fx_transaction       | json      | FX transaction representing the currency conversion from the payout currency to the destination (beneficiary) currency                                       |
| firc_required               | boolean   | Whether FIRC is required for the payout. Only applicable when the destination currency is INR.                                                               |
| metadata                    | json      | Set of key-value pairs to attach to the payout                                                                                                               |
| mt103                       | string    | MT103 for the payout                                                                                                                                         |
| local                       | json      | Local payout configuration containing fund transfer network details. See local section below.                                                                |
| logistics_tracking_details  | array     | Array of logistics tracking information for goods shipments. Each object contains tracking_number, logistics_provider, and description.                      |
| confirmation_documents      | array     | Array of confirmation documents (MT103, MT199, FIRC, etc.). Each object contains key (document type), type (mime type), and value (document content/URL).  |
| destination_fx_quote        | string    | ID of the FX quote object used for currency conversion at the destination. Begins with 'fx\_'                                                                |
| quote                       | string    | ID of the payout quote used to lock exchange rates for this payout. Begins with 'poq\_'                                                                      |
| available_balance           | integer   | Available balance in the holding currency account after this payout is processed                                                                             |
| is_balance_sufficient       | boolean   | Indicates whether the account has sufficient balance to process this payout                                                                                  |

### beneficiary_details

| Field               | Sub-fields           | type   | Description                                     |
| ------------------- | -------------------- | ------ | ----------------------------------------------- |
| type                |                      | enum   | Beneficiary type - business or individual       |
| name                |                      | string | Name of the beneficiary                         |
| email               |                      | string | Email of the beneficiary                        |
| address             |                      | json   | Address of the beneficiary                      |
|                     | line1                | string | Address line 1                                  |
|                     | line2                | string | Address Line 2                                  |
|                     | city                 | string | City                                            |
|                     | state                | string | State                                           |
|                     | country              | string | ISO 3166-1 alpha-2 country code, in uppercase   |
|                     | postal_code          | string | Postal Code                                     |
| destination_details |                      |        |                                                 |
|                     | type                 | enum   | Type of the destination - bank or payout_wallet |
|                     | bank / payout_wallet | json   | A JSON containing the destination details       |

### bank

| Field          | type   | Description                                                                         |
| -------------- | ------ | ----------------------------------------------------------------------------------- |
| bank_name      | string | Name of the bank                                                                    |
| account_number | string | Account Number                                                                      |
| iban           | string | IBAN                                                                                |
| country        | string | Two-letter country code (ISO 3166-1 alpha-2)                                        |
| currency       | string | Three-letter ISO currency code                                                      |
| branch_name    | string | Name of the branch                                                                  |
| purpose_code   | string | Purpose Code in the Indian context                                                  |
| bank_codes     | json   | Bank Codes (For example - swift_code, ifsc_code). Refer here for the list of codes. |

### payout_wallet

| Field           | type   | Description                                      |
| --------------- | ------ | ------------------------------------------------ |
| deposit_address | string | Deposit Address                                  |
| type            | enum   | Name of the wallet (Type of the deposit address) |
| currency        | string | currency                                         |

### tracking_details

| Field     | Sub-field | type   | Description                    |
| --------- | --------- | ------ | ------------------------------ |
| reference |           | json   | Reference Details for tracking |
|           | type      | enum   | Type of the reference          |
|           | number    | string | Reference Number               |

### payout_fx_transaction

| Field         | Sub-field | type    | Description                                                                                                                                        |
| ------------- | --------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| id            |           | string  | Unique ID for the FX conversion                                                                                                                    |
| object        |           | string  | fx_transaction here                                                                                                                                |
| initial       |           | json    | The initial currency and amount                                                                                                                    |
|               | amount    | integer | Amount in cents in the payout currency. Refer \<https://docs.tazapay.com/docs/decimal-currencies> for decimal handling for various currencies.      |
|               | currency  | string  | ISO 4217 standard, in uppercase.                                                                                                                   |
| exchange_rate |           | float   | Exchange Rate to convert initial currency to the final currency                                                                                    |
| initial       |           | json    | The final currency and amount after conversion                                                                                                     |
|               | amount    | integer | Amount in cents in the destination currency. Refer \<https://docs.tazapay.com/docs/decimal-currencies> for decimal handling for various currencies. |
|               | currency  | string  | ISO 4217 standard, in uppercase.                                                                                                                   |

### local

| Field                 | type   | Description                                                                                                 |
| --------------------- | ------ | ----------------------------------------------------------------------------------------------------------- |
| fund_transfer_network | string | The fund transfer network used for local payouts (e.g., "chats" for Hong Kong, "fps" for Faster Payment System, "sepa" for European payouts) |

### logistics_tracking_details

| Field              | type   | Description                                                     |
| ------------------ | ------ | --------------------------------------------------------------- |
| tracking_number    | string | The tracking number for the shipment                            |
| logistics_provider | string | Name of the logistics/shipping provider (e.g., UPS, DHL, FedEx) |
| description        | string | Additional description about the shipment                       |

### confirmation_documents

| Field | type   | Description                                                                                     |
| ----- | ------ | ----------------------------------------------------------------------------------------------- |
| key   | string | Type of document (e.g., "mt103", "mt199", "firc", "other")                                     |
| type  | string | MIME type of the document (e.g., "application/pdf")                                             |
| value | string | Document content (base64 encoded) or URL to access the document                                 |