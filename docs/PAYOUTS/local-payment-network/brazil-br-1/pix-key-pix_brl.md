---
title: PIX key (pix_brl)
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
Payouts to PIX keys offer a fast, secure, and cost-effective way to disburse funds in Brazil using the country’s instant payment system, PIX. Introduced by the Central Bank of Brazil, PIX enables real-time transactions 24/7, including weekends and holidays. The PIX key acts as a unique identifier linked to a user’s bank account, simplifying the process by eliminating the need to input extensive banking details.

This documentation will guide you through the technical and operational steps required to manage payouts to PIX keys, helping your business leverage this efficient payment solution in Brazil.

# Key Features

* Payouts are instant (real-time)
* Maximum Limit - 100000 BRL

# Building an integration

## Step 1: Initiate a payout request

Tazapay uses a `payout` object to represent your intent to initiate a payout. The payout object tracks state changes from when the payout is initiated to when the beneficiary receives the funds.

Create a payout on your server using Tazapay’s payout API with the following information:

* Payout Amount - The amount in BRL you want to transfer to the beneficiary
* Type of Payout - `Local Payment Network`
* Beneficiary Details
  * Name
  * Type - `business` or `individual`
  * Tax ID
    * CPF (for individuals)
    * CNPJ (for businesses)
  * Destination Details
    * PIX key type
    * PIX key
* [Reason for Payout](https://docs.tazapay.com/docs/purpose)
* Transaction Description - Additional Description for a payout

### Possible values for `deposit_key_type`

* `cpf` - CPF (tax ID) for individuals
* `cnpj` - CNPJ (tax ID) for businesses
* `email` - Email Address
* `phone` - Phone
* `random` - Unique String

### Validations for PIX key

Ensure the following validations on your application for customer input for PIX key. Proper error handling should be implemented for cases where validations fail.

<Table align={["left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        PIX Key type
      </th>

      <th>
        Description
      </th>

      <th>
        Validation
      </th>

      <th>
        Example
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Tax ID
      </td>

      <td>
        The customer's CPF (for individuals) or CNPJ (for businesses)
      </td>

      <td>
        Must contain only numeric characters (no dashes, dots, or spaces\
        Length: CPF (11 digits), CNPJ (14 digits)
      </td>

      <td>
        34960826312
      </td>
    </tr>

    <tr>
      <td>
        Email
      </td>

      <td>
        The customer's email address.
      </td>

      <td>
        Must be a valid email format.\
        Should include an @ symbol and a domain (e.g., gmail.com).\
        Ensure there are no spaces or invalid characters.
      </td>

      <td>
        [john.doe@me.com](mailto:john.doe@me.com)
      </td>
    </tr>

    <tr>
      <td>
        Phone Number
      </td>

      <td>
        The customer's phone number in international format
      </td>

      <td>
        Must start with a + symbol.\
        Followed by the country code, then the last 2 numbers of the area code (DDD), and finally the phone number.\
        Only numeric characters allowed (no dashes, spaces, or special characters)
      </td>

      <td>
        \+5541985652123
      </td>
    </tr>

    <tr>
      <td>
        Random Key
      </td>

      <td>
        A unique string used as a PIX key
      </td>

      <td>
        Accept all characters, including alphanumeric, dashes (-), and special characters.\
        Length: No restrictions.
      </td>

      <td>
        wea478j-1O6l-03fm-t5gh-4L98er7785m2
      </td>
    </tr>
  </tbody>
</Table>

### Sample Request cURL

```bash
curl --request POST \
  --url https://service.tazapay.com/v3/payout \
  --header 'Idempotency-Key: ref_64528' \
  --header 'accept: application/json' \
  --header 'content-type: application/json' \
  --data '{
  "beneficiary_details": {
    "type": "individual",
    "name": "John Doe",
    "tax_id": "03655122063",
    "destination_details": {
      "type": "local_payment_network",
      "local_payment_network": {
        "type": "pix_brl",
        "deposit_key_type":"random",
        "deposit_key": "this_is_the_key_which_the_customer_inputs"
      }
    }
  },
  "amount": 10000,
  "currency": "BRL",
  "holding_currency": "USD",
  "purpose": "PYR030",
  "transaction_description": "Customer Balance Withdrawal",
  "type": "local_payment_network",
  "reference_id": "ref_64528"
}'
```

### Response

```json
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 10000,
        "balance_transaction": "btr_47294720302",
        "beneficiary": "bnf_ct8kquudb40u4ue8vcr0",
        "beneficiary_details": {
            "address": null,
            "destination": "lpn_r7w09r70wr",
            "destination_details": {
                "local_payment_network": {
                    "type": "pix_brl",
                  	"deposit_key_type":"random",
                    "deposit_key": "this_is_the_key_which_the_customer_inputs"
                },
                "type": "local_payment_network"
            },
            "documents": [],
            "email": "",
            "name": "John Doe",
            "national_identification_number": "",
            "phone": null,
            "tax_id": "03655122063",
            "type": "individual"
        },
        "charge_type": "",
        "created_at": "2025-01-20T11:07:40.716489Z",
        "currency": "BRL",
        "documents": [],
        "holding_currency": "USD",
        "id": "pot_cu72sv5i92bkana1hi8g",
        "logistics_tracking_details": [],
        "metadata": null,
        "mt103": "",
        "object": "payout",
        "payout_fx_transaction": {
            "exchange_rate": 1,
            "final": {
                "amount": 10000,
                "currency": "BRL"
            },
            "id": "fx_cu72sv08k2gk0gu7bk8g",
            "initial": {
                "amount": 10000,
                "currency": "BRL"
            },
            "object": "fx_transaction"
        },
        "purpose": "PYR030",
        "reference_id": "ref_64528",
        "statement_descriptor": "",
        "status": "processing",
        "status_description": "",
        "tracking_details": null,
        "transaction_description": "Customer Balance Withdrawal",
        "type": "local_payment_network"
    }
}
```

> `id` is the unique identifier you can use to track the payout.

## Alternatively, Creating a beneficiary and then initiating a payout

To align with your workflow, you can also choose to split Step 1 into two steps

* Step 1A: Creating a beneficiary using the [Create Beneficiary endpoint](https://docs.tazapay.com/reference/create-beneficiary)
* Step 1B: Initiating a payout using the [Create Payout endpoint](https://docs.tazapay.com/reference/create-payout)

### Step 1A: Creating a beneficiary

Tazapay uses a `beneficiary` object to the represent the receiver of funds of a payout. Pass the beneficiary name, type, tax ID, the PIX key type and the PIX key to /v3/beneficiary endpoint.

### Possible values for `deposit_key_type`

* `cpf` - CPF (tax ID) for individuals
* `cnpj` - CNPJ (tax ID) for businesses
* `email` - Email Address
* `phone` - Phone
* `random` - Unique String

### Validations for PIX key

Ensure the following validations on your application for customer input for PIX key. Proper error handling should be implemented for cases where validations fail.

<Table align={["left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        PIX Key type
      </th>

      <th>
        Description
      </th>

      <th>
        Validation
      </th>

      <th>
        Example
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Tax ID
      </td>

      <td>
        The customer's CPF (for individuals) or CNPJ (for businesses)
      </td>

      <td>
        Must contain only numeric characters (no dashes, dots, or spaces\
        Length: CPF (11 digits), CNPJ (14 digits)
      </td>

      <td>
        34960826312
      </td>
    </tr>

    <tr>
      <td>
        Email
      </td>

      <td>
        The customer's email address.
      </td>

      <td>
        Must be a valid email format.\
        Should include an @ symbol and a domain (e.g., gmail.com).\
        Ensure there are no spaces or invalid characters.
      </td>

      <td>
        [john.doe@me.com](mailto:john.doe@me.com)
      </td>
    </tr>

    <tr>
      <td>
        Phone Number
      </td>

      <td>
        The customer's phone number in international format
      </td>

      <td>
        Must start with a + symbol.\
        Followed by the country code, then the last 2 numbers of the area code (DDD), and finally the phone number.\
        Only numeric characters allowed (no dashes, spaces, or special characters)
      </td>

      <td>
        \+5541985652123
      </td>
    </tr>

    <tr>
      <td>
        Random Key
      </td>

      <td>
        A unique string used as a PIX key
      </td>

      <td>
        Accept all characters, including alphanumeric, dashes (-), and special characters.\
        Length: No restrictions.
      </td>

      <td>
        wea478j-1O6l-03fm-t5gh-4L98er7785m2
      </td>
    </tr>
  </tbody>
</Table>

### Sample Request cURL

```bash
curl --request POST \
  --url https://service.tazapay.com/v3/beneficiary \
  --header 'accept: application/json' \
  --header 'authorization: Basic YWtalajlf2QTBJMk1WMlBCR0RSNVJZQjk6c2tfNmVSbk5ZZW5ZdUNUWkw3TUdJbXo0VUF0MDVycHRoaVRScGtLVDJoT1hvTWxqUGthMlg1QU4yWWx2UWljVE05M1VFaHM0WFRuRElESFlGWjJVVXRwdm81TnRBRHVNa3lWQkZueXNucEtpUE1od043QnFrUG5nY3lOTGk4U0lpTTc=' \
  --header 'content-type: application/json' \
  --data '{
  "type": "individual",
  "name": "John Doe",
  "tax_id": "03655122063",
  "destination_details": {
    "type": "local_payment_network",
    "local_payment_network": {
      "type": "pix_brl",
      "deposit_key_type":"random",
      "deposit_key": "this_is_the_key_which_the_customer_inputs"
    }
  }
}'
```

### Response

```json
{
    "status": "success",
    "message": "",
    "data": {
        "address": null,
        "created_at": "2025-01-20T11:37:02.698196Z",
        "destination": "lpn_cu73anngp69raq2h90pg",
        "destination_details": {
            "local_payment_network": {
                "type": "pix_brl",
              	"deposit_key_type":"random",
                "deposit_key": "this_is_the_key_which_the_customer_inputs"
            },
            "type": "local_payment_network"
        },
        "documents": [],
        "email": "",
        "id": "bnf_cu73anli92bkana1ireg",
        "metadata": null,
        "name": "John Doe",
        "national_identification_number": "",
        "object": "beneficiary",
        "phone": null,
        "tax_id": "03655122063",
        "type": "individual"
    }
}
```

> `id` is the unique identifier for a beneficiary. Pass this in the Create Payout API to initiate a payout.

### Step 1B: Initiating a payout to the existing beneficiary

Create a payout on your server using Tazapay’s [payout API](https://docs.tazapay.com/reference/create-payout) with the following information:

* Payout Amount and Currency - The amount you want to transfer to the beneficiary
* Beneficiary ID
* Type of Payout - `local_payment_network`
* [Reason for Payout](https://docs.tazapay.com/docs/purpose)
* Transaction Description - Additional Description for a payout

### Sample cURL

```bash
curl --request POST \
  --url https://service-sandbox.tazapay.com/v3/payout \
  --header 'accept: application/json' \
  --header 'authorization: Basic YWtfdGVzdF9ZTFNVQUUwVjRCSEpIOFg0ODZPQzpza190ZXN0X0hNOEM3SEVSV1BmODVPZnFCMXhLTUJJMWlENnVWYTEyUWN2VE5ZeVJhSHhRZjVTOW9pZUtoOVZzejg3cnhtSEpaSlcyTHdVc0NSY2RWbUR0d0U4Q0VkdWNIUXRnNVQzVjl1NkltQWludkdiMjhWeXhTVVlsTTFMWWllbU80THFt' \
  --header 'content-type: application/json' \
  --data '{
  "beneficiary": "bnf_col3peio6qm3es8tqed0",
  "amount": 10000,
  "currency": "BRL",
  "purpose": "PYR030",
  "type": "local_payment_network",
  "reference_id": "ref_64528",
  "transaction_description": "Customer Balance Withdrawal"
}'
```

### Response

```json
{
    "status": "success",
    "message": "",
    "data": {
        "amount": 10000,
        "balance_transaction": "btr_47294720302",
        "beneficiary": "bnf_ct8kquudb40u4ue8vcr0",
        "beneficiary_details": {
            "address": null,
            "destination": "lpn_r7w09r70wr",
            "destination_details": {
                "local_payment_network": {
                    "type": "pix_brl",
                    "deposit_key": "this_is_the_key_which_the_customer_inputs"
                },
                "type": "local_payment_network"
            },
            "documents": [],
            "email": "",
            "name": "John Doe",
            "national_identification_number": "",
            "phone": null,
            "tax_id": "03655122063",
            "type": "individual"
        },
        "charge_type": "",
        "created_at": "2025-01-20T11:07:40.716489Z",
        "currency": "BRL",
        "documents": [],
        "holding_currency": "USD",
        "id": "pot_cu72sv5i92bkana1hi8g",
        "logistics_tracking_details": [],
        "metadata": null,
        "mt103": "",
        "object": "payout",
        "payout_fx_transaction": {
            "exchange_rate": 1,
            "final": {
                "amount": 10000,
                "currency": "BRL"
            },
            "id": "fx_cu72sv08k2gk0gu7bk8g",
            "initial": {
                "amount": 10000,
                "currency": "BRL"
            },
            "object": "fx_transaction"
        },
        "purpose": "PYR030",
        "reference_id": "ref_64528",
        "statement_descriptor": "",
        "status": "processing",
        "status_description": "",
        "tracking_details": null,
        "transaction_description": "Customer Balance Withdrawal",
        "type": "local_payment_network"
    }
}
```

> `id` is the unique identifier for a payout. You can use this to track the payout.

## Handle Payout Events

A payout is in the `processing` state after it is successfully initiated. The payout can move to one of the following three states from the processing state:

1. **requires\_action** - This is when the payout requires additional information. These additional information are typically required for reasons of regulatory compliance. Tazapay will reach out to your registered email address specifying the exact requirements and the next steps. After you have provided the necessary information, Tazapay will review and the payout can subsequently move to either `succeeded` or `failed`.
2. **succeeded** - The beneficiary has successfully received the funds. 
3. **failed** - This is the state when the payout fails. Any funds deducted for the payout will be credited back to your account. Tazapay specifies the reason for the failure in the field `status_description`

> Tazapay delivers [webhooks](https://docs.tazapay.com/docs/payout-webhook) to your registered endpoint notifying you of any event of interest for the payout.

> 📘
>
> The payout will fail in case the tax\_id (CPF or CNPJ) entered does not match the tax\_id linked to the PIX key. It is recommended to display this message to the users on the PIX key collection screen on your application.

## Simulating Payouts on Sandbox

* All payouts created on the test environment (sandbox) will automatically move to processing and eventually to succeeded. 
* Payouts created with amount `200000` will move to failed.
* Suggested values for PIX keys

| deposit\_key\_type | deposit\_key                                            |
| :----------------- | :------------------------------------------------------ |
| cpf                | 34960826312                                             |
| cnpj               | 34960826312123                                          |
| email              | [first.last@tazapay.com](mailto:first.last@tazapay.com) |
| phone              | \+5541985652123                                         |
| random             | abc-123                                                 |
