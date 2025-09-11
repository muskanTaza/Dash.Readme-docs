---
title: FIRC - Key Considerations
deprecated: false
hidden: false
metadata:
  robots: index
---
## Overview

When processing payouts to India, Tazapay generates a **Foreign Inward Remittance Advice (FIRA)** in compliance with the **Reserve Bank of India (RBI)** regulations.

The **Purpose Code** selected during the payout request determines:

* How the transaction is classified under RBI guidelines.
* The **type of FIRA** that will be generated.
* Whether the payout is successfully processed or rejected.

⚠️ **Important:**

* FIRCs/FIRAs are generated **strictly based on the Purpose Code chosen at the time of processing**.
* **They cannot be edited or revised later.**
* Incorrect purpose code selection may result in **RFIs (Requests for Information), delays, or outright rejection of the payment** by banking partners.

***

## How Purpose Codes Work in Tazapay

* Tazapay provides a set of **Tazapay Purpose Codes (PYRxxx)** that merchants can choose from when initiating a payout.
* Each Tazapay Purpose Code is **mapped to a valid RBI Purpose Code**, ensuring compliance.
* The mapping includes restrictions on **Remitter Type** and **Beneficiary Type**, (where applicable).

For full details of valid codes, refer to [Purpose Codes Valid for India Payouts](https://docs.tazapay.com/docs/purpose-codes-valid-for-india-payouts).

***

## Best Practices for Using Purpose Codes

* **Identify the exact nature of the transaction** (goods, software, services, tax, etc.).
* **Select the correct Tazapay Purpose Code (PYRxxx)** at the time of payout initiation.
* **Avoid generic selections** – the wrong code can cause compliance flags.
* **Cross-check remitter and beneficiary types** – certain codes are restricted to individuals only, corporates only, or a combination.

***

## Key Compliance Notes

* FIRAs are generated **only once**, based on the original purpose code.
* **No edits or re-issuance** are allowed post-transaction.
* Incorrect selection may lead to:
  * RFIs (bank asking for more information)
  * Delays in processing
  * Rejection of payment

✅ By following the correct **Tazapay Purpose Code → RBI Purpose Code mapping**, your India payouts will remain **compliant, seamless, and avoid unnecessary delays.**
