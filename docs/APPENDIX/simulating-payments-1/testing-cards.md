---
title: Testing Cards
excerpt: >-
  When testing your integration with Tazapay, you can use the following test
  card numbers to simulate various scenarios. These cards will not carry out any
  real transactions, but they will return responses as if the transactions were
  being processed by a live system. This enables you to test your integration
  thoroughly without incurring any actual costs.  ###
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
### Test Card Details

| Category                | Scenarios                                 | Card No.         | CVV                    | Expiry          | "Password/PIN(Case sensitive)" |
| ----------------------- | ----------------------------------------- | ---------------- | ---------------------- | --------------- | ------------------------------ |
| Without 3DS             | Transaction Success                       | 4556218578001529 | Any 3 numerical digits | Any future date | -                              |
| Without 3DS             | Transaction Declined                      | 4804262554494753 | Any 3 numerical digits | Any future date | -                              |
| With 3DS - Frictionless | Authentication Successful                 | 4532691318874448 | Any 3 numerical digits | Any future date | -                              |
| With 3DS - Frictionless | Authentication Failure                    | 4929653796729263 | Any 3 numerical digits | Any future date | -                              |
| With 3DS - Frictionless | Authorization Successful                  | 4716858016270272 | Any 3 numerical digits | Any future date | -                              |
| With 3DS - Frictionless | Authorization failure- Insufficient funds | 4556225847192831 | Any 3 numerical digits | Any future date | -                              |
| With 3DS - Challenge    | Authentication Successful                 | 4716959793397708 | Any 3 numerical digits | Any future date | 101010!                        |
| With 3DS - Challenge    | Authentication Failure                    | 4716959793397708 | Any 3 numerical digits | Any future date | Any wrong pin                  |
| With 3DS - Challenge    | Authorization Successful                  | 4916243871650546 | Any 3 numerical digits | Any future date | -                              |
| With 3DS - Challenge    | Authorization failure- Insufficient funds | 4024007127258902 | Any 3 numerical digits | Any future date | -                              |

### Handling Test Card Scenarios

To ensure your integration can handle different card responses, it's important to test various scenarios. Use the provided test card numbers to simulate responses like successful transactions, insufficient funds, and declined transactions. This testing helps in identifying how your application handles different outcomes and ensures a smooth user experience.

### Prerequisites

1. User should have access to the Tazapay [sandbox](https://dashboard-sandbox.tazapay.com/) 
2. The user should use the sandbox API keys to authenticate for hitting the relevant endpoints.

### Using Test Cards

When using test cards, keep the following in mind:

* **Do not use real card information**: Always use the provided test card numbers to avoid any unintended real transactions.
* **Expiry dates**: You can use any future date for the expiry date unless specified otherwise.
* **Security code (CVV)**: Use the provided CVV for each card number. For test purposes, any three-digit code should be acceptable.

### Common Testing Scenarios

1. **Successful Payment**: Ensure that a transaction using a test card for a successful transaction returns the expected success response.
2. **Insufficient Funds**: Test your error handling by simulating transactions with cards that are set to decline due to insufficient funds.
3. **Card Declined**: Validate your application's ability to handle declined transactions gracefully.
4. **Expired Card**: Ensure your system correctly identifies and handles expired cards.

### Conclusion

Thorough testing with the provided test cards ensures that your integration with Tazapay is robust and handles various real-world scenarios effectively. This leads to a smoother payment experience for your users and minimizes the risk of unexpected issues in production.

For any issues or further assistance, please refer to our support documentation or contact our support team at [support@tazapay.com](mailto:support@tazapay.com).
