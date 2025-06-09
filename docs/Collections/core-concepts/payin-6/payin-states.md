---
title: Payin states
excerpt: A payin transitions through multiple statuses
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
The following flowchart details the possible status of a payin

![](https://files.readme.io/5e40336-image.png)

| Name                      | Description                                                                                                                                     |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| requires\_payment\_method | Payment Method details need to be attached to the payin to proceed with the payment                                                             |
| requires\_action          | An action needs to be taken by the customer for the payment to go through                                                                       |
| processing                | All the actions have been performed by the customer, Tazapay is still waiting to confirm the payment. Not all payment methods have this status. |
| succeeded                 | The payin is successful                                                                                                                         |
| cancelled                 | The payin is cancelled                                                                                                                          |
