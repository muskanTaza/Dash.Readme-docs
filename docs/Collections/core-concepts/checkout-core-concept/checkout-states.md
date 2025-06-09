---
title: Checkout States
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The following flowchart details the possible payment status for checkout sessions:

<Image align="center" className="border" border={true} src="https://files.readme.io/2adc953-image.png" />

| Name       | Description                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| unpaid     | The customer has not made the payment and further action is required from the customer                                                                                                                                                                                                                                                                                                                                                    |
| processing | The customer has performed all the actions but Tazapay is yet to receive the payment. It is very rare that a checkout session stays in this state unless the payment method chosen is not an instant one. For example, a checkout session stays in the processing state when the payment method chosen is local bank transfer / wire transfer. Offline payments take some time for the intermediary banking institutions to process them. |
| paid       | The payment for the checkout session is successful                                                                                                                                                                                                                                                                                                                                                                                        |
