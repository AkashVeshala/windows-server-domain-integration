# 🖥️ Windows Server Domain Integration Lab

![Windows Server](https://img.shields.io/badge/Windows%20Server-2016-blue?style=for-the-badge&logo=windows)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Domain%20Services-0078D4?style=for-the-badge)
![VirtualBox](https://img.shields.io/badge/VirtualBox-Virtualization-183A61?style=for-the-badge&logo=virtualbox)

---

## 📌 What is this project?

This lab simulates a real enterprise network environment using two Windows Server 2016 machines. I set up a fully functional Active Directory domain from scratch — configuring a Domain Controller, joining a Member Server to the domain, and verifying end-to-end authentication.

The goal was to understand how centralized authentication and domain-based management works in an actual enterprise setup — not just in theory.

---

## 🖧 Lab Environment

| Component         | Details                        |
|-------------------|--------------------------------|
| OS                | Windows Server 2016            |
| Virtualization    | VirtualBox (NAT + Internal Network) |
| Domain Name       | workstam.com                   |
| Domain Controller | DC01 — IP: 192.168.1.10        |
| Member Server     | SRV01 — IP: 192.168.1.11       |
| DNS Server        | 192.168.1.10 (DC01)            |

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────┐
│         DC01 – Domain Controller    │
│         IP: 192.168.1.10            │
│                                     │
│  • Active Directory Domain Services │
│  • DNS Server                       │
│  • Domain Authentication            │
└──────────────────┬──────────────────┘
                   │ Domain: workstam.com
                   │ Authentication
                   ▼
┌─────────────────────────────────────┐
│         SRV01 – Member Server       │
│         IP: 192.168.1.11            │
│                                     │
│  • Joined to workstam.com           │
│  • Authenticates via DC01           │
│  • DNS points to 192.168.1.10       │
└─────────────────────────────────────┘
```

---

## ⚙️ What I Actually Did

### 1️⃣ Static IP Configuration on Domain Controller
Set a static IP on DC01 so the DNS and domain services stay stable and reachable by all machines in the network.

![Static IP](1_static_ip.png)

---

### 2️⃣ Installed Active Directory Domain Services
Installed the AD DS role along with the DNS Server role on DC01 — this is what enables centralized user authentication and domain name resolution across the network.

![AD DS Installation](2_ad_ds_install.png)

---

### 3️⃣ Promoted Server to Domain Controller
After installing AD DS, I promoted DC01 to a Domain Controller and created a brand new forest for the domain.

![Domain Promotion](3_domain_promotion.png)

---

### 4️⃣ Created the Domain Forest
Set up a new forest with the domain name `workstam.com` — this became the root of the entire domain environment.

![Forest Creation](4_forest_creation.png)

---

### 5️⃣ DNS Configuration on Member Server
Pointed SRV01's DNS to DC01's IP (192.168.1.10) so it could resolve the domain name and communicate with the Domain Controller.

![DNS Settings](5_dns_settings.png)

---

### 6️⃣ Network Connectivity Test
Verified that SRV01 could reach DC01 by pinging `workstam.com` — confirmed DNS resolution was working correctly before attempting to join the domain.

![Ping Test](9_ping_test.png)

---

### 7️⃣ Joined Member Server to the Domain
Switched SRV01 from a local workgroup to the `workstam.com` domain. This is where the actual domain join happens.

![Workgroup to Domain Join](6_workgroup_to_domain_join.png)

---

### 8️⃣ Verified Domain Join in Active Directory
After restarting SRV01, I confirmed it appeared under the Computers container in Active Directory Users and Computers on DC01 — proof that the join was successful.

![Domain Join](7_domain_join.png)

---

### 9️⃣ Domain Login Verification
Logged into SRV01 using domain credentials to confirm that authentication through DC01 was working end-to-end.

![Domain Login](8_domain_login.png)

---

### 🔟 User Group Membership Check
Checked user group membership using the "Member Of" tab in Active Directory to verify proper group assignment.

![User Member Of Tab](10_user_memberof.png)

---

## 🚧 Challenges Faced

- Configuring the static IP and DNS correctly before promoting the server — getting this wrong causes the domain promotion to fail
- Making sure SRV01's DNS pointed to DC01 before attempting the domain join — a common mistake that blocks the whole process
- Understanding the difference between a Workgroup and a Domain environment and how authentication changes between the two

---

## ✅ What I Learned

- How Active Directory Domain Services works in a real network
- Why DNS is critical in a domain environment — without it, nothing works
- How domain join works under the hood and what happens after a machine joins
- How centralized authentication replaces local logins in enterprise environments
- Troubleshooting connectivity and DNS issues before domain operations

---

## 🎯 Final Outcome

- ✔ Deployed Active Directory Domain Services from scratch
- ✔ Created and configured a new domain — workstam.com
- ✔ Successfully joined a member server to the domain
- ✔ Verified DNS resolution and network connectivity
- ✔ Confirmed end-to-end domain authentication with domain credentials

---

## 👤 About Me

**Veshala Akash** — aspiring IAM & Systems engineer passionate about identity, access management, and enterprise infrastructure.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/veshala-akash-b47734362)

---

> 💡 *This lab is part of my hands-on learning journey in Windows Server administration and Active Directory. I believe building things from scratch is the best way to truly understand how enterprise environments work.*
