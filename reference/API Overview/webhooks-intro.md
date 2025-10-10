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
Webhooks are setup on an account level from the dashboard as that gives users an interface to look at any successful or failed webhooks requests and also re-trigger them if required. Use this [guide](https://docs.tazapay.com/docs/webhooks-guides#/) to setup webhooks

[**Deprecated**] A webhook URL can also be provided as a request parameter in request bodies for certain endpoints which will notify you of any change in the underlying object status.

**Note ** - We are in process of deprecating webhooks on transaction level, it is a best practice to setup webhooks at account level as they also give you a ability to self-serve webhooks signature verification and webhooks re-triggers. Please do not setup both the methods as they will lead to duplicate webhooks on your server.

You don’t need to schedule tasks on your side or continuously poll our endpoints to track changes in the status of a Tazapay object. Instead, simply set up webhooks via the Tazapay merchant dashboard for the endpoints you want to receive real-time notifications.

It is necessary that you configure your endpoint URL to acknowledge Tazapay's webhooks with standard HTTP Codes.
For example, pass 2xx for a successful POST request receipt on your server.

If Tazapay does not receive a 2xx acknowledgement, it will retry sending webhooks to the endpoint for a period of 24 hours. Click <a href="https://docs.tazapay.com/docs/retry-policy" target="_blank">here</a> for the detailed retry policy.

> 📘 Not receiving webhooks?
>
> In case of any server block or not receiving a response to your webhook URL, try whitelisting the below IP addresses:
> Test Mode (Sandbox) : <b>13.213.226.109</b>
> Live Mode (Production) : <b>52.77.198.235</b>
