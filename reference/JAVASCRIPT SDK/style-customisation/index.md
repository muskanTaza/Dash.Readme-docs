---
title: Style Customisation
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
The Tazapay SDK allows you to optionally specify your own style rules to customise the user interface of the payment page.

### Style Object Definition

The style object represents CSS properties of various elements on the payment page. Use the element selector and css property name as key and css property value as value

```json Style Object
style: {
  "element_cssproperty": "value",
  "primaryButton_background": "blue",
  "primaryButton_borderRadius" "20px"
}
```

> 👍 Auto-Generate the Style object:
>
> You can use the tool on [this website](https://demo.tazapay.com/config) to customise the UI component and then generate the style object for your client-side code.
>
> Using the token obtained in Step 2 for the sandbox (test) environment, you can also see a [live demo](https://demo.tazapay.com/preview) of the functioning of your UI component.
