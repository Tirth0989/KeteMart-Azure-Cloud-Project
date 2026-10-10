# KeteMart Azure Cloud Project

An Azure cloud solution prototype for a retail business, developed for COMP615 Assessment 2. This repository contains the evidence portfolio documenting the architecture, deployed resources, security configuration, operations, and cost planning.

**Author:** Tirth Kaileshkumar Patel

## Evidence portfolio

[Download the KeteMart Evidence Portfolio](docs/KeteMart_Evidence_Portfolio.docx)

The Word document contains the architecture diagram, labelled Azure screenshots, design explanations, and a final evidence checklist. Download it and open it in Microsoft Word or another DOCX-compatible editor to view the full portfolio.

## Project scope

The solution combines a customer-facing ASP.NET Core application with a planned Windows-based legacy application environment. It explores managed hosting, relational data, network segmentation, credential management, document storage, monitoring, and cloud governance.

| Area | Azure services and configuration | Status described in the portfolio |
| --- | --- | --- |
| Customer web application | Azure App Service and ASP.NET Core | Working application and a saved Todo record shown |
| Database | Azure SQL Database | Provisioning and application connectivity documented |
| Secret storage | Azure Key Vault | Enabled SQL password secret documented; value hidden |
| Automated deployment | GitHub Actions and App Service Deployment Center | Pipeline configured and triggered; complete deliberate before/after change evidence unfinished |
| Legacy workload | Windows Server 2022 virtual machine | VM provisioned; IIS and legacy application deployment unfinished |
| Networking | Virtual Network, workload subnet, GatewaySubnet, and NSG | Resource configuration documented |
| Remote administration | Point-to-Site VPN Gateway | Gateway and root certificate configuration documented; successful VPN and tunneled RDP session not demonstrated |
| Shared files | Azure Files | Share created; bidirectional access not demonstrated |
| Document storage | Private Blob container and lifecycle policy | Storage and policy documented; Cool after 30 days and Archive after 90 days without modification |
| Monitoring | Log Analytics and Azure Monitor alerts | Workspace and two CPU alert rules documented |
| Governance | Resource groups, naming conventions, tags, and budget alerts | Configuration documented |
| Backup | Azure Backup | Planned; not configured |
| Infrastructure as code | Bicep networking template referenced by the document | Original template not supplied in this repository; live deployment not demonstrated |

## Architecture overview

The customer application uses App Service with Azure SQL Database. A SQL administrator password secret is stored in Key Vault. The portfolio documents an App Service connection string separately; it does not establish a working Key Vault reference or managed identity integration.

The legacy VM is placed in a dedicated subnet. A Point-to-Site VPN is the intended administration route, and the temporary public RDP rule was removed from the final configuration. The successful administrative connection remains unfinished.

Blob Storage handles document retention, Azure Files provides the planned file-sharing layer, and Log Analytics and alert rules support operational monitoring.

## Resource organisation

| Resource group | Functional area |
| --- | --- |
| `rg-ketemart-network` | Virtual network, network security group, and VPN Gateway |
| `rg-ketemart-web` | App Service, Azure SQL, and Key Vault |
| `rg-ketemart-legacy` | Windows virtual machine |
| `rg-ketemart-storage` | Blob Storage and Azure Files |
| `rg-ketemart-ops` | Monitoring and planned backup resources |

The prototype uses the New Zealand North region. Tags identify the project, environment, owner, and assessment cost centre.

## Repository contents

```text
KeteMart-Azure-Cloud-Project/
├── README.md
└── docs/
    └── KeteMart_Evidence_Portfolio.docx
```

This is an evidence and documentation repository. The application source code, GitHub Actions workflow, and original `main.bicep` file were not included in the supplied attachment. There are no deployment commands in this repository.

## Completion and limitations

The Azure for Students credit allowance was exhausted before all tasks were completed. The portfolio records these limitations explicitly.

Remaining work includes:

- Completing and demonstrating a successful Point-to-Site VPN connection and RDP session through the tunnel.
- Installing IIS and deploying the legacy application.
- Demonstrating Azure Files read/write access from both the VM and a local computer.
- Adding the original Bicep template and demonstrating its Azure deployment.
- Capturing a complete CI/CD before-and-after application change.
- Configuring Azure Backup and demonstrating recovery protection.
- Configuring the service endpoints identified in the portfolio.

## Cost planning

The portfolio includes a proposed monthly cost table and discussion of the USD 100 Azure for Students allowance. The VPN Gateway was identified as a major source of prototype credit consumption.

Its production cost figures are assessment estimates rather than a verified current quotation. Region, service availability, runtime, storage use, and administrative access choices must be checked before a real deployment.

## Skills demonstrated

- Azure resource provisioning and organisation
- ASP.NET Core application hosting and Azure SQL connectivity
- GitHub Actions deployment configuration
- Azure Key Vault and role-based access control
- Virtual networks, subnetting, and network security groups
- Point-to-Site VPN configuration and troubleshooting
- Blob lifecycle policies and Azure Files provisioning
- Log Analytics, monitoring alerts, tagging, and budget planning
- Technical documentation and evidence reporting
