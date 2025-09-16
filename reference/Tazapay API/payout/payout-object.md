---
title: Payout object
deprecated: false
hidden: true
metadata:
  robots: index
---
\<Columns layout="auto">
&#x20; \<column>
&#x20;   \<h2>Amount\</h2>
&#x20; \</column>

&#x20; \<column>
&#x20;   \<code>\{
&#x20; "amount": 100,
&#x20; "amount\_paid": 0,
&#x20; "billing\_details": \{
&#x20;         "address": \{
&#x20;             "city": "Singapore",
&#x20;             "country": "SG",
&#x20;             "line1": "1st Street",
&#x20;             "line2": "2nd Avenue",
&#x20;             "postal\_code": "43004",
&#x20;             "state": "Singapore"
&#x20;           },
&#x20;         "label": "Home",
&#x20;         "name": "Andrea Lark",
&#x20;         "phone": \{
&#x20;             "calling\_code": "65",
&#x20;             "number": "87654321"
&#x20;           }
&#x20;       },
&#x20; "cancel\_url": "https\://mystore.com/try\_again",
&#x20; "cancelled\_at": null,
&#x20; "client\_token": "JsU19R\_Li9cwVksJGUfAajZ3r2A9ArU7Qk3j5r0cpVg=",
&#x20; "confirm": false,
&#x20; "created\_at": "2024-10-07T07:10:21.894488Z",
&#x20; "customer": "cus\_crtqrhth90j0121gpt50",
&#x20; "customer\_details": \{
&#x20;         "country": "SG",
&#x20;         "email": "andrea\@example.com",
&#x20;         "name": "Andrea Lark",
&#x20;         "phone": \{
&#x20;             "calling\_code": "65",
&#x20;             "number": "87654321"
&#x20;           }
&#x20;       },
&#x20; "holding\_currency": "INR",
&#x20; "id": "pay\_cs1oina7a5ng2a3ng12g",
&#x20; "invoice\_currency": "INR",
&#x20; "items": \[],
&#x20; "latest\_payment\_attempt": "",
&#x20; "latest\_payment\_attempt\_data": null,
&#x20; "metadata": \{
&#x20;         "key1": "value1",
&#x20;         "key2": "value2",
&#x20;         "key3": "value3"
&#x20;       },
&#x20; "object": "payin",
&#x20; "paid\_in\_excess": false,
&#x20; "partially\_paid": false,
&#x20; "payment\_attempts": \[],
&#x20; "payment\_method\_details": \{
&#x20;         "paynow\_sgd": \{},
&#x20;         "type": "paynow\_sgd"
&#x20;       },
&#x20; "reference\_id": "123",
&#x20; "shipping\_details": \{
&#x20;         "address": \{
&#x20;             "city": "Singapore",
&#x20;             "country": "SG",
&#x20;             "line1": "1st Street",
&#x20;             "line2": "2nd Avenue",
&#x20;             "postal\_code": "43004",
&#x20;             "state": "Singapore"
&#x20;           },
&#x20;         "label": "Home",
&#x20;         "name": "Andrea Lark",
&#x20;         "phone": \{
&#x20;             "calling\_code": "65",
&#x20;             "number": "87654321"
&#x20;           }
&#x20;       },
&#x20; "statement\_descriptor": "tzp\*string",
&#x20; "status": "requires\_payment\_method",
&#x20; "status\_description": "",
&#x20; "success\_url": "https\://mystore.com/success\_page",
&#x20; "transaction\_data": \[],
&#x20; "transaction\_description": "test",
&#x20; "transaction\_documents": \[],
&#x20; "webhook\_url": "https\://mystore.com/internal/webhook"
}\</code>
&#x20; \</column>
\</Columns>
