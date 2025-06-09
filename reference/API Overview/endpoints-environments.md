---
title: Endpoints and Environments
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
Tazapay API is served over <a href = "https://en.wikipedia.org/wiki/HTTPS" target="_blank">HTTPS</a> and unencrypted HTTP connections are not supported. Tazapay API has the following endpoints:

###Live mode (Production)
This is our Live environment where we process real transactions and actual money movement happens. You will need to use the following URL for all live mode API calls: https://api.tazapay.com.

###Test Mode (Sandbox)
You can use this environment to test the transactions and workflows before going Live. You will need to use the following URL for all sandbox API calls: https://api-sandbox.tazapay.com. The Tazapay API docs allow you to test our API. While using the docs to test APIs, you are using our test environment.
[block:callout]
{
  "type": "info",
  "body": "Money movement, actual verification of documents for escrow completion, and KYB processes will not be available in Sandbox. If needed, we can work with you to mock success and failure responses for specific APIs to test the end to end flow. Please drop a note on <a href = \"mailto: support@tazapay.com\" target=\"_blank\">support@tazapay.com</a> with your request. For testing real movement of money and verification of documents and KYB, you can initiate a transaction in Live mode.",
  "title": "Mocking Scenarios in Test Mode"
}
[/block]