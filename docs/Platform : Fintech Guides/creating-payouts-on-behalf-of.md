---
title: Creating Payouts on Behalf Of Businesses
excerpt: >-
  This technical guide helps you build an integration for creating payouts on
  behalf of your sub-merchants
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
As a fintech / platform, you can effortlessly create multiple sub-entities on Tazapay for your merchants all accessible from a single dashboard. You can then create payouts on behalf of these entities. This structure ensures transparency and compliance in the payment flow for all the stakeholders, while still empowering you to manage and direct payouts.

Here’s how you can integrate with Tazapay as a platform / fintech

1. Create your own account
2. Get your account approved
3. Create Entities corresponding to your sub-merchants using APIs / dashboard
4. Get the sub-merchants approved
5. Create Payouts on behalf of the sub-merchants

# Create your own account

You can create your own account by signing up on the Tazapay dashboard at [https://dashboard.tazapay.com.](https://dashboard.tazapay.com.) You can also [add multiple users from your team](https://support.tazapay.com/how-do-i-invite-team-members-into-my-tazapay-account) with different levels of access to your account.

For testing, you can sign up on Tazapay’s sandbox environment at [https://dashboard-sandbox.tazapay.com](https://dashboard-sandbox.tazapay.com)

# Get your account approved

Once you have signed up for your Tazapay account, you’ll need to complete a few steps to get it approved:

* [Submit KYB documents:](https://support.tazapay.com/how-do-i-complete-kyb-kyc) This typically includes the business details, business Representatives / UBO / Director details and the supporting documents
* Wait for Approval: The approval process can range from 3-5 business days to a few weeks depending on the completeness of documents, verification requirements and complexity of your business. During this time, you will receive email notifications from Tazapay’s compliance for additional requirements.
* Start Using Tazapay: Once approved, you will receive a confirmation email and your account will be fully activated. You can now start adding sub-merchants.

Tazapay’s sandbox (test) environment does not require approval. All the accounts are approved on sign-up.

# Create entities on Tazapay corresponding to your sub-merchants

You can create entities on Tazapay corresponding to your sub-merchant either using the API or the dashboard

## Creating and submitting entity using the dashboard

Creating an entity and submitting the documents for verification from the dashboard is a straightforward process. You can refer to [this guide](https://support.tazapay.com/submitting-an-entity-for-approval) to learn creating an entity using the Tazapay dashboard.

## Creating an entity using API

### Step 1: Create an entity

Tazapay uses an entity object to represent a sub-merchant. The entity object also tracks the approval status as it changes from created to approved. 

Create an entity on your server with the business name and the industry vertical.

### Sample Request cURL

```bash
curl --request POST \
  --url https://service-sandbox.tazapay.com/v3/entity \
  --data '{
  "name": "New Business",
  "vertical":"Ecommerce-Dropshipping"
}'
```

### Response

```bash
{
  "status": "success",
  "message": "",
  "data": {
    "approval_status": "initiated",
    "approval_status_description": "",
    "approved_at": null,
    "created_at": "2024-11-06T18:13:36.329851596Z",
    "description": "",
    "documents": [],
    "email": "",
    "id": "ent_cslr3k41kl1roj573p3g",
    "metadata": null,
    "name": "New Business",
    "object": "entity",
    "operating_address": {
      "city": "",
      "country": "",
      "line1": "",
      "line2": "",
      "postal_code": "",
      "state": ""
    },
    "pending_documents": [],
    "phone": {
      "calling_code": "",
      "number": ""
    },
    "reference_id": "",
    "registration_address": {
      "city": "",
      "country": "",
      "line1": "",
      "line2": "",
      "postal_code": "",
      "state": ""
    },
    "registration_date": "",
    "registration_number": "",
    "representatives": [],
    "statement_descriptor": "",
    "submit": false,
    "submitted_at": null,
    "tax_id": "",
    "type": "",
    "vertical": "Ecommerce-Dropshipping",
    "website": ""
  }
}
```

> `id` is the unique identifier representing the entity

### Step 2: Submit an entity

Submit an already created entity on your server using Tazapay’s [Submit Entity API](https://docs.tazapay.com/reference/submit-entity) with the `id` field from Step 1 and the following mandatory information:

1. Type of the entity
2. Business Registration Address
3. Business Operating Address
4. Business Registration Number
5. Details of Authorized Representatives
   1. Name
   2. Date of Birth
   3. Nationality
   4. Ownership Percentage
   5. Roles
   6. Proof of Identity
   7. Proof of Address
6. Business Documents
   1. Certificate of Incorporation
   2. Proof of Address
   3. Certificate of domain ownership (if applicable)

### Sample Request cURL

```bash
curl --request POST \
  --url https://service.tazapay.com/v3/entity/ent_csmd1m41kl1roj57ems0/submit \
  --data '{
  "type": "company",
  "registration_address": {
    "line1": "Address line1",
    "line2": "Address line2",
    "city": "Address City",
    "state": "Address State",
    "country": "SG",
    "postal_code": "75918"
  },
  "operating_address": {
    "line1": "Address line1",
    "line2": "Address line2",
    "city": "Address City",
    "state": "Address State",
    "country": "SG",
    "postal_code": "75918"
  },
  "registration_number": "RG001",
  "representatives": [
    {
      "first_name": "John",
      "last_name": "Doe",
      "date_of_birth": "10-08-1987",
      "nationality": "US",
      "ownership_percentage": 52.27,
      "roles": [
        "shareholder"
      ],
      "documents": [
        {
          "description": "proof_of_identity",
          "file_name": "Cypress.png",
          "type": "identity",
          "sub_type": "national_id",
          "tag": "identityProofTypeFrontDoc",
          "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
        },
        {
          "description": "proof_of_address",
          "file_name": "Cypress.png",
          "type": "address",
          "sub_type": "drivers_license",
          "tag": "AddressProofDoc",
          "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
        }
      ]
    },
    {
      "first_name": "Alice",
      "last_name": "Doe",
      "date_of_birth": "05-03-1989",
      "nationality": "US",
      "ownership_percentage": 23.22,
      "roles": [
        "shareholder"
      ],
      "documents": [
        {
          "description": "proof_of_identity",
          "file_name": "Cypress.png",
          "type": "identity",
          "sub_type": "national_id",
          "tag": "identityProofTypeFrontDoc",
          "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
        },
        {
          "description": "proof_of_address",
          "file_name": "Cypress.png",
          "type": "address",
          "sub_type": "drivers_license",
          "tag": "AddressProofDoc",
          "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
        }
      ]
    }
  ],
  "documents": [
    {
      "description": "business_registration_proof",
      "file_name": "Cypress.png",
      "type": "business",
      "sub_type": "other",
      "tag": "registrationProofDoc",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    },
    {
      "description": "operating_address_proof",
      "file_name": "Cypress.png",
      "type": "business",
      "sub_type": "other",
      "tag": "AddressProofDoc",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    },
    {
      "description": "shareholding_structure",
      "file_name": "Cypress.png",
      "type": "business",
      "sub_type": "other",
      "tag": "beneficialOwnershipDoc",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    }
  ]
}'
```

### Response

```bash
{
  "status": "success",
  "message": "",
  "data": {
    "approval_status": "submitted",
    "approval_status_description": "",
    "created_at": "2024-11-07T14:38:16.569983Z",
    "description": "",
    "documents": [],
    "email": "",
    "id": "ent_csmd1m41kl1roj57ems0",
    "metadata": {},
    "name": "New Business 2",
    "object": "entity",
    "operating_address": {
      "city": "Address City",
      "country": "SG",
      "line1": "Address line1",
      "line2": "Address line2",
      "postal_code": "75918",
      "state": "Address State"
    },
    "pending_documents": [],
    "phone": null,
    "reference_id": "",
    "registration_address": {
      "city": "Address City",
      "country": "SG",
      "line1": "Address line1",
      "line2": "Address line2",
      "postal_code": "75918",
      "state": "Address State"
    },
    "registration_date": "",
    "registration_number": "RG001",
    "representatives": [],
    "statement_descriptor": "",
    "submit": true,
    "submitted_at": "2024-11-07T14:38:28.473680062Z",
    "tax_id": "",
    "type": "company",
    "vertical": "Ecommerce-Dropshipping",
    "website": ""
  }
}
```

### Step 1A: Creating and submitting the entity in a single step

You can also create and submit an entity on your server in a single step using Tazapay’s [Create Entity API](https://docs.tazapay.com/reference/create-entity) by setting the submit flag as `true` and providing the following mandatory information:

1. Business Name
2. Type of the entity
3. Business Registration Address
4. Business Operating Address
5. Business Registration Number
6. Details of Authorized Representatives
   1. Name
   2. Date of Birth
   3. Nationality
   4. Ownership Percentage
   5. Roles
   6. Proof of Identity
   7. Proof of Address
7. Business Documents
   1. Certificate of Incorporation
   2. Proof of Address
   3. Certificate of domain ownership (if applicable)

### Request Body

```bash
curl --request POST \
  --url https://service.tazapay.com/v3/entity \
  --data '{
  "name": "New Business 3",
  "vertical": "Ecommerce-Dropshipping",
  "submit": true,
  "type": "company",
  "registration_address": {
    "line1": "Address line1",
    "line2": "Address line2",
    "city": "Address City",
    "state": "Address State",
    "country": "SG",
    "postal_code": "75918"
  },
  "operating_address": {
    "line1": "Address line1",
    "line2": "Address line2",
    "city": "Address City",
    "state": "Address State",
    "country": "SG",
    "postal_code": "75918"
  },
  "registration_number": "RG001",
  "representatives": [
    {
      "first_name": "John",
      "last_name": "Doe",
      "date_of_birth": "10-08-1987",
      "nationality": "US",
      "ownership_percentage": 52.27,
      "roles": [
        "shareholder"
      ],
      "documents": [
        {
          "description": "proof_of_identity",
          "file_name": "Cypress.png",
          "type": "identity",
          "sub_type": "national_id",
          "tag": "identityProofTypeFrontDoc",
          "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
        },
        {
          "description": "proof_of_address",
          "file_name": "Cypress.png",
          "type": "address",
          "sub_type": "drivers_license",
          "tag": "AddressProofDoc",
          "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
        }
      ]
    },
    {
      "first_name": "Alice",
      "last_name": "Doe",
      "date_of_birth": "05-03-1989",
      "nationality": "US",
      "ownership_percentage": 23.22,
      "roles": [
        "shareholder"
      ],
      "documents": [
        {
          "description": "proof_of_identity",
          "file_name": "Cypress.png",
          "type": "identity",
          "sub_type": "national_id",
          "tag": "identityProofTypeFrontDoc",
          "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
        },
        {
          "description": "proof_of_address",
          "file_name": "Cypress.png",
          "type": "address",
          "sub_type": "drivers_license",
          "tag": "AddressProofDoc",
          "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
        }
      ]
    }
  ],
  "documents": [
    {
      "description": "business_registration_proof",
      "file_name": "Cypress.png",
      "type": "business",
      "sub_type": "other",
      "tag": "registrationProofDoc",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    },
    {
      "description": "operating_address_proof",
      "file_name": "Cypress.png",
      "type": "business",
      "sub_type": "other",
      "tag": "AddressProofDoc",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    },
    {
      "description": "shareholding_structure",
      "file_name": "Cypress.png",
      "type": "business",
      "sub_type": "other",
      "tag": "beneficialOwnershipDoc",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    }
  ]
}'
```

### Response:

```bash
{
  "status": "success",
  "message": "",
  "data": {
    "approval_status": "submitted",
    "approval_status_description": "",
    "approved_at": null,
    "created_at": "2024-11-07T14:47:56.506606329Z",
    "description": "",
    "documents": [
      {
        "description": "business_registration_proof",
        "document_id": "doc_csmd674a2n8o3aq6rghg",
        "file_name": "kyb_doc29163_7November2024_Cypress.png",
        "sub_type": "other",
        "tag": "registrationProofDoc",
        "type": "business",
        "updated_at": "2024-11-07T14:47:56.513671Z",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc29163_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS7DUAJFTI%2F20241107%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241107T144756Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjELr%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkgwRgIhAIgTlC3AOWsaADMmzchljlrOMllo%2FhRoEwjlUHzOnF7JAiEAwy5K8fEO26dMGTpYBs5iNp6QWwmtKhLsdvk7LnVuDUQq9AMIQxABGgwyODg0MTczNzMwOTMiDIQf9yK2jaNpDfEG4irRA1wEoBslTAYu4MANL6fStwrkzON98A8GZQRd1BIg%2B9qed%2Bo6vaYwcjv97M1VpPTmFpEJRHpC%2Bj1F17ajhtmOAcwx0GfRG5o2BfnHq9vPJMfZIYsumiphLREF4z4rZFKPG3NSAtVF%2BhWmpHrE4VNmgi7lViH16wCminB80aDw5o3INDljwAlNOMFTBojOs3SNUAFTOvFIB7YzgSjXK6%2B4i%2BCFktiAj%2Fq0xmRMl2C%2BxgTZvKllu%2F23Hxv21nJmH%2FE26DgGWf5geCWUUirIa3mzoRS8axJ2n3pmWTNkJyeA%2B26NEzjppLOP2DNazXeJV1oj%2FlZvQC46FfZVcRuEcy%2BmzV2PXWCCwhwNblLD92ej0mhJ4SxW7wvLCLf9tZI0bndkFgqyXBipj1O1%2FCw5SdfvpuXV7O3uDPHRr%2FGs9Q3adTxLU4cIv83Zh7BcglsCjBRPuX%2Bz97ie8LpzIZ6J%2BY7CHm5q7F4LBXHe4dAj6e11c6f%2F2Uc93pzktPK17ByZMNJIp8cBinLEfeSilEQt%2BhYe7HwEQEHUo%2BrwVia27mXX0UXJaVOcOc9M6GJCOOQE9As%2B8yPyL2KPAA6SUgW%2FBXDmGs5c2cWhAD%2FQ%2FaeBQMWGWCUllzC0k7K5BjqkAQ0q6kSX2jKM16O8%2F%2BNOe6qTRCvFDsRZPkjTd%2BUVpcuTI9vWeClvxJ7SE22mHczqe6RgC3YjxEyKx84nuD4wkxPFGy5xXrCj0gCrEGdiWrUVev9fg8AFWbwTtpHi7Ayyb%2BC9WvWCk0vdZX1rayJvxk9vSrVgEwbq%2BY%2BPpfPOYNuYvIBQ4cDF3qRdq0ZsLq3aRQRGjGAOFaQ03qc1%2FWGYnTlP%2Bwtw&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=2dcd585cd3238e92340046432dc16df8b353be01aa75d07d554d52f16a58cc36"
      },
      {
        "description": "operating_address_proof",
        "document_id": "doc_csmd674a2n8o3aq6rgi0",
        "file_name": "kyb_doc85048_7November2024_Cypress.png",
        "sub_type": "other",
        "tag": "AddressProofDoc",
        "type": "business",
        "updated_at": "2024-11-07T14:47:56.513671Z",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc85048_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS7DUAJFTI%2F20241107%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241107T144756Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjELr%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkgwRgIhAIgTlC3AOWsaADMmzchljlrOMllo%2FhRoEwjlUHzOnF7JAiEAwy5K8fEO26dMGTpYBs5iNp6QWwmtKhLsdvk7LnVuDUQq9AMIQxABGgwyODg0MTczNzMwOTMiDIQf9yK2jaNpDfEG4irRA1wEoBslTAYu4MANL6fStwrkzON98A8GZQRd1BIg%2B9qed%2Bo6vaYwcjv97M1VpPTmFpEJRHpC%2Bj1F17ajhtmOAcwx0GfRG5o2BfnHq9vPJMfZIYsumiphLREF4z4rZFKPG3NSAtVF%2BhWmpHrE4VNmgi7lViH16wCminB80aDw5o3INDljwAlNOMFTBojOs3SNUAFTOvFIB7YzgSjXK6%2B4i%2BCFktiAj%2Fq0xmRMl2C%2BxgTZvKllu%2F23Hxv21nJmH%2FE26DgGWf5geCWUUirIa3mzoRS8axJ2n3pmWTNkJyeA%2B26NEzjppLOP2DNazXeJV1oj%2FlZvQC46FfZVcRuEcy%2BmzV2PXWCCwhwNblLD92ej0mhJ4SxW7wvLCLf9tZI0bndkFgqyXBipj1O1%2FCw5SdfvpuXV7O3uDPHRr%2FGs9Q3adTxLU4cIv83Zh7BcglsCjBRPuX%2Bz97ie8LpzIZ6J%2BY7CHm5q7F4LBXHe4dAj6e11c6f%2F2Uc93pzktPK17ByZMNJIp8cBinLEfeSilEQt%2BhYe7HwEQEHUo%2BrwVia27mXX0UXJaVOcOc9M6GJCOOQE9As%2B8yPyL2KPAA6SUgW%2FBXDmGs5c2cWhAD%2FQ%2FaeBQMWGWCUllzC0k7K5BjqkAQ0q6kSX2jKM16O8%2F%2BNOe6qTRCvFDsRZPkjTd%2BUVpcuTI9vWeClvxJ7SE22mHczqe6RgC3YjxEyKx84nuD4wkxPFGy5xXrCj0gCrEGdiWrUVev9fg8AFWbwTtpHi7Ayyb%2BC9WvWCk0vdZX1rayJvxk9vSrVgEwbq%2BY%2BPpfPOYNuYvIBQ4cDF3qRdq0ZsLq3aRQRGjGAOFaQ03qc1%2FWGYnTlP%2Bwtw&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=f58aa2d31b685b7029957fdc06df649548e1d663cba55d41ed600f74db93b233"
      },
      {
        "description": "shareholding_structure",
        "document_id": "doc_csmd674a2n8o3aq6rgig",
        "file_name": "kyb_doc65561_7November2024_Cypress.png",
        "sub_type": "other",
        "tag": "beneficialOwnershipDoc",
        "type": "business",
        "updated_at": "2024-11-07T14:47:56.513671Z",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc65561_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS7DUAJFTI%2F20241107%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241107T144757Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjELr%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkgwRgIhAIgTlC3AOWsaADMmzchljlrOMllo%2FhRoEwjlUHzOnF7JAiEAwy5K8fEO26dMGTpYBs5iNp6QWwmtKhLsdvk7LnVuDUQq9AMIQxABGgwyODg0MTczNzMwOTMiDIQf9yK2jaNpDfEG4irRA1wEoBslTAYu4MANL6fStwrkzON98A8GZQRd1BIg%2B9qed%2Bo6vaYwcjv97M1VpPTmFpEJRHpC%2Bj1F17ajhtmOAcwx0GfRG5o2BfnHq9vPJMfZIYsumiphLREF4z4rZFKPG3NSAtVF%2BhWmpHrE4VNmgi7lViH16wCminB80aDw5o3INDljwAlNOMFTBojOs3SNUAFTOvFIB7YzgSjXK6%2B4i%2BCFktiAj%2Fq0xmRMl2C%2BxgTZvKllu%2F23Hxv21nJmH%2FE26DgGWf5geCWUUirIa3mzoRS8axJ2n3pmWTNkJyeA%2B26NEzjppLOP2DNazXeJV1oj%2FlZvQC46FfZVcRuEcy%2BmzV2PXWCCwhwNblLD92ej0mhJ4SxW7wvLCLf9tZI0bndkFgqyXBipj1O1%2FCw5SdfvpuXV7O3uDPHRr%2FGs9Q3adTxLU4cIv83Zh7BcglsCjBRPuX%2Bz97ie8LpzIZ6J%2BY7CHm5q7F4LBXHe4dAj6e11c6f%2F2Uc93pzktPK17ByZMNJIp8cBinLEfeSilEQt%2BhYe7HwEQEHUo%2BrwVia27mXX0UXJaVOcOc9M6GJCOOQE9As%2B8yPyL2KPAA6SUgW%2FBXDmGs5c2cWhAD%2FQ%2FaeBQMWGWCUllzC0k7K5BjqkAQ0q6kSX2jKM16O8%2F%2BNOe6qTRCvFDsRZPkjTd%2BUVpcuTI9vWeClvxJ7SE22mHczqe6RgC3YjxEyKx84nuD4wkxPFGy5xXrCj0gCrEGdiWrUVev9fg8AFWbwTtpHi7Ayyb%2BC9WvWCk0vdZX1rayJvxk9vSrVgEwbq%2BY%2BPpfPOYNuYvIBQ4cDF3qRdq0ZsLq3aRQRGjGAOFaQ03qc1%2FWGYnTlP%2Bwtw&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=91e0ae8aed2fd0c18c17495fec5ea0acdca87a0d0b298f0c20a148305405c6da"
      }
    ],
    "email": "",
    "id": "ent_csmd6741kl1roj57ereg",
    "metadata": null,
    "name": "New Business 3",
    "object": "entity",
    "operating_address": {
      "city": "Address City",
      "country": "SG",
      "line1": "Address line1",
      "line2": "Address line2",
      "postal_code": "75918",
      "state": "Address State"
    },
    "pending_documents": [],
    "phone": {
      "calling_code": "",
      "number": ""
    },
    "reference_id": "",
    "registration_address": {
      "city": "Address City",
      "country": "SG",
      "line1": "Address line1",
      "line2": "Address line2",
      "postal_code": "75918",
      "state": "Address State"
    },
    "registration_date": "",
    "registration_number": "RG001",
    "representatives": [
      {
        "address": null,
        "created_at": null,
        "date_of_birth": "10-08-1987",
        "documents": [
          {
            "description": "proof_of_identity",
            "document_id": "",
            "file_name": "Cypress.png",
            "sub_type": "national_id",
            "tag": "identityProofTypeFrontDoc",
            "type": "identity",
            "updated_at": null,
            "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
          },
          {
            "description": "proof_of_address",
            "document_id": "",
            "file_name": "Cypress.png",
            "sub_type": "drivers_license",
            "tag": "AddressProofDoc",
            "type": "address",
            "updated_at": null,
            "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
          }
        ],
        "first_name": "John",
        "last_name": "Doe",
        "nationality": "US",
        "ownership_percentage": 52.27,
        "person_id": "",
        "phone": null,
        "roles": [
          "shareholder"
        ],
        "updated_at": null
      },
      {
        "address": null,
        "created_at": null,
        "date_of_birth": "05-03-1989",
        "documents": [
          {
            "description": "proof_of_identity",
            "document_id": "",
            "file_name": "Cypress.png",
            "sub_type": "national_id",
            "tag": "identityProofTypeFrontDoc",
            "type": "identity",
            "updated_at": null,
            "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
          },
          {
            "description": "proof_of_address",
            "document_id": "",
            "file_name": "Cypress.png",
            "sub_type": "drivers_license",
            "tag": "AddressProofDoc",
            "type": "address",
            "updated_at": null,
            "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
          }
        ],
        "first_name": "Alice",
        "last_name": "Doe",
        "nationality": "US",
        "ownership_percentage": 23.22,
        "person_id": "",
        "phone": null,
        "roles": [
          "shareholder"
        ],
        "updated_at": null
      }
    ],
    "statement_descriptor": "",
    "submit": true,
    "submitted_at": "2024-11-07T14:47:56.506606403Z",
    "tax_id": "",
    "type": "company",
    "vertical": "Ecommerce-Dropshipping",
    "website": ""
  }
}
```

# Getting the sub-merchants approved

The approval process can range from 3-5 business days to a few weeks depending on the completeness of documents, verification requirements and complexity of the entity’s business. During this time, you will receive email notifications from Tazapay’s compliance for additional requirements.

### Providing additional information using the dashboard

You can refer to [this guide](https://support.tazapay.com/what-is-the-process-for-approving-a-sub-entity) to provide additional requirements which may be required during the approval process.

### Providing additional information using API

* During the approval process, Tazapay’s compliance may request you for additional information / documents. In such cases, the approval\_status of the entity will move to `requires_action` and you will receive a corresponding webhook event.\
  *Refer to this for the payload of the webhook event.*
* The `pending_documents` key in the entity object will contain the list of pending documents.

Sample Webhook Payload

```json
{
  "type": "entity.approval_requires_action",
  "id": "evt_ct9e2dad75jtea8fbkl0",
  "object": "event",
  "created_at": "2024-12-06T11:34:13.288875131Z",
  "data": {
    "email": "",
    "submitted_at": "2024-11-07T14:47:56.545548Z",
    "created_at": "2024-11-07T14:47:56.506606Z",
    "operating_address": {
      "line1": "Address line1",
      "line2": "Address line2",
      "postal_code": "75918",
      "city": "Address City",
      "state": "Address State",
      "country": "SG"
    },
    "registration_address": {
      "line1": "Address line1",
      "line2": "Address line2",
      "postal_code": "75918",
      "city": "Address City",
      "state": "Address State",
      "country": "SG"
    },
    "object": "entity",
    "approval_status": "requires_action",
    "name": "New Business 3",
    "vertical": "Ecommerce-AgriProducts-Florists and Novelty Products",
    "registration_number": "RG001",
    "id": "ent_csmd6741kl1roj57ereg",
    "type": "company",
    "representatives": [
      {
        "address": {},
        "phone": {},
        "created_at": "2024-11-07T14:47:56.513671Z",
        "updated_at": "2024-11-07T14:47:56.513671Z",
        "first_name": "John",
        "last_name": "Doe",
        "date_of_birth": "10-08-1987",
        "nationality": "US",
        "person_id": "psn_csmd674a2n8o3aq6rgjg",
        "roles": [
          "shareholder"
        ],
        "documents": [
          {
            "updated_at": "2024-11-07T14:47:56.513671Z",
            "document_id": "doc_csmd674a2n8o3aq6rgkg",
            "type": "address",
            "sub_type": "drivers_license",
            "file_name": "kyb_doc52904_7November2024_Cypress.png",
            "description": "proof_of_address",
            "tag": "AddressProofDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc52904_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2YNDBDLG%2F20241206%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241206T113413Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEHEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhAM7UJg0ZZPkYjZ58cZL0uiaKExs4sv3%2FE4FXEOsm94sSAiB57T6IJqx143NF9mK8UYtSS%2FvpXBj54%2Fo%2FznSxP7jYGir0AwgqEAEaDDI4ODQxNzM3MzA5MyIMnzBeF8rGkG0L8IpsKtEDSKNRLV4xNkA%2B%2FDBvtsWAD7ojx4vkwFYtaFlJjyjEOBslXDcQPO%2BJkbou%2F4EKtnGzf1wFYefaV6qrgBHdz7oFTBO61Wlen8oI3hrJJ1YYjf5UhHO5hMgKSmaK%2BYIy9sfkgExeJZKVwB%2Bn1jB5x8%2FkIwkPED8u5D8bbJXM4k%2FlR1EUd9530fCkDOhOcSedNJkeNXsTKTaeS7lS75WBi9sgct92VgRi0NZodT0VPLOuGFBz2NIZW0myvwzXecCu6305S2s1H7%2F75Lm2xQJKbPxnC8jwYXbGs6SiRnI0jmBiCsRs78Yj%2FPSigwNWBt%2BALmHKUIU8zEbaoY3psWwUVyd4q%2F9x08jsjGh9Q9T17bkAY7pPtmrMoJ0IABLXmEXIJKpvcpBxBgT%2FtRZH6PTg3LB6XgFBWAJFeoM%2B01LTjX%2BLdfWNu5yvTKHxLXcsnZqG2BIKXaIDs7Mf4QIdmpXRmiVn93EuTM2d0MAtjdYet9MgPKjVrIYlcWyJxRoAwH4nEy%2FlgxVixSZhxA4xsGc305xSAi%2F369JdCZO7c0Bf19AGM3BbSWXUVgGHOghfy1WiwhIK%2B%2B8Oj%2BeAROZYC35wUIb0ciu8nwhyAuXtDUfRnTkUeb6HMP77yroGOqUBcU9Y2WkT9yHVRj0fEt2LjqUBUNXxLHmEabGzwrBY9yNxczktEK3VU7b5SCPeKjucdxAw7eArg9W8NqNIoJuHfdDZuQDZGyQ0ATkYd4VcGo6jlMe8mzQjynSFGLHMMUCnnTIEzQWymk4E7H1hVFLQcu%2FUDwIvm1%2Fg16uwLQNTQK%2Fibqzgg0KirQxunkUWywvMU0GJ9wxIhLmI0%2BAXnnXheEq5BcEF&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=bdbe8fd6789196c3f07ac70b7ac9ecafbfae12087db7f347d7bf4a90f6678a79"
          },
          {
            "updated_at": "2024-11-07T14:47:56.513671Z",
            "document_id": "doc_csmd674a2n8o3aq6rgk0",
            "type": "identity",
            "sub_type": "national_id",
            "file_name": "kyb_doc38835_7November2024_Cypress.png",
            "description": "proof_of_identity",
            "tag": "identityProofTypeFrontDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc38835_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2YNDBDLG%2F20241206%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241206T113413Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEHEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhAM7UJg0ZZPkYjZ58cZL0uiaKExs4sv3%2FE4FXEOsm94sSAiB57T6IJqx143NF9mK8UYtSS%2FvpXBj54%2Fo%2FznSxP7jYGir0AwgqEAEaDDI4ODQxNzM3MzA5MyIMnzBeF8rGkG0L8IpsKtEDSKNRLV4xNkA%2B%2FDBvtsWAD7ojx4vkwFYtaFlJjyjEOBslXDcQPO%2BJkbou%2F4EKtnGzf1wFYefaV6qrgBHdz7oFTBO61Wlen8oI3hrJJ1YYjf5UhHO5hMgKSmaK%2BYIy9sfkgExeJZKVwB%2Bn1jB5x8%2FkIwkPED8u5D8bbJXM4k%2FlR1EUd9530fCkDOhOcSedNJkeNXsTKTaeS7lS75WBi9sgct92VgRi0NZodT0VPLOuGFBz2NIZW0myvwzXecCu6305S2s1H7%2F75Lm2xQJKbPxnC8jwYXbGs6SiRnI0jmBiCsRs78Yj%2FPSigwNWBt%2BALmHKUIU8zEbaoY3psWwUVyd4q%2F9x08jsjGh9Q9T17bkAY7pPtmrMoJ0IABLXmEXIJKpvcpBxBgT%2FtRZH6PTg3LB6XgFBWAJFeoM%2B01LTjX%2BLdfWNu5yvTKHxLXcsnZqG2BIKXaIDs7Mf4QIdmpXRmiVn93EuTM2d0MAtjdYet9MgPKjVrIYlcWyJxRoAwH4nEy%2FlgxVixSZhxA4xsGc305xSAi%2F369JdCZO7c0Bf19AGM3BbSWXUVgGHOghfy1WiwhIK%2B%2B8Oj%2BeAROZYC35wUIb0ciu8nwhyAuXtDUfRnTkUeb6HMP77yroGOqUBcU9Y2WkT9yHVRj0fEt2LjqUBUNXxLHmEabGzwrBY9yNxczktEK3VU7b5SCPeKjucdxAw7eArg9W8NqNIoJuHfdDZuQDZGyQ0ATkYd4VcGo6jlMe8mzQjynSFGLHMMUCnnTIEzQWymk4E7H1hVFLQcu%2FUDwIvm1%2Fg16uwLQNTQK%2Fibqzgg0KirQxunkUWywvMU0GJ9wxIhLmI0%2BAXnnXheEq5BcEF&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=b013fbad7eb8fa0290f0a9dd24d073a0f4a0d0daea1fa1abfa6398caa69ed3ac"
          }
        ],
        "ownership_percentage": 52.27
      },
      {
        "address": {},
        "phone": {},
        "created_at": "2024-11-07T14:47:56.513671Z",
        "updated_at": "2024-11-07T14:47:56.513671Z",
        "first_name": "Alice",
        "last_name": "Doe",
        "date_of_birth": "05-03-1989",
        "nationality": "US",
        "person_id": "psn_csmd674a2n8o3aq6rglg",
        "roles": [
          "shareholder"
        ],
        "documents": [
          {
            "updated_at": "2024-11-07T14:47:56.513671Z",
            "document_id": "doc_csmd674a2n8o3aq6rgm0",
            "type": "identity",
            "sub_type": "national_id",
            "file_name": "kyb_doc70953_7November2024_Cypress.png",
            "description": "proof_of_identity",
            "tag": "identityProofTypeFrontDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc70953_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2YNDBDLG%2F20241206%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241206T113413Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEHEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhAM7UJg0ZZPkYjZ58cZL0uiaKExs4sv3%2FE4FXEOsm94sSAiB57T6IJqx143NF9mK8UYtSS%2FvpXBj54%2Fo%2FznSxP7jYGir0AwgqEAEaDDI4ODQxNzM3MzA5MyIMnzBeF8rGkG0L8IpsKtEDSKNRLV4xNkA%2B%2FDBvtsWAD7ojx4vkwFYtaFlJjyjEOBslXDcQPO%2BJkbou%2F4EKtnGzf1wFYefaV6qrgBHdz7oFTBO61Wlen8oI3hrJJ1YYjf5UhHO5hMgKSmaK%2BYIy9sfkgExeJZKVwB%2Bn1jB5x8%2FkIwkPED8u5D8bbJXM4k%2FlR1EUd9530fCkDOhOcSedNJkeNXsTKTaeS7lS75WBi9sgct92VgRi0NZodT0VPLOuGFBz2NIZW0myvwzXecCu6305S2s1H7%2F75Lm2xQJKbPxnC8jwYXbGs6SiRnI0jmBiCsRs78Yj%2FPSigwNWBt%2BALmHKUIU8zEbaoY3psWwUVyd4q%2F9x08jsjGh9Q9T17bkAY7pPtmrMoJ0IABLXmEXIJKpvcpBxBgT%2FtRZH6PTg3LB6XgFBWAJFeoM%2B01LTjX%2BLdfWNu5yvTKHxLXcsnZqG2BIKXaIDs7Mf4QIdmpXRmiVn93EuTM2d0MAtjdYet9MgPKjVrIYlcWyJxRoAwH4nEy%2FlgxVixSZhxA4xsGc305xSAi%2F369JdCZO7c0Bf19AGM3BbSWXUVgGHOghfy1WiwhIK%2B%2B8Oj%2BeAROZYC35wUIb0ciu8nwhyAuXtDUfRnTkUeb6HMP77yroGOqUBcU9Y2WkT9yHVRj0fEt2LjqUBUNXxLHmEabGzwrBY9yNxczktEK3VU7b5SCPeKjucdxAw7eArg9W8NqNIoJuHfdDZuQDZGyQ0ATkYd4VcGo6jlMe8mzQjynSFGLHMMUCnnTIEzQWymk4E7H1hVFLQcu%2FUDwIvm1%2Fg16uwLQNTQK%2Fibqzgg0KirQxunkUWywvMU0GJ9wxIhLmI0%2BAXnnXheEq5BcEF&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=9a04acef75ac1916754817d0c8ee1360b412e5f6be7f9190ce170ae05c771b10"
          },
          {
            "updated_at": "2024-11-07T14:47:56.513671Z",
            "document_id": "doc_csmd674a2n8o3aq6rgmg",
            "type": "address",
            "sub_type": "drivers_license",
            "file_name": "kyb_doc27474_7November2024_Cypress.png",
            "description": "proof_of_address",
            "tag": "AddressProofDoc",
            "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc27474_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2YNDBDLG%2F20241206%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241206T113413Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEHEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhAM7UJg0ZZPkYjZ58cZL0uiaKExs4sv3%2FE4FXEOsm94sSAiB57T6IJqx143NF9mK8UYtSS%2FvpXBj54%2Fo%2FznSxP7jYGir0AwgqEAEaDDI4ODQxNzM3MzA5MyIMnzBeF8rGkG0L8IpsKtEDSKNRLV4xNkA%2B%2FDBvtsWAD7ojx4vkwFYtaFlJjyjEOBslXDcQPO%2BJkbou%2F4EKtnGzf1wFYefaV6qrgBHdz7oFTBO61Wlen8oI3hrJJ1YYjf5UhHO5hMgKSmaK%2BYIy9sfkgExeJZKVwB%2Bn1jB5x8%2FkIwkPED8u5D8bbJXM4k%2FlR1EUd9530fCkDOhOcSedNJkeNXsTKTaeS7lS75WBi9sgct92VgRi0NZodT0VPLOuGFBz2NIZW0myvwzXecCu6305S2s1H7%2F75Lm2xQJKbPxnC8jwYXbGs6SiRnI0jmBiCsRs78Yj%2FPSigwNWBt%2BALmHKUIU8zEbaoY3psWwUVyd4q%2F9x08jsjGh9Q9T17bkAY7pPtmrMoJ0IABLXmEXIJKpvcpBxBgT%2FtRZH6PTg3LB6XgFBWAJFeoM%2B01LTjX%2BLdfWNu5yvTKHxLXcsnZqG2BIKXaIDs7Mf4QIdmpXRmiVn93EuTM2d0MAtjdYet9MgPKjVrIYlcWyJxRoAwH4nEy%2FlgxVixSZhxA4xsGc305xSAi%2F369JdCZO7c0Bf19AGM3BbSWXUVgGHOghfy1WiwhIK%2B%2B8Oj%2BeAROZYC35wUIb0ciu8nwhyAuXtDUfRnTkUeb6HMP77yroGOqUBcU9Y2WkT9yHVRj0fEt2LjqUBUNXxLHmEabGzwrBY9yNxczktEK3VU7b5SCPeKjucdxAw7eArg9W8NqNIoJuHfdDZuQDZGyQ0ATkYd4VcGo6jlMe8mzQjynSFGLHMMUCnnTIEzQWymk4E7H1hVFLQcu%2FUDwIvm1%2Fg16uwLQNTQK%2Fibqzgg0KirQxunkUWywvMU0GJ9wxIhLmI0%2BAXnnXheEq5BcEF&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=97959f78ff22fcd04039e377fcb19c8e60d58225261b24d786ef78f58b8d38c0"
          }
        ],
        "ownership_percentage": 23.22
      }
    ],
    "documents": [
      {
        "updated_at": "2024-11-07T14:47:56.513671Z",
        "document_id": "doc_csmd674a2n8o3aq6rgig",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc65561_7November2024_Cypress.png",
        "description": "shareholding_structure",
        "tag": "beneficialOwnershipDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc65561_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2YNDBDLG%2F20241206%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241206T113413Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEHEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhAM7UJg0ZZPkYjZ58cZL0uiaKExs4sv3%2FE4FXEOsm94sSAiB57T6IJqx143NF9mK8UYtSS%2FvpXBj54%2Fo%2FznSxP7jYGir0AwgqEAEaDDI4ODQxNzM3MzA5MyIMnzBeF8rGkG0L8IpsKtEDSKNRLV4xNkA%2B%2FDBvtsWAD7ojx4vkwFYtaFlJjyjEOBslXDcQPO%2BJkbou%2F4EKtnGzf1wFYefaV6qrgBHdz7oFTBO61Wlen8oI3hrJJ1YYjf5UhHO5hMgKSmaK%2BYIy9sfkgExeJZKVwB%2Bn1jB5x8%2FkIwkPED8u5D8bbJXM4k%2FlR1EUd9530fCkDOhOcSedNJkeNXsTKTaeS7lS75WBi9sgct92VgRi0NZodT0VPLOuGFBz2NIZW0myvwzXecCu6305S2s1H7%2F75Lm2xQJKbPxnC8jwYXbGs6SiRnI0jmBiCsRs78Yj%2FPSigwNWBt%2BALmHKUIU8zEbaoY3psWwUVyd4q%2F9x08jsjGh9Q9T17bkAY7pPtmrMoJ0IABLXmEXIJKpvcpBxBgT%2FtRZH6PTg3LB6XgFBWAJFeoM%2B01LTjX%2BLdfWNu5yvTKHxLXcsnZqG2BIKXaIDs7Mf4QIdmpXRmiVn93EuTM2d0MAtjdYet9MgPKjVrIYlcWyJxRoAwH4nEy%2FlgxVixSZhxA4xsGc305xSAi%2F369JdCZO7c0Bf19AGM3BbSWXUVgGHOghfy1WiwhIK%2B%2B8Oj%2BeAROZYC35wUIb0ciu8nwhyAuXtDUfRnTkUeb6HMP77yroGOqUBcU9Y2WkT9yHVRj0fEt2LjqUBUNXxLHmEabGzwrBY9yNxczktEK3VU7b5SCPeKjucdxAw7eArg9W8NqNIoJuHfdDZuQDZGyQ0ATkYd4VcGo6jlMe8mzQjynSFGLHMMUCnnTIEzQWymk4E7H1hVFLQcu%2FUDwIvm1%2Fg16uwLQNTQK%2Fibqzgg0KirQxunkUWywvMU0GJ9wxIhLmI0%2BAXnnXheEq5BcEF&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=ac04ee3fa48e1c7d945ae03cfaca3e1f977b6649bc081a60ac164e8578ffacd1"
      },
      {
        "updated_at": "2024-11-07T14:47:56.513671Z",
        "document_id": "doc_csmd674a2n8o3aq6rgi0",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc85048_7November2024_Cypress.png",
        "description": "operating_address_proof",
        "tag": "AddressProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc85048_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2YNDBDLG%2F20241206%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241206T113413Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEHEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhAM7UJg0ZZPkYjZ58cZL0uiaKExs4sv3%2FE4FXEOsm94sSAiB57T6IJqx143NF9mK8UYtSS%2FvpXBj54%2Fo%2FznSxP7jYGir0AwgqEAEaDDI4ODQxNzM3MzA5MyIMnzBeF8rGkG0L8IpsKtEDSKNRLV4xNkA%2B%2FDBvtsWAD7ojx4vkwFYtaFlJjyjEOBslXDcQPO%2BJkbou%2F4EKtnGzf1wFYefaV6qrgBHdz7oFTBO61Wlen8oI3hrJJ1YYjf5UhHO5hMgKSmaK%2BYIy9sfkgExeJZKVwB%2Bn1jB5x8%2FkIwkPED8u5D8bbJXM4k%2FlR1EUd9530fCkDOhOcSedNJkeNXsTKTaeS7lS75WBi9sgct92VgRi0NZodT0VPLOuGFBz2NIZW0myvwzXecCu6305S2s1H7%2F75Lm2xQJKbPxnC8jwYXbGs6SiRnI0jmBiCsRs78Yj%2FPSigwNWBt%2BALmHKUIU8zEbaoY3psWwUVyd4q%2F9x08jsjGh9Q9T17bkAY7pPtmrMoJ0IABLXmEXIJKpvcpBxBgT%2FtRZH6PTg3LB6XgFBWAJFeoM%2B01LTjX%2BLdfWNu5yvTKHxLXcsnZqG2BIKXaIDs7Mf4QIdmpXRmiVn93EuTM2d0MAtjdYet9MgPKjVrIYlcWyJxRoAwH4nEy%2FlgxVixSZhxA4xsGc305xSAi%2F369JdCZO7c0Bf19AGM3BbSWXUVgGHOghfy1WiwhIK%2B%2B8Oj%2BeAROZYC35wUIb0ciu8nwhyAuXtDUfRnTkUeb6HMP77yroGOqUBcU9Y2WkT9yHVRj0fEt2LjqUBUNXxLHmEabGzwrBY9yNxczktEK3VU7b5SCPeKjucdxAw7eArg9W8NqNIoJuHfdDZuQDZGyQ0ATkYd4VcGo6jlMe8mzQjynSFGLHMMUCnnTIEzQWymk4E7H1hVFLQcu%2FUDwIvm1%2Fg16uwLQNTQK%2Fibqzgg0KirQxunkUWywvMU0GJ9wxIhLmI0%2BAXnnXheEq5BcEF&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=e237f0ac8e13b556d21d02aae0c1920f45f7f7da120b005e4249fda7bc5c409f"
      },
      {
        "updated_at": "2024-11-07T14:47:56.513671Z",
        "document_id": "doc_csmd674a2n8o3aq6rghg",
        "type": "business",
        "sub_type": "other",
        "file_name": "kyb_doc29163_7November2024_Cypress.png",
        "description": "business_registration_proof",
        "tag": "registrationProofDoc",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_csmd674a2n8o3aq6rgf0/kyb_doc29163_7November2024_Cypress.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2YNDBDLG%2F20241206%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20241206T113413Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEHEaDmFwLXNvdXRoZWFzdC0xIkcwRQIhAM7UJg0ZZPkYjZ58cZL0uiaKExs4sv3%2FE4FXEOsm94sSAiB57T6IJqx143NF9mK8UYtSS%2FvpXBj54%2Fo%2FznSxP7jYGir0AwgqEAEaDDI4ODQxNzM3MzA5MyIMnzBeF8rGkG0L8IpsKtEDSKNRLV4xNkA%2B%2FDBvtsWAD7ojx4vkwFYtaFlJjyjEOBslXDcQPO%2BJkbou%2F4EKtnGzf1wFYefaV6qrgBHdz7oFTBO61Wlen8oI3hrJJ1YYjf5UhHO5hMgKSmaK%2BYIy9sfkgExeJZKVwB%2Bn1jB5x8%2FkIwkPED8u5D8bbJXM4k%2FlR1EUd9530fCkDOhOcSedNJkeNXsTKTaeS7lS75WBi9sgct92VgRi0NZodT0VPLOuGFBz2NIZW0myvwzXecCu6305S2s1H7%2F75Lm2xQJKbPxnC8jwYXbGs6SiRnI0jmBiCsRs78Yj%2FPSigwNWBt%2BALmHKUIU8zEbaoY3psWwUVyd4q%2F9x08jsjGh9Q9T17bkAY7pPtmrMoJ0IABLXmEXIJKpvcpBxBgT%2FtRZH6PTg3LB6XgFBWAJFeoM%2B01LTjX%2BLdfWNu5yvTKHxLXcsnZqG2BIKXaIDs7Mf4QIdmpXRmiVn93EuTM2d0MAtjdYet9MgPKjVrIYlcWyJxRoAwH4nEy%2FlgxVixSZhxA4xsGc305xSAi%2F369JdCZO7c0Bf19AGM3BbSWXUVgGHOghfy1WiwhIK%2B%2B8Oj%2BeAROZYC35wUIb0ciu8nwhyAuXtDUfRnTkUeb6HMP77yroGOqUBcU9Y2WkT9yHVRj0fEt2LjqUBUNXxLHmEabGzwrBY9yNxczktEK3VU7b5SCPeKjucdxAw7eArg9W8NqNIoJuHfdDZuQDZGyQ0ATkYd4VcGo6jlMe8mzQjynSFGLHMMUCnnTIEzQWymk4E7H1hVFLQcu%2FUDwIvm1%2Fg16uwLQNTQK%2Fibqzgg0KirQxunkUWywvMU0GJ9wxIhLmI0%2BAXnnXheEq5BcEF&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=83a011520ebf93007361d35151ad4208d0c36c2df89005b61383bcae054683f6"
      }
    ],
    "pending_documents": [
      "Identification Proof for Mr. John Doe"
    ],
    "submit": true
  }
}
```

* Use the [Upload Document API](https://docs.tazapay.com/reference/upload-document) to submit pending documents for further review by Tazapay compliance team\
    Sample Request Body
  ```json
  curl --request POST \
    --url https://service.tazapay.com/v3/document \
    --header 'accept: application/json' \
    --header 'content-type: application/json' \
    --data '{
    "type": "Identification Proof for Mr. John Doe",
    "reference": "ent_csmd6741kl1roj57ereg",
    "url": "https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Ek8pqaB-WCjq5Qvty_0ulg.jpeg"
  }'
  ```
    Sample Response
  ```json
  {
    "status": "success",
    "message": "",
    "data": {
      "created_at": "2024-12-06T11:46:07.961758473Z",
      "description": "",
      "id": "doc_ct9e7vvvfes2ls2j64i0",
      "metadata": null,
      "name": "kyb_doc68226_6December2024",
      "object": "document",
      "reference": "ent_csmd6741kl1roj57ereg",
      "type": "Identification Proof for Mr. John Doe",
      "url": "https://s3.ap-southeast-1.amazonaws.com/f55c23015b"
    }
  }
  ```
* After submitting all the pending documents, the approval\_status of the entity will move to processing. In case further documents are required, you will receive a webhook and an email notification and the approval\_status of the entity will move to requires\_action.
* On successful approval, you will receive a webhook and the approval\_status of the entity will move to approved.\
  Refer here for the sample webhook structure.
* Once approved, you are ready to initiate payouts on behalf of the entity (sub-merchant).
* <br />

# Create Payouts on behalf of Entities

You can initiate payouts on behalf of entities (sub-merchants) either from the Tazapay dashboard or using the API.

### Creating Payouts on behalf of entities from the Tazapay dashboard

Refer to [this guide](https://support.tazapay.com/how-do-i-create-payouts-on-behalf-of) to create payout on behalf of entities from the dashboard.

### Creating Payouts on behalf of entities using API

* Use the on\_behalf\_of field in the payout API to create a payout on behalf of another entity. Pass the entity ID as the value of the on\_behalf\_of key while initiating a payout.
* Refer to [this detailed guide](https://docs.tazapay.com/docs/building-an-integration-payouts) on building a payout integration with Tazapay.
