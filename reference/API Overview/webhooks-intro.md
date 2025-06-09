---
title: Webhooks
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
A webhook URL can now be provided as a request parameter in request bodies for certain endpoints which will notify you of any change in the underlying object status. 

You don't have to schedule tasks at your end or deploy your resources at polling our endpoints periodically to know of a change in the status of a Tazapay object. Pass a webhook\_url in the payload of APIs and Tazapay will notify your server with a POST request of any change in the status of the object. Please make sure to set the webhook\_url under HTTPS, else the webhooks would not be triggered!

It is necessary that you configure your endpoint URL to acknowledge Tazapay's webhooks with standard HTTP Codes.\
For example, pass 2xx for a successful POST request receipt on your server.

If Tazapay does not receive a 2xx acknowledgement, it will retry sending webhooks to the endpoint for a period of 36 hours. Click <a href = "https://docs.tazapay.com/docs/retry-policy" target="_blank">here</a> for the detailed retry policy.

List of Tazapay objects which trigger a webhook response:

1. [Checkout](doc:checkout-webhook) 
2. [Escrow](doc:escrow-webhook) 
3. [Refund](doc:refund-webhook)
4. [Global Collection Account](doc:collection-account)

> 📘 Not receiving webhooks?
>
> In case of any server block or not receiving a response to your webhook URL, try whitelisting the below IP addresses:\
> Test Mode (Sandbox) : <b>13.213.226.109</b>\
> Live Mode (Production) : <b>52.77.198.235</b>
