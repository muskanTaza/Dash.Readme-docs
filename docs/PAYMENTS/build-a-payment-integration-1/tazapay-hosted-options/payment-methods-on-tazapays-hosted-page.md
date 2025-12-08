---
title: Payment Methods on Tazapay's Hosted Page
deprecated: false
hidden: true
metadata:
  robots: index
---
# Overview

Tazapay Checkout is a prebuilt, hosted payment page optimized for conversion. It allows merchants to redirect customers to a Tazapay-hosted page where they can select a payment method and complete their purchase. This guide provides an overview of how to integrate Tazapay Checkout, covering setup, customization, and usage.

# Integration Steps

## Step 1: Set up your Tazapay account

Before integrating Tazapay Checkout, ensure you have an approved Tazapay account with API keys available.

## Step 2: Create a Checkout Session

The Checkout Session is the core concept in Tazapay Checkout. It contains all the details about the transaction, such as the amount, currency, customer details and the payment methods.

> Related Link: <a href="https://docs.tazapay.com/reference/create-checkout" target="_blank">Checkout API</a>

### Sample cURL

```Text cURL
curl --request POST \
  --url https://service-sandbox.tazapay.com/v3/checkout \
  --header 'accept: application/json' \
  --header 'authorization: Basic YWtfdGVzaF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
  --header 'content-type: application/json' \
  --data '{
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea@example.com",
    "country": "VN"
  },
  "invoice_currency": "USD",
  "amount": 10000,
  "transaction_description": "1 x T-shirt",
  "payment_methods":["bank_push_vnd"]
}'
```

## Step 3: Redirect customers to Tazapay checkout

Calling the checkout API in Step 2 provides the following response. Redirect the customer to Tazapay's hosted payment page using the URL.

```Text JSON
{
  "status": "success",
  "message": "",
  "data": {
    "amount": 10000,
    "amount_paid": 0,
    "billing_details": null,
    "cancel_url": "",
    "created_at": "2024-07-19T10:11:07.832914998Z",
    "customer": "cus_cq8i3c4j2pdpn2r2lah0",
    "customer_details": {
      "country": "VN",
      "email": "andrea@example.com",
      "name": "Andrea Lark",
      "phone": {
        "calling_code": "",
        "number": ""
      }
    },
    "customer_fee_percentage": 0,
    "expires_at": null,
    "holding_currency": "USD",
    "id": "chk_cqd3nep5ct0u7aakeco0",
    "invoice_currency": "USD",
    "items": [],
    "latest_payment_attempt": "",
    "metadata": null,
    "object": "checkout",
    "paid_in_excess": false,
    "partially_paid": false,
    "payin": "chk_cqd3nep5ct0u7aakeco0",
    "payment_attempts": [],
    "payment_methods": [
      "bank_push_vnd"
    ],
    "payment_status": "unpaid",
    "payment_status_description": "",
    "reference_id": "",
    "remove_payment_methods": [],
    "shipping_details": null,
    "statement_descriptor": "",
    "status": "active",
    "success_url": "",
    "token": "tGxhgHg5USrT3Gizxu-aL-GFF5FhyaCT4KHyXQXcxZE=",
    "transaction_data": [],
    "transaction_description": "1 x T-shirt",
    "transaction_documents": [],
    "url": "https://checkout-sandbox.tazapay.com/transaction/tGxhgHg5USrT3Gizxu-aL-GFF5FhyaCT4KHyXQXcxZE="
  }
}
```

## Step 4: Handle post-payment events

Tazapay sends events to your webhook endpoint to notify you about changes in the Checkout Session status. Set up a webhook endpoint to handle events like checkout.paid.

> Related Links:
>
> 1. List of checkout events
> 2. List of payment attempt events
> 3. Configuring your webhook endpoint on the Tazapay dashboard

# Customisation and Configuration

You can configure the appearance and behaviour of the Checkout Page

## Logo

You can add your logo to the Checkout Page

> Related Guide: Adding logo to the Checkout Page

## Transaction Description

You can add a transaction description to display to the customer on the Checkout Page. This is typically the description of the goods / services the merchant is paying for. Pass appropriate values in the `transaction_description` field in the checkout API.

## Payment Methods

The `payment_methods` field in the checkout API allows you to specify payment methods that you would want for a particular checkout session. The payment methods added to the field would be only surfaced on the hosted payment page.

Additionally, you can also remove payment methods for a particular transaction using the `remove_payment_methods` field.

> **Payment Method Nomenclature**
>
> Each payment method is represented by a unique string in Tazapay. The name for a payment method is the combination of the payment method name and the currency in which the customer is charged. For example, the name for Paynow in Singapore is `paynow_sgd`
>
> Related Links:
>
> 1. List of payment methods supported by Tazapay
> 2. [Collection Methods API](https://docs.tazapay.com/reference/collection-methods-api) - This returns the Tazapay name and other properties of each payment method
