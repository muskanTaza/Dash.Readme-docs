---
title: Integrating Client-Side
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
The integration can be completed in three steps:

1. Include Tazapay’s JavaScript (JS) file (client-side)
2. Fetch token for a payment session (server-side)
3. Instantiate Tazapay’s Javascript SDK using the token (client-side)

# Step 1: Include Tazapay’s Javascript (JS) file (client-side)

Add the below snippet to your application to load Tazapay’s Javascript SDK

### Sandbox (test environment)

`<script type="text/javascript" src="https://js-sandbox.tazapay.com/v2.0-sandbox.js"></script>`

### Production (live environment)

`<script type="text/javascript" src="https://js.tazapay.com/v2.0.js"></script>`

# Step 2: Fetching token for a session (server-side)

You can fetch the token from the response of the checkout session. Please refer to [this document](https://docs.tazapay.com/docs/checkout-core-concept) for creating a checkout session.

```Text Checkout API response
{  
  "status": "success",  
  "message": "Payment Link created successfully",  
  "data": {  
     "token": "TqT3aDYXn6bqRuyrR6zeef15E_E7wEjWT9w_fQl_ZgHTjwwONIeOivCBV83bWHBXR9"  
  }  
}
```

The token can be passed to your client side (or Front End) to instantiate Tazapay’s Javascript SDK which will allow Tazapay to know the unique transaction for which the customer is making the payment.

> 🚧 Your API keys are your responsibility
> 
> Since the checkout API involves using your API keys, the checkout session should always be created on your server-side. Do not share your API keys to any unauthorised parties. This includes publicly accessible areas such as GitHub, client-side code, etc. An unauthorised party can create transactions on your behalf if they get a hold of your API keys.

# Step 3: Instantiate Tazapay’s Javascript SDK using token (client-side)

Once you have loaded Tazapay’s Javascript file into your client-side application using Step 1, you can instantiate Tazapay’s UI component for that particular payment using the clientToken that you have passed onto your client side (Refer Step 2).  
You can refer to the following code snippets to instantiate Tazapay’s UI component on your website/application for a particular checkout session:

- Keep the division tag in your application to load the UI component.
  ```Text Division Tag
  <div id="tz-checkout"></div>
  ```
- Instantiate UI component for checkout using token and other parameters

  ```Text Instantiation
  const options = {
    clientToken: token, // Use the token obtained at step2.
    callbacks: {
      onPaymentSuccess: () => { console.log ("success") }, 
      onPaymentFail: () => { console.log ("fail") },
      onPaymentMethodSelected: () => { console.log ("onPaymentMethodSelected") }, // optional
      onPaymentCancel: () => { console.log ("onPaymentCancel") }, // optional
    },
    style: {}, // optional, for customising your integration,
    config: {
      redirectionTarget: "self" // optional -> "self" or "new_window"
      popup: false // optional -> true or false // by default iframe will be embedded
      origins: 'https://your.siteOrigin,https://your.host.siteOrigin', // required only, if tazapay iframe embedded site(your site) is loaded inside an another site/iframe(your host site).
    },
  };

  window.tazapay.checkout(options);


  ```