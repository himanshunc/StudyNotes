---
title: "IAM"
date: 2025-07-17
description: "Understanding AWS IAM with Concepts, Use Cases & Real-World Examples"
tags: ["aws", "iam"]
categories: ["AWS"]
---

# 🔐 What is IAM? (Layman’s Understanding)

Imagine your AWS account is a **house**. IAM is the lock and key system:

- You control who can enter (users, roles)
- What they can access (policies)
- And what actions they can perform (read/write/etc.)

💡 Example: You want to allow a developer to manage EC2 but not S3? IAM makes it easy.

---

## IAM Core Concepts

- **Users**: Named human identities
- **Groups**: Collection of users with common policies
- **Roles**: For apps, EC2s, Lambda to assume permissions
- **Policies**: JSON rules for permission control
- **MFA**: Adds extra layer of login protection

---

## IAM Use Cases

- Secure multi-user environments
- Provide temporary access to consultants
- EC2 accessing S3 using a role
- Cross-account access

---

## IAM Best Practices

- Don’t use root user for daily tasks
- Enforce strong password/MFA policies
- Use roles instead of long-term access keys
- Apply least privilege to all policies
