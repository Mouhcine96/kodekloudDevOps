# Task 1 – Dedicated Apache Application User Creation  
## Project Nautilus – xFusionCorp Industries

---

## 1. Context

Project Nautilus is a three-tier LAMP-based application deployed in the Stratos Datacenter (North America Region).

Application Tier:
- Linux
- Apache HTTP Server
- MariaDB
- PHP

To enhance security, xFusionCorp follows a principle of **dedicated system users per web application**.  
This limits privilege escalation and lateral movement in case of compromise.

This task applies to:

- Server: stapp02.stratos.xfusioncorp.com
- IP: 172.16.238.11
- Tier: Application Server 2
- Environment: Production-like lab environment

---

## 2. Objective

Create a custom Apache application user with the following specifications:

- Username: kareem
- UID: 1126
- Home Directory: /var/www/kareem

Security goal:
Isolate application execution context using a dedicated Linux user.

---

## 3. Implementation Steps

### 3.1 Connect to Application Server 2 (via Jump Host)

#```bash
ssh steve@stapp02.stratos.xfusioncorp.com

---

# Elevate privileges:
sudo -i

---

## 3.2 Verify UID Availability
Before assigning a static UID, ensure it is not already in use:
# getennt passwd 1126
No output indivated the UID is available.

---

## 3.3 Create Dedicated Applivation User
useradd -u 1126 -d /var/www/kareem -m kareem
# Explanation:
- -u 1126 -> Assign specific UID
- -d /var/www/kareem -> Set custom home directory
- -m -> Create home directory automatically

---

## 3.4 Secure Directory Ownership and Permissions
chown -R kareem:kareem /var/www/kareem
chmod 750 /var/www/kareem
# Permission model:
- Owner → full access (rwx)
- Group → read & execute
- thers → no access

---

## 4. Validation
# Confirm user creation:
id kareem
# Expected output:
uid=1126(kareem) gid=1126(kareem) groups=1126(kareem)
# Verify directory:
ls -ld /var/www/kareem
# Expected:
drwxr-x---  kareem kareem  /var/www/kareem

---

## 5. Security Considerations
- Dedicated user reduces blast radius in case of web exploitation.
- No shared application execution context.
- Controlled directory permissions prevent unauthorized access.
- Static UID ensures predictable identity management in multi-node environments.
In clustered environments (stapp01–03), UID consistency is important for shared storage compatibility (e.g., NAS filer).

---

## 6. Production Considerations
In a real production deployment, additional hardening may include:
- Assigning non-interactive shell (/sbin/nologin)
- Managing group-based access if Apache runs under a different service account
- SELinux context adjustments (if enforcing mode enabled)
- Integration with central identity management (LDAP / FreeIPA)

---

## 7. Result
The custom Apache user kareem has been successfully created on Application Server 2 with:
- UID 1126
- Dedicated application directory
- Restriced access permissions
# The implementation aligns with Nautilus application tier security design principles.
