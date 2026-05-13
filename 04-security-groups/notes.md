# Phase 4 — Security Groups

## Group Design
All security groups created in dedicated Groups OU.
Scope: Global | Type: Security

## Department Groups
| Group | Members |
|---|---|
| Sales_All | All 7 Sales users |
| Logistics_All | All 5 Logistics users |
| Visuals_All | All 6 Visual users |
| HR_All | Andy Mack |
| Finance_All | Will Thompson |
| IT_All | Jacob White |
| Risk_All | All 6 Risk users |
| Cleaning_All | All 4 Cleaning users |
| Leadership_All | Stacy Bond, Sandy Birks |

## Role-Based Groups
| Group | Purpose |
|---|---|
| All_Managers | All managers across every department |
| All_Leads | All leads across every department |
| All_Employees | All standard employees across every department |

## Key Decisions
- Used Global scope — users and groups exist within single domain
- Department managers included in both department group and All_Managers
- No duplicate accounts created for Leadership — existing accounts added to groups
- Followed AGDLP model: Accounts → Global Groups → Domain Local → Permissions

## Screenshots
- Sales_All group Properties showing Members tab
  ![Sales_All group members showing all 7 users with OU paths](https://github.com/abaez0/active-directory-homelab/blob/main/04-security-groups/AD%20Sales_ALL%20Group.png)
  
- All_Managers group Properties showing cross-department membership
![All_Managers group showing cross-department managers](https://github.com/abaez0/active-directory-homelab/blob/main/04-security-groups/AD%20All_Managers.png)



