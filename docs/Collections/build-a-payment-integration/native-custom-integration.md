---
title: Native Custom Integration
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
Tazapay's [Payin API ](https://docs.tazapay.com/reference/create-payin)allows for a native custom integration, which provides a high degree of flexibility and control over the payment experience. This means you can tailor the payment process to fit seamlessly into your application, offering a more cohesive user experience.

### Advantages of Native Custom Integration:

* **Custom User Experience:** Design the payment flow to match your application's look and feel.
* **Flexible Payment Methods:** Easily add or modify payment methods as needed.
* **Enhanced Security:** Implement security measures tailored to your specific requirements.
* **Detailed Control:** Gain granular control over the payment process, including error handling and status tracking.

# How the Payin API works

## Lifecycle of a payin

1. **Create a Payin:** Begin by creating a Payin on your server. This specifies the amount, currency, and other details of the payment.
2. **Confirm the Payin:** Confirm the Payin on your server/client-side, potentially requiring customer authentication.
3. **Complete the Payment:** Handle post-payment activities based on the payment outcome.

> Related Links:
>
> 1. [Payin API](https://docs.tazapay.com/reference/create-payin)
> 2. [Guide to integrate with individual local payment methods](https://docs.tazapay.com/docs/native-integration-guides)
> 3. [Integrating with Cards](https://docs.tazapay.com/reference/custom-flow)
