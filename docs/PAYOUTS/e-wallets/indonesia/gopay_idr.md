---
title: gopay_idr
excerpt: >-
  GoPay is a leading digital payment platform and the core financial service
  embedded within the Gojek super app (ride-hailing, food delivery, etc.). It's
  a must-have for paying for Gojek services, Tokopedia purchases (since they
  merged), and is widely used for online/offline transactions, bill payments,
  and transfers. Its strength is its deep integration with the Gojek ecosystem.
deprecated: false
hidden: true
metadata:
  robots: index
---
## **Key Features**

* Payouts are **instant (real-time)**
* **Minimum limits** – IDR 1108000
* **Maximum limits** – IDR 1994400000
* **Available 24/7**, including weekends and holidays

## **Building an Integration**

### **Step 1: Initiate a payout request**

Tazapay uses a **payout object** to represent your intent to initiate a payout. The payout object tracks state changes from initiation to the moment the beneficiary’s e-wallet account is credited.

Create a payout on your server using **Tazapay’s Payout API** with the following information:

* **Payout Amount** – The amount in local currency (IDR) to transfer
* **Beneficiary Details**
  * **Name**
  * **Type** – `business` or `individual`
* **Destination Details**
  * **Destination Type**: `local_payment_network`
  * **Mobile Wallet Type**: `gopay_idr`
  * **Deposit key type**: `phone`
  * **Deposit key**: `+62 XXXXXXXXXX`
* **Reason for Payout**
* **Transaction Description** – Additional description for the payout

## **Validations for Mobile Wallet Account Number**

Proper error handling must be implemented for cases where validations fail.

| Country            | Description                      | Validation                                                                                                                                      | Example                          |
| :----------------- | :------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------- |
| **ID – Indonesia** | E-Wallet account number (mobile) | Must be a valid Indonesian mobile number:`^(?:+62\|62\|0)8[1-9][0-9]{6,9}$` Starts with +62/62/0 followed by 8; total 9–12 digits after prefix. | `+628123456789` or `08123456789` |

<Callout icon="❌" theme="default">
  ### Invalid examples: +627123456789 (wrong for ID)
</Callout>

### Sample Request cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payout \
     --header 'accept: application/json' \
     --header 'authorization: Basic XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX' \
     --header 'content-type: application/json' \
     --data '
{
  "beneficiary_details": {
    "destination_details": {
      "type": "local_payment_network",
      "local_payment_network": {
        "type": "gopay_idr",
        "deposit_key_type": "phone",
        "deposit_key": "+628123456789"
      }
    },
    "name": "John Doe",
    "type": "individual"
  },
  "purpose": "PYR010",
  "amount": 1000,
  "currency": "IDR",
  "transaction_description": "Payout for 2 PCs"
}
```

### Response

```json
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 1000,
        "balance_transaction": "",
        "beneficiary": "bnf_d464knig6mi0so65mr9g",
        "beneficiary_details": {
            "address": null,
            "date_of_birth": "",
            "destination": "",
            "destination_details": {
                "local_payment_network": {
                    "currency": "IDR",
                    "deposit_key": "+628123456789",
                    "type": "gopay_idr"
                },
                "type": "local_payment_network"
            },
            "documents": [],
            "email": "",
            "is_doc_verification_required": false,
            "name": "John Doe",
            "name_local": "",
            "national_identification_number": "",
            "party_classification": "",
            "phone": null,
            "registration_number": "",
            "tax_id": "",
            "type": "individual",
            "verification_status": ""
        },
        "charge_type": "",
        "confirmation_documents": [],
        "created_at": "2025-11-06T07:12:31.089369Z",
        "currency": "IDR",
        "destination_fx_quote": "fx_d464knhbcijftsa0na40",
        "documents": [],
        "holding_currency": "IDR",
        "holding_fx_quote": "fx_d464knhbcijftsa0na3g",
        "holding_fx_transaction": {
            "exchange_rate": 1,
            "final": {
                "amount": 1000,
                "currency": "IDR"
            },
            "id": "fx_d464knhbcijftsa0na3g",
            "initial": {
                "amount": 1000,
                "currency": "IDR"
            },
            "object": "fx_transaction"
        },
        "id": "pot_d464knig6mi0so65mr90",
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
                "amount": 1000,
                "currency": "IDR"
            },
            "id": "fx_d464knhbcijftsa0na40",
            "initial": {
                "amount": 1000,
                "currency": "IDR"
            },
            "object": "fx_transaction"
        },
        "purpose": "PYR010",
        "quote": "",
        "reference_id": "",
        "statement_descriptor": "",
        "status": "processing",
        "status_description": "",
        "tracking_details": null,
        "transaction_description": "Payout for 2 PCs",
        "type": "local_payment_network"
    }
}
```
