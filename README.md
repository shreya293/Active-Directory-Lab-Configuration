# Active-Directory-Lab-Configuration
A comprehensive guide to deploying a Windows Server 2022 Active Directory environment, including Domain Controller setup, DNS configuration, and Client machine integration.

## 🏗️ Phase 1: Hypervisor & Virtual Environment Setup

The foundation of this lab is built on a Type-2 Hypervisor. I chose **VMware Workstation Pro** for its robust virtual networking capabilities, which are essential for simulating a corporate Active Directory environment.

### 1.1 Acquiring VMware Workstation Pro
Since the acquisition of VMware by Broadcom, the software is now hosted on the Broadcom Support Portal. This step involved:
1. Creating a **Broadcom Support Account**.
2. Completing **Trade Compliance and Download Conditions** to authorize the software use.
3. Selecting the latest stable release: **VMware Workstation Pro 17.0 for Windows (Version 17.6.4)**.

---

### 📷 Documentation: The Download Process

<details>
<summary><b>Click to view detailed installation steps & screenshots</b></summary>

#### 1. Portal Registration & Compliance
*Creating a professional account on the Broadcom Support Portal to access enterprise virtualization tools.*

<img src="https://github.com/user-attachments/assets/4f8a4279-a38b-48ee-9d44-34fba3c2cf2b" width="600" height="700" />

#### 2. Software Selection
*Navigating the product catalog to select the industry-standard VMware Workstation Pro 17.0.*

<img src="https://github.com/user-attachments/assets/4178a151-3dd5-4fdd-b482-2219867a6b5d" width="600" height="700"/>

#### 3. Finalizing Download (v17.6.4)
*click on download (make sure you have checked the terms and condition)*

<img width="600" height="700" alt="Screenshot (69)" src="https://github.com/user-attachments/assets/0cf5ec7c-c6d7-4e2b-a330-c617d3ae5880" />
</details>

## 🏗️ Phase 2: Windows Server 2022 Installation

With the hypervisor ready, the next phase is deploying the core of our lab: the **Windows Server 2022** instance. This machine will eventually be promoted to a Domain Controller.

### 2.1 Sourcing the Operating System
I obtained the Windows Server 2022 ISO through the **Microsoft Evaluation Center**. 

<p align="center">
  <img width="600" height="700" alt="Screenshot 2026-03-14 001154" src="https://github.com/user-attachments/assets/69dd3e84-66c0-4455-ab17-87412d668470" />
  <br>
  <i>Figure 1: Selecting the 64-bit ISO download for localized English (United States).</i>
</p>

Choosing the ISO format instead of a VHD (Virtual Hard Disk) allowed for a full manual installation, providing deeper control over the partitioning and initial setup phases.

---
### 🛠️ Step-by-Step Installation Gallery

For a clean portfolio experience, I have summarized the core installation steps below.

<details>
<summary><b>Click to view detailed installation steps & screenshots</b></summary>

#### 1. Virtual Hardware Configuration
I provisioned the VM with **More then 2GB of RAM** and **2 vCPUs**. While Windows Server can run on less, these specs ensure the "Desktop Experience" (GUI) remains responsive during lab tasks.

<img  src="https://github.com/user-attachments/assets/70451f9e-753d-4b4b-b935-382d3e065058" width="600" height="700"/>

#### 2. Selecting the Operating System Version
During the setup boot, I selected **Windows Server 2022 Datacenter Evaluation (Desktop Experience)**. 
> **Why?** The 'Desktop Experience' is vital for this lab as it provides the Graphical User Interface (GUI) required to manage Active Directory through Server Manager.

<img width="600" height="700" src="https://github.com/user-attachments/assets/a418b110-e65e-4adc-ba45-040dc65cf6bd" />

#### 3. Storage Allocation
I allocated a **60GB Virtual Hard Disk**. I used the 'Custom' installation path to ensure the OS was installed cleanly on the unallocated space of Drive 0.

<img width="600" height="700" src="https://github.com/user-attachments/assets/7be32f7b-28c5-4b87-ad8b-75eb6109d4c1" />

#### 4. Post-Installation & Verification
After the files were copied and the system rebooted, I configured the built-in **Administrator account** with a secure password. The installation was verified as successful upon reaching the **Server Manager Dashboard**.

<img width="600" height="700" src="https://github.com/user-attachments/assets/f18d7d06-1588-41e2-8020-a3e4e03aef4e" />

</details>

## 🏗️ Phase 3: Windows 11 Client Deployment

The final piece of our lab infrastructure is the **Windows 11 Client**. This machine will serve as the target workstation that we will eventually join to the `SERVER_2022` domain.

### 3.1 Meeting Windows 11 Requirements
Deploying Windows 11 in a virtual environment requires specific security configurations that differ from older versions of Windows.
* **TPM 2.0:** Enabled via VMware 'Virtual TPM' encryption.
* **RAM:** 4GB (Minimum requirement for stable performance).
* **Storage:** 64GB NVMe Virtual Disk.

---

### 🛠️ Step-by-Step Client Gallery

<details>
<summary><b>Click to view detailed Client setup & screenshots</b></summary>

#### 1. Encrypting for TPM Support
Because Windows 11 requires a Trusted Platform Module (TPM), I configured the VM with 'Partial Encryption.' This allows VMware to emulate the TPM chip required for a successful installation.

<img width="600" height="700" src="https://github.com/user-attachments/assets/8a045fec-f40c-4d21-90a7-961ca492321c" />

#### 2. Hardware Summary
I verified the hardware allocation to ensure the guest OS had sufficient resources to run the modern Windows 11 interface without lag.

<img width="600" height="700" src="https://github.com/user-attachments/assets/848e0016-e019-45d4-aaa2-7335db1c1cb0" />

#### 3. Out-of-Box Experience (OOBE)
Once the installation files were copied, I moved through the OOBE phase, selecting the correct region (United States/India) and keyboard layouts to ensure system localization.

<img width="600" height="700" alt="Screenshot (38)" src="https://github.com/user-attachments/assets/872e7ceb-6999-4f96-88d9-3342b56ba6c9" />

#### 4. Account Integration & Sync
I linked the machine to a Microsoft account. This step is useful for modern lab environments to test how cloud-synced accounts interact with local Active Directory domains later on.

<img width="600" height="700" alt="Screenshot (63)" src="https://github.com/user-attachments/assets/9de5ec9f-9ba7-4530-931c-92d629d9a40f" />

#### 5. Deployment Success
The process concluded with a successful boot to the Windows 11 desktop, confirming the client is ready for network configuration.

<img width="600" height="700" alt="Screenshot (66)" src="https://github.com/user-attachments/assets/994e8086-2f8f-47b5-9e68-97d3b76cd576" />

</details>

---

### 📝 Infrastructure Milestone Reached
At this point, the core lab environment is physically (virtually) built:
1. **Hypervisor:** VMware Workstation Pro 17.6.4 Installed.
2. **Server:** Windows Server 2022 Installed.
3. **Client:** Windows 11 Professional Installed.
---

### 📝 Phase 2 Technical Summary
* **OS Version:** Windows Server 2022 Datacenter (v21H2)
* **Installation Type:** Desktop Experience (GUI)
* **Storage:** 60GB Thin Provisioned Disk
* **Final State:** Functional standalone server ready for Network Configuration.

# 🛠️ Phase 4: PowerShell Environment Installation & Configuration

A detailed, 40-step visual guide to setting up and securing a complete PowerShell environment for administration and automation.

# 🚀 Windows Server & PowerShell Portfolio

## 📂 Phase 4 Breakdown
* [View Sub-Phase 1: Server Setup](#sub-phase-1-server-setup)
* [View Sub-Phase 2: Next Steps](#)

---

## 🛠️ Sub-Phase 1: Server Setup
<a name="sub-phase-1-server-setup"></a>

| Step | Action | Technical Description | Screenshot Reference |
| :--- | :--- | :--- | :--- |
| **01** | **Start Server** | Initialize Server Manager and navigate to the Manage menu. | ![Step 1](./images/image%201.png) |
| **02** | **Role Selection** | Selecting Role-based installation for AD DS deployment. | ![Step 2](./images/image%202.png) |
| **03** | **AD DS Setup** | Provisioning Active Directory Domain Services. | ![Step 3](./images/image%203.png) |
| **04** | **Features** | Selecting Migration Tools and LAN services. | ![Step 4](./images/image%204.png) |
| **05** | **Dashboard** | Final verification of the Server Manager Dashboard. | ![Step 5](./images/image%205.png) |

### Module 4.4: Sub-Phase 4 (Final Verification)
Post-installation testing, version checks, and connectivity validation.
> **[View Sub-Phase 4 Documentation](./04.4_SubPhase4.md)**
