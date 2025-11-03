---
title: Customers
excerpt: ''
deprecated: false
hidden: false
icon: far fa-user
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
A fundamental Tazapay API object that helps businesses to create customers with whom they want to do transactions repeatedly. It stores customer information, enabling businesses to manage transaction creation and provide a better user experience.

## Object Structure

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
