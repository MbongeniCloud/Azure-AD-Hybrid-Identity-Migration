#  Enterprise Hybrid Identity Migration & Security Implementation (Azure)

 Security-Focused |  Cloud Architecture |  Real-World Scenario

---

## Project Overview

Designed and implemented an enterprise-grade hybrid identity solution by migrating an on-premises Windows Server Active Directory environment to Microsoft Entra ID (Azure AD). This project simulates a real-world corporate identity migration using industry-standard tools and security best practices.

---

## Business Value

| Outcome | Impact |
|---|---|
| Reduced on-prem infrastructure dependency | Lower hardware & maintenance costs |
| Enabled secure remote authentication | Supports hybrid & remote workforce |
| Self-Service Password Reset (SSPR) | Reduces IT helpdesk tickets by ~20% |
| Centralised identity management | Single pane of glass for user access |
| Password Hash Synchronisation | Seamless SSO without ADFS complexity |

---

## Architecture

This solution uses a hybrid identity model integrating on-premises Active Directory with Microsoft Entra ID (Azure AD).

```
┌─────────────────────────────────┐
│     On-Premises Environment     │
│                                 │
│  ┌──────────────────────────┐   │
│  │  Windows Server 2025 VM  │   │
│  │  (Hosted on Azure IaaS)  │   │
│  │                          │   │
│  │  Active Directory DS     │   │
│  │  Domain: corp.local      │   │
│  │  Users: Admin, Jane,     │   │
│  │         Jacob, Mbongeni  │   │
│  └────────────┬─────────────┘   │
└───────────────┼─────────────────┘
                │
                ▼
┌──────────────────────────────────┐
│   Microsoft Entra Connect Sync   │
│   • Password Hash Sync (PHS)     │
│   • Identity synchronisation     │
│   • Attribute filtering          │
└──────────────┬───────────────────┘
               │
               ▼
┌──────────────────────────────────┐
│    Microsoft Entra ID (Azure AD) │
│                                  │
│  ┌─────────────┐  ┌───────────┐  │
│  │    Users &  │  │   SSPR    │  │
│  │   Groups    │  │  (Reset)  │  │
│  └─────────────┘  └───────────┘  │
│  ┌─────────────┐  ┌───────────┐  │
│  │     MFA     │  │  Entra    │  │
│  │   (Admin)   │  │  Connect  │  │
│  └─────────────┘  └───────────┘  │
└──────────────────────────────────┘
```

---

## Technologies Used

| Technology | Purpose |
|---|---|
| Microsoft Azure (IaaS) | Cloud infrastructure hosting |
| Windows Server 2025 | On-premises AD environment |
| Active Directory Domain Services (AD DS) | On-prem identity provider |
| Microsoft Entra Connect Sync | Identity synchronisation engine |
| Password Hash Synchronisation (PHS) | Secure credential sync |
| Self-Service Password Reset (SSPR) | End-user password management |
| Microsoft Entra ID (Azure AD) | Cloud identity platform |

---

## What I Built

1. Deployed Windows Server 2025 VM on Azure (IaaS)
2. Promoted server to Domain Controller — configured `corp.local` forest
3. Created domain users and groups (Admin, Jane, Jacob, Mbongeni)
4. Installed and configured Microsoft Entra Connect Sync
5. Enabled Password Hash Synchronisation (PHS) for seamless cloud auth
6. Configured Self-Service Password Reset (SSPR) for all users
7. Verified successful user sync to Microsoft Entra ID
8. Enabled MFA for privileged admin account

---

## Security Implementation

| Control | Status | Details |
|---|---|---|
| MFA for Admin Accounts |  Enabled | Protects privileged access |
| Password Hash Sync (PHS) |  Enabled | Avoids plaintext credential exposure |
| Self-Service Password Reset |  Configured | Reduces attack surface of helpdesk |
| Least Privilege Access |  Applied | Role-based admin separation |
| Identity Secure Score |  100% | Verified in Entra admin center |

---

## Challenges Overcome

| Challenge | Resolution |
|---|---|
| Azure subscription quota limits | Requested quota increase via Azure Portal |
| VM availability zone restrictions | Adjusted deployment region |
| OAuth browser security configuration | Manually configured trusted zones for Entra Connect |
| MFA setup for admin account | Enrolled via Microsoft Authenticator app |
| Active Directory replication timing | Used `repadmin` to force sync and verify |

---

## Screenshots

### 1. Azure VM — Domain Controller Deployed
> Windows Server 2025 VM provisioned on Azure IaaS, configured as the on-premises Active Directory Domain Controller (`corp.local`).

*(See `/screenshots/01-azure-vm-deployed.png`)*

---

### 2. Microsoft Entra ID — Admin Center Overview
> Tenant dashboard showing Identity Secure Score at **100%**, Entra Connect enabled, and 4 users synced from on-premises AD.

*(See `/screenshots/02-entra-admin-center.png`)*

---

### 3. Users Successfully Synchronised
> 4 domain users (Admin, Jane, Jacob, Mbongeni) successfully synchronised from on-premises Active Directory to Microsoft Entra ID via Entra Connect Sync.

*(See `/screenshots/03-users-synced.png`)*

---

### 4. Self-Service Password Reset Configured
> SSPR enabled in the Entra admin center, allowing users to reset passwords from any device without contacting IT support.

*(See `/screenshots/04-sspr-configured.png`)*

---

## Screenshots
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/8ff8c9b9-34a2-4e6d-b55d-a8d9810e04f5" />

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/1cd7def5-fa2f-41ab-8ec1-7c8c5cf63a74" />

<img width="1366" height="754" alt="image" src="https://github.com/user-attachments/assets/29ded00c-d0ed-4abe-ace8-f169e63bc060" />

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/3f502f1e-ab0e-410b-acd8-9991241b7832" />


## Future Improvements

> These represent the next phase of maturity for this architecture:

- [ ] **Conditional Access Policies** — enforce access controls based on user risk, location, and device compliance
- [ ] **Azure AD Identity Protection** — automated risk-based sign-in detection
- [ ] **Privileged Identity Management (PIM)** — just-in-time privileged access for admins
- [ ] **Zero Trust Architecture** — never trust, always verify across all resources
- [ ] **Azure Monitor & Sentinel** — centralised logging, alerting, and SIEM integration
- [ ] **Azure Files integration** — secure cloud file share for hybrid users
- [ ] **Seamless SSO** — extend to SaaS apps via Enterprise Applications

---

## Skills Demonstrated

-  Cloud Infrastructure Provisioning (Azure IaaS)
-  Identity & Access Management (IAM)
-  Hybrid Cloud Architecture Design
-  Enterprise Security Configuration
-  Directory Synchronisation & Replication
-  Active Directory Administration

---

## Author

**Mbongeni** | [GitHub: MbongeniCloud](https://github.com/MbongeniCloud)

> *This lab simulates enterprise-grade hybrid identity migration as practised in real corporate environments.*
