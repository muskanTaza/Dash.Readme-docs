---
title: Webhook Guide
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
Tazapay provides full control and visibility over your webhook events. This guide explains how to:

* Configure webhook endpoints
* Enable/Disable webhooks endpoints
* View webhook event logs
* Re-trigger webhook events
* Authenticate webhooks
* Manage user permissions

***

## Configuring Webhooks on Tazapay

To start receiving webhook events, you must first configure your webhook endpoint.

### Steps to Configure

1. Go to `Settings > Webhooks`
2. Click **Add Webhook URL**
3. Fill in the following fields:

| Field                 | Description                                                             |
| --------------------- | ----------------------------------------------------------------------- |
| `Name`                | Friendly identifier for your webhook                                    |
| `URL`                 | The full endpoint URL on your server                                    |
| `Events to Subscribe` | Select the event types you want (e.g. `checkout.paid`, `payout.failed`) |

Once confirmed , Tazapay will begin sending events to the specified URL when matching events occur.

***

## Enabling or Disabling Webhooks

You can toggle the active/inactive status of a webhook at any time.

### How to Toggle

1. Navigate to `Settings > Webhooks`
2. Select the webhook you'd like to manage
3. Use the **Enable/Disable** toggle on the webhook listing page or settings option inside the webhook detail page to manage the status of the webhook.

### Behavior

* **Enabled**: Events matching the selected types will be sent
* **Disabled**: No events will be sent until re-enabled

> Disabling a webhook does not delete it or affect previously sent events.

<br />

## Viewing Webhook Logs

You can inspect detailed logs for each webhook event via the dashboard.

### Accessing Logs

1. Go to `Settings > Webhooks`
2. Click the webhook name or select `View details`

### Webhook Details

* **Webhook Name & URL**
* **Status**: Enabled/Disabled
* **Secret Token**
* **Total Events Triggered**
* **Event Logs Table** with filters and search

### Log Entry Fields

| Field               | Description                                                      |
| ------------------- | ---------------------------------------------------------------- |
| `Last Attempt Date` | Timestamp of last delivery                                       |
| `Event ID`          | Unique ID, e.g. `evt_ctc0lfqe4e771g7bbof0`                       |
| `Response Code`     | HTTP status returned by your server (e.g., `200`, `503`)         |
| `Event Type`        | Event name like `checkout.paid` or `payment.failed`              |
| `Reference Id`      | Payment id related to the webhook e.g. `chk_d1382lo4jjk32r7ri8r` |

### Filtering and Searching

You can filter logs by:

* Created Date - Timestamp when the webhook event was created.
* Event type
* Response code

You can also search by **Event ID** or **Payment ID**.

***

## Re-triggering Webhook Events

You can re-send webhook events if they were missed or failed.

### Re-trigger a Single Event

Click the **Resend** button next to the event log. A loading spinner will show while the event is being resent.

> Limit: Each event can be resent up to 3 times within 24 hours.

### Re-trigger Multiple Events

1. Select multiple log entries using checkboxes.
2. Click **Bulk Resend**.
3. Events will be resent one by one in the background.

> Tip: Use the sandbox environment to test webhooks before retrying in production.

***

## Authenticating Webhooks

Tazapay signs each webhook request. You should verify the signature to ensure the webhook came from us.

### How It Works

1. Each request includes a `webhook-signature` header.
2. You need to generate the same signature at your end and verify it with the one sent with the webhook
3. Signature is build using event\_id, payload, timestamp and the secret token

👉 [View detailed implementation guide](https://docs.tazapay.com/docs/webhook-authentication)

***

## Managing Permissions

You can restrict access to webhook logs and actions by managing team permissions.

### Manage via Dashboard

Go to `Settings > Manage Team > Edit`

| Permission              | Default for New Users |
| ----------------------- | --------------------- |
| View Webhooks           | ✅ Enabled             |
| Edit/Retrigger Webhooks | ❌ Disabled            |
| View Secret Token       | ❌ Disabled            |
| Regenerate Secret Token | ❌ Disabled            |

> If a user doesn’t have access to specific transactions, they won’t see the related webhook events.

***

## Testing in Sandbox

Use the **Sandbox Environment** to test webhook integration safely.

* Supports all webhook events
* Avoids triggering production workflows
* Prevents rate limit issues or costs

***

## Support

If you need help:

📩 Email us at [support@tazapay.com](mailto:support@tazapay.com)