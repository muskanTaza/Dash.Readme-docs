---
title: 'Guide to MT103: Explanation and Usage'
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
# What are different MT (Message Type) categories and the significance of MT103 in global finance?

## MT Categories:

The Society for Worldwide Interbank Financial Telecommunication (SWIFT) categorizes MTs into several types based on their function:

* MT1xx: Customer payments and other direct debits
* MT2xx: Financial institution transfers
* MT3xx: Treasury transactions
* MT4xx: Collections
* MT5xx: Securities
* MT6xx: Treasury markets
* MT7xx: Documentary credits
* MT9xx: Cash management and status

### **What is an MT103?**

MT103 is a standardized SWIFT message type used for making international wire transfers. It is part of the SWIFT message format, which facilitates communication between banks globally. MT103 messages provide detailed information about the transaction, including the sender, beneficiary, and transaction details. 

### MT103: Significance

MT103 is a specific message type within the MT1xx category. It's the most common message format used for cross-border customer payments. Here's what makes it important:

* Standardization: MT103 provides a globally recognized standard for payment instructions, ensuring smooth interoperability between banks worldwide.
* Comprehensive Information: It carries detailed payment information, including:
  * Sender and beneficiary details
  * Bank account numbers (IBAN, if applicable)
  * SWIFT codes (BIC) of banks involved
  * Payment amount and currency
  * Purpose of payment
  * Regulatory information (if required)
* Automation: Structured format allows for automated processing by banks, reducing manual intervention and speeding up transactions.
* Transparency: Provides a clear audit trail, facilitating tracking and reconciliation.

***

### **MT103 Message Structure**

MT103 messages are structured in specific fields defined by SWIFT standards. Below is the general breakdown:

### **1. Basic Header Block** (Block 1)

Identifies the sender’s bank.

```
{1:F01AAAABBBBXXXX0000000000}
```

* **F**: Message type indicator (F for financial messages)
* **01**: Application ID (01 for SWIFT FIN)
* **AAAABBBBXXXX**: Bank identifier of the sender (SWIFT code)
* **0000000000**: Session and sequence numbers

### **2. Application Header Block** (Block 2)

Identifies the receiver’s bank and message type.

```
{2:I103BBBBCCDDXXXXN}
```

* **I103**: Message type (MT103)
* **BBBBCCDDXXXX**: Receiver’s SWIFT code

### **3. User Header Block** (Optional, Block 3)

Contains optional custom information for the sender or receiver.

* **\{108:ST10302501220720}** : Transaction reference number.
* **\{111:001}** : Message priority.
* **\{121: a5949ec1-5c90-4d22-b1aa-f1e8ec0da5d2}** : Unique transaction identifier.
  * This is the `UETR` number which the beneficiary can share with their bank to track the status of this payment.

### **4. Text Block** (Block 4)

Contains the main details of the transaction, organized by field codes:

```
:20:ABC123XYZ                <--- Transaction Reference Number
:23B:CRED                    <--- Bank Operation Code (Credit Transfer)
:32A:241122USD10000,00       <--- Value Date, Currency, and Amount
:50K:/12345678               <--- Ordering Customer’s Account Number
JOHN DOE                    <--- Ordering Customer’s Name
:59:/87654321                <--- Beneficiary’s Account Number
JANE SMITH                  <--- Beneficiary’s Name
:70:/INV12345 Payment Details <--- Remittance Information
:71A:OUR                     <--- Details of Charges (OUR = Sender pays all fees)
```

***

### **Commonly Used Fields in MT103**

| **Field Code** | **Description**                     | **Example**                |
| -------------- | ----------------------------------- | -------------------------- |
| :20:           | Transaction Reference               | ABC123XYZ                  |
| :23B:          | Bank Operation Code                 | CRED                       |
| :32A:          | Value Date, Currency, and Amount    | 241122USD10000,00          |
| :50K:          | Ordering Customer’s Account Details | /12345678\\nJOHN DOE       |
| :59:           | Beneficiary’s Account Details       | /87654321\\nJANE SMITH     |
| :70:           | Remittance Information              | Payment for invoice #12345 |
| :71A:          | Charges Details                     | OUR (Sender pays all fees) |

***

### **How to Read an MT103 Message?**

1. **Identify Key Sections**:
   * Look for fields like `:20:` (Transaction Reference), `:50K:` (Sender’s Details), and `:59:` (Beneficiary’s Details).
2. **Understand Field Codes**:
   * Familiarize yourself with commonly used field codes and their meanings.
3. **Check Critical Details**:
   * Verify the amount, currency, and beneficiary account information.
4. **Locate Additional Details**:
   * Use `:70:` for remittance details and `:71A:` for charge codes.

***

# **MT103 FAQs**

### **Q1: Can MT103 be used as proof of payment?**

Yes, MT103 is often used as proof of payment since it contains all transaction details, including sender, receiver, and amount.

### **Q2: What does the charge code in MT103 mean?**

* **OUR**: Sender pays all charges.
* **SHA**: Charges are shared between sender and receiver.
* **BEN**: Beneficiary pays all charges.

### **Q3: Can I track an MT103 payment?**

Yes, the transaction reference (`:20:`) and SWIFT network allow banks to track MT103 payments.

### **Q4: How long does an MT103 transfer take?**

Typically, 1-3 business days, depending on the intermediary banks and jurisdictions.

***

### **Conclusion**

MT103 is a crucial message type in cross-border payments, ensuring secure and transparent transactions. By understanding its structure and usage, businesses and individuals can leverage it for effective payment processing, tracking, and reconciliation.
