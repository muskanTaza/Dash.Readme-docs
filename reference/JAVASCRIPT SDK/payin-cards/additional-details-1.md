---
title: Additional Details
excerpt: Contains Information on payin cards UI
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
## 1. Cards Configuration

Below is the list of configurations for the card UI, please check the description and use depending on the use case.

[block:parameters]
{
  "data": {
    "h-0": "Config Property Name",
    "h-1": "Description",
    "h-2": "Possible values",
    "0-0": "**styles**",
    "0-1": "You can use style configurations to customize most of the user interface elements. ",
    "0-2": "Please check the [style guide](https://docs.tazapay.com/reference/style-customisation)",
    "1-0": "**showLabels**",
    "1-1": "Used to show card field labels like Card Number, Expiry Date, and CVV Number on top of each field.  \nBy default it is false. if you need to show these labels add this in the config object and set it to true.",
    "1-2": "Boolean(true/false)",
    "2-0": "**hideErrors**",
    "2-1": "Used to hide errors shown on the payment page. By default it is false. if you need to change it to true to hide payment errors, please handle those errors which you also get in \"change\" event.",
    "2-2": "Boolean(true/false)",
    "3-0": "**layout**",
    "3-1": "It is an optional field. By default, the value will be \"two-rows\". means the card number will be in the first row and the expiration date, cvv will be in the second row.  \n\"one-row\" means all the 3 fields card number, exp date, and CVV will be in one row. Please provide the necessary width for better UI.  \n\"three-rows\" mean each will be in one row.",
    "3-2": "String(\"one-row\", \"two-rows\", \"three-rows\")",
    "4-0": "**cvvMask**",
    "4-1": "To mask cvv field in card form. By default it is true",
    "4-2": "Boolean(true/false)",
    "5-0": "**customPayButton**",
    "5-1": "By default it is false. change it to true if you need a custom pay button instead of a Tazapay in-built pay button. please refer to [guide](https://docs.tazapay.com/reference/integrating-cards-for-payin-api#step-2b-listen-for-the-click-event-on-the-pay-button) for integration details.",
    "5-2": "Boolean(true/false)"
  },
  "cols": 3,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]

## 2. Cards Events

Below is the list of events for the card UI, please check the description and use the events according to your use case.

1. **Ready**: The ready event is triggered when the embed is fully rendered and can trigger the below events.

   1. **Event Data**: Below is the data emitted for this ready event.

   | Field     | Sub-field | type   | Description                                                   |
   | --------- | --------- | ------ | ------------------------------------------------------------- |
   | embedType |           | string | The type of embed that emitted this event. In this case card. |

   2. **Sample Handler**: Handling a card ready event.

   ```javascript
   cardEmbed.on('ready', (event) =>  {
     // Handle ready event like remove spinner, etc.
   });
   ```

2. **Change**: The change event is triggered when certain keys related to the embed change.

   1. **Event Data**: Below is the data emitted for this change event.

   | Field     | Sub-field       | type    | Description                                                                                                             |
   | --------- | --------------- | ------- | ----------------------------------------------------------------------------------------------------------------------- |
   | embedType |                 | string  | The type of embed that emitted this event. In this case card.                                                           |
   | empty     |                 | boolean | true if the embed is empty                                                                                              |
   | complete  |                 | boolean | true if the embed is well-formed and potentially complete. That is the merchant can use this to enable their pay button |
   | error     |                 | json    | Any error that we surface to the customer while they are typing                                                         |
   | value     |                 | json    |                                                                                                                         |
   |           | cardholder_name | string  | Cardholder name entered by the customer on the embed                                                                    |
   | scheme    |                 | string  | Card scheme - visa, mastercard, american_express                                                                        |

   2. **Sample Response**: 

   ```javascript
   // Sample response.
   {
     complete: false,
     brand: 'visa',
     embedType: 'card',
     empty: false,
     error: {
       cardNumber: "Enter the card number",
       expDate: "Enter valid expiry date",
       cvv: "",
       name: "",
     },
     value: { cardholder_name: "" },
   }
   ```

   3. **Sample Handler**: Handling a card change event.

   ```javascript
   cardEmbed.on('change', (event) =>  {
     if (event.complete) {
       // enable payment button
     } else if (event.error) {
       // show validation to customer
     }
   });
   ```

3. **Focus**: The focus event is triggered when the embed gains focus. This can happen when a user clicks on an input element, or uses the keyboard (like the Tab key) to navigate to it.

   1. **Event Data**: Below is the data emitted for this focus event.

   | Field     | Sub-field | type   | Description                                                   |
   | --------- | --------- | ------ | ------------------------------------------------------------- |
   | embedType |           | string | The type of embed that emitted this event. In this case card. |

   2. **Sample Handler**: Handling a card focus event.

   ```javascript
   cardEmbed.on('focus', (event) => {
     // Handle focus event
   });
   ```

4. **Blur**: The blur event is triggered when the embed loses focus.

   1. **Event Data**: Below is the data emitted for this blur event.

   | Field     | Sub-field | type   | Description                                                   |
   | --------- | --------- | ------ | ------------------------------------------------------------- |
   | embedType |           | string | The type of embed that emitted this event. In this case card. |

   2. **Sample Handler**: Handling a card blur event.

   ```javascript
   cardEmbed.on('blur', (event) =>  {
     // Handle blur event
   });
   ```

5. **Escape**: The escape event is triggered when the escape key is pressed within an embed.

   1. **Event Data**: Below is the data emitted for this escape event.

   | Field     | Sub-field | type   | Description                                                   |
   | --------- | --------- | ------ | ------------------------------------------------------------- |
   | embedType |           | string | The type of embed that emitted this event. In this case card. |

   2. **Sample Handler**: Handling a card escape  event.

   ```javascript
   cardEmbed.on('escape', (event) => {
     // Handle escape event
   });
   ```