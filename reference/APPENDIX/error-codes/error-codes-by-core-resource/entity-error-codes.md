---
title: Entity
deprecated: false
hidden: false
metadata:
  robots: index
---
| Error Code | Error Message                                                                                                                                                      | Category                  |
| ---------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------ |
|       2600 | Field 'name' is required and cannot be empty.                                                                                                                      | Core Entity Validation    |
|       2601 | Field 'email' is required and must be a valid email address.                                                                                                       | Core Entity Validation    |
|       2602 | Field is required and must be a valid type and cannot be updated                                                                                                   | Core Entity Validation    |
|       2603 | Field 'registration\_address' is required and cannot be empty.                                                                                                     | Address Validation        |
|       2604 | Field 'state' is required and must be a valid ISO 3166-2 state code.                                                                                               | Address Validation        |
|       2605 | Field 'country' is required and must be a valid ISO 3166-1 alpha-2 country code.                                                                                   | Address Validation        |
|       2606 | Field 'postal\_code' is required and must be a valid postal code.                                                                                                  | Address Validation        |
|       2607 | Field 'operating\_address' is required and cannot be empty when submitting an entity.                                                                              | Address Validation        |
|       2608 | Field 'vertical' is required and must be a valid vertical.                                                                                                         | Core Entity Validation    |
|       2609 | Please provide a valid website URL.                                                                                                                                | Core Entity Validation    |
|       2610 | Field 'registration\_number' is required and cannot be empty.                                                                                                      | Core Entity Validation    |
|       2611 | Please provide atleast one representative details.                                                                                                                 | Representative Validation |
|       2612 | Representative name is required and cannot be empty.                                                                                                               | Representative Validation |
|       2613 | Representative date of birth is required and cannot be empty.                                                                                                      | Representative Validation |
|       2614 | Please provide a valid nationality for the representative.                                                                                                         | Representative Validation |
|       2615 | Please provide a valid positive percentage for the representative ownership.                                                                                       | Representative Validation |
|       2616 | Please provide atleast one representative role.                                                                                                                    | Representative Validation |
|       2617 | Field 'documents' is required and cannot be empty for submitting an entity.                                                                                        | Document Validation       |
|       2618 | Please provide a valid document sub type.                                                                                                                          | Document Validation       |
|       2619 | Please provide a valid document URL.                                                                                                                               | Document Validation       |
|       2620 | Source is invalid, please provide valid source.                                                                                                                    | Core Entity Validation    |
|       2621 | Entity creation is disabled for this particular account. Please reach out to [support@tazapay.com](mailto:support@tazapay.com) for further details and assistance. | Business Rules            |
|       2622 | Field is required and must be a valid xid type with prefix 'ent\_'                                                                                                 | Core Entity Validation    |
|       2623 | Please provide a valid tax\_id                                                                                                                                     | Core Entity Validation    |
|       2624 | Please provide at least one valid created time parameter                                                                                                           | Query Validation          |
|       2625 | Field is required and must be a positive integer from 1 to 100                                                                                                     | Query Validation          |
|       2626 | Please provide 'Gt' with a valid timestamp value or provide either one of 'Gt' or 'Gte' parameter.                                                                 | Query Validation          |
|       2627 | Please provide 'Gte' with a valid timestamp value or provide either one of 'Gt' or 'Gte' parameter.                                                                | Query Validation          |
|       2628 | Please provide 'Lt' with a valid timestamp value or provide either one of 'Lt' or 'Lte' parameter.                                                                 | Query Validation          |
|       2629 | Please provide 'Lte' with a valid timestamp value or provide either one of 'Lt' or 'Lte' parameter.                                                                | Query Validation          |
|       2630 | Field 'relationship' is required and cannot be empty and It should be of valid when submitting an entity.                                                          | Business Rules            |
|       2631 | Field 'purpose\_of\_use' is required and cannot be empty and It should be of valid when submitting an entity.                                                      | Business Rules            |
|       2632 | Field 'city' is required and must be a valid city name.                                                                                                            | Address Validation        |
|       2633 | Please provide a valid onboarding package URL.                                                                                                                     | Core Entity Validation    |
|       2634 | Please provide a valid phone number along with a valid calling code.                                                                                               | Contact Validation        |
|       2635 | Please provide a valid calling code along with a valid phone number.                                                                                               | Contact Validation        |
|       2636 | Entity cannot be submitted at the moment due to it current status                                                                                                  | Business Rules            |
|       2637 | Field 'on\_behalf\_of' is required and cannot be empty when submitting an entity of relationship 'fourth\_party'                                                   | Business Rules            |
|       2218 | Field 'on\_behalf\_of' is invalid or not linked with the provided account                                                                                          | Business Rules            |
|       2420 | Field must be valid xid type with prefix 'ent\_'                                                                                                                   | Scorecard Validation      |