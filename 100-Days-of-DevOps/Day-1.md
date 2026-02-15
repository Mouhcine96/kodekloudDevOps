# 100 Days of DevOps – Day 1  
## Linux User Setup with Non-Interactive Shell

---

## 🎯 Objective

Create a system user named `javed` with a non-interactive shell on **App Server 2 (stapp02)**.

The purpose of this user is to support automation tools (e.g., backup agents) without allowing interactive login access.

---

## 🏗 Infrastructure Context

| Server | Hostname | IP Address | Role |
|--------|----------|------------|------|
| stapp02 | stapp02.stratos.xfusioncorp.com | 172.16.238.11 | Nautilus Application Server 2 |

---

## 🔐 Why Non-Interactive Shell?

A non-interactive shell prevents:

- SSH login
- Direct shell access
- Manual command execution

This is considered a **security best practice** for service accounts.

Service accounts should:
- Run background services
- Not allow human login access

---

## 🛠 Implementation Steps

### 1️⃣ Connect to App Server 2

# ```bash
ssh steve@172.16.238.11

---

# 2️⃣ Switch to Root
sudo -i

---

# 3️⃣ Create User with Non-Interactive Shell
useradd -s /sbin/nologin javed

---

# If /sbin/nologin is not available:
cat /etc/shells

---

# Then use the available path, for example:
useradd -s /usr/sbin/nologin javed

---

#🔍 Verification Check /etc/passwd:
grep javed /etc/passwd

---

# Expected output:
javed:x:100x:100x::/home/javed:/sbin/nologin

---

# Attempt login test:
su - javed

---

# Expected result:
This account is currently not available.

---

# 📚 What I Learned Today

Difference between interactive and non-interactive shells

How Linux stores user configuration in /etc/passwd

Why service accounts should not allow login access

How to define a custom shell during user creation

How to verify correct shell configuration

Security fundamentals for automation accounts

---

# **🔐 Security Takeaways**
-Never create service users with /bin/bash

-Apply the Principle of Least Privilege

-Always verify shell configuration after user creation

-Service users should only exist for automation purposes

---

# 🚀 DevOps Perspective

In real production environments, non-interactive users are used for:

-Backup agents

-Monitoring agents

-CI/CD runners

-Database services

This is foundational Linux security knowledge required for DevOps and infrastructure roles.
