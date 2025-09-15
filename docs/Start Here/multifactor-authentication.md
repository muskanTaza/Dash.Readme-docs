---
title: MultiFactor Authentication
excerpt: >-
  MFA ensures only verified users gain access by requiring multiple
  authentication factors.
deprecated: false
hidden: true
metadata:
  robots: index
---
MFA adds an extra layer of security by requiring a second verification step beyond your password. It is mandatory for all Tazapay accounts at login and during high-risk actions.

# Setup

1. On login, you’ll be prompted to set up MFA.
2. Choose a method: Passkey (recommended), SMS code, or Authenticator App (TOTP).
3. Complete Verification.
4. Save your recovery codes securely for backup access.

You can also configure MFA in Settings > Security > Multi-Factor Authentication.

# MFA methods

* **Passkey (Recommended)** - Uses Face ID, fingerprint, or device lock.
* **SMS Code** - Receive a 6-digit code via text. Ensure your phone number is up to date.
* **Authenticator App (TOTP)** - Works offline with apps like Google Authenticator, 1Password, or Authy. Generates a new 6-digit code every 30s.
* **Recovery Codes** - One-time use backup codes provided during setup. Store offline in a secure location.
