---
title: Decimal Currencies
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
> 📘 
> 
> **Minor Unit: **The minor unit of a currency refers to the number of digits after the decimal separator that the currency can have.

All the currencies have distinct minor units, either 0, 2, 3 or 4. The entire list can be accessed [here](https://www.six-group.com/dam/download/financial-information/data-center/iso-currrency/lists/list-one.xls).

The `amount` key for will always accept the denomination value with 2 decimal places in an integer format.

**Example:** Consider three currencies, a 3 decimal currency KWD, a 2 decimal currency INR and a 0 decimal currency JPY. 

- For INR, if you want the amount to be 100.89, you pass 10089 as the value for the amount key. 
- For JPY, if you want the amount to be 100, you pass 10000. The last 2 digits will always be considered as 0 even if the values are different than 0. 
- For KWD, if you want the amount to be 100.899, you can pass 10089 as the value for the amount key. Tazapay’s system will not accept the third decimal place of 3 digit currencies. If you pass 100899, it will be considered as KWD 1008.990.