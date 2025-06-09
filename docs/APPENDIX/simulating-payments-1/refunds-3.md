---
title: Refunds
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
### Endpoint

<https://service-sandbox.tazapay.com/v3/refund>

### Types of Refunds

1. **Full Refund:** It refers to the total amount paid by the buyer for a transaction. A merchant can specify the same amount while creating the refund request for the said transaction.
2. **Partial Refund:** It refers to a part of the total amount paid by the buyer for a transaction. A merchant can specify any amount less than the total buyer paid amount to request a partial refund

**_Note_**: _The burden of Tazapay fee is always borne by the merchant in case of refunds._

### Common Testing Scenarios

1. **Successful Refunds**: For simulating a successful full or partial refund, merchant can enter the amount to refund and create a refund request. All refunds created in sandbox are updated as successful within ~1-2 mins except failure cases.
2. **Refund Failure**: For simulating a failed full or partial refund, merchant can enter the amount as `20000 cents` in invoice currency create a refund request. All refunds created with the said amount in sandbox are updated as failed within ~1-2 mins.