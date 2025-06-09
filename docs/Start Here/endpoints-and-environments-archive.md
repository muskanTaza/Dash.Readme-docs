---
title: Endpoints and Environments
excerpt: >-
  Tazapay has 2 environments for testing and production purposes. The APIs are
  served over https and unencrypted http connections are not supported.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
### Sandbox
You can use this environment to test the transactions and workflows before going Live. You will need to use the following URL for all sandbox API calls: `https://api-sandbox.tazapay.com`
[block:callout]
{
  "type": "info",
  "body": "Money movement, actual verification of documents for escrow completion, and KYB processes will not be available in Sandbox. If needed, we can work with you to mock success and failure responses for specific APIs to test the end to end flow. Please drop a note on api@tazapay.com with your request.  For testing real movement of money and verification of documents and KYB, you can initiate a transaction in the production environment.",
  "title": "Please Note"
}
[/block]
### Production (Live environment)
This is our Live environment where we process real transactions and actual money movement happens. You will need to use the following URL for all production API calls: `https://api.tazapay.com`