---
title: Checkout
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
## Card Payment:

```Text Sample Webhook Response for a Card Payment
{
	"status": "success",
	"data": {
		"txn_no": "2305-468522",
		"state": "Payment_Received",
		"sub_state": "Generic",
		"invoice_currency": "USD",
		"invoice_amount": 3500,
		"partner_reference_id": "5d88414f-7250-4ad7-499f-d6133aa44d5c",
		"payment": {
			"collection_method": "Card",
			"remarks": "payment received",
			"payable_amount": 3605,
			"paid_amount": 3605,
			"collection_currency": "HKD",
			"fx_rate": 7.995913,
			"transaction_id": "59349934-e085-41ad-922c-97b84e48b747",
			"sender_details": {
				"amount": 2882527,
				"card_scheme": "Visa",
				"currency_code": "HKD",
				"email": "ansurajK@test.com",
				"ip": "0.0.0.0",
				"issuer_country_code": "US",
				"issuing_bank": "",
				"last_four_digits": "4242",
				"name": "Test",
				"statement_descriptor": "Tazapay*Business"
			}
		},
		"attributes": {
			"secretKey": "WfZ+X1E42AMoavHslNOg25dxfQIMWfgpfHJCLVURaIUWHPsioiXYdX1d6C0qNx5k"
		},
		"collect_amount": 0,
		"disburse_amount": 0,
		"fee_amount": 0,
		"fee_percentage": 0
	}
}
```

## Response parameters:

| Parameter        | Description                                    |
| ---------------- | ---------------------------------------------- |
| txn_no           | `string` The txn_no for the request made       |
| invoice_currency | `string` The invoice currency                  |
| invoice_amount   | `float` Invoice amount                         |
| state            | `string` The state / status of the payment     |
| sub_state        | `string` The sub state / status of the payment |

**Related Guide:** <a href="https://docs.tazapay.com/docs/checkout-object-states" target="_blank">Checkout states and substates</a>