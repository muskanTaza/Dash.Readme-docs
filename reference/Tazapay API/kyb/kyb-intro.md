---
title: Introduction to KYB
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Know Your Business or simply KYB is an extension of KYC laws implemented to reduce money laundering. KYB is a set of practices to verify a business. It includes verification of registration credentials, location, the UBOs (Ultimate Beneficial Owners) of that business, etc.

Tazapay is required to collect and verify end customer information before completing transactions. For sellers, KYB must be done anytime before the release of payment to the seller.

KYB's are only done once. To check if a user has their KYB completed, you can call the <a href = "https://tazapay-api-developer.readme.io/reference/kyb-status-api" target="_blank">GET KYB Status API.</a>

**For a business entity,** we require:

* Business Name
* Country
* Address Proof
* Incorporation Document
* Details of Representatives, Directors and Ultimate beneficial owners (UBOs)

**For Representatives/Owners (>25% shareholding)  of a business entity**, we require:

* First Name
* Last Name
* Role in the business
* Residence Country
* Proof of Identity
* Proof of Address
* Ownership percent in the business

> For businesses where no-one owns more than 25% of the company, please upload a signed declaration that no-one owns more than 25% of the company.

```json KYB object
{
        "account_id": "78e2fde6-a3bb-410c-99b7-56773fea7da8",
        "application_id": "a01d242d-8860-4b67-9632-0ff51a1bb3c7",
        "application_state": "not_started",
        "entity_name": "Company",
        "application_type": "Business",
        "business": {
            "id": "f891cc0e-cfba-41c4-9e82-fdc702fd2564",
            "name": "api integration v2",
            "type": null,
            "same_operating_address": false,
            "incorporation_no": "GST-2344566",
            "address_line_1": "Block.1, abc",
            "address_line_2": "XYZ area",
            "city": "Chennai",
            "state": "TamilNadu",
            "country": "India",
            "zip_code": "600069",
            "entity_type": "",
            "entity_name": null,
            "trading_name": "",
            "category": null,
            "sub_category": "",
            "years_in_business": "",
            "annual_turnover": "",
            "website": "",
            "date_of_incorporation": null,
            "custom_attrs": {
                "transaction_id": "123"
            },
            "documents": [
                {
                    "id": "438433c9-4ea9-40f9-a389-bea3bcf8f0f9",
                    "proof_type": "Business",
                    "type": "Other",
                    "tag": "",
                    "url": "https://kyb-service-sandbox.s3.ap-southeast-1.amazonaws.com/20c749d6-9341-4aa5-a363-80d17c15ee40/busRegProof.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIA2WN5GPXZGDAL5QI4%2F20220412%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20220412T105709Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEJv%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgMijR7GhzcAt0i7MqNemWxsTIHF5itgSDjrQV28LeqtsCIQDq3vorgnc1GaoirojCD0JmyIc%2F%2F5WU2q1u6aUncn8ooCqwAghEEAEaDDczNTM3MzA2NTcxNCIMqJOo%2FnvVmqN8PRF%2FKo0CYhr87f8NjP4hauvRDJdAicvTlUrHRXdUE%2FrKSPvSeGcwySt87PpBT7DsR9zZEjOlYyNwrrcZcIgaePfWYTlA4vY7Z1IV0uP%2F942EPp6w%2BPDh4%2FTWlMZcd2Ea2QTtSraa4OyusNY5fCfhMUUFSGjgZlosKDIVPSvkNBVFiRGFsuSTi9t7j8qZVKQ7pR1UcPB8Kpggl5sOXP8GatYMl3eCug10heN1ZWSM7DGquog7lsxaXgKoifb3iJCddA2pXeenrDN%2F%2F7MxbpGoI%2BxQOxzPVPMr%2BEAMR5wDd3HErDZCRe80R9Ks6wz36Q63z7LK2eTcakCXNclYbcfEpLXSt%2BHndZCsqxajO5d7qGR5zWcwhLbVkgY6mgFVofyEbG0egB8tflNPl1CKJRaExxzLR3zSZFiNRKfx1lTL64LK2j%2FxLn3%2BDguk3ncu3Gl5vd9hFgRagDern9t0yEvQul0x4jSHLqAmb39cNKKzvZvZGek4DAt%2FF4rYUqQ4qIuQs64tcWpoYF91LsniEqK9J9z53oh1EL7HgkbbvFbVnqbul19v7ypU1gdE2hFyRB0R%2FQq21HUP&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3D%22%22&X-Amz-Signature=1f13ebd761919eb14eeada032c05568c2f41f7a02db21a44bf6b7fa61552f62f",
                    "file_name": "busRegProof.png",
                    "name": "Business Registration Proof",
                    "description": "Business Registration Proof"
                },
                {
                    "id": "8166009f-c1d4-4a49-b37f-991dfaf97ab1",
                    "proof_type": "Address",
                    "type": "Other",
                    "tag": "addressProofDoc",
                    "url": "https://kyb-service-sandbox.s3.ap-southeast-1.amazonaws.com/20c749d6-9341-4aa5-a363-80d17c15ee40/busAddressProof.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIA2WN5GPXZGDAL5QI4%2F20220412%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20220412T105709Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEJv%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgMijR7GhzcAt0i7MqNemWxsTIHF5itgSDjrQV28LeqtsCIQDq3vorgnc1GaoirojCD0JmyIc%2F%2F5WU2q1u6aUncn8ooCqwAghEEAEaDDczNTM3MzA2NTcxNCIMqJOo%2FnvVmqN8PRF%2FKo0CYhr87f8NjP4hauvRDJdAicvTlUrHRXdUE%2FrKSPvSeGcwySt87PpBT7DsR9zZEjOlYyNwrrcZcIgaePfWYTlA4vY7Z1IV0uP%2F942EPp6w%2BPDh4%2FTWlMZcd2Ea2QTtSraa4OyusNY5fCfhMUUFSGjgZlosKDIVPSvkNBVFiRGFsuSTi9t7j8qZVKQ7pR1UcPB8Kpggl5sOXP8GatYMl3eCug10heN1ZWSM7DGquog7lsxaXgKoifb3iJCddA2pXeenrDN%2F%2F7MxbpGoI%2BxQOxzPVPMr%2BEAMR5wDd3HErDZCRe80R9Ks6wz36Q63z7LK2eTcakCXNclYbcfEpLXSt%2BHndZCsqxajO5d7qGR5zWcwhLbVkgY6mgFVofyEbG0egB8tflNPl1CKJRaExxzLR3zSZFiNRKfx1lTL64LK2j%2FxLn3%2BDguk3ncu3Gl5vd9hFgRagDern9t0yEvQul0x4jSHLqAmb39cNKKzvZvZGek4DAt%2FF4rYUqQ4qIuQs64tcWpoYF91LsniEqK9J9z53oh1EL7HgkbbvFbVnqbul19v7ypU1gdE2hFyRB0R%2FQq21HUP&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3D%22%22&X-Amz-Signature=d473c9ae9042bb7bf83b3e823af3f5f3d9b14e770dea26766077f62dd69b2b72",
                    "file_name": "busAddressProof.png",
                    "name": "Business Address Proof",
                    "description": "Business Address Proof"
                }
            ],
            "description": ""
        },
        "representative": {
            "id": "ad44d3b3-b3a2-407f-9f98-d277b7e7142a",
            "first_name": "Steve",
            "last_name": "Rogers",
            "same_operating_address": false,
            "dob": "",
            "address_line_1": "add 1",
            "address_line_2": "add 2",
            "city": "Chennai",
            "state": "TamilNadu",
            "country": "India",
            "zip_code": "600069",
            "mobile_number": "9090929229",
            "nationality": "",
            "ownership_percent": 50,
            "ownership_status": false,
            "type": "Representative",
            "roles": [],
            "documents": [
                {
                    "id": "bcdae991-83be-4f75-a09b-e61df815eba2",
                    "proof_type": "Identity",
                    "type": "Passport",
                    "tag": "identityProofTypeFrontDoc",
                    "url": "https://kyb-service-sandbox.s3.ap-southeast-1.amazonaws.com/20c749d6-9341-4aa5-a363-80d17c15ee40/passportback.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIA2WN5GPXZGDAL5QI4%2F20220412%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20220412T105709Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEJv%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgMijR7GhzcAt0i7MqNemWxsTIHF5itgSDjrQV28LeqtsCIQDq3vorgnc1GaoirojCD0JmyIc%2F%2F5WU2q1u6aUncn8ooCqwAghEEAEaDDczNTM3MzA2NTcxNCIMqJOo%2FnvVmqN8PRF%2FKo0CYhr87f8NjP4hauvRDJdAicvTlUrHRXdUE%2FrKSPvSeGcwySt87PpBT7DsR9zZEjOlYyNwrrcZcIgaePfWYTlA4vY7Z1IV0uP%2F942EPp6w%2BPDh4%2FTWlMZcd2Ea2QTtSraa4OyusNY5fCfhMUUFSGjgZlosKDIVPSvkNBVFiRGFsuSTi9t7j8qZVKQ7pR1UcPB8Kpggl5sOXP8GatYMl3eCug10heN1ZWSM7DGquog7lsxaXgKoifb3iJCddA2pXeenrDN%2F%2F7MxbpGoI%2BxQOxzPVPMr%2BEAMR5wDd3HErDZCRe80R9Ks6wz36Q63z7LK2eTcakCXNclYbcfEpLXSt%2BHndZCsqxajO5d7qGR5zWcwhLbVkgY6mgFVofyEbG0egB8tflNPl1CKJRaExxzLR3zSZFiNRKfx1lTL64LK2j%2FxLn3%2BDguk3ncu3Gl5vd9hFgRagDern9t0yEvQul0x4jSHLqAmb39cNKKzvZvZGek4DAt%2FF4rYUqQ4qIuQs64tcWpoYF91LsniEqK9J9z53oh1EL7HgkbbvFbVnqbul19v7ypU1gdE2hFyRB0R%2FQq21HUP&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3D%22%22&X-Amz-Signature=2fe4ddcb3fecd6a995d21d08a80bd99362724966248ce86b17cebe3da3d3c45d",
                    "file_name": "passportback.jpg",
                    "name": "Address proof",
                    "description": "representative passport"
                },
                {
                    "id": "f6c3d79b-ef49-4eca-a634-a5f9e4c70edc",
                    "proof_type": "Identity",
                    "type": "Passport",
                    "tag": "identityProofTypeBackDoc",
                    "url": "https://kyb-service-sandbox.s3.ap-southeast-1.amazonaws.com/20c749d6-9341-4aa5-a363-80d17c15ee40/passportback.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIA2WN5GPXZGDAL5QI4%2F20220412%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20220412T105709Z&X-Amz-Expires=3600&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEJv%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLXNvdXRoZWFzdC0xIkcwRQIgMijR7GhzcAt0i7MqNemWxsTIHF5itgSDjrQV28LeqtsCIQDq3vorgnc1GaoirojCD0JmyIc%2F%2F5WU2q1u6aUncn8ooCqwAghEEAEaDDczNTM3MzA2NTcxNCIMqJOo%2FnvVmqN8PRF%2FKo0CYhr87f8NjP4hauvRDJdAicvTlUrHRXdUE%2FrKSPvSeGcwySt87PpBT7DsR9zZEjOlYyNwrrcZcIgaePfWYTlA4vY7Z1IV0uP%2F942EPp6w%2BPDh4%2FTWlMZcd2Ea2QTtSraa4OyusNY5fCfhMUUFSGjgZlosKDIVPSvkNBVFiRGFsuSTi9t7j8qZVKQ7pR1UcPB8Kpggl5sOXP8GatYMl3eCug10heN1ZWSM7DGquog7lsxaXgKoifb3iJCddA2pXeenrDN%2F%2F7MxbpGoI%2BxQOxzPVPMr%2BEAMR5wDd3HErDZCRe80R9Ks6wz36Q63z7LK2eTcakCXNclYbcfEpLXSt%2BHndZCsqxajO5d7qGR5zWcwhLbVkgY6mgFVofyEbG0egB8tflNPl1CKJRaExxzLR3zSZFiNRKfx1lTL64LK2j%2FxLn3%2BDguk3ncu3Gl5vd9hFgRagDern9t0yEvQul0x4jSHLqAmb39cNKKzvZvZGek4DAt%2FF4rYUqQ4qIuQs64tcWpoYF91LsniEqK9J9z53oh1EL7HgkbbvFbVnqbul19v7ypU1gdE2hFyRB0R%2FQq21HUP&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3D%22%22&X-Amz-Signature=2fe4ddcb3fecd6a995d21d08a80bd99362724966248ce86b17cebe3da3d3c45d",
                    "file_name": "passportback.jpg",
                    "name": "Address proof",
                    "description": "representative passport"
                }
            ],
            "email": "",
            "contact_code": "+91",
            "website": ""
        }
    }
```

### Body Parameters:

| Parameter                                    | Description                                                                                                                                                                                                                                                  |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| account\_id<br><small>required</small>       | `string` Tazapay account UUID of the user                                                                                                                                                                                                                    |
| application\_type<br><small>required</small> | `string` Type of the application. `individival` or`business` <br>For business details, please check [business](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTA2-post-kyb#business)                                              |
| entity\_name<br><small>required</small>      | `string` Name of the business/Individual (for example - "My Shop"/"John Doe")                                                                                                                                                                                |
| submit<br><small>required</small>            | `boolean` To ensure the KYB application is picked up for verification, please pass "submit":true.<br><small>You cannot update the KYB application anymore after 'submit' : 'true' is passed. To keep the option of editing, pass 'submit' : 'false'.</small> |
| business<br><small>required</small>          | `representative` Business details only if business <br> Please check [business](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTA2-post-kyb#business)                                                                             |
| representative<br><small>required</small>    | `representative` Representative details only if business <br> Please check [representative](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTA2-post-kyb#representative)                                                           |
| owner<br><small>required</small>             | `owner` List of owner with their details only if business <br> Please check [owner](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTA2-post-kyb#owner)                                                                            |

### business:

| Parameter                                           | Description                                                                                                                                                                          |
| --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| name<br><small>required</small>                     | `string` Name of the business. Example: "My Shop"                                                                                                                                    |
| type<br><small>optional</small>                     | `string` Can be either `Sole Proprietorship`, `Partnership`, `Company` or `Other`                                                                                                    |
| incorporation\_no<br><small>optional</small>        | `string` Incorporation number for the business                                                                                                                                       |
| address\_line\_1<br><small>optional</small>         | `string` Address line 1                                                                                                                                                              |
| address\_line\_2<br><small>optional</small>         | `string` Address line 2                                                                                                                                                              |
| city<br><small>optional</small>                     | `string` Business's city                                                                                                                                                             |
| state<br><small>optional</small>                    | `string` Business's state                                                                                                                                                            |
| country<br><small>required</small>                  | `string` Business's country                                                                                                                                                          |
| zip\_code<br><small>optional</small>                | `string` Zip code - part of the address                                                                                                                                              |
| trading\_name<br><small>optional</small>            | `string` Trading name for the business                                                                                                                                               |
| years\_in\_business <br><small>optional</small>     | `string` Number of years in which the business is operational.<br> Can be: `< 1 year`,`1-5 years`,`5-10 years`,or`> 10 years`                                                        |
| annual\_turnover<br><small>optional</small>         | `string` Annual turnover for the Business                                                                                                                                            |
| website <br><small>optional</small>                 | `string` Business website URL                                                                                                                                                        |
| date\_of\_incorporation <br><small>optional</small> | `string` Date of incorporation for the business                                                                                                                                      |
| custom\_attrs  <br><small>optional</small>          | `json` Tunnelled add-on fields                                                                                                                                                       |
| documents <br><small>required</small>               | `object` List of documents to be used for verification<br>Please check [documents](https://developer.tazapay.com/docs/tazapay-API-documentation/ZG9jOjI4MzI2OTA2-post-kyb#documents) |

### representative:

| Parameter                                      | Description                                                                                                                                                                       |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| first\_name<br><small>required</small>         | `string` Representative's first name                                                                                                                                              |
| last\_name<br><small>required</small>          | `string` Representative's last name                                                                                                                                               |
| dob<br><small>optional</small>                 | `string` Representative's date of birth                                                                                                                                           |
| address\_line\_1<br><small>>optional</small>   | `string` Address line 1                                                                                                                                                           |
| address\_line\_2<br><small>>optional</small>   | `string` Address line 2                                                                                                                                                           |
| city<br><small>optional</small>                | `string` Representative's city                                                                                                                                                    |
| state<br><small>optional</small>               | `string` Representative's state                                                                                                                                                   |
| country<br><small>optional</small>             | `string` Representative's country                                                                                                                                                 |
| zip\_code<br><small>>optional</small>          | `string` Zip code                                                                                                                                                                 |
| mobile\_number <br><small>optional</small>     | `string` Representative's mobile number                                                                                                                                           |
| ownership\_percent <br><small>required</small> | `int` Representative's ownership percentage. Value must be between 0-100                                                                                                          |
| roles<br><small>required</small>               | `string[]` Representative's role. Can be one or more than one of these: `Director` `Shareholder` `Beneficial Owner` `Authorised Signatory` `Authorized Representative` or `Other` |
| documents<br><small>required</small>           | `documents` List of documents to be used for verification <br> Please check [documents](https://developer.tazapay.com/docs/tazapay-API-documentation/bb44cec3c939b-kyb#documents) |

### owner:

| Parameter                                      | Description                                                                                                                                                                       |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| first\_name<br><small>required</small>         | `string` Owner's first name                                                                                                                                                       |
| last\_name<br><small>required</small>          | `string` Owner's last name                                                                                                                                                        |
| dob<br><small>optional</small>                 | `string` Owner's date of birth                                                                                                                                                    |
| address\_line\_1<br><small>optional</small>    | `string` Address line 1                                                                                                                                                           |
| address\_line\_2<br><small>optional</small>    | `string` Address line 2                                                                                                                                                           |
| city<br><small>optional</small>                | `string` Owner's city                                                                                                                                                             |
| state<br><small>optional</small>               | `string` Owner's state                                                                                                                                                            |
| country<br><small>optional</small>             | `string` Owner's country                                                                                                                                                          |
| zip\_code<br><small>optional</small>           | `string` Zip code                                                                                                                                                                 |
| mobile\_number <br><small>optional</small>     | `string` Owner's mobile number                                                                                                                                                    |
| ownership\_percent <br><small>required</small> | `int` Owner's ownership percentage. Value must be between 0-100                                                                                                                   |
| roles<br><small>required</small>               | `string[]` Owner's role. Can be one or more than one of these: `Director`, `Shareholder`, `Beneficial Owner`, `Authorised Signatory`, `Authorized Representative` or `Other`      |
| documents<br><small>required</small>           | `documents` List of documents to be used for verification <br> Please check [documents](https://developer.tazapay.com/docs/tazapay-API-documentation/bb44cec3c939b-kyb#documents) |

### documents:

| Parameter                                            | Description                                                                               |
| ---------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| proof\_type <br><small>required</small>              | `string` Proof type. Can be `Identity`, `Business`, `Person`, `Additional Doc`, `Address` |
| type<br><small>required</small>                      | `string` Document type. Can be: `Driver's License`, `National ID`, `Passport`, or `Other` |
| name<br><small>required only if type=`Other`</small> | `string`  Document type if not listed in "type"                                           |
| url<br><small>required</small>                       | `string`  Direct download link (dynamically downloadable format)                          |
| description<br><small>optional</small>               | `string` Description about the document                                                   |
| file\_name<br><small>required</small>                | `string` Name of the file attached                                                        |

> 🚧
>
> The document URL should be uploaded in downloadable format (dynamic)
