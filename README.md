# Active-Directory-Lab-Configuration
A comprehensive guide to deploying a Windows Server 2022 Active Directory environment, including Domain Controller setup, DNS configuration, and Client machine integration.

# Active Directory Lab Configuration

## 🏗️ Phase 1: Hypervisor & Virtual Environment Setup

The foundation of this lab is built on a Type-2 Hypervisor. I chose **VMware Workstation Pro** for its robust virtual networking capabilities, which are essential for simulating a corporate Active Directory environment.

### 1.1 Acquiring VMware Workstation Pro
Since the acquisition of VMware by Broadcom, the software is now hosted on the Broadcom Support Portal. This step involved:
1. Creating a **Broadcom Support Account**.
2. Completing **Trade Compliance and Download Conditions** to authorize the software use.
3. Selecting the latest stable release: **VMware Workstation Pro 17.0 for Windows (Version 17.6.4)**.

---

### 📷 Documentation: The Download Process

#### 1. Portal Registration & Compliance
![broadcom 1](https://github.com/user-attachments/assets/4f8a4279-a38b-48ee-9d44-34fba3c2cf2b)

*Creating a professional account on the Broadcom Support Portal to access enterprise virtualization tools.*

#### 2. Software Selection

*Navigating the product catalog to select the industry-standard VMware Workstation Pro 17.0.*
![broadcom 2](https://github.com/user-attachments/assets/4178a151-3dd5-4fdd-b482-2219867a6b5d)

#### 3. Finalizing Download (v17.6.4)
<img width="1366" height="768" alt="Screenshot (73)" src="https://github.com/user-attachments/assets/e472fa51-c4a4-4a60-89bd-cecc87075c6f" />

*Verifying the build version (17.6.4) and completing the download of the executable.*
