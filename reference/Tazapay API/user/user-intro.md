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
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"account_id\":\"38fef28e-5514-4513-879c-a8e413bfe5ae\",\n  \"customer_id\":\"Mybusiness_customer_1\",\n  \"ind_bus_type\":\"Business\",\n  \"country\":\"IN\",\n  \"email\":\"info@radiumconstruction.com\",\n  \"business_name\":\"Radium Construction\",\n  \"contact_code\":\"+91\",\n  \"contact_number\":\"4561230890\"\n}",
      "language": "json",
      "name": "Business User Object"
    },
    {
      "code": "{\n  \"account_id\":\"d5ae4b67-1dc3-49d1-b5b1-0174851a76d0\",\n  \"customer_id\":\"Mycustomer_1\",\n  \"ind_bus_type\":\"Individual\",\n  \"country\":\"IN\",\n  \"email\":\"john.doe@me.com\",\n  \"first_name\":\"John\",\n  \"last_name\":\"Doe\",\n  \"contact_code\":\"+91\",\n  \"contact_number\":\"1234567890\"\n}",
      "language": "json",
      "name": "Individual User Object"
    }
  ]
}
[/block]
## Body Parameters

The payload for body should be submitted in `application/json` format.

Parameter                                                                 | Description
--------                                                                  | --------
email<br><small>required</small>                                          | `string` User's email address
first_name<br><small>required **only if** ind_bus_type is Individual</small>   | `string` User's first name. Not needed for `Business` type users.
last_name<br><small>required **only if** ind_bus_type is Individual</small>    | `string` User's last name. Not needed for `Business` type users.
contact_code<br><small>optional</small>                                   | `string` Mobile country code of the user
contact_number <br><small>optional</small>                                | `string` User's mobile number
country<br><small>required</small>                                        | `string` User's country, in ISO 3166 standard alpha-2 code. eg: SG, IN, US, etc. <br></brThe>The complete list can be fetched from [Country Codes](ref:country-codes) 
ind_bus_type<br><small>required</small>                                   | `string` User's entity type. Can be: `Business` or `Individual`
business_name<br><small>required **only if** ind_bus_type is Business</small> | `string` Name of the business. Not needed for `Individual` type users.
partners_customer_id<br><small>optional</small>                           | `string` User's ID or reference number on your platform