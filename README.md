 <div align="center">

<img src="https://upload.wikimedia.org/wikipedia/commons/9/93/Amazon_Web_Services_Logo.svg" width="190" alt="Amazon Web Services Logo"/>

# AWS VPC Peering Project

### Secure Private Communication Between Two Amazon VPCs

[![AWS](https://img.shields.io/badge/Cloud-AWS-orange?logo=amazonaws)](https://aws.amazon.com/)
[![Service](https://img.shields.io/badge/Service-VPC%20Peering-purple)](https://docs.aws.amazon.com/vpc/latest/peering/what-is-vpc-peering.html)
[![Region](https://img.shields.io/badge/Region-ap--southeast--2-blue)](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/)

</div>

---

## 📌 Project Overview

A hands-on AWS networking project demonstrating secure communication between two isolated Virtual Private Clouds (VPCs) using **VPC Peering**.

The project establishes private connectivity between EC2 instances through route tables, security groups, and a bastion host, while validating bidirectional network communication.

## 🏗️ Architecture

| Component | Configuration |
|---|---|
| VPC A | `10.10.0.0/16` |
| VPC B | `10.20.0.0/16` |
| Public Subnet | `10.10.1.0/24` |
| Private Subnet A | `10.10.2.0/24` |
| Private Subnet B | `10.20.1.0/24` |
| Region | Sydney (`ap-southeast-2`) |
| Connectivity | VPC Peering |

### Infrastructure Components

- **VPC A:** Public and private subnet architecture.
- **VPC B:** Private-only network architecture.
- **Bastion Host:** Secure SSH access to private instances.
- **VPC Peering:** Private communication between the two VPCs.
- **Route Tables:** Bidirectional traffic routing.
- **Security Groups:** Controlled SSH and ICMP traffic.

## 🔄 Connectivity Validation

The following tests were performed:

- Forward Ping: App-A → App-B
- Reverse Ping: App-B → App-A
- SSH connectivity to private EC2 instances.
- Controlled ICMP failure testing.
- Connectivity restoration after security group rule recovery.

## 📸 Project Screenshots

### 1. VPC Peering Configuration

![VPC Peering Configuration](screenshots/ss1.png)

### 2. Connectivity Testing

![Connectivity Testing](screenshots/ss2.png)

### 3. EC2 Instance Connect

![EC2 Instance Connect](screenshots/ss3.png)

## 📄 Detailed Project Report

The complete project documentation includes architecture, AWS configurations, route tables, security groups, SSH validation, connectivity testing, and implementation evidence.

<div align="center">

### 📘 AWS VPC Peering Report

**[📖 View Full Project Report (PDF)](Aman_Mishra_EWB_VPC_Peering.pdf)**

*Click to open the report in GitHub's PDF preview.*

</div>

---

## 🛠️ Technologies Used

- Amazon Web Services (AWS)
- Amazon VPC
- VPC Peering
- Amazon EC2
- Security Groups
- Route Tables
- Linux
- SSH

## 🎯 Key Learnings

- Understanding VPC isolation and network architecture.
- Configuring VPC Peering connections.
- Implementing bidirectional routing.
- Managing private EC2 connectivity.
- Applying network-level security controls.
- Troubleshooting connectivity using ICMP and SSH.

## 👨‍💻 Author

**Aman Mishra**  
B.Sc. Information Technology

---

<div align="center">

**Built with ☁️ Amazon Web Services**

</div>
