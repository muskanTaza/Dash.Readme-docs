---
title: gopay_idr
excerpt: >-
  GoPay is a leading digital payment platform and the core financial service
  embedded within the Gojek super app (ride-hailing, food delivery, etc.). It's
  a must-have for paying for Gojek services, Tokopedia purchases (since they
  merged), and is widely used for online/offline transactions, bill payments,
  and transfers. Its strength is its deep integration with the Gojek ecosystem.
deprecated: false
hidden: true
metadata:
  robots: index
---
## **Key Features**

* Payouts are **instant (real-time)**
* **Maximum limits** – as per [Tazapay payout limits sheet](https://docs.google.com/spreadsheets/d/18spHpXBEUqLTQ8dczM9YYQsJID0ysSWGszov7ctHxuM/edit#gid=0)
* **Available 24/7**, including weekends and holidays

## **Building an Integration**

### **Step 1: Initiate a payout request**

Tazapay uses a **payout object** to represent your intent to initiate a payout. The payout object tracks state changes from initiation to the moment the beneficiary’s e-wallet account is credited.

Create a payout on your server using **Tazapay’s Payout API** with the following information:

* **Payout Amount** – The amount in local currency (IDR) to transfer
* **Beneficiary Details**
  * **Name**
  * **Type** – `business` or `individual`
* **Destination Details**
  * **Destination Type**: `local_payment_network`
  * **E-wallet Type**: `gopay_idr`
  * **Deposit key type**: `phone`
  * **Deposit key**: `+62 XXXXXXXXXX`
* **Reason for Payout**
* **Transaction Description** – Additional description for the payout

## **Validations for E-Wallet Account Number**

Proper error handling must be implemented for cases where validations fail.

| Country            | Description                      | Validation                                                                                                                                    | Example                          |
| :----------------- | :------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- | :------------------------------- |
| **ID – Indonesia** | E-Wallet account number (mobile) | Must be a valid Indonesian mobile number:^(?:\+62\|62\|0)8[1-9][0-9]{6,9}$Starts with +62/62/0 followed by 8; total 9–12 digits after prefix. | `+628123456789` or `08123456789` |

<Callout icon="❌" theme="default">
  ### Invalid examples: +627123456789 (wrong for ID)
</Callout>

##
