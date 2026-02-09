---
title: Flow
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

# Step 1: Set up tazapay.js

The Card Embed is automatically available as a feature of tazapay.js. Include the tazapay.js script on your checkout page by adding it to the head of your HTML file. Always load tazapay.js directly from js.tazapay.com to remain PCI compliant. Don’t include the script in a bundle or host a copy of it yourself.

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
> // continue to use library by following below from step 2 here
> });
> ```

# Step 2:  Initialising tazapay.js

```html
const tazapay = await window.tazapay('pk_test_TYooMyTiskhfuvdEDq54NiTphI7jx');
```

The above code creates an instance of the Tazapay object inside the merchant’s client-side project. This created object now serves as an entry-point to the rest of Tazapay’s JS SDK.

# Step 3: Add the card embed to your payment page

The `Card Embed` needs a place to live on your payment page. Create an empty DOM node (container) with a unique ID in your payment form:

```Text Javascript
<form id="payment-form">
  <div id="card-embed">
    <!-- Embed will create form here -->
  </div>
  <button id="submit">Submit</button>
  <div id="error-message">
    <!-- Display error message to your customers here -->
  </div>
</form>

```

# Step 4: Create an instance of the card embed and mount it to the already created DOM containers

```Text Javascript
const embeds = tazapay.embeds();

let configuration = {
	style: {},
	showLabels: false,
	hideErrors: false,
	layout: "two-rows",
	cvvMask: true,
	customPayButton: false,
}

const card = embeds.create("card",configuration);

card.mount("card-embed");
```

* The mount function is a part of the library which attaches the UI component to the DOM container with unique ID.
* This mounting of the card component does require the existence of a client_token which is a unique reference for the transaction.

## Configurations

You can pass the following configurations while instantiating the card embed.

| Property          | Description                                                                                                                                                                                                                      | Possible Values                                                                                      |
| :---------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------- |
| `style`           | Customize the look of the user interface.                                                                                                                                                                                        | Refer to the style guide <a href="https://docs.tazapay.com/reference/style-customisation"> here</a>. |
| `showLabels`      | Show field labels like Card Number, Expiry Date, and CVV on top of each input field. Off by default; set to true to enable.                                                                                                      | `true`/`false`                                                                                       |
| `hideErrors`      | Hide error messages on the embed as the customer types. Off by default; set to true to hide errors (manage errors in "change" event).                                                                                            | `true`/`false`                                                                                       |
| `layout`          | Arrange the card number, expiry, cvv fields in rows. Default is "two-rows" (card number on top, expiry date and CVV below). Options include "one-row" (all fields in a single row) and "three-rows" (each field on its own row). | `"one-row"`, `"two-rows"`, `"three-rows"`                                                            |
| `cvvMask`         | Mask the CVV field. On by default.                                                                                                                                                                                               | `true`/`false`                                                                                       |
| `customPayButton` | Use a custom pay button instead of the default. Off by default; refer to the integration guide to enable.                                                                                                                        | `true`/`false`                                                                                       |

# Step 5: Listening to events

Tazapay's card embed will automatically validate and display any errors as the customers type. You can listen to <a href="https://docs.tazapay.com/reference/change-event"> these events</a>

# Step 6: Listen for the click event on the Pay button

You can either choose to use your own pay button or use the pay button of the card embed.

## Using the card embed's inbuilt pay button

* The SDK provides an easy-to-use event called "payButtonClick" that gets triggered whenever the user clicks on the "Pay" button. You can "listen" for this event and execute your custom code in response.
* To set up your event listener, you'll need to attach it to the card object.

  ```Text Javascript
  card.on("payButtonClick", function(d) {
     // This code block will run when the inbuilt "Pay" button is clicked.
  });

  ```

## Using your custom pay button

1. First off, let's make sure the inbuilt pay button isn't visible, since you're going to use your own custom button. You can do this by adjusting the `customPayButton` in your configuration in Step 4.
2. Enable the pay button to accept clicks by listening to the `change` event. Show the pay button only if complete is `true`. And trigger Step 7 when the customer clicks that pay button.
   _Additional Guide:<a href="https://docs.tazapay.com/reference/change-event"> Change event</a>_

# Step 7: Submitting the payment to Tazapay to create a charge

Disable the Pay Button for further clicks and perform the following actions once the customer clicks on the Pay Button

## Fetching the client-token (server-side)

1. Submitting the payment to create a charge will require a `client_token` which is the unique identifier for a payin or a customer session on your website/application.
2. This unique token is generated as a response of the payin created by a server call to Tazapay's <a href="https://docs.tazapay.com/reference/create-payin"> payin API</a>.
   ```Text JSON
   {
       "status": "success",
       "message": "",
       "data": {
           "client_token": "RMkE8f2FJuRLTZbh-NyEiYoEOEMbwOS4zMbMwFUTTs=",
       }
   }
   ```

> **Idempotent Payin Sessions:** It is required for you to make sure that the requests to create payin are idempotent. For the value of the idempotency key, you can pass the unique order number on your system.
> You can refer to <a href="https://docs.tazapay.com/reference/idempotent-requests"> this guide</a> for the implementation. This will ensure only unique payin are created corresponding to a unique customer journey on your website/application.

## Call the confirmPayment() method

After you have retrieved the client_token, call the confirmPayment() method from the SDK to submit a payment to Tazapay to create a charge.

The function takes the following parameters as input

| Parameter              | Mandatory / Optional    | Description                                                                                                                                                   |
| :--------------------- | :---------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| client_token           | Mandatory               | Refer response of the payin API                                                                                                                               |
| payment_method_details | Mandatory               | This contains two parameters - `type` and `card`                                                                                                              |
| customer_details       | Conditionally Mandatory | Only required if the customer_details are not passed from the server-side                                                                                     |
| billing_details        | Conditionally Mandatory | Refer to the guide <a href="https://docs.tazapay.com/docs/address-validation"> here</a>.                                                                      |
| success_url            | Mandatory               | The customer will be redirected to this URL after a successful charge creation. The customer may be redirected externally to authenticate themselves for 3DS. |
| cancel_url             | Mandatory               | The customer will be redirected to this URL after a failed charge. The customer may be redirected externally to authenticate themselves for 3DS.              |

```Text Javascript
const details = {
  payment_method_details: {
    type: "card",
    card: {
      card: card, // card is a variable which contains card instance, assigned in step 4.
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
      calling_code: "",
      number: "",
    }
  }
  
  // pass any other relevant fields
};
  
tazapay.confirmPayment(client_token, details) // tazapay is a variable in step 2.
  .then((resp) => {
    console.log("confirmPayment promise resolved: ", resp);
    // handle payment success flow, like redirecting to success/thankyou page etc.
	})
  .catch((error) => {
    console.log("confirmPayment promise rejected: ", error);
    // handle payment error, like display error message if it caused by customer, stop custom pay button loading, etc.
	});


```

# Step 8: Display success / failure message to the customer

`tazapay.confirmPayment()` will return a `Promise` which resolves with a `result` object. The object has either:

* `result.payin`
  * This is returned when the charge (payment) is successful.
  * This essentially contains the response of GET /v3/payin
* `result.error`
  * This is returned when there is an error during payment processing or when a charge fails.
  * The `error` object returns the following properties:

| Field | type   | Description                       |
| ----- | ------ | --------------------------------- |
| error | string | Buyer Comprehension for the error |
| code  | string | Error code                        |

***

In case the customer is redirected to an external site to authenticate, the promise will never resolve and the customer will be redirected to the `success_url` passed by you. Make sure to display appropriate message on your success and failure URLs.

# Step 9: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Use the webhook_url field in the payin API to receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

In case of a failed payment attempt, Tazapay sends a `payment_attempt.failed` event with the reason of failure.

| Event                  | Description                       | Next Steps                                                    |
| :--------------------- | :-------------------------------- | :------------------------------------------------------------ |
| payin.succeeded        | The charge creation is successful | Fulfill the goods or services that the customer purchased     |
| payment_attempt.failed | The charge creation failed        | Re-enable the pay button and allow the customer to pay again. |
