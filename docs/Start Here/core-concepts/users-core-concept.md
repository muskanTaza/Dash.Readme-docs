---
title: Users
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
Users are entities who are entitled to the services provided by Tazapay. 

Both buyer and seller details are required to initiate a transaction (checkout or escrow). This can be done by both the <a href="https://docs.tazapay.com/reference/create-user-api" target="_blank">Create User endpoint</a> and <a href="https://app.tazapay.com" target="_blank">Tazapay Dashboard</a>.

To retrieve an existing user account, refer to the [Get User by ID](ref:get-user-by-id-api) or [Get User by Email](ref:get-user-by-email-api) endpoints. 

1. **For Marketplaces:** All entities that participate in a transaction on your platform can be added as users. Buyers, sellers and even the marketplace entity itself can have corresponding Tazapay users.
2. **For SaaS platforms:** All entities that participate in a transaction on your platform can be added as users. Service providers, buyers of services, investors, borrowers, and the platform entity itself can have corresponding Tazapay users.
3. **For eCommerce merchants (single sellers):** All of your buyers that complete a checkout via Tazapay have a corresponding Tazapay user created. For your own entity, you are only required to create a user as a seller on record. 
[block:callout]
{
  "type": "info",
  "body": "When creating the user, you need to mention if they are a \"**Business**\" or an \"**Individual**\" under `ind_bus_type`"
}
[/block]