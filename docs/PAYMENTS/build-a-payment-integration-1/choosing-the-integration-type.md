---
title: Choosing the integration type
deprecated: false
hidden: true
metadata:
  robots: index
---
Tazapay offers flexible integration options to cater to your business needs and technical capabilities. You can either redirect to a `Tazapay Hosted Page` or build a `Custom Native Integration`. Tazapay also provides various [no-code](https://docs.tazapay.com/docs/no-code-options) payment options to help you get started quickly.

## Choosing the right integration option

|                                        | Redirect to a Tazapay hosted page                                                                     | List payment methods on your page                                        | Redirect to a Tazapay hosted page                                                                                    | Tazapay lists the payment methods | Build a custom native integration |
| :------------------------------------- | :---------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------- | :-------------------------------- | :-------------------------------- |
| _Experience_                           | The customer is redirected to Tazapay after they have selected the payment method on your application | The customer is redirected to Tazapay where they choose a payment method | The customer completes the entire payment on your application.                                                       |                                   |                                   |
| _Effort to integrate_                  | Low                                                                                                   | Very low                                                                 | Medium                                                                                                               |                                   |                                   |
| _Payment Success Rates_                | High                                                                                                  | High                                                                     | Very High                                                                                                            |                                   |                                   |
| _API to Integrate_                     | /v3/checkout                                                                                          | /v3/checkout                                                             | /v3/payin                                                                                                            |                                   |                                   |
| _What is sent as part of API response_ | A redirection URL pointing to a Tazapay hosted page                                                   | A redirection URL pointing to a Tazapay hosted page                      | Information corresponding to the payment method. You can choose how best to display this information to the customer |                                   |                                   |
| _Effort to Maintain_                   | Low                                                                                                   | Very low                                                                 | Medium                                                                                                               |                                   |                                   |
| _Integration Guide_                    |                                                                                                       |                                                                          |                                                                                                                      |                                   |                                   |

> 👍 Javascript SDK
>
> You can also integrate with Tazapay's Javascript SDK to directly embed the payment iFrame on your website for all the payment methods as well as cards.
