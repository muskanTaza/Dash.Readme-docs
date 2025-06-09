---
title: Webhooks
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
A callback URL can now be provided as a request parameter in request bodies for certain endpoints which will notify you of any change in the underlying object status. 

You don't have to schedule tasks at your end or deploy your resources at polling our endpoints periodically to know of a change in the status of a Tazapay object. Pass a callback_url in the payload of APIs and Tazapay will notify your server with a POST request of any change in the status of the object. Please make sure to set the callback_url under HTTPS, else the webhooks would not be triggered!

It is necessary that you configure your endpoint URL to acknowledge Tazapay's webhooks with standard HTTP Codes.  
For example, pass 2xx for a successful POST request receipt on your server.

List of Tazapay objects which trigger a webhook response:

1. [Checkout](doc:checkout-webhook) 
2. [KYB (Know Your Business)](doc:kyb-webhook) 
3. [Escrow](doc:escrow-webhook) 

> 📘 Not receiving webhooks?
> 
> In case of any server block or not receiving a response to your callback URL, try whitelisting the below IP addresses:  
> Test Mode (Sandbox) : <b>18.140.192.124</b>  
> Live Mode (Production) : <b>175.41.179.117</b>