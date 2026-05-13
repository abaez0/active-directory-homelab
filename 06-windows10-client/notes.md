# Phase 6 — Windows 10 Client

## Setup
- Installed Windows 10 Pro (required for domain join — Home edition cannot join a domain)
- Configured VM with 8GB RAM, 4 CPUs, 50GB storage
- Set network adapter to Bridged Adapter to enable communication with Domain Controller

## Network Configuration
- Disabled IPv6 on client network adapter to prevent DNS override
- Set static DNS server to Domain Controller IP: 192.168.1.167
- Verified connectivity using ping and nslookup

## Domain Join
- Renamed computer to WIN10-CLIENT
- Joined homelab.local domain via System Properties → Computer Name → Change
- Authenticated with domain Administrator credentials
- Restarted machine to complete domain join

## Verification
- Login screen updated to show HOMELAB domain
- Logged in as domain user jawhi (Jacob White — IT Admin)
- Ran gpresult /r to confirm GPOs applying correctly
- Confirmed applied GPOs: Default Domain Policy, Password Policy, 
  USB Storage Restrictions, Login Banner, Screen Lock Policy

## Troubleshooting Encountered
- IPv6 DNS was overriding IPv4 DNS settings causing domain resolution failure
  - Resolution: Disabled IPv6 on network adapter
- GPO password settings not applying from custom GPO
  - Resolution: Password policy must be configured in Default Domain Policy
- Windows Firewall on Server blocking domain traffic
  - Resolution: Temporarily disabled firewall to confirm domain join, 
    then re-enabled and added specific firewall rules

## Screenshots
- Windows 10 login screen showing HOMELAB domain
- Desktop logged in as Jacob White (domain user)
- gpresult /r output showing applied GPOs
