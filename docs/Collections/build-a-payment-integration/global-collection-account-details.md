---
title: Global Collection Account
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Viewing your active Collection Accounts

You can view the collection accounts configured for your account on the [Tazapay dashboard](https://dashboard.tazapay.com). 

> To configure collection accounts, please reach out to [support@tazapay.com](mailto:support@tazapay.com)

### Accessing the Collection Accounts Tab

Look at the left panel of the dashboard after logging in. Click on the tab labelled `Collection Accounts`. You will be navigated to the screen displaying your Collection Account details.

<Image align="center" className="border" border={true} src="https://files.readme.io/d50eacc-Screenshot_2024-02-16_at_6.07.54_PM.png" />

### Viewing Collection Account Details

Once on the Collection Accounts screen, all Virtual Account details configured for collection are displayed.\
For each collection account, you can view the Account Name, Account Number, Currency, Bank, Swift Code (if applicable), and Local Routing Number (if applicable).

<Image align="center" className="border" border={true} src="https://files.readme.io/5b25382-Screenshot_2024-02-16_at_6.11.22_PM.png" />

# Viewing Collects (Incoming Payments to the Collection Accounts)

Incoming Payments to the Collection Accounts are called collects.

You can view collects in your collection accounts on [Tazapay's dashboard](https://dashboard.tazapay.com).

### Accessing Transactions

* Once logged in, click on the`Transactions` tab located on the left-hand side vertical navigation bar.
* A listing screen will appear displaying the following columns:
  * **Payment ID:** A unique identifier for each collect, starts with `col_`
  * **Status:** The status of the collect - succeeded, failed or on\_hold
  * **Invoice Amt:** The amount in the currency collected
  * **Date:** The timestamp at which the collect was created
  * **Payment Method:** Indicates whether the collect was made using Local bank Transfer or Wire Transfer
  * **Settled Date:** The date on which the collected funds were transferred to your registered bank account.

<Image align="center" className="border" border={true} src="https://files.readme.io/8ef873b-image.png" />

### Searching for collection records

Use the search tab at the top-left corner of the screen to find a specific collect ID. You can perform a full search with the exact ID or a partial search with a part of the ID.

<Image align="center" className="border" border={true} src="https://files.readme.io/573ff95-image.png" />

### Viewing Collect Details

To view the expanded details for a collect, you can simply click on the Payment ID starting with `col_` on the `Transactions` screen and it will redirect you to the collection summary screen. The screen will display the following information -

**Your business details (Account Details):**

| Fields          | Description                                            |
| :-------------- | :----------------------------------------------------- |
| Account ID      | Unique Tazapay Account ID for your registered business |
| Account Email   | User Email                                             |
| Account Country | Business Registration Country                          |
| Business Name   | Registered Name of your business                       |

**Collection Details**

| Fields                          | Description                                                                                       |
| :------------------------------ | :------------------------------------------------------------------------------------------------ |
| Collection Amount               | The amount credited for the payment                                                               |
| Fees                            | Tazapay Fees for the payment                                                                      |
| Payment Method                  | The payment method                                                                                |
| Receiving Account Number / IBAN | The account number (or IBAN in case the currency is EUR) of the receiving account for the payment |
| Status                          | The status of the collect - its usually `succeeded`. Rarely can be `on_hold` or `failed`          |

**Sender Details**

> The availability of this information is subject to the sender entering this in their banking application used to transfer funds

| Fields                 | Description                                                |
| :--------------------- | :--------------------------------------------------------- |
| Name                   | Name of the sender                                         |
| Bank                   | The details of the bank account this payment was made from |
| Reference              | Any reference number entered by the sender                 |
| Additional Information | Additional information entered by the sender               |

<br />

<Image align="center" className="border" border={true} src="https://files.readme.io/74e3662-image.png" />

# After Collection

You can choose to do the following with the funds in your collection accounts:

1. **Receive Settlements:** After collection, Tazapay converts and transfers the collected funds to the bank account and currency of your choice on a periodic basis. This is the default configuration for your account.
2. **Make Payouts:** You can choose to make payouts to third-parties in 60+ currencies using the collected funds. You can reach out to [support@tazapay.com](mailto:support@tazapay.com) to disable auto-settlements and enable payouts for your account.
