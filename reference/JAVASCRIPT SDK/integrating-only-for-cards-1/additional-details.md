---
title: Additional Details
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
## 1. Checkout Method

Here is the list of objects used in the checkout method to initialize the iframe.

### 1A: callbacks

Here is the list of events available in which you can add callback and handle results.

1. **PaymentSuccess**: This event is triggered once payment is successful. This event is used to notify you regarding payment success. You can add callback and handle things like redirecting to the Thankyou/Order Summary page, etc.
2. **PaymentFailed**: This event is triggered once payment is failed. This event is used to notify you regarding payment failure.
3. **PaymentClicked**: This event is triggered once the In-built pay button is triggered by the customer. This event is used to notify you regarding payment initiation. You should add a callback and validate the details mentioned in [step 4](https://docs.tazapay.com/reference/integrating-only-for-cards#step-4-validate-details).
4. **Validate**: This event is triggered once the validation is done. This event is used to get the validated results. You should add a callback and handle the validated results as mentioned in [step 4B](https://docs.tazapay.com/reference/integrating-only-for-cards#step-4b-handle-validation-results).
5. **PayButtonState**: This event is triggered whenever the button state(disabled, progress) changes. This event is used for the merchant who is using their own button instead of the in-built button. You can add callback and handle things like progress and disabled state which we provide based on our handling.
6. **PaymentError**: This event is triggered whenever an error occurs(except validation errors) in the overall flow. This event is used to notify the error with an error message.  You can add a callback and handle errors mentioned in [step 6](https://docs.tazapay.com/reference/integrating-only-for-cards#step-6-handle-payment-errors).

### 1B: payment

Here is the list of payment info available.

1. **key**: Need to send the public key here. which you can get from the Tazapay dashboard, under the settings -> API Keys section. Quick links [sandbox](https://dashboard-sandbox.tazapay.com/settings/api) and [production](https://dashboard.tazapay.com/settings/api)
2. **method**: For now only card payment is available in s2s, so by default needs to be sent as a `card`.
3. **currency**: It resembles collection currency, that is the currency in which the customer/user needs to pay.
4. **country**: It resembles the customer/user country, that is the country from which the customer pays.
5. **layout**: It is an optional field. By default, the value will be two-rows. means the card number will be in the first row and the expiration date, cvv will be in the second row.\
   inline/one-row means all the 3 fields card number, exp date, and CVV will be in one row. Please provide the necessary width for better UI.\
   three-rows mean each will be in one row.

### 1C: config

Here is the list of payment configs available.

1. **customPayButton**: By default it is false. change it to true if you need a custom pay button instead of a Tazapay in-built pay button. please refer to [step 3B](https://docs.tazapay.com/reference/integrating-only-for-cards#step-3b-using-the-custom-pay-button) for integration details.
2. **hideErrors**: Used to hide errors shown on the payment page. By default it is false. if you need to change it to true to hide payment errors, please handle those errors which you also get in paymentErrors event. refer to [step 6](https://docs.tazapay.com/reference/integrating-only-for-cards#step-6-handle-payment-errors) for integration.
3. **showLabels**: Used to show card field labels like Card Number, Expiry Date, and CVV Number on top of each field.\
   By default it is false. if you need to show these labels add this in the config object and set it to true.
4. **origins**: Details are not required if your application/site doesn't load our iframe inside any other site/iframe.
   * In the event the Tazapay iFrame is being rendered from within multiple nested iFrames, all ancestors in the chain must be provided as a comma-separated list.
   * like If our Tazapay Iframe is embedded in another site/iframe, and you are using that embedded site/iframe inside your application, then you need to provide ancestor origins details as follows:
   * **Example:**\
     The primary origin that will be interacting with the Tazapay iFrame: test1.com\
     Subsequent origins that will render test1.com: test2.com\
     The origin string would then be [https://test1.com,https://test2.com](https://test1.com,https://test2.com)

### 1D: style

Please check the [style guide.](https://docs.tazapay.com/reference/input-styles) for style customization And add the needed style accordingly.

## 2. validate method

Below is the info that is currently supported in the validate method.

### 2A: card

By default card details will be validated by calling the validate method. And the results will be provided in onValidate event. please refer to the [step 4B](https://docs.tazapay.com/reference/integrating-only-for-cards#step-4-validate-details) for integration details.

### 2B: billingDetails

The billingDetails validation is required for US and CA customers. For the rest of the customers no need to validate/pass billingDetails in the validate method. These are the [validation rules](https://docs.google.com/document/d/19QEKZ0bq1T-Qm9y4Lgj-cOEHWx-h2-rf0sCAtYxNul8/edit) we follow to validate billing details, we suggest adding these rules on your end to validate details during customer adding details so that the payment flow will be seamless.

## 3. confirmCardPayment

Below is the info needed to pass to confirm payment.

### 3A: clientToken

This is the required field where merchants need to pass the token that is used to process payment on the Tazapay end. The token value can be obtained from the v3 checkout API call.

### 3B: billingDetails

This billingDetails is required for US and CA customer transactions. Here merchants need to pass the validated billingDetails to process the payment seamlessly without getting any internal validation errors.
