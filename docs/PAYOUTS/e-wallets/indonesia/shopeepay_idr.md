---
title: shopeepay_idr
excerpt: >-
  ShopeePay is the mobile wallet arm of the Shopee e-commerce platform. It is
  crucial for seamless, rewarded payments within the Shopee app, offering
  generous incentives like cashback and free shipping vouchers. It is rapidly
  expanding its offline presence using QRIS to become an everyday payment option
  outside of the marketplace.
deprecated: false
hidden: true
metadata:
  robots: index
---
## **Key Features**

* Payouts are **instant (real-time)**
* **Minimum limits** – IDR 1
* **Maximum limits** – IDR 20,000,000
* **Available 24/7**, including weekends and holidays

## **Building an Integration**

### **Step 1: Initiate a payout request**

Tazapay uses a **payout object** to represent your intent to initiate a payout. The payout object tracks state changes from initiation to the moment the beneficiary’s wallet account is credited.

Create a payout on your server using **Tazapay’s Payout API** with the following information:

* **Payout Amount** – The amount in local currency (IDR) to transfer
* **Beneficiary Details**
  * **Name**
  * **Type** – `business` or `individual`
* **Destination Details**
  * **Destination Type**: `local_payment_network`
  * **Mobile Wallet Type**: `shopeepay_idr`
  * **Deposit key type**: `phone`
  * **Deposit key**: `+62 XXXXXXXXXX`
* **Reason for Payout**
* **Transaction Description** – Additional description for the payout

## **Validations for Mobile Wallet Account Number**

Proper error handling must be implemented for cases where validations fail.

| **Country**        | **Description**                       | **Validation**                                    | **Example** |                                                                                          |                                  |
| :----------------- | :------------------------------------ | :------------------------------------------------ | :---------- | :--------------------------------------------------------------------------------------- | :------------------------------- |
| **ID – Indonesia** | Mobile Wallet account number (mobile) | Must be a valid Indonesian mobile number:`^(?:+62 | 62          | 0)8[1-9][0-9]{6,9}$` Starts with +62/62/0 followed by 8; total 9–12 digits after prefix. | `+628123456789` or `08123456789` |

<Callout icon="❌" theme="default">
  ### **Invalid examples: +627123456789 (wrong for ID)**
</Callout>

### **Sample Request cURL**

JSON

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
        "type": "shopeepay_idr",
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

### **Response**

JSON

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
                    "type": "shopeepay_idr"
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

## **Alternatively: Creating a beneficiary and then initiating a payout**

You can also choose to split Step 1 into two steps:

* **Step 1A:** Create a **Beneficiary** using `POST /v3/beneficiary`
* **Step 1B:** Initiate a **Payout** using `POST /v3/payout`

### **Sample Request – Create Beneficiary**

```bash
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/beneficiary \
     --header 'accept: application/json' \
     --header 'authorization: Basic XXXXXXXXXXXXXXXXXXXXXXXXXXXX' \
     --header 'content-type: application/json' \
     --data '
{
  "type": "business",
  "destination_details": {
    "type": "local_payment_network",
    "local_payment_network": {
      "type": "gopay_idr",
      "deposit_key_type": "phone",
      "deposit_key": "+628123456789"
    }
  },
  "name": "John Doe"
}
'
```

***

### **Response – Create Beneficiary**

```json
{
    "status": "success",
    "message": "",
    "data": {
        "address": null,
        "created_at": "2025-11-10T06:27:26.496576Z",
        "date_of_birth": "",
        "destination": "lpn_d48objl7ovv4hchl4cq0",
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
        "id": "bnf_d48objig6mi0so6o0iag",
        "is_doc_verification_required": false,
        "metadata": null,
        "name": "John Doe",
        "name_local": "",
        "national_identification_number": "",
        "object": "beneficiary",
        "party_classification": "",
        "phone": null,
        "registration_number": "",
        "tax_id": "",
        "type": "business",
        "verification_status": "succeeded"
    }
}
```

> id is the unique identifier for a beneficiary. Pass this in the Create Payout API to initiate a payout.

***

### **Step 1B: Initiating a payout to the existing beneficiary**

```bash
curl --request POST \
  --url https://service.tazapay.com/v3/payout \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
    "beneficiary": "bnf_d48objig6mi0so6o0iag",
    "amount": 5000,
    "currency": "IDR",
    "purpose": "PYR030",
    "type": "local_payment_network",
    "reference_id": "ref_88022",
    "transaction_description": "Customer Wallet Withdrawal"
  }'

```

***

### **Response – Payout**

```json
{
  "status": "success",
  "message": "",
  "data": {
    "id": "pot_cu99sv5i92bkana1hi8g",
    "beneficiary": "bnf_d48objig6mi0so6o0iag",
    "amount": 5000,
    "currency": "IDR",
    "status": "processing",
    "transaction_description": "Customer Wallet Withdrawal",
    "created_at": "2025-05-16T10:20:40.716Z"
  }
}

```

> id is the unique identifier for a payout. You can use this to track the payout.

***

## **Handle Payout Events**

A payout is in the **processing** state after it is successfully initiated.

The payout can move to one of the following states from **processing**:

* **requires_action** – Additional information required (e.g., regulatory or KYC).
* **succeeded** – Beneficiary’s wallet credited successfully.
* **failed** – Payout failed. Any funds deducted are credited back to your account.
  * The failure reason is provided in the field `status_description`.

Tazapay delivers **webhooks** to your registered endpoint notifying you of any payout-related event.

***

> 📘 Note:
>
> The payout will fail if the **account_number** (mobile) does not match the wallet account details registered with the provider.

***

## **Simulating Payouts on Sandbox**

* All payouts created on **sandbox** automatically move to `processing` → `succeeded`.
* Payouts created with **amount = 200000** will move to **failed**.
