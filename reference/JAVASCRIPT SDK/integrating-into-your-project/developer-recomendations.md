---
title: Developer Recomendations
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
> Tazapay recommends creating a checkout session (using the POST /v3/checkout endpoint) as soon as you have the necessary data from the customer (name, country and email). This reduces the time to load Tazapay's UI component for the customer.

## Reduce the wait time for your customers

Use preloading to load payment module in advance and reduce wait time for users.

```javascript
window.addEventListener("load", (event) => {
  
  //Preload tazapay payment UI as soon as the document loads 
  window.tazapay.preload(); // no arg required here 
});
```

```javascript
//Call below method only once the clientToken is available 
const options: {
  clientToken: "...",
}
window.tazapay.checkout(options);
```