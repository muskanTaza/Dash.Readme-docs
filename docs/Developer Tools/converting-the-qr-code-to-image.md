---
title: Converting the QR code to image
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
1. **Get QR Code:**

   Get the *qr\_code* from the API response.
2. **Basic Decode:**

   Decode the *qr\_code* data (which is encoded using Base64 encoding).

   Example: In JS,

   ```jsx
   const decodedQrCode = window.atob(qr_code);
   ```
3. **Convert to QR Image URL:**

   Use any known internal method of your programming language or use an external library to convert decodedQrCode to QR image URL.

   Example: [**qrcode**](https://www.npmjs.com/package/qrcode) npm package, sample code block as per the npm package readme doc,

   For ES6/ES7

   ```jsx
   import QRCode from 'qrcode'

   let **qr_url =** null;

   // With promises
   QRCode.toDataURL(decodedQrCode)
     .then((url) => {
       console.log(url)
   		**qr_url** = url;
     })
     .catch((err) => {
       console.error(err)
     })
   ```
4. Render QR Image:

   set the **qr\_url** in the src attribute of image element in HTML.

   Example:

   ```jsx
   <img
   		:src="qr_url" // QR image url to render in UI.
   		class="" // add relevant styles 
   		alt="QR image"
   />
   ```
