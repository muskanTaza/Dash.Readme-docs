---
title: Using Basic Auth on API Docs
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
## Sandbox URL

All APIs sent on the documentation will be linked to the sandbox to allow testing and prevent real, accidental transactions from happening.

You'll need to use the API keys from our [Sandbox](https://sandbox.tazapay.com) instead of using your Production API keys.

## Basic Auth

Tazapay's APIs uses basic auths, but the nomenclature for authentication headers on our API docs is different from production.

### Username

This is where you will enter your API key. This is the random set of strings after access to API is granted.

### Password

Your secret key is your password. The random string from the secret key is longer than the API key.