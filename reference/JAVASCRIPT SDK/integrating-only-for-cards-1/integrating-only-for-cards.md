---
title: Integrating only for Cards
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
If you're planning to use Tazapay exclusively for collecting card payments then you can further optimize the payment experience using the Card Checkout.

Here are the steps you need to follow to integrate the card-only option on your website

# Step 1: Include Tazapay’s Javascript (JS) file (client-side)

Add the below snippet to your application to load Tazapay’s Javascript SDK

### Sandbox (test environment)

`<script type="text/javascript" src="https://js-sandbox.tazapay.com/v2.0-sandbox.js"></script>`

### Production (live environment)

`<script type="text/javascript" src="https://js.tazapay.com/v2.0.js"></script>`

# Step 2: Initialise Tazapay SDK

### Step 2A: Div Container

Keep the division tag in your application to load the card collection UI component.

```Text Division Tag
<div id="tz-checkout"></div>
```

### Step 2B: Checkout Method

While initializing the SDK the checkout method can accept a payment object.

1. The payment object requires a Public key. This can be found on the Tazapay dashboard, under the settings -> API Keys section.
2. The currency resembles collection currency, that is the currency in which the user needs to pay.
3. The layout field can be either inline, two-rows or three-rows.
4. Refer to the details of the origins mentioned [here](https://docs.tazapay.com/reference/additional-details#1c-config) and provide the necessary details.

```javascript
window.tazapay.checkout({
   callbacks: {
      onPaymentSuccess : (msg) => { console.log("payment succeeded") },
      onPaymentFail : (msg) => { console.log("payment failed") },
      onValidate: (results) => { console.log("validation results", results) }
      ...
    },
    payment: {
      key: "<YOUR_PUBLIC_KEY>",
      method: "card",
      currency: "USD", // collection currency
      country: "US",
      layout: 'two-rows'(default), // optional
    },
    config: { // optional
    	origins: 'https://embeddedSite.com,https://parentSite.com', // check details as follows in step 4.
    },
    style: {}, // optional, for customising your integration, refer step 7.

}
```

# Step 3: Listen for the Click event on the Pay button

You can use the native inbuilt pay button or your own custom pay button

### Step 3A: Using the native inbuilt button

1. Whenever the user clicks on the inbuilt pay button a PaymentClicked event is triggered
2. Add a callback for the onPaymentClicked event.
3. Use this event to validate the details mentioned in step 4.

```javascript
window.tazapay.checkout({
  callbacks: {
    onPaymentClicked: () => {
    	// Trigger window.tazapay.validate() method as per step 4.
    },
  	...
  },
  payment: {
      ...
  }
}
```

### Step 3B: Using the custom pay button

1. Use the config option to hide the inbuilt button.
2. When the user clicks on your custom button, validate the details mentioned in step 4.
3. You can update the state of your custom button by listening to the PayButtonState event.

> 🚧 
> 
> If you are using a custom payment button, to avoid potential issues such as multiple clicks or double debits, utilize our PayButtonState event to accurately retrieve button states (similar to those we provide for our built-in button). 
> 
> You should only enable your Pay button once the customer has passed all the validations and there are no `validation failed` events. 
> 
> You should make sure to call the confirmCardPayment() function only after you have disabled the custom pay button. Only enable the pay button after you receive an error callback.

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

# Step 4: Validate Details

Validate the payment payload before creating a transaction.

### Step 4A: Validate Method

> 👍 Billing Details Validation
> 
> It is required for you to make sure that the billingDetails passing are validated from your side. Here are the [validation rules](https://docs.google.com/document/d/19QEKZ0bq1T-Qm9y4Lgj-cOEHWx-h2-rf0sCAtYxNul8/edit) we follow to validate billing details, we recommend that you implement these rules or validate method on your end to validate details as the customer adds billing information, ensuring a seamless payment flow.

1. By default card details will be validated by calling the validate method.
2. If you need to validate the billing details, pass the details in the validate method.

NOTE: The billingDetails validation is required for US and CA customers. For the rest of the customers no need to validate/pass billingDetails in the validate method.

```javascript
// for validating card details alone.
window.tazapay.validate()

----------- or ----------

// for validating card details and billingDetails.
// for US and CA country, billingDetails is required. provide details as below.
window.tazapay.validate({
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

### Step 4B: Handle Validation Results

1. Once the details are validated, the Validate event is triggered with the results.
2. Add a callback for the onValidate event and use this event to handle validated results.
3. In the onValidate callback, check validation by card.isValid, billingDetails.isValid(optional) (which is required validation only for US, and CA Customer transactions.)
   1. if all the fields validated are true. then proceed to step 5.
   2. else handle errors received in card.errors and billingDetails.errors. It's an array of objects, each object contains a name representing a field name, label represents an error label. And get the correct details from the customer and validate again.

```javascript javasc
window.tazapay.checkout({
    callbacks: {
      onValidate: (results) => {
        
        // below are the sample result structure.
        results contains a object => {
          card: { // by default contains card field.
            isValid: true/false,
            errors: [
              {
                name: "cvv", // field name
                label: "Cvv is Required" // error label
              }
              ...
            ]
          },
          billingDetails: { // details available, if passed in validate method to validate.
            isValid: true/false,
            errors: [
              {
                name: "state", // field name
                label: "state is Required" // error label
              }
              ...
            ]
          }                  
        }
        
        // below, if condition is based on info provided to validate.
        // if billingDetails not passed ignore that in condition.
        if(card.isValid && billingDetails.isValid){
          do step 5.
        }else{
          handle validated error results.
          like show error.label in UI for respective error.name field 
          and get correct details from customer and validate again.
        }
        
      }
      ...
    },
     payment: {},
}

```

# Step 5: Trigger the payment flow

Once all details validated are valid proceed payment flow

### Step 5A: Fetching token for a session (server-side)

> 👍 Idempotent Checkout Sessions
> 
> It is required for you to make sure that the requests to create checkout sessions are idempotent. As idempotency key, you can pass the unique order number on your system. You can refer <a href = "https://docs.tazapay.com/reference/idempotent-requests" target="_blank">this guide</a> for the implementation.
> 
> This will ensure only unique checkout sessions are created corresponding to a unique customer journey on your website/application.

You can fetch the token from the response of the checkout session. Please refer to [this document](https://docs.tazapay.com/docs/checkout-intro) for creating a checkout session.

```Text Checkout API response
{  
  "status": "success",  
  "message": "Payment Link created successfully",  
  "data": {  
     "token": "TqT3aDYXn6bqRuyrR6zeef15E_E7wEjWT9w_fQl_ZgHTjwwONIeOivCBV83bWHBXR9"  
  }  
}
```

The token can be passed to your client-side (or Front End) to instantiate Tazapay’s Javascript SDK which will allow Tazapay to know the unique transaction for which the customer is making the payment.

### Step 5B: ConfirmCardPayment Method

Once the token is available, use the confirmCardPayment method from SDK to trigger the payment flow.

1. Pass the token in the clientToken field, to SDK via confirmCardPayment method.
2. Additionally, pass the validated billing details( in Step 4) object only for US and CA customer country transactions.

```javascript
window.tazapay.confirmCardPayment({
    clientToken: '<TOKEN>',
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

# Step 6: Handle payment errors

Various scenarios can lead to an error while processing the payment. You can monitor such errors using the PaymentError event.

1. The PaymentError event can be used to show custom-styled error messages.
2. It can also be used to update the application state.
3. By default, the error messages will be displayed in the payment section. This can be disabled by setting the hideErrors config option to true.

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
})
```

# Step 7: Use Style configuration

You can use style configurations to customize most of the user interface elements. Please check the [style guide.](https://docs.tazapay.com/reference/input-styles)

# Step 8: Additional Details

Please take a look at this [additional details](https://docs.tazapay.com/reference/additional-details) page for more details regarding the fields and methods used in the integration flow to understand its use case in-depth and add it to the flow.