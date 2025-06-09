---
title: >-
  poli_nzd, linkaja_idr, internet_banking_cop, fawry_egp, bank_push_php,
  internet_banking_zar, grabpay_php, paymaya_php, giropay_eur, blik_pln,
  mobile_money_kes, mobile_money_tzs, mobile_money_ugx, mobile_money_ghs,
  mobile_money_egp, bank_push_kes, bank_push_ngn, bank_initiation_eur,
  bank_initiation_gbp, shopeepay_idr, alipay_cny, eps_eur, multibanco_eur,
  mybank_eur, bancontact_eur, p24_eur, p24_pln, momo_vnd, shopeepay_vnd,
  doku_idr, upi_inr, internet_banking_inr, mobile_banking_thb, fpx_corp_myr,
  fpx_ind_myr
excerpt: >-
  These payment methods are a part of redirect type experience offered by
  Tazapay.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
**Redirect Experience** refers to a payment interface that is not embedded directly within a merchant’s platform. This experience allows users to complete transactions after being redirected to external sites and thus include one extra step in completing the payment.

### Types

1. **Default Redirect**: In this experience, user can directly simulate the payment success or failure on the redirect screen.
2. **Redirect with input:** There are payment methods which require some additional input from user on the payment screen such as bank selection or user\_id, password, etc. For this, we have pre-filled dummy details and user can enter any alphanumeric value to progress. Only once the input is selected, the user can simulate the payment scenarios.

### Prerequisites

1. User should have access to the Tazapay [sandbox](https://dashboard-sandbox.tazapay.com/) 
2. The user should use the sandbox API keys to authenticate for hitting the relevant endpoints.

### Common Testing Scenarios

1. **Successful Payment**: Ensure that a transaction using a native payment method for a successful simulation returns the expected success response.
2. **Payment Failure:** Ensure that a transaction using a native payment method for a failure simulation returns the expected success response.
3. **Expiry**: Certain payment methods due to downstream implications, you can ensure the behavior by simulating the expiry use case.

### Simulation Steps

1. Login to Tazapay [sandbox](https://dashboard-sandbox.tazapay.com).
2. Go to >> Create >> transaction
3. Add new customer / search existing and select
4. Add Invoice amount and Transaction description >> Click create link.
5. From the success screen, copy the payment link and open in a new tab.
6. Choose payment method >> This will redirect you to an external Tazapay hosted dummy screen which can be your bank screen or other gateway in the actual production. 
7. Simulate success/ Simulate failure/ Simulate expiry on the redirect screen.

### API Simulation

Alternatively, users can test by hitting the following endpoints with required params 

1. For Payins: [https://service-sandbox.tazapay.com/v3/payin](https://service-sandbox.tazapay.com/v3/payin)
   1. For Payin API, all transactions irrespective of the amount that are created in the sandbox environment are marked as successful within \~1-2 mins. Similarly, any payin created with amount as `20000 cents` will be marked as failed.
2. For Checkout: [https://service-sandbox.tazapay.com/v3/checkout](https://service-sandbox.tazapay.com/v3/checkout)

### Conclusion

The Tazapay redirect experience simulation guide provides a comprehensive framework to understand and test the payment experience. By following these steps, merchants can ensure a smooth, seamless, and reliable payment process for their users, enhancing overall satisfaction and trust.

For further details and support, please refer to the Tazapay documentation or contact the Tazapay support team.
