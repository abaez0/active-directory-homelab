# Active Directory Home Lab

## Overview
A fully functional Active Directory environment built from scratch using VirtualBox. 
This lab simulates a real corporate network with a Windows Server 2022 Domain Controller 
and a Windows 10 client machine joined to the domain. The project demonstrates core 
sysadmin and security skills including AD configuration, user management, group policy 
enforcement, and security event monitoring.

---

## Environment
| Component | Details |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Domain Controller | Windows Server 2022 Standard Evaluation |
| Client Machine | Windows 10 Pro |
| Domain Name | homelab.local |
| Domain NetBIOS | HOMELAB |

---

## What Was Built

### 1. Domain Controller Setup
- Installed and configured Windows Server 2022
- Promoted server to Domain Controller
- Configured DNS integrated with Active Directory
- Domain: homelab.local (Forest and Domain Functional Level: 2016)

### 2. Organizational Unit Structure
- Designed a realistic OU hierarchy simulating a retail/warehouse organization
- 9 departments: Sales, Logistics, Visual, HR, Finance, IT, Risk, Cleaning, Leadership
- Sub-OUs per department reflecting real organizational levels (Managers, Leads, Employees)

### 3. User Accounts
- Created 30 user accounts across all departments
- Applied consistent naming convention: first 2 letters of first name + first 3 letters of last name
- Configured all accounts with temporary passwords and forced password change on first login
- Duplicate username resolution handled with sequential numbering (e.g. chben1)

### 4. Security Groups
- Created department groups (Sales_All, Logistics_All, etc.)
- Created role-based groups (All_Managers, All_Leads, All_Employees)
- Applied Global scope and Security type following industry standard AGDLP model

### 5. Group Policy Objects
| GPO | Scope | Purpose |
|---|---|---|
| Password Policy | Domain | 14 char minimum, complexity, 90 day expiry, 24 password history |
| Account Lockout | Domain | 5 attempts, 30 min lockout, 30 min counter reset |
| Login Banner | Domain | Legal warning displayed before every login |
| USB Storage Restriction | Domain | Blocks all removable storage domain-wide |
| Screen Lock Policy | Domain | Auto-locks after 5 minutes of inactivity |
| Restrict Control Panel | Employees OUs | Prevents standard employees from accessing system settings |

### 6. Windows 10 Client
- Deployed Windows 10 Pro VM
- Configured DNS to point to Domain Controller
- Successfully joined machine to homelab.local domain
- Verified domain user authentication on client machine
- Confirmed GPO application using gpresult /r

### 7. Security Testing & Event Log Analysis
- Simulated brute force attack by triggering account lockout (5 failed attempts)
- Located and unlocked locked account via AD Users and Computers
- Analyzed Windows Security Event Log for:
  - Event ID 4625 — Failed logon attempts
  - Event ID 4740 — Account lockout
- Verified Control Panel restriction applied to Employees but not IT staff
- Confirmed Login Banner displays on every login attempt

---

## Key Skills Demonstrated
- Active Directory deployment and configuration
- Organizational Unit design and user lifecycle management
- Group Policy creation, linking, and troubleshooting
- Security hardening following principle of least privilege
- Windows Event Log analysis and security monitoring
- DNS configuration and troubleshooting in an AD environment
- Network troubleshooting between virtualized machines
- Documentation and lab methodology

---

## Lessons Learned
- Password policies for domain users must be configured in the Default Domain Policy, 
  not a custom GPO linked to an OU
- IPv6 DNS can override IPv4 DNS settings and must be accounted for in network configuration
- GPO changes require either a gpupdate /force or machine restart to apply immediately
- Snapshots should be taken at every major milestone to enable safe rollback
- Account lockout events (4740) clearly identify the affected account and source machine, 
  making them valuable for security investigations

---

## Screenshots
*(Screenshots organized by phase in repository folders)*
