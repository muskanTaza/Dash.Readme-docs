---
title: Entity Object
deprecated: false
hidden: false
metadata:
  robots: index
---
```json
{
  "status": "success",
  "message": "",
  "data": {
      "approval_status": "approved",
      "approval_status_description": "Approved for payouts only",
      "approved_at": "2025-10-09T02:55:52.284767Z",
      "created_at": "2025-10-08T05:18:11.700575Z",
      "description": "",
      "documents": [
          {
              "description": "Recent utility bill",
              "document_id": "doc_d3iv85v58tg9dlpipu2g",
              "file_name": "kyb_doc82697_2October2025_202590_894374483.pdf",
              "sub_type": "other",
              "tag": "",
              "type": "address",
              "updated_at": "2025-09-08T05:18:15.228195Z",
              "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-test-doc"
            },
          {
              "description": "Passport front",
              "document_id": "doc_d3iv85v58tg9dlpipu1g",
              "file_name": "kyb_doc10723_8October2025_docapture_manual-6.jpg",
              "sub_type": "passport",
              "tag": "identityProofTypeFrontDoc",
              "type": "identity",
              "updated_at": "2025-10-08T05:18:15.228195Z",
              "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-test-doc"

            },
          {
              "description": "Passport back",
              "document_id": "doc_d3iv85v58tg9dlpipu20",
              "file_name": "kyb_doc38625_8October2025_docapture_manual-6.jpg",
              "sub_type": "passport",
              "tag": "identityProofTypeBackDoc",
              "type": "identity",
              "updated_at": "2025-10-08T05:18:15.228195Z",
              "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-test-doc"

            }
        ],
      "email": "",
      "id": "ent_d3iv84vs8ud68hm8dba40",
      "metadata": {},
      "name": "James Brwon",
      "object": "entity",
      "on_behalf_of": "",
      "onboarding_package_url": "",
      "operating_address": null,
      "pending_documents": [],
      "phone": {
          "calling_code": "",
          "number": ""
        },
      "purpose_of_use": [
          "payout"
        ],
      "reference_id": "",
      "registration_address": {
          "city": "Bangkok",
          "country": "TH",
          "line1": "151/1 Richmond Boulevard, Lumpini",
          "line2": "",
          "postal_code": "10330",
          "state": "Pathumwan"
        },
      "registration_date": "",
      "registration_number": "",
      "rejected_at": null,
      "relationship": "customer",
    "representatives": [
      {
        "first_name": "Msk",
        "last_name": "Msk",
        "date_of_birth": "2119-11-09",
        "address": {
          "line1": "123 Main Street",
          "line2": "Apt 5B",
          "city": "New Delhi",
          "state": "Delhi",
          "postal_code": "110018",
          "country": "IN"
        },
        "nationality": "IN",
        "phone": {
          "calling_code": "91",
          "number": "9876543210"
        },
        "ownership_percentage": 20,
        "roles": ["beneficial_owner"],
        "documents": [
          {
            "description": "Passport front",
            "document_id": "doc_csbm1ta5grahc4olhpe0",
            "file_name": "kyb_doc91055_22October2024_PassportFront.png",
            "sub_type": "passport",
            "tag": "identityProofTypeFrontDoc",
            "type": "identity",
            "updated_at": "2024-10-22T08:23:21.528098Z",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service-qa/kyb_doc91055_22October2024_PassportFront.png"
          }
			],
      "source_of_wealth": null,
      "statement_descriptor": "",
      "submit": true,
      "submitted_at": "2025-10-01T05:18:15.228732Z",
      "tax_id": "",
      "type": "individual",
      "vertical": "",
      "website": ""
    }
}
```

<br />

## Object Parameters

| Field                       | Type    | Description                                                                                                                                                          |
| --------------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id                          | string  | The unique Tazapay identifier for the entity. Example: `ent_d3iv84vs8ud68hm8dba40`.                                                                                  |
| object                      | string  | The type of object, always `"entity"`.                                                                                                                               |
| name                        | string  | The full name of the entity or individual. Example: `James Brown`.                                                                                                   |
| type                        | enum    | The type of entity. [Values: `individual`, `business`].                                                                                                              |
| relationship                | string  | The relationship type of the entity with Tazapay. Example: `customer`.                                                                                               |
| approval_status             | enum    | The approval status of the entity. [Values: `approved`, `rejected`, `pending`, `resubmitted`].                                                                       |
| approval_status_description | string  | Description of the approval status. Example: `Approved for payouts only`.                                                                                            |
| approved_at                 | string  | Timestamp when the entity was approved (ISO 8601). Example: `2025-10-09T02:55:52.284767Z`.                                                                           |
| created_at                  | string  | Timestamp when the entity record was created (ISO 8601). Example: `2025-10-08T05:18:11.700575Z`.                                                                     |
| submitted_at                | string  | Timestamp when the KYB/KYC submission was made (ISO 8601).                                                                                                           |
| submit                      | boolean | Indicates whether the KYB submission has been completed.                                                                                                             |
| description                 | string  | Additional notes or description for the entity.                                                                                                                      |
| email                       | string  | The email address associated with the entity.                                                                                                                        |
| phone                       | object  | Phone details of the entity. See **[Phone Object](https://docs.tazapay.com/update/reference/phone-object#/)**.                                                       |
| registration_number         | string  | The official business registration number for the entity.                                                                                                            |
| registration_date           | string  | Date of business registration or incorporation (ISO 8601).                                                                                                           |
| registration_address        | object  | Registered address of the entity. See **[Address Object](https://docs.tazapay.com/update/reference/address-object#/)**.                                              |
| operating_address           | object  | Operating address of the entity. May be empty if same as registration address. See **[Address Object](https://docs.tazapay.com/update/reference/address-object#/)**. |
| tax_id                      | string  | The tax identification number of the entity.                                                                                                                         |
| purpose_of_use              | array   | List of purposes for which the entity is using Tazapay. Example: `["payout"]`.                                                                                       |
| source_of_wealth            | string  | Information on the source of funds or wealth for the entity.                                                                                                         |
| statement_descriptor        | string  | Custom descriptor that appears on the end customer’s statement.                                                                                                      |
| reference_id                | string  | The merchant’s own reference identifier for the entity.                                                                                                              |
| vertical                    | string  | The industry vertical or business category of the entity.                                                                                                            |
| website                     | string  | The entity’s website URL. Example: `https://example.com`.                                                                                                            |
| documents                   | array   | List of submitted documents for verification. See **[Document Object](https://docs.tazapay.com/update/reference/document-object#/)**.                                |
| pending_documents           | array   | List of pending documents required for completion.                                                                                                                   |
| representatives             | array   | List of authorised representatives of the entity. Check the [representatives](#Representative) table below.                                                          |
| metadata                    | object  | Custom key-value metadata attached to the entity.                                                                                                                    |
| on_behalf_of                | string  | Account ID if the entity was created on behalf of another account.                                                                                                   |
| onboarding_package_url      | string  | URL to download or view the onboarding package for the entity.                                                                                                       |
| approval_status_description | string  | Additional notes about the approval result.                                                                                                                          |
| rejected_at                 | string  | Timestamp when the entity was rejected, if applicable.                                                                                                               |
| relationship                | string  | Describes the relationship of the entity to Tazapay (e.g., `customer`, `partner`, `vendor`).                                                                         |

<br />

## Representative

<br />

| Field                | Type   | Description                                                                                                                                  |
| -------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------- |
| first_name           | string | The first name of the representative.                                                                                                        |
| last_name            | string | The last name of the representative.                                                                                                         |
| date_of_birth        | string | Date of birth of the representative in ISO 8601 format.                                                                                      |
| address              | object | The address of the representative. See **[Address Object](https://docs.tazapay.com/update/reference/address-object#/)**.                     |
| nationality          | string | Two-letter ISO country code indicating the representative’s nationality.                                                                     |
| phone                | object | The phone details of the representative. See **[Phone Object](https://docs.tazapay.com/update/reference/phone-object#/)**.                   |
| ownership_percentage | number | The ownership percentage the representative holds in the entity.                                                                             |
| roles                | array  | List of roles or capacities the representative serves in. Example: `["director", "beneficial_owner"]`.                                       |
| documents            | array  | List of documents submitted for this representative. See **[Document Object](https://docs.tazapay.com/update/reference/document-object#/)**. |
