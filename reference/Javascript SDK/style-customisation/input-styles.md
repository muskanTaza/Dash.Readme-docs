---
title: Input Styles
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
### Input Field Styling (only for Card Form)

We provide plenty of styling options for the Input fields

```json Style Object
style: {
  "input-base_margin": "0px 0px 0px 0px !important",
  "input-base_padding": "20px",
  "input-base_outline": "none",
  "input-base_borderWidth": "0px",
  "input-base_borderColor": "black",
  "input-base_borderStyle": "solid",
  "input-base_borderRadius": "5px",
  "input-base_width": "100%",
  "input-base_height": "45px",
  "input-base_fontFamily": "Arial, sans-serif",
  "input-base_fontSize": "14px",
  "input-base_fontWeight": "600",
  "input-base_color": "black",
  "input-base_background": "white",
  "input-base_boxShadow": "0px 0px 2px 0px #80808080 inset",
  "input-base_boxSizing": "border-box",
}
```

You can also use above styling options for various input field states like focus and error. These style properties can also be used for the validation error message shown below input fields.

```json Style Object
style: {
  "input-focus_borderColor": "blue",
  "input-error_borderColor": "red",
  "inputErrorMessage_color": "red",
}
```

You can even style the placeholder.

```json Style Object
style: {
  "input-placeholder_fontFamily": "Arial, sans-serif",
  "input-placeholder_fontSize": "14px",
  "input-placeholder_fontWeight": "400",
  "input-placeholder_color": "darkgray",
}
```

Below options can be used to style the card form.

```json Style Object
style: {
  "card-input_gap": "0.5rem",
  "cardInputLogo_height": "3rem",
  "cardInputLogo_width": "3rem",
  "cardInputLogo_padding": "0.6rem",
}
```
