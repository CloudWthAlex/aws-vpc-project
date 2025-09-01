# 🌐 AWS VPC Creation Project

This project documents my hands-on practice in **creating a custom Amazon VPC** with a single public subnet as part of my **#200DaysOfCloudEngineer** journey.  

It covers the full workflow from **launching the VPC wizard** to **verifying the configuration** and handling troubleshooting steps.

---

## 📌 Project Overview

- **Cloud Provider**: AWS  
- **Service Used**: Amazon VPC  
- **Objective**: Create a Virtual Private Cloud with one public subnet.  
- **Outcome**: Successfully launched and verified a working VPC environment.  

---

## ⚙️ Configuration Details

| Setting                  | Value                |
|---------------------------|----------------------|
| VPC IPv4 CIDR Block      | `192.168.0.0/18`    |
| IPv6 CIDR Block          | None                |
| VPC Name                 | `First VPC`         |
| Public Subnet CIDR       | `192.168.1.0/26`    |
| Availability Zone        | No Preference       |
| Subnet Name              | `Public Subnet`     |

---

## 📖 Step-by-Step Workflow

```mermaid
flowchart TD
    Start([🚀 Start VPC Creation]) --> Search[🔍 Search for VPC in AWS Console]
    Search --> Dashboard[📊 Open VPC Dashboard]
    Dashboard --> LaunchWizard[🧙 Click Launch VPC Wizard]
    LaunchWizard --> SelectConfig[📑 Select 'VPC with Single Public Subnet']
    SelectConfig --> Configure
    
    subgraph Configure [⚙️ Configuration Settings]
        VPC_CIDR["🌐 VPC IPv4 CIDR: 192.168.0.0/18"]
        No_IPv6["🚫 IPv6 CIDR Block: None"]
        VPC_Name["🏷️ VPC Name: First VPC"]
        Subnet_CIDR["🟦 Public Subnet CIDR: 192.168.1.0/26"]
        AZ["📍 Availability Zone: No Preference"]
        Subnet_Name["📛 Subnet Name: Public Subnet"]
    end
    
    Configure --> Create[✅ Click Create VPC]
    Create --> Success{✨ VPC Creation Successful?}
    
    Success -- Yes --> Verify[🔎 Verify VPC in 'Your VPCs' list]
    Success -- No --> Troubleshoot[🛠️ Troubleshoot CIDR Issues]
    
    Verify --> Complete([🏁 VPC Setup Complete])
    
    Troubleshoot --> CheckCIDR[📏 Check for CIDR overlaps]
    CheckCIDR --> Adjust[✏️ Adjust CIDR blocks if needed]
    Adjust --> Create

    %% 🎨 STYLES
    style Start fill:#4caf50,stroke:#2e7d32,stroke-width:2px,color:white
    style Search fill:#2196f3,stroke:#0d47a1,stroke-width:2px,color:white
    style Dashboard fill:#2196f3,stroke:#0d47a1,stroke-width:2px,color:white
    style LaunchWizard fill:#2196f3,stroke:#0d47a1,stroke-width:2px,color:white
    style SelectConfig fill:#2196f3,stroke:#0d47a1,stroke-width:2px,color:white

    style VPC_CIDR fill:#ffe082,stroke:#f9a825,stroke-width:1.5px
    style No_IPv6 fill:#ffe082,stroke:#f9a825,stroke-width:1.5px
    style VPC_Name fill:#ffe082,stroke:#f9a825,stroke-width:1.5px
    style Subnet_CIDR fill:#ffe082,stroke:#f9a825,stroke-width:1.5px
    style AZ fill:#ffe082,stroke:#f9a825,stroke-width:1.5px
    style Subnet_Name fill:#ffe082,stroke:#f9a825,stroke-width:1.5px

    style Create fill:#8e24aa,stroke:#4a148c,stroke-width:2px,color:white
    style Success fill:#ff7043,stroke:#bf360c,stroke-width:2px,color:white
    style Verify fill:#00acc1,stroke:#006064,stroke-width:2px,color:white
    style Complete fill:#4caf50,stroke:#2e7d32,stroke-width:2px,color:white

    style Troubleshoot fill:#f44336,stroke:#b71c1c,stroke-width:2px,color:white
    style CheckCIDR fill:#f44336,stroke:#b71c1c,stroke-width:2px,color:white
    style Adjust fill:#f44336,stroke:#b71c1c,stroke-width:2px,color:white
