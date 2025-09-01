# 🌐 AWS VPC Project: Building a Secure Cloud Network

This project demonstrates how to create a *Virtual Private Cloud (VPC)** in AWS with a public subnet, following best practices for IP addressing and scalability.

🎯 **Built for**: Paulo, a startup owner needing ~15,000 private IPs and a public-facing website.

🔧 **Skills Demonstrated**: AWS Networking, CIDR, Subnetting, VPC, Security, RFC 1918

---

## 🎯 Project Goals

- Create a VPC with **~15,000 private IP addresses**
- Use a `192.x.x.x` private IP range
- Allocate **at least 50 IPs** for a public subnet
- Ensure the network is secure and scalable

---

## 🛠️ Technical Implementation

### ✅ VPC Configuration
| Setting | Value |
|--------|-------|
| **VPC Name** | `First VPC` |
| **IPv4 CIDR Block** | `192.168.0.0/18` |
| **Total IPs** | 16,384 (meets 15k requirement) |
| **Public Subnet CIDR** | `192.168.1.0/26` |
| **Public IPs** | 64 (62 usable) |
| **Availability Zone** | No Preference |
| **Internet Gateway** | Enabled |

### 🔍 Why These Choices?

- **`192.168.0.0/18`**: From [RFC 1918](https://datatracker.ietf.org/doc/html/rfc1918), this is a **private IP range** — secure and not reachable from the internet.
- **`/18` = 16,384 IPs**: Next size above 15,000 → efficient use of space.
- **`192.168.1.0/26`**: 64 IPs → more than 50 needed for public servers.
- **Internet Gateway**: Allows public subnet to communicate with the internet.

Tools used:
- [Subnet Calculator](https://www.subnet-calculator.com) → verified IP counts
- AWS VPC Wizard → simplified setup

---

## 🖼️ Network Diagram

![VPC Architecture](diagrams/vpc-network-diagram.png)

> Diagram: VPC with public subnet and internet gateway

---

## 📸 Screenshots

### 1. VPC Creation Wizard
![Create VPC](screenshots/create-vpc-wizard.png)

> Configuring VPC with `192.168.0.0/18` and public subnet `192.168.1.0/26`

### 2. VPC Successfully Created
![Success](screenshots/vpc-success.png)

> Confirmation that the VPC was created

### 3. Route 53 Warning (Ignored)
![Route 53 Error](screenshots/route53-error.png)

> Note: This error is unrelated to VPC functionality and can be ignored.

---

## 🧠 Key Learnings

1. **Private IPs** (`192.168.x.x`, `10.x.x.x`, `172.16.x.x`) are used for internal communication and are **not accessible from the internet**.
2. **CIDR notation** (`/18`, `/26`) determines network size.
3. A **public subnet** needs an **Internet Gateway** to reach the internet.
4. Always plan IP space before building — avoid running out of IPs later.

flowchart TD
    Start([Start VPC Creation]) --> Search[Search for VPC in AWS Console]
    Search --> Dashboard[Open VPC Dashboard]
    Dashboard --> LaunchWizard[Click Launch VPC Wizard]
    LaunchWizard --> SelectConfig[Select 'VPC with Single Public Subnet']
    SelectConfig --> Configure
    
    subgraph Configure [Configuration Settings]
        VPC_CIDR[VPC IPv4 CIDR: 192.168.0.0/18]
        No_IPv6[IPv6 CIDR Block: None]
        VPC_Name[VPC Name: First VPC]
        Subnet_CIDR[Public Subnet CIDR: 192.168.1.0/26]
        AZ[Availability Zone: No Preference]
        Subnet_Name[Subnet Name: Public Subnet]
    end
    
    Configure --> Create[Click Create VPC]
    Create --> Success{VPC Creation Successful?}
    
    Success -- Yes --> Verify[Verify VPC in 'Your VPCs' list]
    Success -- No --> Troubleshoot[Troubleshoot CIDR Issues]
    
    Verify --> Complete([VPC Setup Complete])
    
    Troubleshoot --> CheckCIDR[Check for CIDR overlaps]
    CheckCIDR --> Adjust[Adjust CIDR blocks if needed]
    Adjust --> Create

   

   




