---
title: Managing Payment Methods
excerpt: Choose which payment methods to be displayed to your customer
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
## Overview

Tazapay supports a variety of payment methods for a particular combination of buyer-seller corridor, invoice currency and transaction amount. You can use an interactive widget on the <a href="https://www.tazapay.com" target="_blank">homepage</a> to simulate a trade and find out the available payment methods. Alternatively, you can also use the <a href="https://docs.tazapay.com/reference/collection-methods-api" target="_blank">collect metadata endpoint</a>.

The 'payment_methods' field in the checkout session endpoint allows you to specify payment methods that you would want for a particular checkout session. The payment methods added to the field would be only surfaced on the hosted payment page.

For example, if you only want Wire Transfer and Local Bank Transfer as payment methods in the checkout session, make sure to pass the following field and parameter in the <a href = "https://docs.tazapay.com/reference/create-checkout" target = "_blank">Checkout request body</a>  
`"payment_methods": ["wire_transfer", "local_bank_transfer_sgd"]`

> `local_bank_transfer_sgd` is Local Bank Transfer for Singapore. Similarly, Local Bank Transfer for EU countries is `local_bank_transfer_eur` and so on.

> ❗️ 
> 
> If the "payment_methods" field has some undesired values; ex: ["abc", "xyz"], it will throw an error.

You can also remove payment methods for a particular transaction using the 'remove_payment_methods' field. If you do not want Wire Transfer and Local Bank Transfer as payment methods in the checkout session, make sure to pass the following field and parameter in the <a href = "https://docs.tazapay.com/reference/create-checkout" target = "_blank">Checkout request body</a>  
`"filter": ["wire_transfer", "local_bank_transfer_sgd"]`

> 🚧 
> 
> In case both the fields are present in the request body, the 'payment_methods' field will take precedence.

## Example:

The payment methods available for a buyer from Netherlands are the following for an invoice of USD 500.

- Bank Initiation (Internet Banking) aka `bank_initaition_eur`
- Card aka `card`
- Local Bank Transfer aka `local_bank_transfer_eur`
- Wire Transfer aka `wire_transfer`

If you only want to have Card and Internet Banking as payment methods for the transaction, you can go either of the two ways below:

### Specifying Payment Methods using 'payment_methods' field

This is the part of the payload for POST /v3/checkout API

```Text JSON
 "payment_methods": ["card","bank_initiation_eur"]
```

### Filtering out Payment Methods using 'remove_payment_methods' field

This is the part of the payload for POST /v3/checkout API.

```Text JSON
"remove_payment_methods": ["local_bank_transfer_eur", "wire_transfer"]
```

> 📘 
> 
> Tazapay constantly upgrades its payment collection capabilities by adding new payment methods. It is recommended to use the 'remove_payment_methods' instead of 'payment_methods' field in case you do not want any particular payment method (for example, you may choose to remove asynchronous payment methods like Wire Transfer). Your customers and buyers can access these new payment methods without you having to make any change to your integration.