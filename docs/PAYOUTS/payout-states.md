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
<Image border={false} src="https://files.readme.io/93fc772d07090952da9d7e002e6abd02ae02628e4e9fd7a5874f8b6fc0ad8476-image.png" />

<br />

| State             | Description                                                                                                                                    |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| requires_approval | Payout requires approval from an authorized user. This is applicable to payouts initiated using the Tazapay dashboard                          |
| approval_hold     | This is only applicable for payouts created on behalf of an entity. The payout will be processed after the entity has been approved by Tazapay |
| requires_funding  | The payout needs to be funded to be processed                                                                                                  |
| screening         | The payout is being screened for compliance                                                                                                    |
| compliance_hold   | The payout is on hold for reasons of compliance. Tazapay will reach out to you for next steps.                                                 |
| processing        | The payout is being processed.                                                                                                                 |
| succeeded         | The payout has succeeded.                                                                                                                      |
| requires_action   | An action is required by the account to continue with the payout (e.g., Document Upload, Incorrect bank details, etc).                         |
| failed            | The payout has failed to be initiated. Funds have been returned to your Tazapay balance.                                                       |
| reversed          | The payout has been reversed by the network or the beneficiary bank. Funds have been returned to your Tazapay balance.                         |
