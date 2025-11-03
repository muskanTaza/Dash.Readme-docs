---
title: Document
excerpt: >-
  This object allows you to attach important documents, such as invoices,
  delivery-proof or receipts to payin transactions. It helps keep records
  organized and readily accessible for both businesses and customers.
deprecated: false
hidden: false
icon: far fa-paperclip
metadata:
  title: ''
  description: ''
  robots: noindex
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
    "name": "Purchase proof",
    "object": "document",
    "reference": "esc_ck0og8noclf1aqlh4icg",
    "type": "tracking_url",
    "url": "https://drive.google.com/file/d/1q5kk5YKcCojdTYir-rONXjN7szuXE16m/view?usp=sharing"
}

```

## Parameters

### Document

| Field       | Type                   | Description                                                                                                                                                                       |
| ----------- | ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id          | string                 | The unique Tazapay identifier for the document.                                                                                                                                   |
| object      | string                 | The type of object, which is "document".                                                                                                                                          |
| name        | string                 | The name of the document in case the type is others.                                                                                                                              |
| description | string                 | A description of the document.                                                                                                                                                    |
| url         | string                 | The URL where the uploaded document can be accessed.                                                                                                                              |
| type        | enum                   | The type of the document [Values - goods_delivery_proof, service_delivery_proof, tracking_url, other][Values - goods_delivery_proof, service_delivery_proof, tracking_url, other] |
| reference   | string                 | The Tazapay reference ID of the related object, such as a customer or transaction.                                                                                                |
| created_at  | string (ISO Timestamp) | The date and time when the document was uploaded (in ISO format).                                                                                                                 |
| metadata    | json                   | Set of  key value pairs associated with the document.                                                                                                                             |
