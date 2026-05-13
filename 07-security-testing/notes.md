# Phase 7 — Security Testing & Event Log Analysis

## Tests Performed

### 1. Password Policy Enforcement
- Attempted to set password below 14 characters — rejected by domain ✅
- Attempted to set password without complexity requirements — rejected ✅
- Successfully set compliant password (14+ chars, uppercase, lowercase, number, symbol) ✅
- Error message confirmed: "does not meet length, complexity, or history requirements"

### 2. Control Panel Restriction
- Logged in as Jacob White (IT Admin — not restricted) — Control Panel accessible ✅
- Logged in as Charles Benson (Sales Employee — restricted)
  - Control Panel — access denied message displayed ✅
  - Settings — closed automatically ✅
- Confirmed GPO scoping working correctly by OU membership

### 3. Login Banner
- Verified banner displays before every login attempt ✅
- Title: Authorized Access Only
- Legal warning message displayed and requires acknowledgment before proceeding

### 4. Account Lockout Simulation
- Attempted login as chben with wrong password 5 times consecutively
- Account locked out after 5th attempt ✅
- Error message: "The referenced account is currently locked out"
- Unlocked account via AD Users and Computers → Sales → Employees → 
  Charles Benson → Properties → Account tab → Unlock account ✅
- Successfully logged in after unlock ✅

### 5. Windows Event Log Analysis
- Opened Event Viewer → Windows Logs → Security on Domain Controller
- Filtered for Event ID 4625 (Failed Logon)
  - 9 failed logon events recorded
  - Failure reason: Unknown user name or bad password
  - Timestamps match lockout simulation
- Filtered for Event ID 4740 (Account Lockout)
  - Account locked out: HOMELAB\chben
  - Caller Computer Name: WIN10-CLIENT
  - Timestamp recorded accurately

## Event IDs Reference
| Event ID | Description |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon attempt |
| 4740 | Account locked out |
| 4634 | Account logoff |

## Key Takeaways
- Account lockout policy effectively prevents brute force attacks
- Event logs provide clear forensic evidence of authentication activity
- GPO scoping by OU enables precise access control per user type
- Admin ability to unlock accounts from DC is a core helpdesk skill
- Event ID 4740 is the most useful for identifying lockout source and target

## Screenshots
- Account lockout error message on Windows 10 login screen
- Event ID 4625 filtered view showing failed logon attempts
- Event ID 4740 detail showing HOMELAB\chben locked out from WIN10-CLIENT
- Control Panel access denied message for Sales Employee
- Login banner displaying on Windows 10 client
