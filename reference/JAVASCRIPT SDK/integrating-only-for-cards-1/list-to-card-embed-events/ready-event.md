---
title: Ready event
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
The `ready` event is triggered when the embed is fully rendered and can accept embed.focus calls.

## Method Parameters

1. `event` - mandatory  
   The name of the event, in this case `ready`
2. `handler` - mandatory  
   handler(event) => void is a callback function that a merchant will provide that will be called when the event is fired. When called it will be passed an event object with the following properties:

   | Field     | Sub-field | Type   | Description                                                    |
   | --------- | --------- | ------ | -------------------------------------------------------------- |
   | embedType |           | string | The type of embed that emitted this event. In this case `card` |

## Handling an embed ready event

```Text Javascript
cardEmbed.on('ready', function(event) {
  // Handle ready event
});
```

<br />