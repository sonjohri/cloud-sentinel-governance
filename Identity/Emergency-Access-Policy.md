# Azure Entra ID: Emergency Access (Break-Glass) Policy

## Overview
This policy ensures that administrative access to the tenant remains available 
even if primary authentication methods (MFA) or identity synchronization fails.

## Account Requirements
1. **Cloud-Only:** Accounts must be created directly in Entra ID (not synced from local AD).
2. **Naming Convention:** Use a clear prefix, e.g., `ZZZ-EMERG-ADMIN-DO-NOT-DELETE`.
3. **Domain:** Use the initial `*.onmicrosoft.com` domain.
4. **Roles:** Assign the **Global Administrator** role permanently (not via PIM).

## Hardening Standards (2026 Best Practices)
- **Phishing-Resistant MFA:** Register two unique FIDO2 security keys per account.
- **CA Exclusion:** These accounts MUST be excluded from all Conditional Access policies to prevent lockout during a configuration error.
- **Monitoring:** Configure a **Microsoft Sentinel** alert to trigger a 'Critical' incident if these accounts are ever used for sign-in.

## Storage & Maintenance
- Physical security keys are stored in separate, fireproof safes at different geographical locations.
- Access is tested quarterly (every 90 days) and documented in the project audit log.
