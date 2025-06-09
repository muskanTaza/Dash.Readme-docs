---
title: Refund States
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
# All Possible Refund States:

| State             | Description                                                                                                                                                                                                                                                |
| :---------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| under\_review     | Whenever a refund request is received, Tazapay automatically puts it under\_review. From this state, it can move to either approved or rejected. <i>Refunds are not supported for some payment methods, in which case the state will move to rejected.</i> |
| refund\_initiated | A successful refund has been initiated by Tazapay. It moves to approved upon confirmation of successful refund. <i>In rare cases where the refund fails due to any downstream issues, the refund can move to under\_review for further action.</i>         |
| approved          | The refund is successful.                                                                                                                                                                                                                                  |
| rejected          | The refund failed.                                                                                                                                                                                                                                         |
