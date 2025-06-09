---
title: Listing Payment Methods on your UI
excerpt: Increase conversion and your top line
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Using the <a href = "https://docs.tazapay.com/v3/reference/create-checkout" target = "_blank">checkout API</a>, you can also list the available payment methods for a session on a screen hosted by you. 

The customer selects the payment method from your screen first and are directly redirected to the page where an action is expected of them. 

#### Example:

Suppose there are two payment methods available for a checkout session (Cards and Paynow QR). You can display the payment methods Card and Paynow QR for your customer to select. If the customer selects Paynow QR, you can create a checkout session with the field `payment_methods` containing the value `paynow_sgd`. The URL returned in the response body of the checkout API will display the QR code directly to the customer on redirection.

#### Sample Request Body:

```Text JSON
{
	"invoice_currency": "SGD",
	"amount": 10000,
  "customer_details":{
    "name":"Bob Vance",
    "email":"bob@vanceref.com",
    "country":"SG"
  },
  "transaction_description":"1 x Item",
  "payment_methods":["paynow_sgd"]
}
```