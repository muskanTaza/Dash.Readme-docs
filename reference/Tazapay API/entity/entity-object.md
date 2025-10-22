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
      "representatives": [],
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