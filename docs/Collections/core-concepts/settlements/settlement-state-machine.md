---
title: Settlement State Machine
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
## Settlements using the SWIFT network

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/63fb4c2222c905dd28cc0cb4f091bc88f8dd0a8ab609792b2371b3006d20c543-image.png",
        null,
        null
      ],
      "align": "center"
    }
  ]
}
[/block]


## Settlements using local rails

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/626511e4b3e6b0ca49f6e8b24a67309bb6ccf1b7c46f7ff883a63ebc215f0d76-image.png",
        null,
        null
      ],
      "align": "center"
    }
  ]
}
[/block]


<br />

| State      | Description                                                                                                                         |
| :--------- | :---------------------------------------------------------------------------------------------------------------------------------- |
| created    | When the settlement is created                                                                                                      |
| processing | When the settlement is initiated from Tazapay                                                                                       |
| succeeded  | When the settlement reaches the destination bank account (using local rails) or is initiated from Tazapay (using the SWIFT network) |
| failed     | When the settlement fails                                                                                                           |