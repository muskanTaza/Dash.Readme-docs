---
title: Blur event
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
The `blur` event is triggered when the embed loses focus.

## Method Parameters

1. `event` - mandatory  
   The name of the event, in this case `blur`
2. `handler` - mandatory  
   handler(event) => void is a callback function that a merchant will provide that will be called when the event is fired. When called it will be passed an event object with the following properties:

   | Field     | Sub-field | Type   | Description                                                    |
   | --------- | --------- | ------ | -------------------------------------------------------------- |
   | embedType |           | string | The type of embed that emitted this event. In this case `card` |

## Handling an embed blur event

```Text Javascript
cardEmbed.on('blur', function(event) {
  // Handle blur event
});
```