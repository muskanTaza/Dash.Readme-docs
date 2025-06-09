---
title: Creating Payouts on behalf of Individuals
excerpt: >-
  This technical guide helps you build an integration for creating payouts on
  behalf of your individual customers
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
As a fintech / platform, you can effortlessly create multiple sub-entities on Tazapay for your customers all accessible from a single dashboard. You can then create payouts on behalf of these entities. This structure ensures transparency and compliance in the payment flow for all the stakeholders, while still empowering you to manage and direct payouts.

Here’s how you can integrate with Tazapay as a platform / fintech

1. Create your own account
2. Get your account approved
3. Create Entities corresponding to your customers using APIs / dashboard
4. Get the entities approved
5. Create Payouts on behalf of the entities

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

You can create entities on Tazapay corresponding to your customers either using the API or the dashboard

## Creating and submitting entity using the dashboard

Creating an entity and submitting the documents for verification from the dashboard is a straightforward process. You can refer to [this guide](https://support.tazapay.com/submitting-an-entity-for-approval) to learn creating an entity using the Tazapay dashboard.

## Creating an entity using API

### Step 1: Create an entity

Tazapay uses an entity object to represent an individual. The entity object also tracks the approval status as it changes from created to approved. 

Create an entity on your server with the name and type.

### Sample Request cURL

```bash
curl --request POST \
  --url https://service.tazapay.com/v3/entity \
  --header 'content-type: application/json' \
  --data '{
  "name":"John Doe",
  "type":"individual"
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
    "created_at": "2025-03-28T15:45:15.799594254Z",
    "description": "",
    "documents": [],
    "email": "",
    "id": "ent_cvjc82u8su5b6k0dqccg",
    "metadata": null,
    "name": "John Doe",
    "object": "entity",
    "onboarding_package_url": "",
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
    "purpose_of_use": [],
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
    "relationship": "",
    "representatives": [],
    "statement_descriptor": "",
    "submit": false,
    "submitted_at": null,
    "tax_id": "",
    "type": "individual",
    "vertical": "",
    "website": ""
  }
}
```

> `id` is the unique identifier representing the entity

### Step 2: Submit an entity

Submit an already created entity on your server using Tazapay’s [Submit Entity API](https://docs.tazapay.com/reference/submit-entity) with the `id` field from Step 1 and the following mandatory information:

1. Name
2. type - `individual`
3. email
4. registration\_address - This represents the address of the individual
5. relationship - `customer`
6. purpose\_of\_use - This can be collect or payout or both
7. Proof of Indentity
8. Proof of Address

### Sample Request cURL

```bash
curl --request POST \
  --url https://service.tazapay.com/v3/entity/ent_cvlru8b1d43oq387u9og/submit \
  --data '{
  "email": "john.doe@me.com",
  "registration_address": {
    "line1": "Address Line 1",
    "line2": "Address Line 2",
    "city": "City",
    "state": "State",
    "country": "SG",
    "postal_code": "10038"
  },
  "relationship": "customer",
  "purpose_of_use": [
    "payout"
  ],
  "documents": [
    {
      "type": "identity",
      "sub_type": "other",
      "tag": "passport",
      "file_name": "passport_document",
      "description": "This is front of the passport",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    },
    {
      "type": "address",
      "sub_type": "other",
      "tag": "AddressProofDoc",
      "file_name": "utility_bill",
      "description": "This is utility bill",
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
    "created_at": "2025-04-01T10:25:37.945712Z",
    "description": "",
    "documents": [
      {
        "description": "This is front of the passport",
        "document_id": "doc_cvlrvnf7lagqm79t8h2g",
        "file_name": "kyb_doc27381_1April2025_passport_document",
        "sub_type": "other",
        "tag": "passport",
        "type": "identity",
        "updated_at": "2025-04-01T10:28:45.856622Z",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_cvlru8f7lagqm79t8gl0/kyb_doc27381_1April2025_passport_document?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2MVW4YGP%2F20250401%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20250401T102846Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEFIaDmFwLXNvdXRoZWFzdC0xIkcwRQIgYZrxa5%2F%2BIJLyt6h%2BoBrp2M5qGrZZzWeCbamqpcgO%2B14CIQCq4uw16KIVo7ptVxtxGGrbH2OU2n%2F0i3KnzrHJt%2F2wkir9Awi7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM%2Bz3Ao%2B39OuHOZ80VKtEDMUtYaTzS%2BmWw8gvsPgxh%2F%2BgaGMHF8IPOYkuAG1BrLrweNa9blenMPW%2FHh4K5Uvaj1lczG4eCIfquZI1bT7D%2BPv7CGa2tqN6LPRbCPWYZl0f%2FhrwfxY3RR7kKwK19TZ13nCkbkI%2BHMY9pg81xQdyl9yzHt%2FSDcSXnDdjH4RKbNC8KVLQjyRgBLQF%2FkHgfXh3Y3NskWM2rhELJ7cJ%2FLjGUSZ8M7xhNRKWO78CqbAmNoMn2ohT40InofVoD2zrhIWCracGpyoYO3wt5ueIGozDo3%2FdxhN3YPcZmUZYTTn9D3sYXnPsiiy7oFZBTFbGnoLuWpCZDCTUYCNie%2BTdn7x5woKaRwlywOT3csBY1uJPDbv8F1eFKVYD5BtAXhxBpWXglkeMJzw78wBEXliTYasHhnGKcyZLtMu3H%2BBdPMx9dHB18u1OYz7%2BtcT9Whj8VEsPvgNIVrRloef6C4n6i0hZxx66AJNmQcew5g8%2BXw%2FBLGtcb07Ve4UngmQ0c4CjPCiJp4lVXYvb8E%2B3tV3ujVbbsbLPYNmxJ2wz1at6iv3280edrRkQGqF4yytqdId2LuBwxqDhstzfsUnVP72ohaDgL0yrtkKUdfauUkofM7gJHKuG%2FMMzrrr8GOqUBDVLWWW3T9AvmpvqS7TFqUr0cv2ltiKFhBzVrcv%2BxPh5%2FLRijqAov0FokNxtw67YmTFG7tUzIeI0CBgyEQ7wVm7ukhrMkGqGQG%2B2xCYT19mm4LFTwERh98A3LSqL1s3nemUG3f8%2BcJp7LEryGTYoUFsx4eTGEJ5ce5YZ4RDdfURdRr44VckOA3rREKm2ie3PkG59%2BT75MxM8tiOaQa9rN7TvIgeO3&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=1d4d17d88f9f51c0462086b8bcfce80888246628fecc0a28ff56651b10c67047"
      },
      {
        "description": "This is utility bill",
        "document_id": "doc_cvlrvnn7lagqm79t8h30",
        "file_name": "kyb_doc92390_1April2025_utility_bill",
        "sub_type": "other",
        "tag": "AddressProofDoc",
        "type": "address",
        "updated_at": "2025-04-01T10:28:45.856622Z",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_cvlru8f7lagqm79t8gl0/kyb_doc92390_1April2025_utility_bill?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2MVW4YGP%2F20250401%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20250401T102846Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEFIaDmFwLXNvdXRoZWFzdC0xIkcwRQIgYZrxa5%2F%2BIJLyt6h%2BoBrp2M5qGrZZzWeCbamqpcgO%2B14CIQCq4uw16KIVo7ptVxtxGGrbH2OU2n%2F0i3KnzrHJt%2F2wkir9Awi7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM%2Bz3Ao%2B39OuHOZ80VKtEDMUtYaTzS%2BmWw8gvsPgxh%2F%2BgaGMHF8IPOYkuAG1BrLrweNa9blenMPW%2FHh4K5Uvaj1lczG4eCIfquZI1bT7D%2BPv7CGa2tqN6LPRbCPWYZl0f%2FhrwfxY3RR7kKwK19TZ13nCkbkI%2BHMY9pg81xQdyl9yzHt%2FSDcSXnDdjH4RKbNC8KVLQjyRgBLQF%2FkHgfXh3Y3NskWM2rhELJ7cJ%2FLjGUSZ8M7xhNRKWO78CqbAmNoMn2ohT40InofVoD2zrhIWCracGpyoYO3wt5ueIGozDo3%2FdxhN3YPcZmUZYTTn9D3sYXnPsiiy7oFZBTFbGnoLuWpCZDCTUYCNie%2BTdn7x5woKaRwlywOT3csBY1uJPDbv8F1eFKVYD5BtAXhxBpWXglkeMJzw78wBEXliTYasHhnGKcyZLtMu3H%2BBdPMx9dHB18u1OYz7%2BtcT9Whj8VEsPvgNIVrRloef6C4n6i0hZxx66AJNmQcew5g8%2BXw%2FBLGtcb07Ve4UngmQ0c4CjPCiJp4lVXYvb8E%2B3tV3ujVbbsbLPYNmxJ2wz1at6iv3280edrRkQGqF4yytqdId2LuBwxqDhstzfsUnVP72ohaDgL0yrtkKUdfauUkofM7gJHKuG%2FMMzrrr8GOqUBDVLWWW3T9AvmpvqS7TFqUr0cv2ltiKFhBzVrcv%2BxPh5%2FLRijqAov0FokNxtw67YmTFG7tUzIeI0CBgyEQ7wVm7ukhrMkGqGQG%2B2xCYT19mm4LFTwERh98A3LSqL1s3nemUG3f8%2BcJp7LEryGTYoUFsx4eTGEJ5ce5YZ4RDdfURdRr44VckOA3rREKm2ie3PkG59%2BT75MxM8tiOaQa9rN7TvIgeO3&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=9b9a37bdfb86e0af89b73ae8d01ba4330e3621e310faf7fa6c41aa6a062880ec"
      }
    ],
    "email": "",
    "id": "ent_cvlru8b1d43oq387u9og",
    "metadata": {},
    "name": "John Doe",
    "object": "entity",
    "onboarding_package_url": "",
    "operating_address": null,
    "pending_documents": [],
    "phone": {
      "calling_code": "",
      "number": ""
    },
    "purpose_of_use": [],
    "reference_id": "",
    "registration_address": {
      "city": "City",
      "country": "SG",
      "line1": "Address Line 1",
      "line2": "Address Line 2",
      "postal_code": "10038",
      "state": "State"
    },
    "registration_date": "",
    "registration_number": "",
    "relationship": "",
    "representatives": [],
    "statement_descriptor": "",
    "submit": true,
    "submitted_at": "2025-04-01T10:28:46.226494152Z",
    "tax_id": "",
    "type": "individual",
    "vertical": "",
    "website": ""
  }
}
```

### Step 1A: Creating and submitting the entity in a single step

You can also create and submit an entity on your server in a single step using Tazapay’s [Create Entity API](https://docs.tazapay.com/reference/create-entity) by setting the submit flag as `true` and providing the following mandatory information:

1. Name
2. type - `individual`
3. email
4. registration\_address - This represents the address of the individual
5. relationship - `customer`
6. purpose\_of\_use - This can be collect or payout or both
7. Proof of Indentity
8. Proof of Address

### Request Body

```bash
curl --request POST \
  --url https://service.tazapay.com/v3/entity \
  --data '{
  "name":"Alice Evans",
  "type":"individual",
  "email": "alice.evans@me.com",
  "registration_address": {
    "line1": "Address Line 1",
    "line2": "Address Line 2",
    "city": "City",
    "state": "State",
    "country": "SG",
    "postal_code": "10038"
  },
  "relationship": "customer",
  "purpose_of_use": [
    "payout"
  ],
  "documents": [
    {
      "type": "identity",
      "sub_type": "other",
      "tag": "passport",
      "file_name": "passport_document",
      "description": "This is front of the passport",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    },
    {
      "type": "address",
      "sub_type": "other",
      "tag": "AddressProofDoc",
      "file_name": "utility_bill",
      "description": "This is utility bill",
      "url": "https://ecs7.tokopedia.net/img/cache/700/product-1/2017/9/27/5510391/5510391_9968635e-a6f4-446a-84d0-ff3a98a5d4a2.jpg"
    }
  ],
  "submit":true
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
    "created_at": "2025-04-01T10:33:10.042170388Z",
    "description": "",
    "documents": [
      {
        "description": "This is front of the passport",
        "document_id": "doc_cvls1pn7lagqm79t8hrg",
        "file_name": "kyb_doc52274_1April2025_passport_document",
        "sub_type": "other",
        "tag": "passport",
        "type": "identity",
        "updated_at": "2025-04-01T10:33:10.055488Z",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_cvls1pn7lagqm79t8hpg/kyb_doc52274_1April2025_passport_document?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2MVW4YGP%2F20250401%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20250401T103310Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEFIaDmFwLXNvdXRoZWFzdC0xIkcwRQIgYZrxa5%2F%2BIJLyt6h%2BoBrp2M5qGrZZzWeCbamqpcgO%2B14CIQCq4uw16KIVo7ptVxtxGGrbH2OU2n%2F0i3KnzrHJt%2F2wkir9Awi7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM%2Bz3Ao%2B39OuHOZ80VKtEDMUtYaTzS%2BmWw8gvsPgxh%2F%2BgaGMHF8IPOYkuAG1BrLrweNa9blenMPW%2FHh4K5Uvaj1lczG4eCIfquZI1bT7D%2BPv7CGa2tqN6LPRbCPWYZl0f%2FhrwfxY3RR7kKwK19TZ13nCkbkI%2BHMY9pg81xQdyl9yzHt%2FSDcSXnDdjH4RKbNC8KVLQjyRgBLQF%2FkHgfXh3Y3NskWM2rhELJ7cJ%2FLjGUSZ8M7xhNRKWO78CqbAmNoMn2ohT40InofVoD2zrhIWCracGpyoYO3wt5ueIGozDo3%2FdxhN3YPcZmUZYTTn9D3sYXnPsiiy7oFZBTFbGnoLuWpCZDCTUYCNie%2BTdn7x5woKaRwlywOT3csBY1uJPDbv8F1eFKVYD5BtAXhxBpWXglkeMJzw78wBEXliTYasHhnGKcyZLtMu3H%2BBdPMx9dHB18u1OYz7%2BtcT9Whj8VEsPvgNIVrRloef6C4n6i0hZxx66AJNmQcew5g8%2BXw%2FBLGtcb07Ve4UngmQ0c4CjPCiJp4lVXYvb8E%2B3tV3ujVbbsbLPYNmxJ2wz1at6iv3280edrRkQGqF4yytqdId2LuBwxqDhstzfsUnVP72ohaDgL0yrtkKUdfauUkofM7gJHKuG%2FMMzrrr8GOqUBDVLWWW3T9AvmpvqS7TFqUr0cv2ltiKFhBzVrcv%2BxPh5%2FLRijqAov0FokNxtw67YmTFG7tUzIeI0CBgyEQ7wVm7ukhrMkGqGQG%2B2xCYT19mm4LFTwERh98A3LSqL1s3nemUG3f8%2BcJp7LEryGTYoUFsx4eTGEJ5ce5YZ4RDdfURdRr44VckOA3rREKm2ie3PkG59%2BT75MxM8tiOaQa9rN7TvIgeO3&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=efa21f0d7a060fb2510ccecde7c6f3dea4be183f7e41764675683b6624653c2f"
      },
      {
        "description": "This is utility bill",
        "document_id": "doc_cvls1pn7lagqm79t8hs0",
        "file_name": "kyb_doc50719_1April2025_utility_bill",
        "sub_type": "other",
        "tag": "AddressProofDoc",
        "type": "address",
        "updated_at": "2025-04-01T10:33:10.055488Z",
        "url": "https://s3.ap-southeast-1.amazonaws.com/tazapay-onboarding-service/kyb_cvls1pn7lagqm79t8hpg/kyb_doc50719_1April2025_utility_bill?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAUGJYD3OS2MVW4YGP%2F20250401%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20250401T103310Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEFIaDmFwLXNvdXRoZWFzdC0xIkcwRQIgYZrxa5%2F%2BIJLyt6h%2BoBrp2M5qGrZZzWeCbamqpcgO%2B14CIQCq4uw16KIVo7ptVxtxGGrbH2OU2n%2F0i3KnzrHJt%2F2wkir9Awi7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAEaDDI4ODQxNzM3MzA5MyIM%2Bz3Ao%2B39OuHOZ80VKtEDMUtYaTzS%2BmWw8gvsPgxh%2F%2BgaGMHF8IPOYkuAG1BrLrweNa9blenMPW%2FHh4K5Uvaj1lczG4eCIfquZI1bT7D%2BPv7CGa2tqN6LPRbCPWYZl0f%2FhrwfxY3RR7kKwK19TZ13nCkbkI%2BHMY9pg81xQdyl9yzHt%2FSDcSXnDdjH4RKbNC8KVLQjyRgBLQF%2FkHgfXh3Y3NskWM2rhELJ7cJ%2FLjGUSZ8M7xhNRKWO78CqbAmNoMn2ohT40InofVoD2zrhIWCracGpyoYO3wt5ueIGozDo3%2FdxhN3YPcZmUZYTTn9D3sYXnPsiiy7oFZBTFbGnoLuWpCZDCTUYCNie%2BTdn7x5woKaRwlywOT3csBY1uJPDbv8F1eFKVYD5BtAXhxBpWXglkeMJzw78wBEXliTYasHhnGKcyZLtMu3H%2BBdPMx9dHB18u1OYz7%2BtcT9Whj8VEsPvgNIVrRloef6C4n6i0hZxx66AJNmQcew5g8%2BXw%2FBLGtcb07Ve4UngmQ0c4CjPCiJp4lVXYvb8E%2B3tV3ujVbbsbLPYNmxJ2wz1at6iv3280edrRkQGqF4yytqdId2LuBwxqDhstzfsUnVP72ohaDgL0yrtkKUdfauUkofM7gJHKuG%2FMMzrrr8GOqUBDVLWWW3T9AvmpvqS7TFqUr0cv2ltiKFhBzVrcv%2BxPh5%2FLRijqAov0FokNxtw67YmTFG7tUzIeI0CBgyEQ7wVm7ukhrMkGqGQG%2B2xCYT19mm4LFTwERh98A3LSqL1s3nemUG3f8%2BcJp7LEryGTYoUFsx4eTGEJ5ce5YZ4RDdfURdRr44VckOA3rREKm2ie3PkG59%2BT75MxM8tiOaQa9rN7TvIgeO3&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B&response-content-type=image%2Fjpeg&x-id=GetObject&X-Amz-Signature=c7b23cd1d828d9056097fbf63ba13086d13b84b1ee060fda30096dc210d41982"
      }
    ],
    "email": "alice.evans@me.com",
    "id": "ent_cvls1pj1d43oq387uf3g",
    "metadata": null,
    "name": "Alice Evans",
    "object": "entity",
    "onboarding_package_url": "",
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
    "purpose_of_use": [
      "payout"
    ],
    "reference_id": "",
    "registration_address": {
      "city": "City",
      "country": "SG",
      "line1": "Address Line 1",
      "line2": "Address Line 2",
      "postal_code": "10038",
      "state": "State"
    },
    "registration_date": "",
    "registration_number": "",
    "relationship": "customer",
    "representatives": [],
    "statement_descriptor": "",
    "submit": true,
    "submitted_at": "2025-04-01T10:33:10.042170462Z",
    "tax_id": "",
    "type": "individual",
    "vertical": "",
    "website": ""
  }
}
```

# Getting the individuals approved

The approval process can range from 3-5 business days to a few weeks depending on the completeness of documents and verification requirements. During this time, you will receive email notifications from Tazapay’s compliance for additional requirements.

### Providing additional information using the dashboard

You can refer to [this guide](https://support.tazapay.com/what-is-the-process-for-approving-a-sub-entity) to provide additional requirements which may be required during the approval process.

### Providing additional information using API

* During the approval process, Tazapay’s compliance may request you for additional information / documents. In such cases, the approval\_status of the entity will move to `requires_action` and you will receive a corresponding webhook event.
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

# Create Payouts on behalf of Entities

You can initiate payouts on behalf of entities (individuals) either from the Tazapay dashboard or using the API.

### Creating Payouts on behalf of entities from the Tazapay dashboard

Refer to [this guide](https://support.tazapay.com/how-do-i-create-payouts-on-behalf-of) to create payout on behalf of entities from the dashboard.

### Creating Payouts on behalf of entities using API

* Use the on\_behalf\_of field in the payout API to create a payout on behalf of another entity. Pass the entity ID as the value of the on\_behalf\_of key while initiating a payout.
* Refer to [this detailed guide](https://docs.tazapay.com/docs/building-an-integration-payouts) on building a payout integration with Tazapay.
