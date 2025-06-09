---
title: Customer Object
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
```json
{
  "id": "cus_haiuhfaonfoiaoijfojfajpj123",
  "object": "string",
  "created_at": "2023-07-18 16:34:32",
  "name": "John Doe",
  "email": "john.doe@doe.com",
  "country": "SG",
  "phone": {
    "calling_code": "65",
    "number": "67854321"
  },
  "billing": {
    "name": "John Doe",
    "address": {
      "line1": "Address Line 1",
      "line2": "Address Line 2",
      "city": "Singapore",
      "state": null,
      "country": "SG",
      "postal_code": "76543"
    },
    "phone": {
      "calling_code": "65",
      "number": "7982799"
    }
  },
  "shipping": {
    "name": "John Doe",
    "address": {
      "line1": "Address Line 1",
      "line2": "Address Line 2",
      "city": "Singapore",
      "state": null,
      "country": "SG",
      "postal_code": "76543"
    },
    "phone": {
      "calling_code": "65",
      "number": "7982799"
    }
  },
  "metadata": null
}
```

## Parameters

### Customer

| Field      | Subfield | Type                   | Description                                                               |
| ---------- | -------- | ---------------------- | ------------------------------------------------------------------------- |
| id         |          | string                 | The unique identifier for the customer.                                   |
| object     |          | string                 | The type of object, which is "customer".                                  |
| created_at |          | string (ISO Timestamp) | The timestamp when the customer object was created.                       |
| name       |          | string                 | The name of the customer.                                                 |
| email      |          | string                 | The email address of the customer.                                        |
| country    |          | string                 | The country of the customer (e.g., SG for Singapore).                     |
| phone      |          | object                 | The phone details of the customer. (See Phone Table)                      |
| billing    |          | object                 | The billing details of the customer.                                      |
|            | name     | string                 | The name associated with the billing details.                             |
|            | address  | object                 | The address associated with the billing details. (See Address Table)      |
|            | phone    | object                 | The phone details associated with the billing address. (See Phone Table)  |
| shipping   |          | object                 | The shipping details of the customer.                                     |
|            | name     | string                 | The name associated with the shipping details.                            |
|            | address  | object                 | The address associated with the shipping details. (See Address Table)     |
|            | phone    | object                 | The phone details associated with the shipping address. (See Phone Table) |
| metadata   |          | json                   | Set of key-value pairs attached to the customer                           |

<br />

### Phone

| Field        | Type   | Description                                                     |
| ------------ | ------ | --------------------------------------------------------------- |
| calling_code | string | The international calling code for the customer's phone number. |
| number       | string | The phone number of the customer.                               |

<br />

### Address

| Field       | Type        | Description                                      |
| ----------- | ----------- | ------------------------------------------------ |
| line1       | string      | The first line of the address.                   |
| line2       | string      | The second line of the address                   |
| city        | string      | The city of the address.                         |
| state       | string/null | The state or province of the address (optional). |
| country     | string      | The country code (e.g., SG for Singapore).       |
| postal_code | string      | The postal code of the address.                  |
```