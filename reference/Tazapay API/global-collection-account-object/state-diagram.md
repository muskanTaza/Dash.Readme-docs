---
title: State Diagram
deprecated: false
hidden: true
metadata:
  robots: index
---
&#x20;

```mermaid
stateDiagram-v2
    [*] --> Collection_Account
    Collection_Account --> Enablement_Requested : Request Enablement
    Enablement_Requested --> Enabled : Approve Enablement
    Enablement_Requested --> Enablement_Rejected : Reject Enablement
    Enabled --> Disablement_Requested : Request Disablement
    Disablement_Requested --> Disabled : Approve Disablement
    Disablement_Requested --> Enabled : Reject Disablement

```

<br />

\[\*] --> Collection\_Account\
Collection\_Account --> Enablement\_Requested : Request Enablement
Enablement\_Requested --> Enabled : Approve Enablement
Enablement\_Requested --> Enablement\_Rejected : Reject Enablement
Enabled --> Disablement\_Requested : Request Disablement
Disablement\_Requested --> Disabled : Approve Disablement
Disablement\_Requested --> Enabled : Reject Disablement