---
title: Integrating only for Cards
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
If you're planning to use Tazapay exclusively for collecting card payments then you can further optimise the payment experience by using the Card Checkout.

Follow below steps to provide a delightful payment experience to your customers:

### Step 1: Initialise Tazapay SDK

While initialising the SDK the checkout method can accept a payment object.

1. The payment object requires a Public key. This can be found on Tazapay dashboard, under API Keys section.
2. The currency resembles collection currency, that is the currency in which user needs to pay.
3. The layout field can be either inline, two-rows or three-rows.

```javascript
window.tazapay.checkout({
  callbacks: {
    onPaymentSuccess,
    onPaymentFail,
    onValidation: ({errors}) => {
      errors = errors || [];
      hasErrors = Boolean(errors.length);
      // errors ->  array of objects will consist of all the validations.
      // before calling confirmCardPayment, You can disable or enable the payment button 
      // or display the custom error messages by checking the hasErrors variable and errors data.
    }
  	...
  },
  payment: {
      key: "<YOUR_PUBLIC_KEY>",
      method: "card",
      currency: "USD",
      country: "US",
      origins: 'https://your.site,https://your.host.site',
      layout: 'inline',
  }
}
```

### Step 2: Listen for Click event on the Pay button

You can use the native inbuilt pay button or your own custom pay button

#### Step 2A: Using native inbuilt button

1. Whenever user clicks on the inbuilt pay button a PaymentClicked event is triggered
2. Add a callback for onPaymentClicked event
3. Use this event to generate the client token by calling your backend services.
4. Once Client Token is available, you can proceed with the payment (Step 3).

```javascript
window.tazapay.checkout({
  callbacks: {
    onPaymentClicked: () => {
    	// Call your backend service to get the client_token
      // Then use the client token to continue the payment > Step 3
    },
  	...
  },
  payment: {
      ...
  }
}
```

#### Step 2B: Using custom pay button

1. Use the config option to hide the inbuilt button.
2. When user clicks on your custom button, generate the client token by calling your backend services.
3. Once Client Token is available, you can proceed with the payment (Step 3).
4. You can update the state of your custom button by listening to PayButtonState event.

```javascript
window.tazapay.checkout({
  callbacks: {
    onPayButtonState: ({ payload:state })=>{
      console.log('State changed',state.disabled,state.progress);
    },
  	...
  },
  payment: {
      ...
  },
  config: {
    customPayButton: true
  }
}
```

### Step 3: Trigger the payment flow

Once the client_token is available, use the confirmCardPayment method from SDK to trigger the payment flow.

1. Pass the client token to SDK via confirmCardPayment method
2. Additionally pass the billing details object

```javascript
window.tazapay.confirmCardPayment({
    clientToken: '<CLIENT_TOKEN>',
    billingDetails: {
      name: "",
      address: {
        line1: "",
        line2: "",
        city: "",
        state: "",
        country: "US",
        postal_code: "",
      },
      phone: {
        country_code: "",
        number: "<10_DIGITS>",
      }
    }
})
```

### Step 4: Handle payment errors

There are various scenarios that can lead to an error while processing the payment. You can monitor such errors using the PaymentError event.

1. The PaymentError event can be used to show custom styled error messages.
2. It can also be used to update the application state.
3. By default, the error messages will be displayed in the payment section. This can be disabled by setting hideErrors config option to true.

```javascript
window.tazapay.checkout({
  callbacks: {
    onPaymentError: ({ payload:error })=>{
      console.log('Error occured',error.code,error.title,error.message);
    }
  },
  payment: {
    ...
  },
  config: {
    hideErrors: true
  }
```

### Step 5: Use Style configuration

You can use style configurations to customise most of the user interface elements. Please check the [style guide.](https://docs.tazapay.com/reference/input-styles)