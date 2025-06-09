---
title: Refund
excerpt: >-
  Explore Tazapay's refund management through our API. This guide details how to
  initiate, update, and monitor refunds, catering to scenarios like full and
  partial transaction reversals
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## Refund Overview

A refund is a reversal of a payment transaction, returning the funds to the customer. This can occur under several circumstances:

* **Cancelled Order**: A refund is issued if the buyer cancels the order before it's fulfilled.
* **Product Return**: If a buyer returns a product due to dissatisfaction or a defect, a refund is processed.
* **Failed Transaction**: Refunds are automatically initiated if a payment fails due to technical issues, insufficient funds, or other reasons.
* **Disputed Transaction**: When a payment dispute or chargeback is raised, a refund may be issued pending resolution.
* **Overpayment**: If a buyer overpays or makes duplicate payments, the excess amount is refunded.

Tazapay processes refunds back to the original payment method used by the buyer.

## Types of Refunds

* **Full Refund**: The entire transaction amount is returned to the customer.
* **Partial Refund**: Only a specific portion of the transaction amount is returned, not exceeding the total originally paid.

## Initiating Refunds

Refunds can only be initiated by the merchant. This request can be done in two ways:

### 1\. Via API

Tazapay provides several API endpoints to manage refunds:

* **Initiate Refund**: Start the refund process by providing transaction details. [Initiate Refund API Documentation](https://docs.tazapay.com/reference/refund-api)
* **Update Refund**: Modify details of an existing refund. [Update Refund API Documentation](https://docs.tazapay.com/reference/update-refund)
* **Fetch Refund Status**: Check the current status of a refund. [Fetch Refund Status API](https://docs.tazapay.com/reference/refund-status-api)
* **Cancel Refund**: Cancel a previously initiated refund. [Cancel Refund API Documentation](https://docs.tazapay.com/reference/cancel-refund)

### 2\. Via Dashboard

The step-by-step guide is outlined [here](https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard).

## Refund Eligibility by Payment Methods

Please note that refunds may not be available for all payment methods. See [this list](https://support.tazapay.com/what-payment-methods-are-supported-and-unsupported-for-refunds) to check refund availability on a specific payment method.

## Refunds failing due to incorrect/missing phone numbers

Incase your refunds are failing due to missing or incorrect phone numbers. You can use the customer api to update the phone number of the customer. Check the customer update API - [Update Customer API](https://docs.tazapay.com/reference/get-user-by-id-api)

You can also update customer's phone number via dashboard.

Step 1 -> Navigate to the customer tab

Step 2 -> Select the edit button against the customer you want to update the details for 

<Image align="center" src="https://files.readme.io/d3217a63452f18f4daa173df9dbb29cd7d464462f8ad49016f29c6b3845666ad-Screenshot_2025-03-20_at_5.19.26_PM.png" />

Steps 3 -> Update the phone number and confirm

<Image align="center" src="https://files.readme.io/006e97f60b98d4c2f5f5a30556ea74a8c4f7cdc7749a1f783d10137bf5a35d4e-Screenshot_2025-03-20_at_5.20.24_PM.png" />

Step 4 -> Now you can try re-initiating the refund
