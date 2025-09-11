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

* Tazapay provides a set of **TP Purpose Codes (PYRxxx)** that merchants can choose from when initiating a payout.
* Each TP Purpose Code is **mapped to a valid RBI Purpose Code**, ensuring compliance.
* The mapping includes restrictions on **remitter type**, **beneficiary type**, and **transaction caps** (where applicable).

For full details of valid codes, refer to [Purpose Codes Valid for India Payouts](https://docs.tazapay.com/docs/purpose-codes-valid-for-india-payouts).

## RBI Purpose Code Mapping in Tazapay

Below is the mapping of **Tazapay Purpose Codes (TP Codes)** to the corresponding **RBI Purpose Codes**:

| TP Purpose Code | TP Purpose Code Description                        | Remitter Type           | Beneficiary Type        | Mapped PC Code | RBI Purpose Description                                                               | RBI Code |
| --------------- | -------------------------------------------------- | ----------------------- | ----------------------- | -------------- | ------------------------------------------------------------------------------------- | -------- |
| PYR001          | Payment for Services                               | Individual / Corporates | Individual / Corporates | PC17           | Export of Services – Business & Management Consultancy (≤ ₹15,00,000 per transaction) | P1006    |
| PYR002          | Payment for Software                               | Individual / Corporates | Individual / Corporates | PC21           | Export of Services – Software Consultancy (≤ ₹15,00,000 per transaction)              | P0802    |
| PYR003          | Payments for goods                                 | Individual / Corporates | Individual / Corporates | PC10           | Export of Goods – Export Bills Realization (≤ ₹15,00,000 per transaction)             | P0102    |
| PYR006          | Transfer to own account                            | Individual              | Individual              | PC01           | Credit to NRE Rupee Accounts maintained by NRIs                                       | P0014    |
| PYR010          | Salary                                             | Corporates              | Individual              | PC15           | Salary Payments                                                                       | P1401    |
| PYR018          | Tax Payment                                        | Individual              | Individual / Corporates | PC12           | Tax Payments in India                                                                 | P1306    |
| PYR025          | Education-related expenses                         | Individual              | Individual / Corporates | PC06           | Tuition, boarding, examination fees to schools/colleges                               | P1107    |
| PYR026          | Medical Treatment                                  | Individual              | Individual / Corporates | PC07           | Payments to medical institutions & hospitals in India                                 | P1108    |
| PYR028          | Mutual Fund Investment                             | Individual              | Individual / Corporates | PC03           | Payments to Insurance Companies, Mutual Funds, Postmaster                             | P0601    |
| PYR031          | Advance Payments for goods                         | Individual / Corporates | Individual / Corporates | PC16           | Export of Goods – Advance Payment (≤ ₹15,00,000 per transaction)                      | P0104    |
| PYR032          | Vendor/Contractor payouts for software development | Individual / Corporates | Individual / Corporates | PC21           | Export of Services – Software Consultancy (≤ ₹15,00,000 per transaction)              | P0802    |

👉 The full expanded mapping (including all 30+ codes) is available in the [linked documentation](https://docs.tazapay.com/docs/purpose-codes-valid-for-india-payouts).

***

## Best Practices for Using Purpose Codes

* **Identify the exact nature of the transaction** (goods, software, services, salary, tax, etc.).
* **Select the correct TP Purpose Code (PYRxxx)** at the time of payout initiation.
* **Avoid generic selections** – the wrong code can cause compliance flags.
* **Cross-check remitter and beneficiary types** – certain codes are restricted to individuals only, corporates only, or a combination.
* **Respect transaction caps** – e.g., certain exports and services are capped at ₹15,00,000 per transaction.

***

## Key Compliance Notes

* FIRAs are generated **only once**, based on the original purpose code.
* **No edits or re-issuance** are allowed post-transaction.
* Incorrect selection may lead to:
  * RFIs (bank asking for more information)
  * Delays in processing
  * Rejection of payment

✅ By following the correct **TP Purpose Code → RBI Purpose Code mapping**, your India payouts will remain **compliant, seamless, and avoid unnecessary delays.**
