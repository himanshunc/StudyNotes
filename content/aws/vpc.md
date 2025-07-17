---
title: "AWS VPC – Explained from Scratch"
date: 2025-07-17
draft: false
description: "From Layman to Expert: Understanding AWS VPC with Concepts, Use Cases & Real-World Examples"
tags: ["aws", "vpc", "networking"]
---

## 🧠 What is a VPC? (Layman’s Understanding)

Imagine AWS as a giant apartment complex. A **VPC (Virtual Private Cloud)** is like your **own private flat**:
- You have rooms (subnets)
- You control the main door (security groups, NACLs)
- You decide how to connect rooms to outside (routing, gateways)
- No one enters unless you allow

---

## 🧱 Core VPC Concepts (With Real-Life Mapping)

| Concept              | What It Does                                          | Real-World Mapping                        |
|----------------------|--------------------------------------------------------|--------------------------------------------|
| CIDR Block           | Defines IP address range (e.g., 10.0.0.0/16)           | Apartment’s address space                 |
| Subnets              | Divide CIDR into smaller ranges (public/private)       | Individual rooms (kitchen, bedroom)       |
| Internet Gateway     | Allows public internet access                          | Your main building’s internet connection  |
| NAT Gateway          | Allows private subnet to access internet               | Landline to call outside, but no incoming |
| Route Tables         | Control traffic path                                   | House's wiring setup                      |
| Security Groups      | Instance-level firewall                                | Door lock at room level                   |
| Network ACLs         | Subnet-level firewall                                  | Security guard at floor level             |

---

## 🧪 Example Setup

- CIDR Block: `10.0.0.0/16`
- Public Subnet: `10.0.1.0/24` (hosts bastion, NAT GW)
- Private Subnet: `10.0.2.0/24` (hosts app, DB)
- IGW attached to public
- NAT GW in public, routes private internet traffic

---

## 🌍 Real-World Use Cases

- **Isolate environments**: Keep dev, test, prod separate (e.g., `vpc-dev`, `vpc-prod`)
- **Secure workloads**: Deploy DB in private subnets without internet access
- **Hybrid Cloud**: Extend VPC to on-premises using VPN or Direct Connect

---

## 🧰 Advanced VPC Features – With Explanation & Use Cases

### 🔁 VPC Peering
- **What**: Connect two VPCs privately
- **Use Case**: Allow secure communication between `dev-vpc` and `prod-vpc`
- **Real Example**: Microservices in different VPCs talk via peering

### 🌐 Transit Gateway
- **What**: Central hub to connect multiple VPCs and on-premises networks
- **Use Case**: Hub-spoke model for 10+ VPCs
- **Real Example**: A large enterprise with 5 business units (each with VPC)

### 🔒 VPC Endpoints
- **What**: Access AWS services (like S3, DynamoDB) without public internet
- **Use Case**: Private subnet app uploads data to S3 securely
- **Example**: Financial app stores customer reports to S3 via endpoint

### 🪵 Flow Logs
- **What**: Capture IP-level traffic logs
- **Use Case**: Debug unreachable services
- **Real Example**: Track failed requests to internal DB

### 🌐 IPv6 Support
- **What**: Enables dual-stack networking (IPv4 + IPv6)
- **Use Case**: Global communication, future-proofing
- **Example**: Web-facing services with both IP versions

### 🔍 Traffic Mirroring
- **What**: Copy live traffic for inspection
- **Use Case**: Troubleshoot production bugs
- **Example**: Mirror traffic to a third-party intrusion detection tool

---

## ✅ Best Practices

| Area          | Practice                                      | Example                                 |
|---------------|-----------------------------------------------|-----------------------------------------|
| Subnet Design | Use multiple AZs for HA                       | `/24` subnets in 2 AZs                  |
| Routing       | Default deny, explicit allow                  | NACLs block all except needed ports     |
| Security      | Use SGs for instance-level, NACLs at subnet   | SG: allow port 22, NACL: block unused   |
| Connectivity  | NAT for outbound, endpoint for AWS services   | Private EC2 → NAT GW + S3 endpoint      |
| Logs          | Enable VPC Flow Logs to CloudWatch/S3         | Store 7-day logs for auditing           |

---

## 🧭 Visual Reference (Text Style)

```
          VPC (10.0.0.0/16)
              │
         ┌────┴────┐
         │         │
  Public Subnet   Private Subnet
     │                 │
 IGW/NAT GW        App, DB EC2
```

---

## 🎯 Summary

- VPC gives full control of networking in AWS
- Split into public/private zones with routing
- Supports peering, endpoints, logs, mirror, etc.
- Used in every production-grade AWS deployment
