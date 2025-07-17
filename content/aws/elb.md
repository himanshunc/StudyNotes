---
title: "Elastic Load Balancer (ELB)"
date: 2025-07-17
description: "AWS ELB Explained with Concepts, Use Cases & Examples"
tags: ["aws", "elb"]
categories: ["AWS"]
---

# 🧠 Layman’s Analogy

Imagine a receptionist at a busy hospital. Patients arrive (user requests), and the receptionist decides which doctor (server) will treat them. The receptionist ensures no one doctor is overwhelmed.

---

# 📘 Conceptual Explanation (Basic → Advanced)

### What is an ELB?

Elastic Load Balancer automatically distributes incoming traffic across multiple targets (EC2, containers).

### Types of ELB:
- **Application Load Balancer (ALB)**: Layer 7 (HTTP/S)
- **Network Load Balancer (NLB)**: Layer 4 (TCP)
- **Gateway Load Balancer (GWLB)**: Security appliances

### Advanced:
- Host-based & path-based routing (ALB)
- IP-based targets and private links (NLB)
- SSL termination
- Sticky sessions
- Health checks

---

# 🌍 Real-World Use Cases

- Web applications needing high availability
- Microservices routing with ALB
- Internal apps load-balanced via NLB
- Security VMs with GWLB

---

# ✅ Best Practices

- Use health checks for availability
- Choose ALB for HTTP/HTTPS apps
- Use HTTPS listeners with SSL
- Enable access logs for debugging
- Place behind Route 53 for DNS-level control

---

# 🛠️ Practical Example

**Host-Based Routing with ALB**

1. Create ALB  
2. Define two target groups: `app1`, `app2`  
3. Set listener rules:  
   - `/app1/*` → target group 1  
   - `/app2/*` → target group 2

---

# 🔀 Visual Flow

```
User Request → Load Balancer → Healthy Target (EC2/Container)
```
