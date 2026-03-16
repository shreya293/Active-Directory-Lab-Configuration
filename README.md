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

#### 1. Portal Registration & Compliance
*Creating a professional account on the Broadcom Support Portal to access enterprise virtualization tools.*

<img src="https://github.com/user-attachments/assets/4f8a4279-a38b-48ee-9d44-34fba3c2cf2b" width="600" height="700" />

#### 2. Software Selection
*Navigating the product catalog to select the industry-standard VMware Workstation Pro 17.0.*

<img src="https://github.com/user-attachments/assets/4178a151-3dd5-4fdd-b482-2219867a6b5d" width="600" height="700"/>

#### 3. Finalizing Download (v17.6.4)
*click on download (make sure you have checked the terms and condition)*

<img width="600" height="700" alt="Screenshot (69)" src="https://github.com/user-attachments/assets/0cf5ec7c-c6d7-4e2b-a330-c617d3ae5880" />


## 🏗️ Phase 2: Windows Server 2022 Installation

With the hypervisor ready, the next phase is deploying the core of our lab: the **Windows Server 2022** instance. This machine will eventually be promoted to a Domain Controller.

### 2.1 Sourcing the Operating System
I obtained the Windows Server 2022 ISO through the **Microsoft Evaluation Center**. I specifically chose the **64-bit Edition** to ensure compatibility with modern hardware virtualization features.

---
### 🛠️ Step-by-Step Installation Gallery

For a clean portfolio experience, I have summarized the core installation steps below.

<details>
<summary><b>Click to view detailed installation steps & screenshots</b></summary>

#### 1. Virtual Hardware Configuration
I provisioned the VM with **2GB of RAM** and **2 vCPUs**. While Windows Server can run on less, these specs ensure the "Desktop Experience" (GUI) remains responsive during lab tasks.

<img src="<img  src="https://github.com/user-attachments/assets/70451f9e-753d-4b4b-b935-382d3e065058" width="600" height="700"/>

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

---
### 📝 Phase 2 Technical Summary
* **OS Version:** Windows Server 2022 Datacenter (v21H2)
* **Installation Type:** Desktop Experience (GUI)
* **Storage:** 60GB Thin Provisioned Disk
* **Final State:** Functional standalone server ready for Network Configuration.
