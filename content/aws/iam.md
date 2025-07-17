---
title: "IAM"
date: 2025-07-17
description: "AWS IAM Explained from Scratch with Concepts, Use Cases & Real Examples"
tags: ["aws", "iam"]
categories: ["AWS"]
weight: 9
---

# 🧠 Layman’s Analogy

Imagine your AWS account is a secure office building. IAM is the receptionist and security system: who can enter, what doors they can access, and what actions they can perform inside.

---

# 📘 Conceptual Explanation (Basic → Advanced)

### 🔐 What is IAM?

IAM (Identity and Access Management) controls **who** can do **what** in your AWS account.

### Core Concepts:
- **Users**: Individual identities with credentials
- **Groups**: Collection of users with shared permissions
- **Roles**: Temporary access for apps/services
- **Policies**: JSON-based permission documents
- **MFA**: Adds two-factor authentication

### Advanced:
- **Permissions Boundaries**: Control maximum allowed permissions
- **Cross-Account Roles**: Grant access between AWS accounts
- **Service Control Policies (SCP)**: Org-wide permission control
- **IAM Access Analyzer**: Identify risky permissions

---

# 🌍 Real-World Use Cases

- Allow developers read-only access to CloudWatch
- Enable EC2 instance to fetch S3 content via IAM Role
- Grant cross-account access for auditing
- Provide consultants temporary CLI access

---

# ✅ Best Practices

- Never use root account for daily tasks
- Enforce MFA for all users
- Rotate credentials regularly
- Use IAM roles for applications/services
- Apply least privilege principle in all policies

---

# 🛠️ Practical Example

**Create a Role for EC2 to Access S3**

1. Go to IAM > Roles > Create Role
2. Choose EC2 as trusted service
3. Attach `AmazonS3ReadOnlyAccess` policy
4. Launch EC2 and assign the role
5. EC2 now accesses S3 without access keys

---

# 🔀 Visual Flow

```
IAM
 ├── Users → For human access (CLI/Console)
 ├── Groups → Common policies for teams
 ├── Roles → Access for EC2, Lambda, etc.
 └── Policies → JSON docs defining permissions
```
