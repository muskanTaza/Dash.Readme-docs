---
title: Introduction to Users
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
The user object represents an entity (individual or business) on Tazapay's database. Transactions can be created between users. Example, for a marketplace, the users can be buyers, sellers and the marketplace itself. For individual sellers, the users can be the buyers and the seller themselves.

```json Business User Object
{
  "account_id":"38fef28e-5514-4513-879c-a8e413bfe5ae",
  "customer_id":"Mybusiness_customer_1",
  "ind_bus_type":"Business",
  "country":"IN",
  "email":"info@radiumconstruction.com",
  "business_name":"Radium Construction",
  "contact_code":"+91",
  "contact_number":"4561230890"
}
```
```json Individual User Object
{
  "account_id":"d5ae4b67-1dc3-49d1-b5b1-0174851a76d0",
  "customer_id":"Mycustomer_1",
  "ind_bus_type":"Individual",
  "country":"IN",
  "email":"john.doe@me.com",
  "first_name":"John",
  "last_name":"Doe",
  "contact_code":"+91",
  "contact_number":"1234567890"
}
```

## Body Parameters

The payload for body should be submitted in `application/json` format.

| Parameter                                                                        | Description                                                                                                                                                           |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| email<br/><small>required</small>                                                 | `string` User's email address                                                                                                                                         |
| first\_name<br/><small>required **only if** ind\_bus\_type is Individual</small>  | `string` User's first name. Not needed for `Business` type users.                                                                                                     |
| last\_name<br/><small>required **only if** ind\_bus\_type is Individual</small>   | `string` User's last name. Not needed for `Business` type users.                                                                                                      |
| contact\_code<br/><small>optional</small>                                         | `string` Mobile country code of the user                                                                                                                              |
| contact\_number <br/><small>optional</small>                                      | `string` User's mobile number                                                                                                                                         |
| country<br/><small>required</small>                                               | `string` User's country, in ISO 3166 standard alpha-2 code. eg: SG, IN, US, etc. <br/>The complete list can be fetched from [Country Codes](ref:country-codes)         |
| ind\_bus\_type<br/><small>required</small>                                        | `string` User's entity type. Can be: `Business` or `Individual`                                                                                                       |
| business\_name<br/><small>required **only if** ind\_bus\_type is Business</small> | `string` Name of the business. Not needed for `Individual` type users.                                                                                                |
| partners\_customer\_id<br/><small>optional</small>                                | `string` User's ID or reference number on your platform                                                                                                               |