---
title: Integrating Cards for Payin api
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
If you're planning to use Tazapay exclusively for collecting card payments then you can further optimize the payment experience using the Card Payin.

Here are the steps you need to follow to integrate the card-only option on your website

# Step 1: Include Tazapay’s Javascript (JS) file (client-side)

Add the below snippet to your application to load Tazapay’s Javascript SDK

### Sandbox (test environment)

`<script type="text/javascript" src="https://js-sandbox.tazapay.com/v3.js"></script>`

### Production (live environment)

`<script type="text/javascript" src="https://js.tazapay.com/v3.js"></script>`

> 🚧 Dynamic Injection
> 
> Before injecting the SDK JS dynamically, please use the following event listener to determine when the script has finished loading.
> 
> ```
> window.addEventListener('tazapaySDKReady', () => {
> // continue to use library by following below from step 2 here
> });
> ```

# Step 2: Initialise Tazapay SDK

Keep the division tag in your application to load the card collection UI component.

```Text Division Tag
<div id="payin-card"></div>
```

Use window.tazapay(publishableKey) to create an instance of the Tazapay object. The Tazapay object is your entry point to the rest of the Payin.js SDK.

1. Please refer to the list of configurations for the card UI [guide](https://docs.tazapay.com/reference/additional-details-1#1-cards-configuration), check the description, and use the configuration according to your use case.
2. Please refer to the list of events for the card UI [guide](https://docs.tazapay.com/reference/additional-details-1#2-cards-events), check the description, and use the events according to your use case.

```javascript
const initiateTazapaySDK = async () => {
	try {
    // public key can be found on the Tazapay dashboard, under the settings -> API Keys section.
		const tazapayInstance = await window.tazapay("public_key");
		const embedsInstance = tazapayInstance.embeds();

		let configuration = {
			styles: {},
			showLabels: false,
			hideErrors: false,
			layout: "two-rows",
			cvvMask: true,
			customPayButton: false,
		};

		const cardEmbed = embedsInstance.create("card", configuration);

    // Card Events, Please check events list and use
		cardEmbed.on("ready", () => {
			// this event is to check if iframe is loaded
		});

		cardEmbed.mount("payin-card");
	} catch (error) {
		// payin sdk errors
	}
};
```

# Step 3: Listen for the Click event on the Pay button

You can use the native inbuilt pay button or your own custom pay button

### Using the native inbuilt button

Whenever the user clicks on the inbuilt pay button a "payButtonClick" event is triggered. By using this event trigger step4.

```javascript
cardInstance.on("payButtonClick", (d) => {
	// inbult pay button is clicked
});
```

### Using the custom pay button

1. Use the config option to hide the inbuilt button.
2. You can update the state of your custom button by listening to the "change" event. Show the pay button only if `complete` is true. And trigger step4 when the customer clicks that pay button.

Please refer to the details for the `change` event object [guide](https://docs.tazapay.com/reference/additional-details-1#2-cards-events).

```javascript
cardEmbed.on('change', function(event) {
  // here event will return this object for example:-
 event =>  {
    complete: true,
    scheme: 'visa',
    embedType: 'card',
    empty: false,
    error: undefined,
    value: { cardholder_name: "" },
  } 
});
```

# Step 4: Trigger the payment flow

once the user clicks the pay button do the following steps.

## Step 4A: Fetching client_token for a session (server-side)

> 👍 Idempotent Payin Sessions
> 
> It is required for you to make sure that the requests to create payin are idempotent. As idempotency key, you can pass the unique order number on your system. You can refer this [guide](https://docs.tazapay.com/reference/idempotent-requests) for the implementation.
> 
> This will ensure only unique payin are created corresponding to a unique customer journey on your website/application.

You can fetch the client_token from the response of the create Payin API. Please refer to the [guide](https://docs.tazapay.com/reference/create-payin) for creating a Payin session.

```Text Create Payin Response
{
    "status": "success",
    "message": "",
    "data": {
        "client_token": "RMkE8f2FJuRLTZbh-NyEiYoEOEMbwOS4zMbMwFUTTs=",
    }
}
```

## Step 4B: Call confirmPayment() method

Once you get "client_token", use the confirmPayment method from SDK to trigger the payment confirmation.

1. Need to pass the below details:-
   1. `client_token` which you get from creating a Payin API response.
   2. `payment_method_details`which should contain the `type` as card and `card`object where need to pass the cardEmbed, a variable used in step2, which holds the card instance created.
   3. `customer_details` and `billing_details`Only If the buyer's country is the US or CA. Please refer to this [guide](https://docs.tazapay.com/reference/confirm-payin) for the value structure for the customer and billing details.

> 👍 Billing Details Validation
> 
> It is required for you to make sure that the billingDetails passing are validated from your side. Here are the [validation rules](https://docs.google.com/document/d/19QEKZ0bq1T-Qm9y4Lgj-cOEHWx-h2-rf0sCAtYxNul8/edit) we follow to validate billing details, we recommend that you implement these rules on your end to validate details as the customer adds billing information, ensuring a seamless payment flow.

2. Additionally, you can pass a few other details if required in the SDK payload. Please refer to the body params [guide](https://docs.tazapay.com/reference/confirm-payin) for the additional payloads.
3. Handle the confirmPayment results according to your use-case and for the payment status rely on the [webhook](https://docs.tazapay.com/reference/webhooks-intro) you passed `webhook_url` on creating Payin or on this confirmPayment SDK method.

```javascript
const details = {
  payment_method_details: {
    type: "card",
    card: {
      card: cardEmbed, // cardEmbed is a variable which contains card instance, assigned in step2.
    },
  },
	customer_details: {
    country: "",
    email: "",
    name: "",
    phone: {
      calling_code: "",
      number: ""
    }
  },
	billing_details: {
    name: "",
    address: {
      line1: "",
      line2: "",
      city: "",
      state: "",
      country: "",
      postal_code: "",
    },
    phone: {
      country_code: "",
      number: "",
    }
  }
  
  // pass any other additional details mentioned in 3rd point.
};
  
tazapayInstance.confirmPayment(client_token, details) // tazapayInstance is a variable in step2.
  .then((resp) => {
    console.log("confirmPayment promise resolved: ", resp);
    // handle payment success flow, like redirecting to success/thankyou page etc.
	})
  .catch((error) => {
    console.log("confirmPayment promise rejected: ", error);
    // handle payment error, like display error message if it caused by customer, stop custom pay button loading, etc.
	});

```