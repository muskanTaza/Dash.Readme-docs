---
title: Payout States
excerpt: A payout transitions through the following states
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
<Image align="center" src="https://files.readme.io/5f16bdf1f8f14195906739607392f3b559d62a2f5dc824a096e3a13b403c506e-payout_state_machine.png" />

<br />

| State              | Description                                                                                                                                    |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| requires\_approval | Payout requires approval from an authorized user.                                                                                              |
| approval\_hold     | This is only applicable for payouts created on behalf of an entity. The payout will be processed after the entity has been approved by Tazapay |
| requires\_funding  | The payout needs to be funded to be processed                                                                                                  |
| screening          | The payout is being screened for compliance                                                                                                    |
| compliance\_hold   | The payout is on hold for reasons of compliance. Tazapay will reach out to you for next steps.                                                 |
| processing         | The payout is being processed.                                                                                                                 |
| succeeded          | The payout has succeeded.                                                                                                                      |
| requires\_action   | An action is required by the account to continue with the payout (e.g., Document Upload, Incorrect bank details, etc).                         |
| failed             | The payout has failed.                                                                                                                         |
| reversed           | The payout has been reversed. Funds have been returned to the original account.                                                                |
