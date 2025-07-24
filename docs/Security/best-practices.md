---
title: Best Practices
deprecated: false
hidden: false
metadata:
  robots: index
---
# 1. Setup RBAC for all your users

## Understanding RBAC: Role-Based Access Control

### What Is RBAC?

Role-Based Access Control (RBAC) is a security and access management system that grants permissions to users based on their assigned roles within an organization.

### Why RBAC Is Important:

**Granular Control:** Instead of giving all users full access, RBAC lets you define roles such as Viewer, Editor, Finance, Operations, etc.—each with specific permissions.

**Operational Efficiency:** Employees can perform their duties without needing unnecessary access or depending on others.

**Security by Design:** Limits the potential damage from accidental or malicious misuse by ensuring users only have the access they need.

**Audit Readiness:** Because each action is tied to a specific user, RBAC provides a clear and accountable audit trail of who did what and when.

🧠 Think of RBAC as assigning “job responsibilities” inside a system, ensuring that people only touch what they’re responsible for.

## How RBAC Helps with MFA

While MFA strengthens your account by requiring a second verification step (e.g., an authenticator app or OTP), RBAC complements MFA by eliminating common operational and security challenges:

### Without RBAC:

Everyone relies on a central account with one shared MFA method.

If the device with MFA is lost or a key person is unavailable, the entire team is locked out.

No visibility into which team member performed which action.

### With RBAC:

Each team member has individual login credentials and their own MFA setup.

If one person loses access, it doesn't affect the rest of the team.

Every action is traceable to an individual, improving accountability and security.

✅ Best Practice: Always add users under RBAC roles rather than sharing a central login, especially when MFA is enforced.

<br />

# 2. Secure your recovery codes at a safe location

## Why Recovery Codes Are Critical:

Recovery codes are your backup access if your primary MFA method is lost (e.g., lost/stolen phone, uninstalled app). Without these codes, you may be permanently locked out of your account.

## What Happens if You Lose Them:

If you lose access to both your MFA device and recovery codes, you cannot access your account.

You will need to contact Tazapay Support and undergo manual identity verification. This process includes document checks and may delay access.

⚠️ Warning: Tazapay cannot bypass MFA without identity verification. Avoid downtime by saving your codes securely.

## Best Practices for Recovery Codes:

* Save them in a secure password manager.
* Do not store them in plain text or unsecured notes.
* Print them and store them in a safe physical location, like a locked cabinet.