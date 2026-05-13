# Phase 1 — Domain Controller Setup

## Steps Completed
- Installed Windows Server 2022
- Added Active Directory Domain Services role
- Promoted server to Domain Controller
- Configured domain: homelab.local
- Forest and Domain Functional Level: Windows Server 2016
- DNS configured and integrated with AD

## Screenshots
- AD Users and Computers open showing homelab.local domain tree
- Server Manager showing AD DS installed
<img width="971" height="925" alt="image" src="https://github.com/user-attachments/assets/8fc0db53-ecd4-46fa-a294-04999640fac9" />


## Key Decisions
- Used .local suffix to avoid conflicts with public DNS
- Set functional level to 2016 (highest available)
- Left DNS Server and Global Catalog enabled on DC (industry standard)
