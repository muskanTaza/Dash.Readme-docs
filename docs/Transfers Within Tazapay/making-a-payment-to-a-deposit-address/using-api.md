---
title: Using API
deprecated: false
hidden: false
metadata:
  robots: index
---
## Step 1: Initiate a payout request

Tazapay uses a `payout` object to represent your intent to initiate a payout to another accouont on Tazapay. The payout object tracks state changes from when the payout is initiated to when the beneficiary receives the funds.

Create a payout on your server using Tazapay’s payout API with the following information:

1. Payout Amount and Currency - The amount you want to transfer to the beneficiary
2. Beneficiary Details
   1. Type - `business` or `individual`
   2. Deposit Address - Deposit Address of the Beneficiary’s Tazapay Account
3. Type of Payout - `tazapay_account`
4. Holding Currency (optional) - The currency in your balance you want to fund the payout from
5. Reason for payout

### Sample Request cURL

```curl
curl --request POST \
  --url https://service.tazapay.com/v3/payout \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "purpose": "PYR005",
  "amount": 10000,
  "currency": "USD",
  "holding_currency": "USD",
  "type": "tazapay_account",
  "transaction_description": "E20",
  "beneficiary_details": {
    "type":"business",
    "destination_details":{
      "type":"tazapay_account",
      "tazapay_account":{
        "deposit_address":"hrknew10@tzp"
      }
    }
  }
}'
```

### Response

```json
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 10000,
    "balance_transaction": "",
    "beneficiary": "bnf_d21fu49kn8fb8eonham0",
    "beneficiary_details": {
      "address": null,
      "date_of_birth": "",
      "destination": "",
      "destination_details": {
        "tazapay_account": {
          "deposit_address": "hrknew10@tzp"
        },
        "type": "tazapay_account"
      },
      "documents": [],
      "email": "",
      "name": "",
      "national_identification_number": "",
      "party_classification": "",
      "phone": null,
      "registration_number": "",
      "tax_id": "",
      "type": "business"
    },
    "charge_type": "",
    "confirmation_documents": [],
    "created_at": "2025-07-25T04:27:19.705179Z",
    "currency": "USD",
    "documents": [],
    "holding_currency": "USD",
    "holding_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 10000,
        "currency": "USD"
      },
      "id": "fx_d21gf9vfi97uerbjg3i0",
      "initial": {
        "amount": 10000,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "id": "pot_d21gf9pkn8fb8eonk5h0",
    "local": {
      "fund_transfer_network": ""
    },
    "logistics_tracking_details": [],
    "metadata": null,
    "mt103": "",
    "object": "payout",
    "payout_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 10000,
        "currency": "USD"
      },
      "id": "fx_d21gf9vfi97uerbjg3ig",
      "initial": {
        "amount": 10000,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "purpose": "PYR005",
    "reference_id": "",
    "statement_descriptor": "",
    "status": "processing",
    "status_description": "",
    "tracking_details": null,
    "transaction_description": "E20",
    "type": "tazapay_account"
  }
}
```

> `id` is the unique identifier for the payout. You can use this to track the payout.

### Alternatively, creating a beneficiary and then creating a payout

To align with your workflow, you can choose to split Step 1 into two steps

* Step 1A: Creating a beneficiary using the [Create Beneficiary endpoint](https://docs.tazapay.com/reference/create-beneficiary)
* Step 1B: Initiating a payout using the [Create Payout endpoint](https://docs.tazapay.com/reference/create-payout)

### Step 1A: Create a Beneficiary

Tazapay uses a `beneficiary` object to represent the receiver of funds of a payout. Pass the beneficiary type and their deposit address to /v3/beneficiary endpoint.

### Sample Request cURL

```curl
curl --request POST \
  --url https://service.tazapay.com/v3/beneficiary \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "type":"business",
  "destination_details": {
    "type": "tazapay_account",
    "tazapay_account": {
       "deposit_address":"realitee@tzp"
    }
  }
}'
```

### Response

```json
{
  "status": "success",
  "message": "",
  "data": {
    "address": null,
    "created_at": "2025-07-25T03:50:41.787382Z",
    "date_of_birth": "",
    "destination": "tac_d21fu49u2ef2bt5bosq0",
    "destination_details": {
      "tazapay_account": {
        "deposit_address": "hrknew10@tzp"
      },
      "type": "tazapay_account"
    },
    "documents": [],
    "email": "",
    "id": "bnf_d21fu49kn8fb8eonham0",
    "metadata": null,
    "name": "",
    "national_identification_number": "",
    "object": "beneficiary",
    "party_classification": "",
    "phone": null,
    "registration_number": "",
    "tax_id": "",
    "type": "business"
  }
}
```

> `id` is the unique identifier for a beneficiary. Pass this in the Create Payout API to initiate a payout.

### Step 1B: Initiating a payout to an existing beneficiary

Create a payout on your server using Tazapay’s [payout API](https://docs.tazapay.com/reference/create-payout) with the following information:

* Payout Amount and Currency - The amount you want to transfer to the beneficiary
* Beneficiary ID
* Type of Payout - Tazapay Account
* Holding Currency (optional) - The currency in your balance you want to fund the payout from
* Reason for Payout

### Sample cURL

```curl
curl --request POST \
  --url https://service.tazapay.com/v3/payout \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "purpose": "PYR005",
  "amount": 10000,
  "currency": "USD",
  "holding_currency": "USD",
  "type": "tazapay_account",
  "transaction_description": "E20",
  "beneficiary": "bnf_d21fu49kn8fb8eonham0"
}'
```

### Response

```json
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 10000,
    "balance_transaction": "",
    "beneficiary": "bnf_d21fu49kn8fb8eonham0",
    "beneficiary_details": {
      "address": null,
      "date_of_birth": "",
      "destination": "tac_d21fu49u2ef2bt5bosq0",
      "destination_details": {
        "tazapay_account": {
          "deposit_address": "hrknew10@tzp"
        },
        "type": "tazapay_account"
      },
      "documents": [],
      "email": "",
      "name": "",
      "national_identification_number": "",
      "party_classification": "",
      "phone": null,
      "registration_number": "",
      "tax_id": "",
      "type": "business"
    },
    "charge_type": "",
    "confirmation_documents": [],
    "created_at": "2025-07-25T08:15:22.392694Z",
    "currency": "USD",
    "documents": [],
    "holding_currency": "USD",
    "holding_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 10000,
        "currency": "USD"
      },
      "id": "fx_d21jq6nfi97uerbjoh3g",
      "initial": {
        "amount": 10000,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "id": "pot_d21jq6hkn8fb8eoo0g70",
    "local": {
      "fund_transfer_network": ""
    },
    "logistics_tracking_details": [],
    "metadata": null,
    "mt103": "",
    "object": "payout",
    "payout_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 10000,
        "currency": "USD"
      },
      "id": "fx_d21jq6nfi97uerbjoh30",
      "initial": {
        "amount": 10000,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "purpose": "PYR005",
    "reference_id": "",
    "statement_descriptor": "",
    "status": "processing",
    "status_description": "",
    "tracking_details": null,
    "transaction_description": "E20",
    "type": "tazapay_account"
  }
}
```

> `id` is the unique identifier for a payout. You can use this to track the payout

## Step 2: Handle Payout events

A payout is in the `processing` state after it is successfully initiated. The payout can move to one of the following three states from the processing state:

1. **requires\_action** - This is when the payout requires additional information. These additional information are typically required for reasons of regulatory compliance. Tazapay will reach out to your registered email address specifying the exact requirements and the next steps. After you have provided the necessary information, Tazapay will review and the payout can subsequently move to either `succeeded` or `failed`.
2. **succeeded** - Depending on the beneficiary country, this is the state of the payout when the funds have reach the destination bank or will reach in a few business days.
3. **failed** - This is the state when the payout fails. Any funds deducted for the payout will be credited back to your account. Tazapay specifies the reason for the failure in the field `status_description`

> Tazapay delivers webhooks to your registered endpoint notifying you of any event of interest for the payout.