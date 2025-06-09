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

The 'payment\_methods' field in the checkout session endpoint allows you to specify payment methods that you would want for a particular checkout session. The payment methods added to the field would be only surfaced on the hosted payment page.

For example, if you only want Wire Transfer and Local Bank Transfer as payment methods in the checkout session, make sure to pass the following field and parameter in the <a href = "https://docs.tazapay.com/reference/create-checkout" target = "_blank">Checkout request body</a>\
`"payment_methods": ["Wire Transfer", "Local Bank Transfer"]`

> ❗️
>
> If the "payment\_methods" field has some undesired values; ex: \["abc", "xyz"], it will throw an error.

You can also filter out payment methods or remove payment methods for a particular transaction using the 'filter' field. If you do not want Wire Transfer and Local Bank Transfer as payment methods in the checkout session, make sure to pass the following field and parameter in the <a href = "https://docs.tazapay.com/reference/create-checkout" target = "_blank">Checkout request body</a>\
`"filter": ["Wire Transfer", "Local Bank Transfer"]`

> 🚧
>
> In case both the fields are present in the request body, the 'payment\_methods' field will take precedence.

## Example:

The payment methods available for a buyer from Australia are the following for an invoice of USD 500.

* New Payment Platform
* Bank Redirect
* Card
* Local Bank Transfer
* Wire Transfer

If you only want to have Card and New Payment Platform as payment methods for the transaction, you can go either of the two ways below:

### Specifying Payment Methods using 'payment\_methods' field

This is the payload which you can pass in the POST /v1/checkout API.

```Text JSON
{
    "buyer": {
        "email": "buyer+au@au.buyer",
        "country": "AU",
        "ind_bus_type": "Business",
        "business_name": "Legends Private Limited"
    },
    "fee_paid_by": "buyer",
    "fee_percentage": 100,
    "invoice_currency": "USD",
    "invoice_amount": 500,
    "txn_description": "Game Cards",
    "payment_methods": ["Card","New Payment Platform"]
}
```

### Filtering out Payment Methods using 'filter' field

This is the payload which you can pass in the POST /v1/checkout API.

```Text JSON
{
    "buyer": {
        "email": "buyer+au@au.buyer",
        "country": "AU",
        "ind_bus_type": "Business",
        "business_name": "Legends Private Limited"
    },
    "fee_paid_by": "buyer",
    "fee_percentage": 100,
    "invoice_currency": "USD",
    "invoice_amount": 500,
    "txn_description": "Game Cards",
    "filter": ["Bank Redirect","Local Bank Transfer","Wire Transfer"]
}
```

> 📘
>
> Tazapay constantly upgrades its payment collection capabilities by adding new payment methods for a buyer-seller combination. It is recommended to use the 'filter' instead of 'payment\_methods' field in case you do not want any particular payment method (for example, *you may choose to remove asynchronous payment methods like Wire Transfer*). Your customers and buyers can access these new payment methods without you having to make any change to your integration.
