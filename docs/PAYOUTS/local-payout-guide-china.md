---
title: 'Local Payout Guide: China'
excerpt: >-
  This guide details processing local payouts in China using  Tazapay’s [Create
  Payout API](https://docs.tazapay.com/reference/create-payout), covering
  essential requirements and parameters for successful transactions.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Key Requirements for China Payouts

Successful cross-border payments to China via Tazapay require specific parameters:

* **Beneficiary Name**: Must be provided in Chinese characters.
* **Beneficiary Bank Name**: Must be provided in Chinese characters.
* **National Identification Number**: Mandatory for individual beneficiaries.
* **Logistics Tracking Details**: Required information includes:
  * logistic_provider_name (mandatory)
  * logistic_provider_code (optional)
  * tracking_number (mandatory)
* **Invoice Upload**: Mandatory for all payouts.
* **Contract Upload**:  Required for specific payout purpose codes (refer to table below):

| **Code** | **Description**                                                                                         |
| -------- | ------------------------------------------------------------------------------------------------------- |
| PYR001   | Payment for Services                                                                                    |
| PYR002   | Payment for Software                                                                                    |
| PYR004   | Travel Services                                                                                         |
| PYR005   | Vendor / Contractor Payouts                                                                             |
| PYR007   | Investment in Shares                                                                                    |
| PYR008   | Purchase of Property                                                                                    |
| PYR009   | Repayment of Loans                                                                                      |
| PYR010   | Salary                                                                                                  |
| PYR011   | Payment of Property Rental                                                                              |
| PYR012   | Information Service Charges                                                                             |
| PYR013   | Advertising & Public relations-related expenses                                                         |
| PYR014   | Royalty fees, trademark fees, patent fees, and copyright fees                                           |
| PYR015   | Fees for brokers, front end fee, commitment fee, guarantee fee and custodian fee                        |
| PYR016   | Fees for advisors, technical assistance, and academic knowledge, including remuneration for specialists |
| PYR017   | Representative office expenses                                                                          |
| PYR018   | Tax Payment                                                                                             |
| PYR020   | Construction costs/expenses                                                                             |
| PYR021   | Insurance Premium                                                                                       |
| PYR023   | Insurance Claims Payment                                                                                |
| PYR024   | Family Maintenance                                                                                      |
| PYR025   | Education-related student expenses                                                                      |
| PYR026   | Medical Treatment                                                                                       |
| PYR027   | Donations                                                                                               |
| PYR028   | Mutual Fund Investment                                                                                  |
| PYR029   | Currency Exchange                                                                                       |
| PYR030   | User Withdrawal                                                                                         |
| PYR031   | Advance Payments for goods                                                                              |

# Sample Request Body

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payout \
     --header 'accept: application/json' \
     --header 'authorization: Basic XXXXXXxxxxxxxxXXXXX' \
     --header 'content-type: application/json' \
     --data '
{
  "beneficiary_details": {
    "destination_details": {
      "type": "bank",
      "bank": {
        "bank_codes": {
          "swift_code": "Testswift",
					"cnaps":"2749827482"
        },
        "account_number": "124353",
        "bank_name": "圳市腾",
        "country": "CN",
        "currency": "CNY"
      }
    },
    "name": "深圳市腾***有限公司",
    "type": "individual",
    "national_identification_number": "1234567890" 
  },
  "purpose": "PYR028",
  "logistics_tracking_details": {
    "logistics_provider_name": "CargoWave",
    "logistics_provider_code": "CGW",
    "tracking_number": "924U798274"
  },
  "amount": 10000,
  "currency": "CNY",
  "holding_currency": "USD",
  "documents": [
    {
      "type": "invoice",
      "url": "sample_url"
    },
    {
      "type": "contract",
      "url": "sample_url"
    }
  ]
}
'
```

# Sample Response Body

```json
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 10000,
        "balance_transaction": "btr_crv2q2hh1l071n2fjb70",
        "beneficiary": "bnf_crv2pf1h1l071n2fjapg",
        "beneficiary_details": {
            "address": null,
            "destination": "",
            "destination_details": {
                "bank": {
                    "account_number": "124353",
                    "account_type": "",
                  "bank_codes": {
											"swift_code": "Testswift",
											"cnaps":"2749827482"
                    },
                    "bank_name": "圳市腾",
                    "country": "CN",
                    "currency": "CNY",
                    "firc_required": false,
                    "purpose_code": ""
                },
                "type": "bank"
            },
            "chinese_id": "361723721",
            "logistics_tracking_details":{
              "logistics_provider":{
                "name":"Cargowave",
                "code":"CGW"
              },
              "tracking_number":"924U798274"},
            "email": "",
            "name": "深圳市腾***有限公司",
            "phone": null,
            "tax_id": "",
            "type": "individual"
        },
        "charge_type": "",
        "created_at": "2024-10-03T05:35:06.796479Z",
        "currency": "CNY",
        "documents":{
		         "type":"invoice",
		         "url":"sample_url"
		         }
		         {
		         "type":"contract",
		         "url":"sample_url"
		         }
        "holding_currency": "USD",
        "holding_fx_transaction": {
            "exchange_rate": 6.735621,
            "final": {
                "amount": 10000,
                "currency": "CNY"
            },
            "id": "fx_crv2q2gdj96g452dfo0g",
            "initial": {
                "amount": 1485,
                "currency": "USD"
            },
            "object": "fx_transaction"
        },
        "id": "pot_crv2q2hh1l071n2fjb6g",
        "metadata": null,
        "mt103": "",
        "object": "payout",
        "payout_fx_transaction": {
            "exchange_rate": 1,
            "final": {
                "amount": 10000,
                "currency": "CNY"
            },
            "id": "fx_crv2q2gdj96g452dfo00",
            "initial": {
                "amount": 10000,
                "currency": "CNY"
            },
            "object": "fx_transaction"
        },
        "purpose": "PYR007",
        "reference_id": "",
        "statement_descriptor": "",
        "status": "processing",
        "status_description": "",
        "tracking_details": null,
        "transaction_description": "",
        "type": "local"
    }
}
```

# Important Note

1. When creating a beneficiary via the Create Beneficiary API, ensure the `national_identification_number` is provided for individual beneficiaries.  Failure to do so will result in payout creation failure. You will need to add a new beneficiary with the required information.
2. Similarly. if the payout is created for an individual, we will need the company name to which they are associated in order to process. In addition, we will need them to share additional docs as well.
