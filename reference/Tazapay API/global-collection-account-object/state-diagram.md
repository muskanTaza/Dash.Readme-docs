---
title: State Diagram
deprecated: false
hidden: false
metadata:
  robots: index
---
```Text mermaid
stateDiagram
  [*] --> Open
  Open --> Active : login
  Active --> Open : logout
  Active --> Suspended : timeout
  Suspended --> Active : reactivate
  Suspended --> Closed : close
  Active --> Closed : close
  Closed --> [*]
```