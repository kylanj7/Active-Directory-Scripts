# Active Directory Scripts Collection

![GitHub stars](https://img.shields.io/github/stars/yourusername/active-directory-scripts?style=social)
![GitHub forks](https://img.shields.io/github/forks/yourusername/active-directory-scripts?style=social)
![GitHub issues](https://img.shields.io/github/issues/yourusername/active-directory-scripts?style=social)
![License](https://img.shields.io/github/license/yourusername/active-directory-scripts)

A comprehensive collection of PowerShell scripts for managing and automating Active Directory Domain Services (AD DS) tasks with Azure integration capabilities.

## 📋 Overview

This repository contains production-ready PowerShell scripts for AD administrators to streamline common tasks and automate AD management processes. The collection covers everything from basic domain controller management to advanced security configurations and Azure integrations.

## ✨ Features

- **Comprehensive Coverage**: Scripts for all major AD management areas
- **Well-Documented**: Clear comments and examples for each script
- **Azure Integration**: Tools to connect on-premises AD with Azure services
- **Security-Focused**: Best practices for secure AD management
- **Easy to Use**: Organized by functional categories

## 🗂️ Repository Structure

```
active-directory-scripts/
├── domain-controller/
│   ├── install-adds.ps1
│   └── create-forest.ps1
├── user-management/
│   ├── query-disabled-users.ps1
│   └── find-inactive-computers.ps1
├── group-policy/
│   ├── create-gpo.ps1
│   └── link-gpo.ps1
├── fsmo/
│   ├── view-domain-roles.ps1
│   └── view-forest-roles.ps1
├── permissions/
│   └── grant-password-reset.ps1
├── remoting/
│   ├── enable-psremoting.ps1
│   └── create-remote-session.ps1
├── virtualization/
│   └── install-hyperv.ps1
├── backup/
│   ├── install-server-backup.ps1
│   └── create-backup.ps1
├── clustering/
│   ├── install-failover.ps1
│   └── create-cluster.ps1
├── security/
│   ├── enable-credential-guard.ps1
│   └── check-defender-status.ps1
└── azure-integration/
    ├── install-file-sync.ps1
    └── register-arc-server.ps1
```

## 🚀 Quick Start

```powershell
# Clone the repository
git clone https://github.com/yourusername/active-directory-scripts.git

# Navigate to the repository
cd active-directory-scripts

# Example: Find computers that haven't logged in for 90 days
$time = (Get-Date).AddDays(-90)
Get-ADComputer -Filter {LastLogonTimeStamp -lt $time} -Properties LastLogonTimeStamp
```

## 📚 Script Categories

### Domain Controller Management
Tools for installing and configuring domain controllers.

### User and Computer Management
Scripts to efficiently manage user accounts and computer objects.

### Group Policy Management
Streamline creation and management of Group Policy Objects.

### FSMO Role Management
View and transfer Flexible Single Master Operation roles.

### Permission Management
Set and audit Active Directory permissions.

### PowerShell Remoting
Configure and use PowerShell Remoting in your environment.

### Virtualization with Hyper-V
Manage virtual infrastructure supporting your AD environment.

### Backup and Recovery
Ensure your AD environment is properly backed up.

### High Availability and Failover Clustering
Implement resilient AD infrastructure.

### Security Management
Enhance the security posture of your Active Directory.

### Azure Integration
Connect your on-premises AD with Azure services:
- Azure Active Directory
- Azure File Sync
- Azure Backup
- Azure Arc
- Azure Update Management

## 💡 Examples

### Find and disable inactive user accounts
```powershell
# Find users who haven't logged in for 60 days
$inactiveTime = (Get-Date).AddDays(-60)
$inactiveUsers = Get-ADUser -Filter {LastLogonDate -lt $inactiveTime -and Enabled -eq $true} -Properties LastLogonDate

# Disable the inactive accounts
$inactiveUsers | Disable-ADAccount
```

### Bulk create users from CSV
```powershell
# Import users from CSV and create accounts
Import-Csv "new-users.csv" | ForEach-Object {
    New-ADUser -Name $_.Name -GivenName $_.FirstName -Surname $_.LastName -SamAccountName $_.Username -UserPrincipalName "$($_.Username)@contoso.com" -AccountPassword (ConvertTo-SecureString $_.Password -AsPlainText -Force) -Enabled $true
}
```

## 📝 Prerequisites

- Windows PowerShell 5.1 or PowerShell Core 7.x
- Active Directory PowerShell module
- Appropriate permissions in your AD environment
- For Azure integration: Azure PowerShell modules

## 🔄 Updates and Contributions

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Microsoft Documentation
- PowerShell Community
- Everyone who has contributed to this project

## 📧 Contact

Questions or feedback? Open an issue or contact the repository owner.

---

⭐ Star this repository if you find it useful!
