---
title: Orchestrating multi-currency wallets
excerpt: >-
  This guides you to use Tazapay's infrastructure to orchestrate multi-currency
  wallets for your customers
deprecated: false
hidden: false
metadata:
  robots: index
---
## Overview

Tazapay enables platforms to onboard and verify individuals (e.g., employees, contractors, freelancers) and disburse payouts to them using a compliant, secure, and PSD2-aligned payment infrastructure. This guide outlines the process flow and responsibilities involved in KYC and payout capabilities through Tazapay.

This guide is ideal for platforms such as Employers of Record (EORs), marketplaces, or education platforms that want to:

* Onboard individuals
* Perform global KYC verification
* Allow individuals to collect funds
* Facilitate payouts using collected funds

***

## Key Concepts

**Individual Entity**\
A legal identity representing an individual (e.g., employee or contractor)

**Beneficiary**\
The destination bank account / wallet to allow the individuals to withdraw to. This is linked to the individual entity

**KYC**\
Know Your Customer verification process. This provides the facility to onboard an individual faster.

**Platform**\
The business integrating with Tazapay to facilitate onboarding, and payouts.

**PSP (Payment Service Provider)**\
Tazapay functions as a PSP under PSD2 regulations and hence can collect or disburse funds on behalf of the individuals.

**Payer**

The payer avails the services of the individual.

**Payee**

The payee is the individual who receives payment for their services.

***

## Flow

### Onboarding Individuals

1. The platform submits the basic details of the individual on Tazapay using [the Entity endpoints](https://docs.tazapay.com/reference/create-entity)
2. Post submission, the individual is reviewed by Tazapay's compliance and approved for payments.
3. You can add local bank account for the individual using [the beneficiary endpoints.](https://docs.tazapay.com/reference/create-beneficiary)

### Configuring collection accounts for the Individuals

1. You can set instructions for accounts in certain currencies to be configured by default as soon as the entity is approved.

2. You can also request for accounts to be configured on an ad-hoc basis.

3. As soon as a collection account is configured for an individual, Tazapay notifies you on email as well as through the [collection account creation webhooks](https://docs.tazapay.com/docs/collection-account).

### Tracking incoming payments from payers

Each incoming payment to Tazapay is represented by a collect object. The collect object contains the details of the destination account and recipient which enables reconciliation. Refer to [this guide](https://docs.tazapay.com/docs/collect) for webhook events.

### Making Payouts to the bank accounts

1. You can make payouts to the beneficiary destinations on behalf of the entities created during onboarding using [the Payout API](https://docs.tazapay.com/reference/create-payout).

2. Related Guide: [Click here](https://docs.tazapay.com/docs/building-an-integration-payouts)

## Ledgering - Tracking balances of each entity

Tazapay supports balance information at an omnibus level, that is, the cumulative balances of the individuals are aggregated. However, you can track individual balances using various endpoints from Tazapay. This flexibility allows you to dynamically configure pricing for individuals by adding a markup on Tazapay's pricing.

This is illustrated by the following example

**Incoming Funds**

Suppose Tazapay's pricing is 1% for any collection. There is an incoming payment of USD 5000 for an individual. Tazapay will credit USD 4950 to the master balance. Suppose the platform has contracted a pricing of 2% with the individual. In this case, the platform can credit USD 4900 to the individual's balance and USD 50 to their commission pool.

**Funds Withdrawal from Tazapay for Individuals**

Suppose Tazapay's pricing is 1% for any withdrawal. The platform has added a markup on this and has contracted a 2% withdrawal fees with the individual. The balance of an individual is USD 5000 and they wish to withdraw these funds to their bank account.  The platform can initiate a payout for USD 4900 (deducting 2%). USD 4900 will be credited to the individual's local bank account and Tazapay will deduct USD 4949 from the omnibus balance. USD 51 is part of the commission pool for the platform

> Alternatively, you also have the ability to configure tiered pricing on Tazapay for the individuals and Tazapay will settle your commission on a periodic basis to your bank account

## Withdrawing Commissions from Tazapay

The platform can choose to withdraw funds from the commission pool on Tazapay by [creating a payout](https://docs.tazapay.com/reference/create-payout) to their own bank account.