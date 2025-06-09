---
title: Payment Attempt States
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
The following flowchart details the possible statuses for a payment attempt:

<Image align="center" className="border" border={true} src="https://files.readme.io/ddd809b-image.png" />

| Name             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| requires\_action | The customer has not made the payment and further action is required from the customer                                                                                                                                                                                                                                                                                                                                                                                    |
| processing       | The customer has performed all the actions but Tazapay is yet to receive the payment. It is very rare that a payment attempt using a particular payment method stays in this state unless the payment method chosen is not an instant one. For example, a payment attempt stays in the processing state when the payment method chosen is local bank transfer / wire transfer. Offline payments take some time for the intermediary banking institutions to process them. |
| succeeded        | The payment attempt is successful                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| failed           | The payment attempt has failed                                                                                                                                                                                                                                                                                                                                                                                                                                            |
