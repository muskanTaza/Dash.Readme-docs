---
title: Overview
deprecated: false
hidden: false
metadata:
  robots: index
---
In certain scenarios, a payout may be reversed by downstream banking or payment networks after it has been processed. When this occurs, TazaPay reflects the reversal directly at the payout level to ensure accurate reconciliation and full auditability.

### With payout reversals:

* Reversed payouts transition to a dedicated terminal state `reversed`
* Reversal amounts reflect actual funds credited back to the Tazapay balance
* Applicable fees and FX differences are transparently itemized
* Reversal-related balance movements are explicitly linked to the original payout

<Image border={false} src="https://files.readme.io/292cf268a58e59d863be1123a4d7011d0b83fc1e2e26b3eb0fea1ffe38563094-image.png" />

<br />
