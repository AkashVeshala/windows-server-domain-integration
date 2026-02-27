# Windows Server Domain Integration Lab

## Project Overview
This lab demonstrates the deployment of an Active Directory Domain environment using two Windows Server 2016 machines in a virtualized infrastructure. The setup simulates a real enterprise network with centralized authentication and domain-based management.

---

## Servers Used
- DC01 – Domain Controller
- SRV01 – Member Server

## Lab Setup

- Windows Server 2016
- VirtualBox (NAT + Internal Network)
- Domain Name: workstam.com
- Domain Controller IP: 192.168.1.10
- Member Server IP: 192.168.1.11
- Preferred DNS on Member Server: 192.168.1.10

 ## Architecture Overview

DC01 (Domain Controller)
- Hosts Active Directory Domain Services
- Hosts DNS Server
- Manages domain authentication

SRV01 (Member Server)
- Joined to workstam.com domain
- Authenticates users via DC01

---

# Domain Controller Configuration

### 1. Static IP Configuration
Configured a static IP address on the Domain Controller to ensure stable DNS and domain services.

![Static IP](1_static_ip.png)

### 2. Installed Active Directory Domain Services
Installed Active Directory Domain Services (AD DS) along with DNS Server role to enable centralized authentication and domain name resolution.

![AD DS Installation](2_ad_ds_install.png)

### 3. Promoted Server to Domain Controller
Promoted the server and created a new forest for the domain.

![Domain Promotion](3_domain_promotion.png)

### 4. Forest Creation
Created a new forest with the domain name `workstam.com`.

![Forest Creation](4_forest_creation.png)

---

# Member Server Configuration

### 5. DNS Configuration
Configured the member server’s DNS settings to point to the Domain Controller IP.

![DNS Settings](5_dns_settings.png)

### 6. Network Connectivity Test
Verified network connectivity and DNS name resolution by successfully pinging workstam.com from the member server, confirming proper communication with the Domain Controller.

![Ping Test](9_ping_test.png)

### 7. Changed from Workgroup to Domain
Switched the system from a local workgroup to the domain environment.

![Workgroup to Domain Join](6_workgroup_to_domain_join.png)

### 8. Domain Join Confirmation
The member server was successfully joined to the workstam.com domain. After restarting the system to complete the process, its presence was verified in Active Directory Users and Computers under the Computers container.

![Domain Join](7_domain_join.png) 

### 9. Domain Login Verification
Logged in using domain credentials to confirm authentication.

![Domain Login](8_domain_login.png)

### 10. User Group Membership
Checked user group membership using the "Member Of" tab in Active Directory.

![User Member Of Tab](10_user_memberof.png)

---

## Skills Demonstrated

- Active Directory Domain Services deployment
- Domain Controller promotion
- DNS configuration in domain environments
- Domain join troubleshooting
- User and group management
- Network connectivity verification

##Final Outcome

- Successfully deployed Active Directory Domain Services
- Created and configured a new domain
- Joined a member server to the domain
- Verified DNS resolution and authentication
- Confirmed proper network communication

This project helped strengthen my understanding of Active Directory, DNS configuration, domain management, and user/group administration in a Windows Server environment.
