---
title: Customer Object
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
```json
{
  "status": "success",
  "message": "customer created successfully",
  "data": {
    "id": "cus_abc123xyz456",
    "object": "customer",
    "created_at": "2025-10-13T14:30:00Z",
    "name": "Andrew Robin",
    "email": "andrew.robin@example.com",
    "country": "US",
    "phone": {
      "calling_code": "1",
      "number": "2025550183"
    },
    "billing_address": [
      {
        "name": "Andrew Robin",
        "address": {
          "line1": "123 Main Street",
          "line2": "Apt 45B",
          "city": "New York",
          "state": "NY",
          "country": "US",
          "postal_code": "10001"
        },
        "phone": {
          "calling_code": "1",
          "number": "2125550199"
        },
				"label":"home"
      }
    ],
    "shipping_address": [
      {
        "name": "Andrew Robin",
        "address": {
          "line1": "789 Broadway Avenue",
          "line2": "Suite 500",
          "city": "New York",
          "state": "NY",
          "country": "US",
          "postal_code": "10003"
        },
        "phone": {
          "calling_code": "1",
          "number": "9175550132"
        },
				"label":"home"
      }
    ],
    "metadata": {
      "referral_code": "REF2025ABC"
    }
  }
}
```

## Parameters

### Customer

| Field            | Subfield | Type                   | Description                                                               |
| ---------------- | -------- | ---------------------- | ------------------------------------------------------------------------- |
| id               |          | string                 | The unique identifier for the customer.                                   |
| object           |          | string                 | The type of object, which is "customer".                                  |
| created_at       |          | string (ISO Timestamp) | The timestamp when the customer object was created.                       |
| name             |          | string                 | The name of the customer.                                                 |
| email            |          | string                 | The email address of the customer.                                        |
| country          |          | string                 | The country of the customer (e.g., SG for Singapore).                     |
| phone            |          | object                 | The phone details of the customer. (See Phone Table)                      |
| billing_address  |          | object                 | The billing details of the customer.                                      |
|                  | name     | string                 | The name associated with the billing details.                             |
|                  | address  | object                 | The address associated with the billing details. (See Address Table)      |
|                  | phone    | object                 | The phone details associated with the billing address. (See Phone Table)  |
|                  | label    | string                 | Denotes the type of address (Example - home, work)                        |
| shipping_address |          | object                 | The shipping details of the customer.                                     |
|                  | name     | string                 | The name associated with the shipping details.                            |
|                  | address  | object                 | The address associated with the shipping details. (See Address Table)     |
|                  | phone    | object                 | The phone details associated with the shipping address. (See Phone Table) |
|                  | label    | string                 | Denotes the type of address (Example - home, work)                        |
| metadata         |          | json                   | Set of key-value pairs attached to the customer                           |

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

<br />