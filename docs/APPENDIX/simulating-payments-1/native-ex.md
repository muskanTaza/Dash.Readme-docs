---
title: >-
  bank_push_vnd, wire_transfer, local_bank_transfer_usd,
  local_bank_transfer_ngn, local_bank_transfer_kes, local_bank_transfer_eur,
  local_bank_transfer_php, local_bank_transfer_nzd, local_bank_transfer_krw,
  local_bank_transfer_jpy, local_bank_transfer_idr, local_bank_transfer_hkd,
  local_bank_transfer_aud, local_bank_transfer_sgd, local_bank_transfer_cad,
  payid_aud, paynow_sgd, shopeepay_php, ovo_idr, stablecoin_usdt,
  stablecoin_usdc, promptpay_thb, bank_push_mxn, local_bank_transfer_vnd,
  qris_idr, bank_push_idr
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
These payment methods are part of native experience offered by Tazapay.

**Native Experience** refers to an integrated, user-friendly payment interface that is embedded directly within a merchant’s platform. This experience allows users to complete transactions without being redirected to external sites, offering a smoother, more cohesive user journey.

### Prerequisites

1. User should have access to the Tazapay [sandbox](https://dashboard-sandbox.tazapay.com/) 
2. The user should use the sandbox API keys to authenticate for hitting the relevant endpoints.

### Common Testing Scenarios

1. **Successful Payment**: Ensure that a transaction using a native payment method for a successful simulation returns the expected success response.
2. **Payment Failure: ** Ensure that a transaction using a native payment method for a failure simulation returns the expected success response.
3. **Expiry**: Certain payment methods expire such as QR based payment methods. You can ensure the behavior by simulating the expiry use case.

### Simulation Steps

1. Login to Tazapay [sandbox](https://dashboard-sandbox.tazapay.com).
2. Go to >> Create >> transaction
3. Add new customer / search existing and select
4. Add Invoice amount and Transaction description >> Click create link.
5. From the success screen, copy the payment link and open in a new tab.
6. Choose payment method >> Simulate success/ Simulate failure/ Simulate expiry on the same screen.

### API Simulation

Alternatively, users can test by hitting the following endpoints with required params 

1. For Payins: <https://service-sandbox.tazapay.com/v3/payin>
   1. For Payin API, all transactions irrespective of the amount that are created in the sandbox environment are marked as successful within ~1-2 mins. Similarly, any payin created with amount as `20000 cents` will be marked as failed.
2. For Checkout: <https://service-sandbox.tazapay.com/v3/checkout>

### Conclusion

The Tazapay native experience simulation guide provides a comprehensive framework to understand and test the integrated payment experience. By following these steps, merchants can ensure a smooth, seamless, and reliable payment process for their users, enhancing overall satisfaction and trust.

For further details and support, please refer to the Tazapay documentation or contact the Tazapay support team.