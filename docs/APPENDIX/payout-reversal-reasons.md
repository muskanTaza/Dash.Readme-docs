---
title: Payout Reversal Reasons
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
This document outlines the possible reasons for payout reversals in the Tazapay system. When a payout is reversed, one of the following reason codes will be provided:

## Payout Reversal Reason Codes

| Reason Code | Description |
| :---------- | :---------- |
| PR1001 | Invalid Or Closed Beneficiary Account |
| PR1002 | Incorrect Beneficiary Details |
| PR1003 | Account Not Eligible For Cross-Border Credits |
| PR1004 | Dormant Or Restricted Account |
| PR2001 | Sanctions Or Screening Failure |
| PR3001 | Unclaimed Or Expired Payout |
| PR3002 | Beneficiary Declined Payment |
| PR0001 | Other |

### Account-Related Issues (PR1xxx)

**PR1001 - Invalid Or Closed Beneficiary Account**
The beneficiary's account is either invalid or has been closed. The payout cannot be processed to this account.

**PR1002 - Incorrect Beneficiary Details**
The beneficiary details provided (such as account number, routing information, or personal details) are incorrect or do not match the account.

**PR1003 - Account Not Eligible For Cross-Border Credits**
The beneficiary's account is not configured to receive cross-border payments or international transfers.

**PR1004 - Dormant Or Restricted Account**
The beneficiary's account is either dormant (inactive for an extended period) or has restrictions that prevent it from receiving payments.

### Compliance Issues (PR2xxx)

**PR2001 - Sanctions Or Screening Failure**
The payout failed compliance screening checks, such as sanctions lists or anti-money laundering (AML) regulations.

### Beneficiary Action Issues (PR3xxx)

**PR3001 - Unclaimed Or Expired Payout**
The payout was not claimed by the beneficiary within the specified timeframe and has expired.

**PR3002 - Beneficiary Declined Payment**
The beneficiary has actively declined or rejected the payment.

### Other Issues (PR0xxx)

**PR0001 - Other**
The payout was reversed for reasons not covered by the specific codes above. Additional details may be provided in the transaction notes.
