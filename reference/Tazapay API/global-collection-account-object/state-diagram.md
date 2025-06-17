---
title: State Diagram
deprecated: false
hidden: true
metadata:
  robots: index
---
```mermaid
stateDiagram-v2
    [*] --> Disabled
    Disabled --> Enablement_Requested : Request Enablement
    Enablement_Requested --> Enabled : Approve Enablement
    Enablement_Requested --> Enablement_Rejected : Reject Enablement
    Enabled --> Disablement_Requested : Request Disablement
    Disablement_Requested --> Disabled : Approve Disablement
    Disablement_Requested --> Enablement_Requested : Re-enable Request
    Enablement_Rejected --> Disabled : Reject Enablement
```