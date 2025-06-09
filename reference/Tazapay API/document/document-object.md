---
title: Document Object
excerpt: >-
  The Tazapay Document API enables seamless linking of documents to various
  transaction types, such as checkout, escrow, payin etc  using a reference ID.
  This feature allows for efficient document management and tracking, ensuring
  that any relevant document, like invoices or contracts, can be associated with
  the correct transaction, enhancing transparency and operational efficiency
  across the platform.
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
    "created_at": "2023-09-13T10:22:12.711645400Z",
    "description": "This is a sample document",
    "id": "doc_ck0oql7oclf1aqlh4jdg",
    "metadata": null,
    "name": "",
    "object": "document",
    "reference": "esc_ck0og8noclf1aqlh4icg",
    "type": "tracking_url",
    "url": "https://drive.google.com/file/d/1q5kk5YKcCojdTYir-rONXjN7szuXE16m/view?usp=sharing"
  }
```

## Parameters

### Document

| Field       | Type                   | Description                                                                                           |
| ----------- | ---------------------- | ----------------------------------------------------------------------------------------------------- |
| id          | string                 | The unique Tazapay identifier for the document.                                                       |
| object      | string                 | The type of object, which is "document".                                                              |
| name        | string                 | The name of the document.                                                                             |
| description | string                 | A description of the document.                                                                        |
| url         | string                 | The URL where the uploaded document can be accessed.                                                  |
| type        | enum                   | The type of the document [Values - goods_delivery_proof, service_delivery_proof, tracking_url, other] |
| reference   | string                 | The Tazapay reference ID of the related object, such as a customer or transaction.                    |
| created_at  | string (ISO Timestamp) | The date and time when the document was uploaded (in ISO format).                                     |
| metadata    | json                   | Set of  key value pairs associated with the document.                                                 |