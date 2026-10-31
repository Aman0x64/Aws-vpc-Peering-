## ☁️ AWS VPC Peering | Private Network Connectivity
<div align="center">

<img src="https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg" alt="AWS Logo" width="180"/>
AWS VPC Peering Project
Secure Private Communication Between Two Amazon VPCs




</div>
<p align="center">
  <b>Connecting Two Isolated AWS Virtual Private Clouds Through Secure VPC Peering</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/AWS-Cloud%20Networking-orange?logo=amazonaws" />
  <img src="https://img.shields.io/badge/Service-VPC%20Peering-blue" />
  <img src="https://img.shields.io/badge/OS-Amazon%20Linux%202023-232F3E?logo=amazonlinux" />
  <img src="https://img.shields.io/badge/Status-Completed-success" />
</p>

---

## 📌 Project Overview

What if two applications hosted in completely separate private networks needed to communicate securely without exposing their servers to the public internet?

This project explores that challenge using **Amazon Web Services (AWS) VPC Peering**.

The objective was to establish private communication between two isolated Virtual Private Clouds (VPCs), configure routing and security rules, and demonstrate connectivity using private IPv4 addresses.

A bastion host provides secure administrative access to the private EC2 instances, while VPC Peering enables direct communication between workloads across both VPCs.

**The result:** Two independent VPCs communicating over private network paths without requiring public IP addresses on either application server.

## 📄 Project Documentation

The complete project report includes the AWS architecture, VPC configuration, route tables, security groups, connectivity testing, SSH validation, and implementation evidence.

📥 **[Download AWS VPC Peering Project Report (PDF)](Aman_Mishra_EWB_VPC_Peering.pdf)**

## 🏗️ Architecture

```text
                    YOUR LAPTOP
                         |
                      SSH / 22
                         |
                  INTERNET GATEWAY
                         |
              ┌──────────────────────┐
              │        VPC A         │
              │     10.10.0.0/16     │
              │                      │
              │   Public Subnet      │
              │    10.10.1.0/24      │
              │                      │
              │    Bastion Host      │
              │     10.10.1.92       │
              │          |           │
              │          | SSH       │
              │          v           │
              │   Private Subnet     │
              │    10.10.2.0/24      │
              │                      │
              │     App Server A     │
              │    10.10.2.111       │
              └──────────┬───────────┘
                         |
                  VPC PEERING
                         |
              ┌──────────┴───────────┐
              │        VPC B         │
              │     10.20.0.0/16     │
              │                      │
              │    Private Subnet    │
              │     10.20.1.0/24     │
              │                      │
              │     App Server B     │
              │    10.20.1.151       │
              │                      │
              │   No Internet Gateway│
              └──────────────────────┘
```

## 🛠️ Technologies & AWS Services

| Technology | Purpose |
|---|---|
| Amazon VPC | Isolated virtual networks |
| VPC Peering | Private communication between VPCs |
| Amazon EC2 | Virtual machine instances |
| Internet Gateway | Public connectivity for VPC A |
| Route Tables | Traffic routing between networks |
| Security Groups | Instance-level traffic filtering |
| Amazon Linux 2023 | EC2 operating system |
| SSH | Secure remote administration |
| ICMP / Ping | Network connectivity testing |

## 🌐 Network Configuration

| Resource | Configuration |
|---|---|
| VPC A | `10.10.0.0/16` |
| VPC B | `10.20.0.0/16` |
| VPC A Public Subnet | `10.10.1.0/24` |
| VPC A Private Subnet | `10.10.2.0/24` |
| VPC B Private Subnet | `10.20.1.0/24` |
| Bastion Host | `10.10.1.92` |
| Application Server A | `10.10.2.111` |
| Application Server B | `10.20.1.151` |
| AWS Region | Sydney (`ap-southeast-2`) |

## 🔐 Security Implementation

Security was configured using AWS Security Groups and private network addressing.

- Application servers have no public IPv4 addresses.
- SSH access to private instances is routed through the bastion host.
- Security groups restrict inbound SSH access to the required source.
- ICMP traffic is permitted between the application servers for connectivity testing.
- VPC B operates without an Internet Gateway.
- Private workloads communicate using private IPv4 addresses.

## 🧪 Testing & Validation

The project was validated through actual terminal commands executed on the EC2 instances.

### 1. Forward Connectivity

Executed from App-A:

```bash
ping -c 4 10.20.1.151
```

**Result:** 4 packets received, 0% packet loss.

### 2. Reverse Connectivity

Executed from App-B:

```bash
ping -c 4 10.10.2.111
```

**Result:** 4 packets received, 0% packet loss.

### 3. Private SSH Access

Connected to App-B through the bastion host:

```bash
ssh -i ~/ewb-vpc-key.pem ec2-user@10.20.1.151
```

**Result:** Successfully accessed the private EC2 instance.

### 4. Controlled Network Failure

Temporarily removed the required ICMP inbound rule, tested connectivity, and restored the rule to verify network recovery.

**Result:** Connectivity was successfully restored after the security rule was reinstated.

## 📚 Key Learnings

Through this project, I gained practical experience with:

- Designing AWS VPC architectures.
- Understanding public and private subnets.
- Configuring route tables and subnet associations.
- Establishing and troubleshooting VPC Peering.
- Implementing least-privilege security group rules.
- Using bastion hosts for private SSH administration.
- Validating network connectivity through ICMP.
- Troubleshooting routing and security-related connectivity failures.

## 📸 Project Evidence

Screenshots and implementation evidence are available in the project report.

**Project Report:** `Aman_Mishra_EWB_VPC_Peering.pdf`

## 👨‍💻 Author

**Aman Mishra**

B.Sc. Information Technology

**Project:** AWS VPC Peering | Connect Two VPCs and Prove Private Connectivity

**Batch:** 1

---

<p align="center">
  <b>BUILD • CONNECT • SECURE • VALIDATE</b>
  <br/>
  <i>Learning Cloud Networking Through Hands-On AWS Implementation.</i>
</p>



## 📸 Project Screenshots

### AWS VPC Peering Configuration
![VPC Peering](screenshots/ss1.png)

### Connectivity Testing
![Connectivity Test](screenshots/ss2.png)

### EC2 Instance Connect
![EC2 Instance Connect](screenshots/ss3.png)
