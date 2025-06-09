---
title: Multi Factor Authentication
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
Tazapay now supports **Multi-Factor Authentication (MFA)** to enhance account security and prevent unauthorized access. This is mandatory due to the introduction of **balances and payouts** on the platform.

***

## 👤 Who Needs to Use MFA?

Every **Tazapay merchant account** user:

* Must **set up MFA**
* Can choose from **Passkey**, **SMS OTP**, or **Authenticator App**
* Can generate **Recovery Codes** as a fallback method

***

## 🔐 Login Flow

### Step 1: Sign In

Enter your **email and password** or **Sign in with Google**

### Step 2: Authenticate

Choose from the available methods:

* **Passkey** (if previously set up)
* **SMS OTP**
* **Authenticator App Code**

***

## ⚙️ Dashboard → Settings → Security Tab

Manage your MFA settings:

* Set up/remove **Passkeys**
* Add/change **mobile number**
* Add/change **Authenticator App**
* Set default 2FA method
* **Generate Recovery Codes**

> 🔒 All changes require 2FA verification

***

## 🆘 Recovery Code Login

If you're locked out of your account:

1. Click **"Sign in another way"**
2. Select **"Use Recovery Code"**
3. Enter the **20+ character code**
4. Code is **one-time use only**

> Don’t have backup codes? Contact [support@tazapay.com](mailto:support@tazapay.com)

***

## 🕒 7-Day Session Memory

* Checkbox: **"Remember me for 7 days"** on login screen
* Skips MFA for 7 days **on the same device**
* Tooltip info:
  > “Enabling this option allows you to log in on this device without requiring two-factor authentication for the next 7 days.”

> ⚠️ Only shown if MFA is enabled

***

## 🔐 Sensitive Operations Require Fresh MFA

Any of these actions require re-authentication if last 2FA > 1 hour ago:

* Payout > $10k
* Refund > $10k
* Add/switch bank accounts
* View/regenerate API keys
* Add/remove passkeys
* Change default MFA method
* Add sub-user / change sub-user rights
* Change password

> Message: *"Please authenticate yourself as you are going to perform a sensitive operation."*

* Passkey is first preference
* Email confirmation sent on completion
