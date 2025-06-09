---
title: Integrate with risk SDK
excerpt: This allows you to integrate with risk SDK and fetch the `session_id`
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
For the best performance of Tazapay's Fraud Detection system, you should integrate the risk SDK into every payment process initiated by shoppers. It captures advanced signals that are leveraged in Tazapay's fraud model. These signals include:

- Device Identification
- Geolocation
- Spoofing Attempts
- Fingerprinting Data

# How it works

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/fc3ef89-image.png",
        null,
        ""
      ],
      "align": "center",
      "border": true
    }
  ]
}
[/block]


# Integrate the risk SDK

## Set up tazapay.js

```Text Production (livemode)
<head>
  <title>Checkout</title>
  <script type="text/javascript" src="https://js.tazapay.com/v3.js"></script>
</head>
```
```Text Sandbox (Testmode)
<head>
  <title>Checkout</title>
  <script type="text/javascript" src="https://js-sandbox.tazapay.com/v3.js"></script>
</head>
```

> 🚧 Dynamic Injection
> 
> Before injecting the SDK dynamically, please use the following event listener to determine when the script has finished loading.
> 
> ```
> window.addEventListener('tazapaySDKReady', () => {
> // continue to use library 
> });
> ```

## Initialising tazapay.js with your public key

```html
const tazapay = await window.tazapay('pk_test_TYooMyTiskhfuvdEDq54NiTphI7jx');
```

The above code creates an instance of the Tazapay object. This created object now serves as an entry-point to the rest of Tazapay’s JS SDK.

> You can fetch the public key from the <a href="https://dashboard.tazapay.com"> Tazapay dashboard</a>.

## Retrieve the session_id

When the customer clicks to pay, publish the device data and retrieve the session_id

```Text Javascript
const session_id = await tazapay.publishRiskData();
```

> The function tazapay.publishRiskData() will create a promise when called which resolves into a session_id string.

## Attach the session_id to the transaction

- Pass the session_id to your server.
- Pass the session_id in the API calls to the following depending on your use case
  - <a href = "https://docs.tazapay.com/reference/create-checkout"> Create Checkout</a>
  - <a href = "https://docs.tazapay.com/reference/create-payin"> Create Payin</a>
  - <a href = "https://docs.tazapay.com/reference/confirm-payin"> Confirm Payin</a>
  - <a href = "https://docs.tazapay.com/reference/create-escrow-api"> Create Escrow</a>

<br>