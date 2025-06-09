---
title: Escape event
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
The `escape` event is triggered when the customer presses the escape key within the embed.

## Method Parameters

1. `event` - mandatory  
   The name of the event, in this case `escape`
2. `handler` - mandatory  
   handler(event) => void is a callback function that a merchant will provide that will be called when the event is fired. When called it will be passed an event object with the following properties:

   | Field     | Sub-field | Type   | Description                                                    |
   | --------- | --------- | ------ | -------------------------------------------------------------- |
   | embedType |           | string | The type of embed that emitted this event. In this case `card` |

## Handling an embed escape event

```Text Javascript
cardEmbed.on('escape', function(event) {
  // Handle escape event
});
```