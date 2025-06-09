---
title: KYB States
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
## KYB States

The flowchart details all possible states for a user's KYB

![621](https://files.readme.io/1bb0f75-KYB_states.jpg "KYB states.jpg")

### All Possible KYB States

| State        | Description                                                                                |
| ------------ | ------------------------------------------------------------------------------------------ |
| not\_started | The KYB applicated is in draft mode. It can be still be edited using the PUT KYB endpoint. |
| initiated    | The KYB application has been submitted and picked up for verification by Tazapay.          |
| pending      | Additional documents required to be submitted or queries to be answered.                   |
| completed    | KYB application has been successfully verified                                             |
| rejected     | KYB application has been rejected.                                                         |
