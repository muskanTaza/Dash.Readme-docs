---
title: Balance
excerpt: >-
  This is an object representing your real time Tazapay balance across different
  currencies.
deprecated: false
hidden: false
icon: far fa-scale-balanced
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# The Balance Object

```Text JSON
{
  "available": [
    {
      "amount": "1212429",
      "currency": "THB"
    },
    {
      "amount": "403917",
      "currency": "USD"
    },
    {
      "amount": "-375345",
      "currency": "SGD"
    },
    {
      "amount": "100000",
      "currency": "PHP"
    },
    {
      "amount": "2469000",
      "currency": "KRW"
    },
    {
      "amount": "10000000",
      "currency": "IDR"
    },
    {
      "amount": "-36291",
      "currency": "EUR"
    },
    {
      "amount": "1090172",
      "currency": "BRL"
    },
    {
      "amount": "-7274",
      "currency": "GBP"
    },
    {
      "amount": "0",
      "currency": "INR"
    }
  ],
  "object": "balance",
  "updated_at": "2024-09-30T10:53:03.314835Z"
}
```

<br />

| Field      | Sub-fields | Type          | Description                                                                                                                              |
| :--------- | :--------- | :------------ | :--------------------------------------------------------------------------------------------------------------------------------------- |
| available  |            | array of json | Available balance in individual currencies                                                                                               |
|            | currency   | string        | Currency, uppercase, ISO-4217 standard                                                                                                   |
|            | amount     | integer       | Amount in cents. For decimal handling of various currencies, refer to the guide [here](https://docs.tazapay.com/docs/decimal-currencies) |
| object     |            | string        | String representing the object's type, Objects of the same type share the same value. It is `balance` here                               |
| updated_at |            | timestamp     | Timestamp at which the balance was last updated                                                                                          |
