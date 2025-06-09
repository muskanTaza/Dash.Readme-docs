---
title: Reconciliation
excerpt: >-
  This section outlines the systematic verification of transaction and
  settlement records, ensuring all financial activities are accurately captured
  and aligned with contractual agreements. Learn detailed steps for volumetric,
  fee/pricing, and disbursement timing reconciliations to maintain transparency
  and accuracy in your financial operations with Tazapay.
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
<h2>Reconciliation Overview</h2>
<p>Reconciliation is a key financial process that ensures all transactions are fully and accurately recorded under a <code>settlement_id</code>. This process guarantees that the deposits made into the merchant's bank account match the amounts reported for the corresponding settlement cycle, which is weekly by default. This alignment is crucial for verifying that what is in the bank accurately reflects the expected settlements.</p>

<h3>How to Reconcile</h3>
<p>To effectively reconcile your accounts, follow these steps:</p>

<ol>
  <li><strong>Download Your Settlement Report:</strong> First, download your settlement report to review your transactions and their details. For guidance on how to do this, see <a href="https://docs.tazapay.com/docs/how-to-download-settlement-report">this link</a>.</li>
  <li><strong>Review Transactions and Settlements:</strong> Use the report and the dashboard to ensure accuracy and completeness in the following areas:</li>
  <ul>
    <li><strong>Verify Fee Amounts:</strong> Check if the fee deductions on your transactions are as expected.</li>
    <li><strong>Verify Funds Deposited:</strong> Ensure the funds deposited into your bank account match those listed in the settlement report. Use this in conjunction with the transaction report to verify the net amount deposited.
      <ul>
        <li>If there is a discrepancy between the amount mentioned in the settlement report and what is in the bank, reach out to your bank as they might have made deductions.</li>
      </ul>
    </li>
    <li><strong>Reconcile With Other Objects:</strong> Use the report to reconcile with other objects such as payins, refunds, and collects, including charges and fees deducted for any refunds, adjustments, or disputes.</li>
  </ul>
</ol>

<p>For a more detailed reconciliation guide with examples, follow <a href="https://docs.tazapay.com/docs/reconciliation-guide">this link</a>.</p>

<h3>Settlements are Disabled for the Following Flows:</h3>
<ol>
  <li><strong>Customers with Global Collection Accounts for Payouts Only:</strong>
    <ul>
      <li>This flow involves customers topping up their balance and using it to process payouts.</li>
    </ul>
  </li>
  <li><strong>Customers Converting Payin Transactions to Balance for Payouts:</strong>
    <ul>
      <li>This refers to customers who process payin transactions, convert these to their balance, and then use this balance to process payouts.</li>
    </ul>
  </li>
</ol>