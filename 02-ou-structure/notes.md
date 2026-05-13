# Phase 2 — Organizational Unit Structure

## OU Design
Designed to reflect a real retail/warehouse organization with 9 departments 
and sub-OUs representing organizational levels within each department.

## Structure
- Sales (Managers, Leads, Employees)
- Logistics (Managers, Leads, Employees)
- Visual (Managers, Leads, Employees)
- HR (Employees)
- Finance (Employees)
- IT (Admins)
- Risk (Managers, Employees)
- Cleaning (Managers, Employees)
- Leadership (Store Manager, Department Managers, Marketing)
- Groups (dedicated OU for all security groups)

## Key Decisions
- Kept single-person departments (HR, Finance, IT) flat — built for growth not current headcount
- Separated Groups into its own OU following best practice
- Used OUs instead of default containers to enable GPO application
- Leadership isolated in its own OU for targeted policy control

## Screenshots
- Full OU tree expanded in AD Users and Computers
- Sales department showing populated sub-OUs

![Full OU tree showing all departments](Screenshot_2026-04-30_202245.png)

![Logistics Employees OU with users](AD_OU_Tree.png)

![Visual Employees OU with users](AD_OU_Tree_2.png)
