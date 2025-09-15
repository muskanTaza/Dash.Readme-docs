---
title: Payin Object
excerpt: >-
  A payin refers to the process through which a merchant collects payments
  through Tazapay’s cross-border payment platform. This can be done through
  various methods such as credit/debit cards, local payment methods, bank
  transfers, or e-wallets, depending on the supported payment options in the
  region.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
```
{
        "amount": 100,
        "amount_paid": 0,
        "billing_details": {
            "address": {
                "city": "Singapore",
                "country": "SG",
                "line1": "1st Street",
                "line2": "2nd Avenue",
                "postal_code": "43004",
                "state": "Singapore"
            },
            "label": "Home",
            "name": "Andrea Lark",
            "phone": {
                "calling_code": "65",
                "number": "87654321"
            }
        },
        "cancel_url": "https://mystore.com/try_again",
        "cancelled_at": null,
        "client_token": "JsU19R_Li9cwVksJGUfAajZ3r2A9ArU7Qk3j5r0cpVg=",
        "confirm": false,
        "created_at": "2024-10-07T07:10:21.894488Z",
        "customer": "cus_crtqrhth90j0121gpt50",
        "customer_details": {
            "country": "SG",
            "email": "andrea@example.com",
            "name": "Andrea Lark",
            "phone": {
                "calling_code": "65",
                "number": "87654321"
            }
        },
        "holding_currency": "INR",
        "id": "pay_cs1oina7a5ng2a3ng12g",
        "invoice_currency": "INR",
        "items": [],
        "latest_payment_attempt": "",
        "latest_payment_attempt_data": null,
        "metadata": {
            "key1": "value1",
            "key2": "value2",
            "key3": "value3"
        },
        "object": "payin",
        "paid_in_excess": false,
        "partially_paid": false,
        "payment_attempts": [],
        "payment_method_details": {
            "paynow_sgd": {},
            "type": "paynow_sgd"
        },
        "reference_id": "123",
        "shipping_details": {
            "address": {
                "city": "Singapore",
                "country": "SG",
                "line1": "1st Street",
                "line2": "2nd Avenue",
                "postal_code": "43004",
                "state": "Singapore"
            },
            "label": "Home",
            "name": "Andrea Lark",
            "phone": {
                "calling_code": "65",
                "number": "87654321"
            }
        },
        "statement_descriptor": "tzp*string",
        "status": "requires_payment_method",
        "status_description": "",
        "success_url": "https://mystore.com/success_page",
        "transaction_data": [],
        "transaction_description": "test",
        "transaction_documents": [],
        "webhook_url": "https://mystore.com/internal/webhook"
    }
```

## Parameters

### Payin

| Field                       | Subfield   | Type                   | Description                                                                |
| --------------------------- | ---------- | ---------------------- | -------------------------------------------------------------------------- |
| amount                      |            | number                 | The total amount of the payin transaction.                                 |
| amount_paid                 |            | number                 | The amount that has already been paid.                                     |
| billing_details             |            | object                 | The billing information for the transaction.                               |
|                             | address    | object                 | The address associated with the billing details. (See Address Table).      |
|                             | label      | string                 | A label for the billing address (e.g., Home, Office).                      |
|                             | name       | string                 | The name associated with the billing details.                              |
|                             | phone      | object                 | The phone details associated with the billing address. (See Phone Table).  |
| cancel_url                  |            | string                 | The URL to redirect the user to if the transaction is canceled.            |
| cancelled_at                |            | string(ISO timestamp)  | The timestamp when the transaction was canceled, if applicable.            |
| client_token                |            | string                 | The client token associated with the payin.                                |
| confirm                     |            | boolean                | Indicates if the transaction is confirmed.                                 |
| created_at                  |            | string (ISO timestamp) | The timestamp when the transaction was created.                            |
| customer                    |            | string                 | The unique identifier for the customer.                                    |
| customer_details            |            | object                 | The customer details related to the transaction.                           |
|                             | country    | string                 | The country of the customer.                                               |
|                             | email      | string                 | The email address of the customer.                                         |
|                             | name       | string                 | The name of the customer.                                                  |
|                             | phone      | object                 | The phone details of the customer. (See Phone Table).                      |
| holding_currency            |            | string                 | The holding currency used for the transaction (e.g., INR).                 |
| id                          |            | string                 | The unique Tazapay identifier for the payin transaction.                   |
| invoice_currency            |            | string                 | The invoice currency for the transaction.                                  |
| items                       |            | array                  | The list of items related to the transaction.                              |
| latest_payment_attempt      |            | string                 | The Tazapay ID of the latest payment attempt.                              |
| latest_payment_attempt_data |            | object/null            | Data related to the latest payment attempt, if available.                  |
| metadata                    |            | object                 | Set of key-value pairs attached to the transaction.                        |
| object                      |            | string                 | The type of object, which is "payin".                                      |
| paid_in_excess              |            | boolean                | Indicates if the payment was made in excess.                               |
| partially_paid              |            | boolean                | Indicates if the payment was partially paid.                               |
| payment_attempts            |            | array                  | The list of payment attempts for this transaction.                         |
| payment_method_details      |            | object                 | The details of the payment method used.                                    |
|                             | paynow_sgd | boolean                | Indicates whether PayNow SGD is available for this transaction.            |
|                             | type       | string                 | The type of payment method used (e.g., paynow_sgd).                        |
| reference_id                |            | string                 | The reference ID for the transaction.                                      |
| shipping_details            |            | object                 | Shipping information for the transaction.                                  |
|                             | address    | object                 | The address associated with the shipping details. (See Address Table).     |
|                             | label      | string                 | A label for the shipping address (e.g., Home, Office).                     |
|                             | name       | string                 | The name associated with the shipping details.                             |
|                             | phone      | object                 | The phone details associated with the shipping address. (See Phone Table). |
| statement_descriptor        |            | string                 | The descriptor to appear on the customer’s statement.                      |
| status                      |            | string                 | The current status of the transaction (e.g., requires_payment_method).     |
| status_description          |            | string                 | A description of the transaction status, if available.                     |
| success_url                 |            | string                 | The URL to redirect the user to upon a successful transaction.             |
| transaction_data            |            | array                  | Additional data related to the transaction.                                |
| transaction_description     |            | string                 | A description of the transaction.                                          |
| transaction_documents       |            | array                  | List of transaction-related documents.                                     |
| webhook_url                 |            | string                 | The URL for webhook notifications related to this transaction.             |

<br />

### Address

| Field       | Type   | Description                                                       |
| ----------- | ------ | ----------------------------------------------------------------- |
| city        | string | The city associated with the address.                             |
| country     | string | The country associated with the address (e.g., SG for Singapore). |
| line1       | string | The first line of the address.                                    |
| line2       | string | The second line of the address (optional).                        |
| postal_code | string | The postal code of the address.                                   |
| state       | string | The state or province associated with the address.                |

<br />

### Phone

| Field        | Type   | Description                                                       |
| ------------ | ------ | ----------------------------------------------------------------- |
| calling_code | string | The international calling code for the phone number.              |
| number       | string | The phone number associated with the billing or shipping address. |

\<Columns layout="auto">
&#x20; \<Column>
&#x20;   \<table>...\</table>
&#x20; \</Column>
&#x20;  &#x20;
&#x20; \<Column>
&#x20;   \`\`\`\{
&#x20;       "amount": 100,
&#x20;       "amount\_paid": 0,
&#x20;       "billing\_details": \{
&#x20;           "address": \{
&#x20;               "city": "Singapore",
&#x20;               "country": "SG",
&#x20;               "line1": "1st Street",
&#x20;               "line2": "2nd Avenue",
&#x20;               "postal\_code": "43004",
&#x20;               "state": "Singapore"
&#x20;           },
&#x20;           "label": "Home",
&#x20;           "name": "Andrea Lark",
&#x20;           "phone": \{
&#x20;               "calling\_code": "65",
&#x20;               "number": "87654321"
&#x20;           }
&#x20;       },
&#x20;       "cancel\_url": "https\://mystore.com/try\_again",
&#x20;       "cancelled\_at": null,
&#x20;       "client\_token": "JsU19R\_Li9cwVksJGUfAajZ3r2A9ArU7Qk3j5r0cpVg=",
&#x20;       "confirm": false,
&#x20;       "created\_at": "2024-10-07T07:10:21.894488Z",
&#x20;       "customer": "cus\_crtqrhth90j0121gpt50",
&#x20;       "customer\_details": \{
&#x20;           "country": "SG",
&#x20;           "email": "andrea\@example.com",
&#x20;           "name": "Andrea Lark",
&#x20;           "phone": \{
&#x20;               "calling\_code": "65",
&#x20;               "number": "87654321"
&#x20;           }
&#x20;       },
&#x20;       "holding\_currency": "INR",
&#x20;       "id": "pay\_cs1oina7a5ng2a3ng12g",
&#x20;       "invoice\_currency": "INR",
&#x20;       "items": \[],
&#x20;       "latest\_payment\_attempt": "",
&#x20;       "latest\_payment\_attempt\_data": null,
&#x20;       "metadata": \{
&#x20;           "key1": "value1",
&#x20;           "key2": "value2",
&#x20;           "key3": "value3"
&#x20;       },
&#x20;       "object": "payin",
&#x20;       "paid\_in\_excess": false,
&#x20;       "partially\_paid": false,
&#x20;       "payment\_attempts": \[],
&#x20;       "payment\_method\_details": \{
&#x20;           "paynow\_sgd": \{},
&#x20;           "type": "paynow\_sgd"
&#x20;       },
&#x20;       "reference\_id": "123",
&#x20;       "shipping\_details": \{
&#x20;           "address": \{
&#x20;               "city": "Singapore",
&#x20;               "country": "SG",
&#x20;               "line1": "1st Street",
&#x20;               "line2": "2nd Avenue",
&#x20;               "postal\_code": "43004",
&#x20;               "state": "Singapore"
&#x20;           },
&#x20;           "label": "Home",
&#x20;           "name": "Andrea Lark",
&#x20;           "phone": \{
&#x20;               "calling\_code": "65",
&#x20;               "number": "87654321"
&#x20;           }
&#x20;       },
&#x20;       "statement\_descriptor": "tzp\*string",
&#x20;       "status": "requires\_payment\_method",
&#x20;       "status\_description": "",
&#x20;       "success\_url": "https\://mystore.com/success\_page",
&#x20;       "transaction\_data": \[],
&#x20;       "transaction\_description": "test",
&#x20;       "transaction\_documents": \[],
&#x20;       "webhook\_url": "https\://mystore.com/internal/webhook"
&#x20;   }\`\`\`
&#x20; \</Column>
\</Columns>
