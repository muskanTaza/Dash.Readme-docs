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
[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/1bb0f75-KYB_states.jpg",
        "KYB states.jpg",
        621,
        241,
        "#fcf9ef"
      ]
    }
  ]
}
[/block]
### All Possible KYB States

State                | Description
--------                 | --------
not_started            | The KYB applicated is in draft mode. It can be still be edited using the PUT KYB endpoint. 
initiated                 | The KYB application has been submitted and picked up for verification by Tazapay.
pending                   | Additional documents required to be submitted or queries to be answered.
completed               | KYB application has been successfully verified
rejected              | KYB application has been rejected.