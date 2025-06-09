---
title: Refund states
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
The following flowchart contains the statuses a refund transitions through:

<Image align="center" className="border" border={true} src="https://files.readme.io/40145b3-image.png" />

| State     | Description                                                                                                                                                                                                                                                                |
| :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| pending   | Whenever a refund request is received, Tazapay automatically puts it under pending. From this status, it can succeed.                                                                                                                                                      |
| succeeded | A refund has succeeded.                                                                                                                                                                                                                                                    |
| failed    | The refund request has failed. This happens very rarely, mostly where the customer is no longer associated with the payment instrument they used to make the payment. In these cases, you can reach out to your customer and ask for their bank details and make a payout. |
| cancelled | The refund request was cancelled                                                                                                                                                                                                                                           |
