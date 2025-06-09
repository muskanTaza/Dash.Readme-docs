---
title: Collect
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
```Text JSON
{
    "metadata": {},
    "created_at": "2024-02-07T11:06:00.421853Z",
    "payer_details": {
        "name": "Hrithik Agarwal",
        "payer_bank": {
            "account_number": "9876542321",
            "name": "State Bank of Mars",
            "address": {
                "line1": "Address Line 1",
                "line2": "Address Line 2",
                "city": "City",
                "state": "state",
                "country": "country",
                "postal_code": "postal code"
            },
            "bank_codes": {
                "swift_code": "SBM001"
            }
        },
        "reference_id": "reffffff",
        "additional_information": "Additional Information for the transaction"
    },
    "id": "col_cn1m8651ed8dn2517esg",
    "object": "collect",
    "currency": "USD",
    "status": "succeeded",
    "type": "wire_transfer",
    "destination": "cca_uafanfianknon792nfak",
    "amount": 100000
}
```

| Field         | Sub-fields             | type      | Description                                                                                                                                                  |
| :------------ | :--------------------- | :-------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id            |                        | string    | Unique ID of the collect. Starts with `col_`                                                                                                                 |
| object        |                        | string    | This is `collect` here                                                                                                                                        |
| amount        |                        | integer   | Amount of the collect in the lowest denomination. Learn more about decimal currencies <a href="https://docs.tazapay.com/docs/decimal-currencies">here</a>. |
| currency      |                        | string    | Currency of the collect                                                                                                                                      |
| status        |                        | enum      | Status of the collect. Can be `succeeded`, `on_hold` or `failed`                                                                                              |
| metadata      |                        | json      | Set of key-value pairs attached to the collect object                                                                                                        |
| created_at    |                        | timestamp | Timestamp at which the collect object is created                                                                                                             |
| payer_details |                        | json      | Details of the payer                                                                                                                                         |
|               | name                   | string    | Payer Name                                                                                                                                                   |
|               | additional_information | string    | Additional information for the collect                                                                                                                       |
|               | payer_bank             | json      | Payer Bank                                                                                                                                                   |
|               | reference              | string    | Reference (if any) entered by the payer                                                                                                                      |
| type          |                        | enum      | Type of the collect (wire\_transfer, local\_bank\_transfer\_\*\*\*)                                                                                          |
| destination   |                        | string    | The global collection account in which the amount is received                                                                                                |

### payer_details.payer_bank

| Field          | Sub-Fields  | type   | Description                                                                           |
| :------------- | :---------- | :----- | :------------------------------------------------------------------------------------ |
| account_number |             | string | Account Number of the payer                                                           |
| name           |             | string | Payer Bank Name                                                                       |
| address        |             | json   | Payer Bank Address                                                                    |
|                | line1       | string | Address line 1                                                                        |
|                | line2       | string | Address line 2                                                                        |
|                | city        | string | City                                                                                  |
|                | state       | string | State                                                                                 |
|                | country     | string | Country (ISO 3166 standard alpha-2 code. eg: SG, IN, US, etc.)                        |
|                | postal_code | string | Postal code or ZIP                                                                    |
| bank_codes     |             | enum   | Can be `swift_code`, `bic`, `ifs_code`, `aba`, `sort_code`, `branch_code`, `bsb_code` |
```