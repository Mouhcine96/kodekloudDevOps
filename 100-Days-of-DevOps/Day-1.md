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


