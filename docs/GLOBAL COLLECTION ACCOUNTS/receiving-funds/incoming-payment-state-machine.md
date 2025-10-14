---
title: Incoming Payment State Machine
excerpt: Collects can transition through the below states
deprecated: false
hidden: false
metadata:
  robots: index
---
* Each incoming payment to the virtual account is represented by a collect object.
* A collect can be created in either of the following states
  * succeeded (it is a terminal state)
  * compliance_hold (in case Tazapay requires more remitter information); The collect will transition to either failed or succeeded from this state.

### State Machine for Collects

<Image align="center" className="border" border={true} src="https://files.readme.io/1dc05f86f0ad1a83389fe4c89bc1ee48a9425c0a5ee87e45f15ddeb48345bab4-refund_state_machine.jpg" />

<br />

<br />