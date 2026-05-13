# Phase 5 — Group Policy Objects

## GPO Summary

### Password Policy (Default Domain Policy)
| Setting | Value |
|---|---|
| Enforce password history | 24 passwords |
| Maximum password age | 90 days |
| Minimum password age | 1 day |
| Minimum password length | 14 characters |
| Password complexity | Enabled |
| Reversible encryption | Disabled |

### Account Lockout Policy (Default Domain Policy)
| Setting | Value |
|---|---|
| Account lockout threshold | 5 invalid attempts |
| Account lockout duration | 30 minutes |
| Reset lockout counter after | 30 minutes |

### Login Banner
- Title: Authorized Access Only
- Message: Legal warning notifying users the system is monitored and access is restricted
- Scope: homelab.local (domain-wide)

### USB Storage Restriction
- All Removable Storage classes: Deny all access — Enabled
- Removable Disks: Deny execute access — Enabled
- Removable Disks: Deny read access — Enabled
- Removable Disks: Deny write access — Enabled
- Scope: homelab.local (domain-wide)

### Screen Lock Policy
- Screen saver: Enabled
- Screen saver timeout: 300 seconds (5 minutes)
- Password protect screen saver: Enabled
- Scope: homelab.local (domain-wide)

### Restrict Control Panel
- Prohibit access to Control Panel and PC Settings: Enabled
- Scope: Employees OUs only (Sales, Logistics, Visual, HR, Finance, IT, Risk, Cleaning)
- Leads and above retain access

## Key Lessons Learned
- Password policies must be set in Default Domain Policy to apply at domain level
- Custom GPOs linked to OUs cannot override domain-level password settings
- GPO changes require gpupdate /force or machine restart to apply immediately
- LSDOU order determines which policy wins when conflicts exist

## Screenshots
- Group Policy Management console showing all GPOs
- Password Policy settings
- Account Lockout Policy settings
- gpresult /r output on Windows 10 client
