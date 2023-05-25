# HardeningKitty

This is the stable version of _HardeningKitty_ from the [Windows Hardening Project by Michael Schneider](https://github.com/0x6d69636b/windows_hardening). The stable version of _HardeningKitty_ is signed with the code signing certificate of _scip AG_. **Since this is the stable version, we do not accept pull requests in this repo, please send them to the [development repo](https://github.com/0x6d69636b/windows_hardening)**. 

_HardeningKitty_ supports hardening of a Windows system. The configuration of the system is retrieved and assessed using a finding list. In addition, the system can be hardened according to predefined values. _HardeningKitty_ reads settings from the registry and uses other modules to read configurations outside the registry.

The script was developed for English systems. It is possible that in other languages the analysis is incorrect. Please create an issue if this occurs.

## How to Run

Run the script with administrative privileges to access machine settings. For the user settings it is better to execute them with a normal user account. Ideally, the user account is used for daily work.

Download _HardeningKitty_ and copy it to the target system (script and lists). Then HardeningKitty can be imported and executed:

```powershell
# For Windows Server 2019 - Domain Controller - Level 1 Compliance
PS C:\tmp> Import-Module .\HardeningKitty.psm1
PS C:\tmp> Invoke-HardeningKitty -Mode Config -Backup -FileFindingList .\lists\cis_windows_server_2019_1.2.1_domain_controller_l1.csv
PS C:\tmp> Invoke-HardeningKitty -Mode HailMary -Report -FileFindingList .\lists\cis_windows_server_2019_1.2.1_domain_controller_l1.csv

# For Windows Server 2022 - Domain Controller - Level 1 Compliance
PS C:\tmp> Import-Module .\HardeningKitty.psm1
PS C:\tmp> Invoke-HardeningKitty -Mode Config -Backup -FileFindingList .\lists\cis_windows_server_2022_1.2.1_domain_controller_l1.csv
PS C:\tmp> Invoke-HardeningKitty -Mode HailMary -Report -FileFindingList .\lists\cis_windows_server_2022_1.2.1_domain_controller_l1.csv

## HardeningKitty Score

Each Passed finding gives 4 points, a Low finding gives 2 points, a Medium finding gives 1 point and a High Finding gives 0 points.

The formula for the HardeningKitty Score is _(Points achieved / Maximum points) * 5 + 1_.

### Rating

| Score | Rating Casual | Rating Professional |
| :---- | :------------ | :------------------ |
| 6 | 😹 Excellent | Excellent |
| 5 | 😺 Well done | Good |
| 4 | 😼 Sufficient | Sufficient |
| 3 | 😿 You should do better | Insufficient |
| 2 | 🙀 Weak | Insufficient |
| 1 | 😾 Bogus | Insufficient |

