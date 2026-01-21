---
title: Viewing Collect (Incoming Payments)
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
You can view collects in your collection accounts on [Tazapay's dashboard](https://dashboard.tazapay.com).

### Accessing Transactions

* Once logged in, click on the`Transactions` tab located on the left-hand side vertical navigation bar.
* A listing screen will appear displaying the following columns:
  * **Payment ID:** A unique identifier for each collect, starts with `col_`
  * **Status:** The status of the collect - created, broadcasted, succeeded, failed or on\_hold
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
| Status                          | The status of the collect - can be `created`, `broadcasted`, `succeeded`, `on_hold` or `failed`. Collect status can be `created` or `broadcasted` for wallets. |
| Transaction Hash                | Unique identifier assigned to this blockchain transaction                                         |

**Sender Details**

> The availability of this information is subject to the sender entering this in their banking application used to transfer funds

### Virtual Account

| Fields                 | Description                                                |
| :--------------------- | :--------------------------------------------------------- |
| Name                   | Name of the sender                                         |
| Bank                   | The details of the bank account this payment was made from |
| Reference              | Any reference number entered by the sender                 |
| Additional Information | Additional information entered by the sender               |

### Wallet

| Fields                         | Description                                    |
| :----------------------------- | :--------------------------------------------- |
| payer\_wallet.deposit\_address | Deposit address of the send on the block chain |
| payer\_wallet.type             | Type of wallet used like Ethereum , Tron etc   |

<br />

<Image align="center" className="border" border={true} src="https://files.readme.io/74e3662-image.png" />
