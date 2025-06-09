---
title: Payments
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
| ERROR CODE | Meaning                                                                                                                                                                                                                                                            |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1500       | The specified txn\_no could not be found                                                                                                                                                                                                                           |
| 1501       | Unable to save the payment session in the database                                                                                                                                                                                                                 |
| 1502       | A required field is missing in the parameters, check our payment API body parameters for required fields                                                                                                                                                           |
| 1503       | Percentage value should be between 0 and 100                                                                                                                                                                                                                       |
| 1516       | Your account is not associated with this transaction/escrow                                                                                                                                                                                                        |
| 1805       | Error updating requested currency                                                                                                                                                                                                                                  |
| 1806       | Invalid escrow state to initiate payment                                                                                                                                                                                                                           |
| 1807       | Payment provider not supported at the moment                                                                                                                                                                                                                       |
| 1808       | Error fetching the seller wallet details for payouts                                                                                                                                                                                                               |
| 1809       | Error creating seller wallet. Please try again, or try a different payment method. eg: If user selected any Rapyd payment options like Paynow QR, Bank Transfer, Prompay, Bank Direct, we used to create a wallet for seller. If that fails, throw this error code |
| 1810       | Error adding wallets to the payment. Please try again, or try a different payment method.                                                                                                                                                                          |
| 1811       | Error saving transaction logs                                                                                                                                                                                                                                      |
| 1812       | Payment failed. Please try again later.                                                                                                                                                                                                                            |
| 1813       | Error fetching collection method                                                                                                                                                                                                                                   |
| 1814       | Error saving payment                                                                                                                                                                                                                                               |
| 1815       | Failed to update payment state                                                                                                                                                                                                                                     |
| 1816       | Error while fetching wallex payment methods                                                                                                                                                                                                                        |
| 1818       | Currency not supported. The requested invoice currency is not supported in the buyer country/seller country's corridor. E.g., INR is not supported in the IN-US corridor                                                                                           |
| 1819       | Payment method not supported. Check for our payment methods in GET collection or GET disburse                                                                                                                                                                      |
| 1820       | Error getting seller trusted flag. Please use a different payment method from cards in the meantime.                                                                                                                                                               |
| 1821       | Error setting user login credentials                                                                                                                                                                                                                               |
