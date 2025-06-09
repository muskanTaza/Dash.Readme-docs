---
title: Authentication
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
The Tazapay API uses <a href="https://en.wikipedia.org/wiki/Basic_access_authentication" target="_blank">Basic Access Authentication</a> or `BASIC AUTH` to authenticate requests. When you sign up for an account, you can view and manage your keys on <a href="https://dashboard.tazapay.com" target="_blank">the Tazapay dashboard</a>. Tazapay API provides you with two types of keys, the API_Key and the API_Secret. You will need to authenticate by providing the base64 encoded key pair in the request Authorization header. 

> 📘 
> 
> Tazapay has separate keys for both test and live environments. Test keys can be generated automatically by logging into the <a href = "https://dashboard-sandbox.tazapay.com/" target = "_blank">sandbox dashboard</a> and live keys by logging into the <a href = "https://dashboard.tazapay.com" target = "_blank">live dashboard</a> after clearing KYB.

All requests to Tazapay API must be made over HTTPS. Requests over HTTP will fail. Requests without authentication will also fail.

<i>NOTE: To go from test mode to live mode, you need to change the endpoint URL along with changing the API keys.</i>

> 🚧 API_Secret key is "secret" for a reason!
> 
> Do not share your API keys to any unauthorised parties. This includes publicly accessible areas such as GitHub, client-side code, etc.  An unauthorised party can create transactions on your behalf if they get a hold of your API keys.

### How to Authenticate

1. `BASIC AUTH` requires a username and a password combined with a colon. Its format is <b>{{username}}:{{password}}</b>.

   <b>NOTE:</b> Your API_Key will serve as the username <<user>> and the API_Secret <<pass>> as the password.

2. The resultant value is encoded into a <a href="https://en.wikipedia.org/wiki/Base64" target="_blank">Base64</a> format.

3. Prefix the Base64 encoded value with <b>Basic</b> and pass it in the <i>Authorization</i> header. 

### Example

1. If your API keys are:

```text API Keys
API_Key : F2W7H8JWMO8398KAPW85
API_Secret : rKHFAffLq5Lnrms3mOBQi71oQmMATH2EByYDyIR2Wd0jGdKeed08WThGVS6v1257
```

2. Following the `BASIC AUTH` format, the value generated is:

```text BASIC AUTH format
F2W7H8JWMO8398KAPW85:rKHFAffLq5Lnrms3mOBQi71oQmMATH2EByYDyIR2Wd0jGdKeed08WThGVS6v1257
```

3. <a href="https://www.base64encode.org/" target="_blank">Encoding the above value</a> into Base64, the resultant value generated is:

```text Base64 value
RjJXN0g4SldNTzgzOThLQVBXODU6cktIRkFmZkxxNUxucm1zM21PQlFpNzFvUW1NQVRIMkVCeVlEeUlSMldkMGpHZEtlZWQwOFdUaEdWUzZ2MTI1Nw==
```

4. Include this Base64 value in the Authorization header with Basic prefix:

```text Authorization header
Authorization: Basic RjJXN0g4SldNTzgzOThLQVBXODU6cktIRkFmZkxxNUxucm1zM21PQlFpNzFvUW1NQVRIMkVCeVlEeUlSMldkMGpHZEtlZWQwOFdUaEdWUzZ2MTI1Nw==
```