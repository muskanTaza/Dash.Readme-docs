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

# Managing MFA

From Settings > Security > MFA, you can:

* Add/remove passkeys
* Update your SMS number
* Replace your authenticator app
* Change your default method
* View or regenerate recovery codes

***

# Best Practices

* Enable at least two MFA methods to prevent lockout.
* Store recovery codes securely and offline.
* Prefer Passkeys for best balance of security and convenience.
* Use role-based access: add teammates via Settings > Manage team > Invite Teammate so each user has independent MFA.

# Support

If you lose access to all MFA methods and recovery codes, contact [support@tazapay.com](mailto:support@tazapay.com). Identity verification will be required.
