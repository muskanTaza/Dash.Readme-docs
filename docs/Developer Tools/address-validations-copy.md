---
title: Address Validations (COPY)
excerpt: Ensure correct input from customers to increase conversion
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
It is mandatory to ensure the following validations for the billing address for customers in United States of America (US) and Canada (CA). This is applicable to:

1. /v3/checkout
2. /v3/escrow
3. confirmCardPayment() function (part of JS SDK)

## Validations

<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th>
        Field
      </th>

      <th>
        Validation
      </th>

      <th>
        Applicable for countries
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        billing\_details.address.country
      </td>

      <td>
        ISO 3166-1 alpha-2 country code in uppercase
      </td>

      <td>
        US, CA
      </td>
    </tr>

    <tr>
      <td>
        billing\_details.address.line1
      </td>

      <td>
        Min 4 characters, Only alphanumeric characters allowed
      </td>

      <td>
        US, CA
      </td>
    </tr>

    <tr>
      <td>
        billing\_details.address.city
      </td>

      <td>
        Only alphanumeric characters allowed
      </td>

      <td>
        US, CA
      </td>
    </tr>

    <tr>
      <td>
        billing\_details.address.state
      </td>

      <td>
        Only alphanumeric characters allowed
      </td>

      <td>
        US, CA
      </td>
    </tr>

    <tr>
      <td>
        billing\_details.address.state
      </td>

      <td>
        Can be the state name or state code (ISO 3166-2), The state names and code can be accessed from <a href = "https://www.iso.org/obp/ui/#iso:code:3166:US" target="_blank">this list</a>
      </td>

      <td>
        US
      </td>
    </tr>

    <tr>
      <td>
        billing\_details.address.postal\_code
      </td>

      <td>
        For US, valid length is 5 or 9 and the format is NNNNN\
        For CA, valid length is 6 and the format is ANA NAN (A-Alphabet, N- Number)
      </td>

      <td>
        US, CA
      </td>
    </tr>

    <tr>
      <td>
        billing\_details.phone.calling\_code
      </td>

      <td>
        Only codes from <a href = "https://en.wikipedia.org/wiki/List_of_country_calling_codes#Zones_3%E2%80%934:_Europe" target = "_blank"> this list </a>
      </td>

      <td>
        US, CA
      </td>
    </tr>

    <tr>
      <td>
        billing\_details.phone.number
      </td>

      <td>
        Only numeric values allowed. Length allowed:\
        USA: 10\
        Canada: 10
      </td>

      <td>
        US, CA
      </td>
    </tr>
  </tbody>
</Table>
