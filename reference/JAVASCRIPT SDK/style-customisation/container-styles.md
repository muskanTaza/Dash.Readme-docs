---
title: Container Styles
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
You have the ability to the customise the UI component to suit your branding and theme. 

### Define sizing constraints for payment element

```json Style Object
style: {
  "container_minWidth": "0%",
  "container_maxWidth": "750px",
  "container_minHeight": "300px",
  "container_maxHeight": "99999px",
  "container-iframe_minWidth": "100%",
  "container-iframe_maxWidth": "750px",
  "container-iframe_minHeight": "300px",
  "container-iframe_maxHeight": "99999px",
}
```

The payment element has a parent wrapper container and a child iframe element.

### Define additional customisation for payment element

```json Style Object
style: {
  "container_zIndex": "1",
  "container_padding": "1rem",
	"container_background": "rgb(0 0 0 / 0.7)", //use for popup
  "container_backdrop": "blur(4px)",
  "container-iframe_background": "transparent",
  "container-iframe-loading_background": "#F4F5F7",
  "container-iframe_borderRadius": "4px",
  "container-iframe_boxshadow": "0px 10px 15px rgba(226, 232, 240, 0.32), 0px 4px 6px rgba(226, 232, 240, 0.5)",
}
```