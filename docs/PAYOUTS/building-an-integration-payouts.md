---
title: Building an integration
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
# Building an Integration

This guides walks you through the process of integrating with Tazapay’s <a href= "https://docs.tazapay.com/reference/create-payout">payout API</a>

## Step 1: Initiate a payout request

Tazapay uses a `payout` object to represent your intent to initiate a payout. The payout object tracks state changes from when the payout is initiated to when the beneficiary receives the funds.

Create a payout on your server using Tazapay’s payout API with the following information: 

- Payout Amount and Currency - The amount you want to transfer to the beneficiary
- Beneficiary Details
  - Name
  - Type - `business` or `individual`
  - Bank Details - Account Number, Bank Name, <a href = "https://docs.tazapay.com/docs/bank-codes">Bank Codes</a>
- Type of Payout - Local Bank Transfer or Wire Transfer
- Holding Currency - The currency in your balance you want to fund the payout from
- Reason for Payout

### Sample Request cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payout \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "beneficiary_details": {
    "type": "individual",
    "destination_details": {
      "type": "bank",
      "bank": {
        "bank_codes": {
          "swift_code": "TMB001"
        },
        "firc_required": false,
        "account_number": "70202894209",
        "bank_name": "Tazapay Mock Bank",
        "country": "SG",
        "currency": "SGD"
      }
    },
    "name": "John Doe"
  },
  "amount": 10000,
  "currency": "SGD",
  "holding_currency": "USD",
  "purpose": "PYR020",
  "type": "local"
}
'
```

### Response

```json
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 10000,
    "beneficiary": "bnf_cokf3jio6qm3es8tpvgg",
    "beneficiary_details": {
      "address": null,
      "destination_details": {
        "bank": {
          "account_number": "70202894209",
          "bank_codes": {
            "swift_code": "TMB001"
          },
          "bank_name": "Tazapay Mock Bank",
          "branch_name": "",
          "country": "SG",
          "currency": "SGD",
          "firc_required": false,
          "purpose_code": ""
        },
        "type": "bank"
      },
      "email": "",
      "name": "John Doe",
      "phone": null,
      "type": "individual"
    },
    "charge_type": "",
    "created_at": "2024-04-24T11:49:34.840983Z",
    "currency": "SGD",
    "holding_currency": "USD",
    "holding_fx_transaction": {
      "exchange_rate": 0.7579,
      "final": {
        "amount": 7579,
        "currency": "USD"
      },
      "id": "fx_cokf3jn4ugprp413op80",
      "initial": {
        "amount": 10000,
        "currency": "SGD"
      },
      "object": "fx_transaction"
    },
    "id": "pot_cokf3jio6qm3es8tpvg0",
    "metadata": null,
    "object": "payout",
    "payout_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 10000,
        "currency": "SGD"
      },
      "id": "fx_cokf3jn4ugprp413op70",
      "initial": {
        "amount": 10000,
        "currency": "SGD"
      },
      "object": "fx_transaction"
    },
    "purpose": "PYR020",
    "statement_descriptor": "",
    "status": "processing",
    "status_description": "",
    "tracking_details": null,
    "type": "local"
  }
}
```

> `id` is the unique identifier for a payout. You can use this to track the payout.

## Alternatively, Creating a beneficiary and then initiating a payout

To align with your workflow, you can also choose to split Step 1 into two steps

- Step 1A: Creating a beneficiary using the [Create Beneficiary endpoint](https://docs.tazapay.com/reference/create-beneficiary)
- Step 1B: Initiating a payout using the [Create Payout endpoint](https://docs.tazapay.com/reference/create-payout)

### Step 1A: Creating a Beneficiary

Tazapay uses a `beneficiary` object to represent the receiver of funds of a payout. Pass the beneficiary name, type and their bank details to /v3/beneficiary endpoint.

### Sample Request cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/beneficiary \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "type": "individual",
  "destination_details": {
    "type": "bank",
    "bank": {
      "bank_codes": {
        "swift_code": "TMB001"
      },
      "firc_required": false,
      "account_number": "70202894209",
      "bank_name": "Tazapay Mock Bank",
      "country": "SG",
      "currency": "SGD"
    }
  },
  "name": "John Doe"
}
'
```

### Response

```json
{
  "status": "success",
  "message": "",
  "data": {
    "address": null,
    "created_at": "2024-04-25T11:21:30.114764Z",
    "destination": "bnk_col3pejgpv3vp26mh9u0",
    "destination_details": {
      "bank": {
        "account_number": "70202894209",
        "bank_codes": {
          "swift_code": "TMB001"
        },
        "bank_name": "Tazapay Mock Bank",
        "branch_name": "",
        "country": "SG",
        "currency": "SGD",
        "firc_required": false,
        "purpose_code": ""
      },
      "type": "bank"
    },
    "email": "",
    "id": "bnf_col3peio6qm3es8tqed0",
    "metadata": null,
    "name": "John Doe",
    "object": "beneficiary",
    "phone": null,
    "type": "individual"
  }
}
```

> `id` is the unique identifier for a beneficiary. Pass this in the Create Payout API to initiate a payout.

### Step 1B: Initiating a payout to an existing beneficiary

Create a payout on your server using Tazapay’s [payout API](https://docs.tazapay.com/reference/create-payout) with the following information: 

- Payout Amount and Currency - The amount you want to transfer to the beneficiary
- Beneficiary Details
- Type of Payout - Local Bank Transfer or Wire Transfer
- Holding Currency - The currency in your balance you want to fund the payout from
- Reason for Payout

### Sample cURL

```json
curl --request POST \
  --url https://service-sandbox.tazapay.com/v3/payout \
  --header 'accept: application/json' \
  --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
  --header 'content-type: application/json' \
  --data '{
  "beneficiary": "bnf_col3peio6qm3es8tqed0",
  "amount": 10000,
  "currency": "SGD",
  "holding_currency": "USD",
  "purpose": "PYR020"
}'
```

### Response

```json
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 10000,
    "beneficiary": "bnf_col3peio6qm3es8tqed0",
    "beneficiary_details": {
      "address": null,
      "destination_details": {
        "bank": {
          "account_number": "70202894209",
          "bank_codes": {
            "swift_code": "TMB001"
          },
          "bank_name": "Tazapay Mock Bank",
          "branch_name": "",
          "country": "SG",
          "currency": "SGD",
          "firc_required": false,
          "purpose_code": ""
        },
        "type": "bank"
      },
      "email": "",
      "name": "John Doe",
      "phone": null,
      "type": "individual"
    },
    "charge_type": "",
    "created_at": "2024-04-25T12:04:32.008478Z",
    "currency": "SGD",
    "holding_currency": "USD",
    "holding_fx_transaction": {
      "exchange_rate": 0.75805,
      "final": {
        "amount": 7580,
        "currency": "USD"
      },
      "id": "fx_col4djv4ugprp413p5mg",
      "initial": {
        "amount": 10000,
        "currency": "SGD"
      },
      "object": "fx_transaction"
    },
    "id": "pot_col4djqo6qm3es8tqev0",
    "metadata": null,
    "object": "payout",
    "payout_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 10000,
        "currency": "SGD"
      },
      "id": "fx_col4djv4ugprp413p5lg",
      "initial": {
        "amount": 10000,
        "currency": "SGD"
      },
      "object": "fx_transaction"
    },
    "purpose": "PYR020",
    "statement_descriptor": "",
    "status": "processing",
    "status_description": "",
    "tracking_details": null,
    "type": "local"
  }
}
```

> `id` is the unique identifier for a payout. You can use this to track the payout.

## Step 2: Handle payout events

A payout is in the `processing` state after it is successfully initiated. The payout can move to one of the following three states from the processing state:

1. **requires_action** - This is when the payout requires additional information. These additional information are typically required for reasons of regulatory compliance. Tazapay will reach out to your registered email address specifying the exact requirements and the next steps. After you have provided the necessary information, Tazapay will review and the payout can subsequently move to either `succeeded` or `failed`. 
2. **succeeded** - Depending on the beneficiary country, this is the state of the payout when the funds have reach the destination bank or will reach in a few business days.
3. **failed** - This is the state when the payout fails. Any funds deducted for the payout will be credited back to your account. Tazapay specifies the reason for the failure in the field `status_description`

> Tazapay delivers webhooks to your registered endpoint notifying you of any event of interest for the payout.