---
title: Focus event
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
The `focus` event is triggered when the embed gains focus. This can happen when a user clicks on an input element, or uses the keyboard (like the Tab key) to navigate to it.

## Method Parameters

1. `event` - mandatory  
   The name of the event, in this case `focus`
2. `handler` - mandatory  
   handler(event) => void is a callback function that a merchant will provide that will be called when the event is fired. When called it will be passed an event object with the following properties:

   | Field     | Sub-field | Type   | Description                                                    |
   | --------- | --------- | ------ | -------------------------------------------------------------- |
   | embedType |           | string | The type of embed that emitted this event. In this case `card` |

## Handling an embed focus event

```Text Javascript
cardEmbed.on('focus', function(event) {
  // Handle focus event
});
```