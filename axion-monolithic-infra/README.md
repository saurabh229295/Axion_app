<div align="center">

# ☁️ Axion Monolithic Infrastructure ☁️

[![Terraform Version](https://img.shields.io/badge/Terraform-%3E%3D1.0.0-623CE4.svg?style=for-the-badge&logo=terraform)](https://www.terraform.io/)
[![Azure Provider](https://img.shields.io/badge/Azure_Provider-v5.2.0-0089D6.svg?style=for-the-badge&logo=microsoft-azure)](https://registry.terraform.io/providers/hashicorp/azurerm/latest)
[![Deployment Status](https://img.shields.io/badge/Deployment-Ready-success.svg?style=for-the-badge&logo=checkmarx)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

*An enterprise-grade, highly-available monolithic architecture deployed on Microsoft Azure using Infrastructure as Code.* 🚀

</div>

---

## 🌟 Overview

Welcome to the **Axion Monolithic Infrastructure** repository! This project provisions a complete, robust, and scalable network and compute topology in Azure using **Terraform**. It strictly follows a modular Parent-Child structure for reusability, maintainability, and clean code architecture.

## 🏗️ Architecture Design

Our infrastructure is logically segregated into secure subnets, ensuring optimal traffic flow and security boundary isolation.

### 🌐 Virtual Network & Subnets
- 🛡️ **Frontend Subnet** (`10.0.1.0/24`) - Hosts the user-facing UI nodes.
- ⚙️ **Backend Subnet** (`10.0.2.0/24`) - Hosts application processing engines.
- 💾 **Database Subnet** (`10.0.3.0/24`) - Secured data layer for persistent storage.

### 💻 Virtual Machines (Ubuntu 24.04 LTS)
| 🖥️ VM Name | 📍 Subnet Location | 🔧 Purpose |
| :--- | :--- | :--- |
| **Axion UI VM** | Frontend Subnet | Serves the main Axion user interface |
| **Telemetry Query VM**| Backend Subnet | Handles complex telemetry queries & metrics |
| **Ingestion VM** | Backend Subnet | Ingests high-throughput real-time data |
| **Database VM** | Database Subnet | Hosts the relational/NoSQL monolithic datastore |

> **Note:** All nodes are provisioned with `Standard_B1s` instances and dynamic network interfaces coupled with Static Public IPs. 

---

## 📂 Repository Structure

This repository is built using a strict **Child-Parent Module** structure.

```text
axion-monolithic-infra/
├── 🌍 environments/
│   └── 🛠️ dev/
│       ├── main.tf              # Entrypoint calling all child modules
│       ├── provider.tf          # Azure Provider & Backend Config
│       ├── variables.tf         # Variable declarations
│       └── terraform.tfvars     # Environment-specific values
└── 📦 modules/
    ├── ☁️ azurerm_linux_virtual_machine  # Bundled VM & NIC provisioning
    ├── 🌐 azurerm_public_ip              # Static/Dynamic Public IPs
    ├── 📦 azurerm_resource_group         # Foundational Resource Groups
    ├── 🧩 azurerm_subnet                 # Secure Subnet definitions
    └── 🕸️ azurerm_virtual_network        # Core VNet architecture
```

---

## 🚀 Getting Started

### 📋 Prerequisites
* [Terraform](https://developer.hashicorp.com/terraform/downloads) v1.0+
* [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) configured and authenticated (`az login`)
* Active Azure Subscription

### ⚙️ Deployment Steps

1️⃣ **Navigate to the Dev Environment**
```bash
cd environments/dev
```

2️⃣ **Initialize Terraform**
*Downloads required providers and initializes the state backend.*
```bash
terraform init
```

3️⃣ **Validate the Configuration**
*Ensures the syntax and module references are perfectly crafted.*
```bash
terraform validate
```

4️⃣ **Plan the Infrastructure**
*Preview the resources that will be created.*
```bash
terraform plan
```

5️⃣ **Apply & Provision**
*Deploy the magic to Azure! ✨*
```bash
terraform apply -auto-approve
```

---

## 🔐 Security & Best Practices

- **Modularity:** 1-to-1 mapping of Terraform resources to reusable child modules.
- **State Management:** Remote backend configuration configured for collaborative state locking and storage.
- **OS Hardening:** Running the latest and most secure **Ubuntu 24.04 LTS**.
- **Variables:** Fully parameterized deployments via `.tfvars` for easy promotion across `dev`, `stage`, and `prod` environments.

---

<div align="center">

Made with ❤️ by the DevOps Insiders Team 

</div>
