---
title: LinkAja
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
# linkaja_idr

Linkaja is a popular digital wallet in Indonesia. When making a payment online, customers can select LinkAja as the payment method. On a mobile device, they get redirected to their pre-installed LinkAja application, otherwise they are redirected to the wallet’s website. The customers can then enter their mobile number, and complete the payment by entering their PIN.

> A customer can pay a minimum of 0.01 USD equivalent IDR and a maximum of 600 USD equivalent IDR using Link Aja on Tazapay

# Integrating on your website / application

## Step 1: Create a payin

Tazapay uses a `payin` object to represent your intent to collect a payment from your customer. The payin object tracks state changes from Link Aja transaction creation to payment completion.  
Create a payin on your server with an amount, invoice_currency `IDR` and a transaction_description using the [create payin API](https://docs.tazapay.com/reference/create-payin)

A payin is created with the status `requires_payment_method`.

### Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/payin \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "invoice_currency": "IDR",
  "amount": 10000000,
  "transaction_description": "1 X Good",
	"webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

## Step 2: Confirm a payin

Confirm the payin created in step 1 using the confirm payin API. Upon confirmation of the payin, a redirection URL is generated. The status of the payin moves to `requires_action`

The following fields are to be passed in the request body

| Field                  | Subfield | type   | Mandatory (Y/N) | Description                                                                                           |
| ---------------------- | -------- | ------ | --------------- | ----------------------------------------------------------------------------------------------------- |
| payment_method_details |          | json   | Y               | Details specific to the payment method required to create a charge                                    |
| success_url            |          | string | Y               | URL where the customer is directed to after a successful payment                                      |
| cancel_url             |          | string | Y               | The URL the customer will be directed to if they decide to cancel payment and return to your website. |

The following sub-fields can be passed in payment_method_details

| Field | Subfield | type | Mandatory (Y/N) | Description                                                     |
| ----- | -------- | ---- | --------------- | --------------------------------------------------------------- |
| type  |          | enum | Y               | The type of the payment method. In this case, it is linkaja_idr |

### Sample cURL

```json
curl --location 'https://service-sandbox.tazapay.com/v3/payin/pay_cnfn18ne9lcetnsshe00/confirm' \
--header 'accept: application/json' \
--header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
--header 'content-type: application/json' \
--data-raw '
{
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea.lark@tazapay.com",
    "country": "ID"
  },
  "success_url":"https://mypage.success",
  "cancel_url":"https://mypage.failure",
  "payment_method_details": {
    "type": "linkaja_idr"
		}
  }
}
'
```

### Combining Steps 1 and 2 into a single step

Instead of making 2 API calls, you can also combine steps 1 and 2 into a single API call. To do so, pass the parameters in both the create payin and confirm payin endpoints to the create payin API.

Also, pass the following field

| Field   | type    | Mandatory (Y/N) | Description                              |
| ------- | ------- | --------------- | ---------------------------------------- |
| confirm | boolean | Y               | To confirm the payin along with creation |

### Sample cURL

```json
curl --location 'https://service-sandbox.tazapay.com/v3/payin' \
--header 'accept: application/json' \
--header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
--header 'content-type: application/json' \
--data-raw '{
  "invoice_currency": "IDR",
  "amount": 10000000,
  "transaction_description": "1 X Good",
  "webhook_url": "https://webhook.site/ref8y92937922",
  "confirm":true,
	"success_url":"https://mypage.success",
  "cancel_url":"https://mypage.failure",
  "customer_details": {
    "name": "Andrea Lark",
    "email": "andrea.lark@tazapay.com",
    "country": "ID"
  },
  "payment_method_details": {
    "type": "linkaja_idr"
    }
  }
}'
```

## Step 3: Redirect the customer to LinkAja

After confirming the payin, access the form field in the response from the data object. This form will
be used to redirect the user to the payment page

```json
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 10000000,
        "amount_paid": 0,
        "billing_details": null,
        "cancel_url": "https://mypage.failure",
        "cancelled_at": null,
        "client_token": "_Rrgfj9OSfEUoeQozz81HH7aRonzXeNSQ9CcgMhB4a0=",
        "confirm": true,
        "created_at": "2025-11-20T08:42:43.565683551Z",
        "customer": "cus_d4fd90np3mil5glh0fh0",
        "customer_details": {
            "country": "ID",
            "email": "andrea.lark@tazapay.com",
            "name": "Andrea Lark",
            "phone": null
        },
        "form": "Jmx0O2h0bWwmZ3Q7Jmx0O2hlYWQmZ3Q7Jmx0O21ldGEgY2hhcnNldD0mIzM0O3V0Zi04JiMzNDsmZ3Q7Jmx0Oy9oZWFkJmd0OyZsdDtib2R5Jmd0OyZsdDtmb3JtIGlkPSYjMzQ7Zm9ybXN1Ym1pdCYjMzQ7IG5hbWU9JiMzNDtmb3Jtc3VibWl0JiMzNDsgYWN0aW9uPSYjMzQ7aHR0cHM6Ly9wYXltZW50LmxpbmthamEuaWQvY2hlY2tvdXQvcGF5bWVudCYjMzQ7IG1ldGhvZD0mIzM0O3Bvc3QmIzM0OyZndDsgJmx0O2lucHV0IHR5cGU9JiMzNDtoaWRkZW4mIzM0OyBuYW1lPSYjMzQ7TWVzc2FnZSYjMzQ7IHZhbHVlPSYjMzQ7TFMwdExTMUNSVWRKVGlCTlpYTnpZV2RsTFMwdExTMEtDbmRqUmsxQmVtdElhVXBxTlZRd1dtNUJVa0ZCV0VOWE9GUlhZa0pIV0hnMGJuSjVaazVGVVU5TGEyZHpNak5vU1hwQk4xQlZiR1pXZUZweFpYbE9XRW9LUjI4NE9ESTBlUzg1V25wR2FWWkZha1E1VXpGemVDOUhSbmxTUW5kclNFMVlSSFpXZGtkR1Z6RkdRVEJTTUV4U1JUbFRjRmREUkZSc0sxbERWalZvYndwR2JERnhTVGRqYjFkU1NIaGpjM2x0VTFOUWRYbHlhR3cwU21adlRubEpkbkJzTUROM2VGbDBRVnBIZGtvMU9VWXJSV3d3Y1dWd1MyOWllR1ZYZDFwNkNsbDFaRU0wVjFWSFNFVnFUV1V4ZW1ZMk9HSk9RbHBGVFdweVJsbEZTRTAwVjNCT1MwMDRPREV5TmpWVmJtNTRhR1V3UnpCNlRtcExibFVyYjJRM01Xb0tjbEpMU1hCU1pWWTVhVGRtTVZWTVQwUjJXRXBFYkhWSU16UmlRVk5KWm1GNVluUnVUa0pGUVVSRk5WQkRiVWs0VWs5QmRrZGlRMFF5UldGdU9ERnRjd29yWW5WUlVVVlhiRk5ZTWsxeVNFUXhURXBUWmpKcWEwMXlZV2hEYURoNlRYb3ZTREV2TlROd1owMUxObVY1U2tGamRuTlllbWRuS3k4NFFXd3laVzFKQ21jdlMycHFjbFpMZDJSNE16WlZUbnBMZDNGdmNsQXljMDlzVkRrd1RuQlRXV2t3V1ZrNFpXZFhRbVJUWWxWbmRESldSRnBsTmxncllWa3dWRUpVUm1VS1ltRkVTMUF3Vmtoc1RXeHJkblZTVFc0clVrNUZXbUZTUlRJMWNVVkdhMVV5V1VWWFEwTjZaRVJxTldoV1FUTjRhVGt6V1ZoS2JIUlVOUzk0TDNSaWR3cFlRM1ZVUkU4eE1qUjBiRnBPT1M5RVp6Z3ZUMWMxUkhGUFVHcEZObGh0VUcxT2VuRjBibkkxYWpoNVJHUjBaRWRQUzNWRGNsaFJPWEpRVTFKWmR6QkpDalJwVEVvNVNtdFNhRmhNWjJFek1DODVSVGR5UW5WM2REZFFOVEJCU1RkRGMxaFFMMGcyUzBkVFQzazRXVmROZG5aQmQyd3lTMlJPYVRCbFdIVTBNVVFLYVZwMlVVWkhNVEJtT1ZreFJFbE9aR3RsYTJRNFlpdDNWbXBYUnl0NmEzZDJUVTlIVmtFck5ubDJZbWQ2VFZjMVN5OHhVbGxXTUN0WmFXRlFVMjVxVXdvMlFVVmpWbkJRT0RGcFVrWkxURlF6YlVkM1FtRmFaV3B1Wm5sTVJtTkZUV0ZMWW5KemNVRTNjVlkxUWtVd1Z6WndTM1pNUmpSQmJsVnNWV0ZQUzNaU0NrOUpVVk13VFVaMFNrMVlWVVZUTm1vNVIyd3liRmhQTVhCSFRHOTZMMGRZYm14SVJFTjJSRU50YVc1VGF6QlZVM05aWm1KaU9WQllhRVJDU0V4dk5qVUtRbmhEZERScVduVXZaekUxU1ZGNlNrWjJZMjVHVWs5SVkwNXBXbXhNVkRrd2N6TmhPVGcyYkVOblpWcEVTR05tT1dWWFYyZDFWbGszVEhkdlMxbHJZZ3BYWkRCcWRpOUViM2g2VEZGc1JWbHlUekpyTmpSUFl6WlJUbGRUUTB0NGMwSktVemszTHpCRFNVZzJUelU1YWxWS1UwZEpSbHBMVEd4RVNESkZUVkpoQ2trM1JFODFjRWRvWlZsbFNYRkVhR016YVhWUVYzSnljVUp3Um1KUFR6aFdNMmx1YmpSb1EwUnJiVGw2VjBaaVRrVTNVWEZMTjNOeGQySjZSbVZsTkVrS1RYRm1lVTlPV2pSeE5FVmxUSGRvWVZoaFJHbGlWVmhzUTNsVFEzUnpjMk00TjJWMGVIQmFZMHM1V0VWQ1owWlNRWGhSV0ZnM1RHaElLMEZ6U1hGQ1NBcEVRMGhyUmxacVFtcE1ZbXh6YTBneWEyUmtaM1JUVWs1SlpVOUtjbVJ2SzFSbVlUUnpaVXBqTTJwNFZFRkJQVDBLUFZsSWJGUUtMUzB0TFMxRlRrUWdUV1Z6YzJGblpTMHRMUzB0fnRhemExNzYzNjI4MTYzNDE2NTc0OTI3JiMzNDsgLyZndDsmbHQ7aW5wdXQgdHlwZT0mIzM0O2hpZGRlbiYjMzQ7IG5hbWU9JiMzNDt1cmwmIzM0OyB2YWx1ZT0mIzM0O2h0dHBzOi8vcGF5bWVudC5saW5rYWphLmlkL2NoZWNrb3V0L3BheW1lbnQmIzM0OyAvJmd0OyZsdDtpbnB1dCB0eXBlPSYjMzQ7c3VibWl0JiMzNDsgdmFsdWU9JiMzNDtzdWJtaXQmIzM0OyBzdHlsZT0mIzM0O2Rpc3BsYXk6IG5vbmUmIzM0OyAvJmd0OyZsdDsvZm9ybSZndDsmbHQ7c2NyaXB0IHR5cGU9JiMzNDt0ZXh0L2phdmFzY3JpcHQmIzM0OyZndDtkb2N1bWVudC5mb3Jtc1smIzM5O2Zvcm1zdWJtaXQmIzM5O10uc3VibWl0KCk7Jmx0Oy9zY3JpcHQmZ3Q7Jmx0Oy9ib2R5Jmd0OyZsdDsvaHRtbCZndDs=",
        "holding_currency": "IDR",
        "id": "pay_d4fd90jksan48piqmve0",
        "invoice_currency": "IDR",
        "items": [],
        "latest_payment_attempt": "pat_d4fd90jksan48piqmvg0",
        "latest_payment_attempt_data": {
            "expires_at": "2025-11-20T08:47:43Z"
        },
        "metadata": null,
        "object": "payin",
        "paid_in_excess": false,
        "partially_paid": false,
        "payment_attempts": [],
        "payment_method_details": {
            "type": "linkaja_idr"
        },
        "reference_id": "",
        "shipping_details": null,
        "statement_descriptor": "",
        "status": "requires_action",
        "status_description": "",
        "success_url": "https://mypage.success",
        "transaction_data": [],
        "transaction_description": "1 X Good",
        "transaction_documents": [],
        "webhook_url": "https://webhook.site/ref8y92937922"
    }
}
```

## Integration Steps 

The data obtained in the form field is a base64 encoded html form. This form contains POST action methods which will make the user land on the appropriate page to make payment.

1. Access the `form` field from api response and decode it to get the actual form

```javascript
let form = response.data.form;
let decodedForm = window.atob(form);
```

2. Parse the decoded form to remove the tags

```javascript
const element = document.createElement("div");
element.innerHTML  decodedForm;
let html = element.textContent;
```

3. Assign this html content to the window object

```javascript
window.document.write(html);
```

4. After this step, Linkaja payment page will be opened on the same tab

<Image align="center" border={false} src="https://files.readme.io/ed44ae56f4fd3b19cddacc9fbaf49487120ec3dccabb2e8370ef46c35223d5bc-Screenshot_2025-11-20_at_2.17.18_PM.png" />

## Step 4: Handle post-payment events

Tazapay sends a `payin.succeeded` event as soon as the funds are received from the customer. Use the `webhook_url` field in the payin API to receive these events and run actions (for example, sending an order confirmation email to your customers, logging the sale in a database, starting a shipping workflow, etc.)

Post a successful payment, the customer will be redirected back to the `success_url`. You will also receive a `payin.succeeded` event on your webhook_url.

In case the customer does not complete the payment within the expiry time or the charge is not successful, the customer is redirected back to the `cancel_url` . From the cancel_url, you can display the list of payment methods again to the customer. To generate a new request, confirm the payin again using Step 2. You will also receive a `payment_attempt.failed` webhook.

| Event                  | Description                                                    | Next Steps                                                                                      |
| ---------------------- | -------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| payin.succeeded        | The customer paid before the expiration of the payment request | Fulfill the goods or services that the customer purchased                                       |
| payment_attempt.failed | The customer did not pay and the request expired               | Allow the customer to generate a new request or complete the payment via another payment method |

## Expiration and cancellation

LinkAja charge requests expire after 5 minutes and the customer cannot pay once the charge request has expired. After expiration, the status of the payin changes to `requires_payment_method.` At this point, you can confirm the payin with another payment method or cancel.

# Test the Integration

You can simulate the following scenarios on the `redirect_url`

1. Successful Payment - Click on `Simulate Success` CTA. A `payin.succeeded` event will be triggered. The status of the payin will change to `succeeded`.
2. Failed Payment - Click on `Simulate Failure` CTA. A `payment_attempt.failed` event will be triggered. The status of the payin will change to `requires_payment_method`.

# Integrating Refunds

You can refund a transaction in two ways - using the [dashboard](https://dashboard.tazapay.com) or using [Refund API](https://docs.tazapay.com/reference/refund-api).

LinkAja does not support partial refunds, the refund has to be for the full value of the transaction.

### Refunding using dashboard

Refer to this guide: \<[https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard>](https://support.tazapay.com/how-do-i-request-a-refund-from-my-dashboard>)

### Refund using API

Sample cURL

```json
curl --request POST \
     --url https://service-sandbox.tazapay.com/v3/refund \
     --header 'accept: application/json' \
     --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
     --header 'content-type: application/json' \
     --data '
{
  "payin": "pay_cmrq5c74r2tr8tu3s2gg",
  "reason": "Customer Return",
  "webhook_url": "https://webhook.site/ref8y92937922"
}
'
```

> For full refund, specifying the amount and currency is not required to initiate a refund.
