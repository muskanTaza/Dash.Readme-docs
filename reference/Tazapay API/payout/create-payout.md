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

## Response Body Object

The Create Payout API returns a payout object with the following structure:

### Response Structure

```json
{
  "status": "success",
  "message": "",
  "data": {
    // Payout object details
  }
}
```

### Payout Object Properties

| Property | Type | Description |
|----------|------|-------------|
| `amount` | integer | Amount of the payout in cents |
| `balance_transaction` | string | Balance transaction ID associated with this payout |
| `beneficiary` | string | ID of the beneficiary receiving the payout |
| `beneficiary_details` | object | Detailed information about the beneficiary |
| `charge_type` | string | For wire transfers only - "shared" or "ours" |
| `created_at` | string | Timestamp when the payout was created (ISO 8601) |
| `currency` | string | Three-letter ISO currency code for the payout |
| `documents` | array | Array of documents attached to the payout |
| `holding_currency` | string | Currency of your balance that funds the payout |
| `holding_fx_transaction` | object | Foreign exchange transaction details for holding currency conversion |
| `id` | string | Unique identifier for the payout |
| `metadata` | object | Set of key-value pairs attached to the payout |
| `mt103` | string | MT103 message for wire transfers |
| `object` | string | Always "payout" |
| `on_behalf_of` | string | ID of the entity the payout is created on behalf of |
| `payout_fx_transaction` | object | Foreign exchange transaction details for payout currency conversion |
| `purpose` | string | Reason code for the payout (e.g., "PYR001") |
| `reference_id` | string | Your unique reference ID for the payout |
| `statement_descriptor` | string | Description that appears on statements |
| `status` | string | Current status of the payout (e.g., "processing", "succeeded") |
| `status_description` | string | Additional details about the current status |
| `tracking_details` | object | Tracking information for the payout |
| `transaction_description` | string | Description of the transaction |
| `type` | string | Type of payout (e.g., "swift", "local", "wallet") |

### Beneficiary Details Object

The `beneficiary_details` object contains:

| Property | Type | Description |
|----------|------|-------------|
| `address` | object | Beneficiary's address information |
| `destination` | string | Destination identifier |
| `destination_details` | object | Details about the destination (bank, wallet, etc.) |
| `documents` | array | Documents associated with the beneficiary |
| `email` | string | Beneficiary's email address |
| `name` | string | Beneficiary's name |
| `phone` | object | Beneficiary's phone details |
| `tax_id` | string | Beneficiary's tax identification |
| `type` | string | Type of beneficiary ("business" or "individual") |

### FX Transaction Object

Both `holding_fx_transaction` and `payout_fx_transaction` contain:

| Property | Type | Description |
|----------|------|-------------|
| `exchange_rate` | number | Exchange rate applied |
| `final` | object | Final amount and currency |
| `id` | string | FX transaction ID |
| `initial` | object | Initial amount and currency |
| `object` | string | Always "fx_transaction" |

## Response Examples

<Tabs>
<Tab title="Swift Bank Payout">

```json
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 100000,
    "balance_transaction": "btr_crv5u81h1l071n2fk1o0",
    "beneficiary": "bnf_crv5r71h1l071n2fjvog",
    "beneficiary_details": {
      "address": {
        "city": "test",
        "country": "US",
        "line1": "test",
        "line2": "test",
        "postal_code": "10038",
        "state": "test"
      },
      "destination": "bnk_crv5r71gb6vrb4oj77kg",
      "destination_details": {
        "bank": {
          "account_number": "test",
          "account_type": "",
          "bank_codes": {
            "aba_code": "test",
            "swift_code": "test"
          },
          "bank_name": "city bank",
          "branch_name": "",
          "country": "US",
          "currency": "USD",
          "firc_required": false,
          "purpose_code": ""
        },
        "type": "bank"
      },
      "documents": [],
      "email": "test@example.com",
      "name": "test",
      "phone": {
        "calling_code": "1",
        "number": "12312312345"
      },
      "tax_id": "test",
      "type": "individual"
    },
    "charge_type": "ours",
    "created_at": "2024-10-03T09:08:48.467222Z",
    "currency": "USD",
    "documents": [],
    "holding_currency": "EUR",
    "holding_fx_transaction": {
      "exchange_rate": 1.059191,
      "final": {
        "amount": 100000,
        "currency": "USD"
      },
      "id": "fx_crv5u80dj96g452dfr2g",
      "initial": {
        "amount": 94412,
        "currency": "EUR"
      },
      "object": "fx_transaction"
    },
    "id": "pot_crv5u81h1l071n2fk1ng",
    "metadata": null,
    "mt103": "",
    "object": "payout",
    "payout_fx_transaction": {
      "exchange_rate": 1,
      "final": {
        "amount": 100000,
        "currency": "USD"
      },
      "id": "fx_crv5u80dj96g452dfr20",
      "initial": {
        "amount": 100000,
        "currency": "USD"
      },
      "object": "fx_transaction"
    },
    "purpose": "PYR001",
    "reference_id": "Test_Ref",
    "statement_descriptor": "tzp*Test",
    "status": "processing",
    "status_description": "",
    "tracking_details": null,
    "transaction_description": "Test Payout",
    "type": "swift",
    "on_behalf_of": ""
  }
}
```

</Tab>
<Tab title="Error Response">

```json
{
  "status": "error",
  "message": "Validation failed",
  "errors": [
    {
      "code": 400,
      "message": "Invalid currency code",
      "remarks": "Currency must be a valid ISO 4217 code"
    }
  ]
}
```

</Tab>
</Tabs>

## Status Values

The payout `status` field can have the following values:

- **`requires_funding`** - Payout created but needs to be funded
- **`processing`** - Payout is being processed
- **`succeeded`** - Payout completed successfully
- **`failed`** - Payout failed
- **`cancelled`** - Payout was cancelled

## Next Steps

After creating a payout, you can:

- [Fetch the payout details](fetch-payout) to check status
- [Update payout metadata](update-payout) if needed
- [Fund the payout](funding-a-payout) if status is `requires_funding`