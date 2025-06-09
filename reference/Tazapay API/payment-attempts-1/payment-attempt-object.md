---
title: Payment Attempt Object
excerpt: >-
  A Tazapay Payment Attempt refers to an instance where a transaction is
  attempted through the Tazapay platform, either as part of a checkout process
  or other payment-related workflows. Each payment attempt captures essential
  details of the transaction, including the amount, currency, payment method,
  status, and any relevant metadata.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Object

```
{
			"id": "pat_ahbfiuahfiuaiofnioain",
			"object": "payment_attempt",
			"created_at": "2023-07-21T14:00:02.576356Z",
			"amount": 148000,
			"charge_currency": "SGD",
			"payin": "chk_cirsp2sl4ar024j0akj0",
			"payment_method_details": {
				"type": "paynow_sgd",
				"paynow_sgd": {}
			},
			"refunded": false,
			"status": "succeeded",
			"status_description": null,
			"final_currency": "USD",
			"fx_transaction": {
				"initial": {
					"currency": "SGD",
					"amount": 148000
				},
				"final": {
					"currency": "USD",
					"amount": 100000
				},
				"exchange_rate": 1.48
			},
			"metadata": null
		}
```

<br />

## Parameters

### Payment Attempt

| Parameter                | Type              | Description                                                                   |
| ------------------------ | ----------------- | ----------------------------------------------------------------------------- |
| id                       | string            | The Tazapay ID of the payment attempt.                                        |
| object                   | string            | The object type, which is "payment\_attempt".                                 |
| created\_at              | string (ISO Date) | The date and time when the payment attempt was created.                       |
| amount                   | number            | The amount attempted to be paid in the charge currency.                       |
| charge\_currency         | string            | The currency in which the payment was attempted (e.g., SGD).                  |
| payin                    | string            | The reference to the payin object related to the checkout transaction.        |
| payment\_method\_details | string            | The payment method details used in this attempt                               |
| refunded                 | boolean           | Indicates whether the payment attempt has been refunded.                      |
| status                   | string            | The status of the payment attempt (e.g., succeeded, failed).                  |
| status\_description      | string            | A description providing more information about the payment attempt status     |
| final\_currency          | string            | The final currency after the payment is converted, if applicable (e.g., USD). |
| fx\_transaction          | object            | Details about the foreign exchange transaction, if any.                       |
| metadata                 | json              | Additional key value pairs related to the payment attempt (optional).         |

<br />

### FX transaction

| Field            | Type   | Description                                                 |
| ---------------- | ------ | ----------------------------------------------------------- |
| exchange\_rate   | number | The exchange rate used for the currency conversion.         |
| final.amount     | number | The final amount after conversion.                          |
| final.currency   | string | The final currency after conversion.                        |
| initial.amount   | number | The initial amount before conversion.                       |
| initial.currency | string | The initial currency before conversion.                     |
| id               | string | The Tazapay ID of the holding foreign exchange transaction. |
