---
title: Create Payout
excerpt: This lets you initiate a payout.
api:
  file: sandbox.json
  operationId: create-payout
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: ''
  description: ''
  robots: index
---
# Create Payout

This lets you initiate a payout.

## Request Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `amount` | integer | Yes | Amount in cents. For decimal handling, refer to [the currency guide](https://docs.tazapay.com/docs/decimal-currencies) |
| `currency` | string | Yes | ISO 4217 standard payout currency (uppercase) |
| `purpose` | string | Yes | Reason for payout. See [detailed list](https://docs.tazapay.com/docs/reasons-for-payout) |
| `transaction_description` | string | Yes | Additional details for the payout |
| `beneficiary_details` | object | No | Beneficiary details (required if no existing beneficiary) |
| `beneficiary` | string | No | ID of existing payout beneficiary |
| `holding_currency` | string | No | Your balance currency to fund the payout |
| `type` | string | No | Type of payout: `local`, `swift`, or `wallet` |
| `charge_type` | string | No | For wire transfers: `shared` or `ours` |
| `reference_id` | string | No | Your unique reference ID |
| `metadata` | object | No | Key-value pairs to attach to the payout |

### Beneficiary Details Object

When creating a new beneficiary, include:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `name` | string | Yes | Beneficiary name |
| `type` | string | Yes | `business` or `individual` |
| `destination_details` | object | Yes | Bank, wallet, or payment network details |
| `email` | string | No | Beneficiary email address |
| `address` | object | No | Beneficiary address (required for wallets) |
| `phone` | object | No | Phone number with calling code |
| `tax_id` | string | No | Tax ID (required for Brazil payouts) |

## Example Request

```json
{
  "amount": 100000,
  "currency": "USD", 
  "holding_currency": "EUR",
  "type": "swift",
  "charge_type": "ours",
  "purpose": "PYR001",
  "reference_id": "Test_Ref",
  "transaction_description": "Test Payout",
  "statement_descriptor": "Test",
  "beneficiary": "bnf_crv5r71h1l071n2fjvog",
  "documents": []
}
```