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

## 📂 Phase 4 Breakdown

* 🖥️ **[View Phase 4.1: Server Role Configuration](#phase-4-1-server-role-configuration)** — *Focuses on AD DS and Feature provisioning.*
* 🌳 **[View Phase 4.2: Domain Controller Promotion](#phase-4-2-domain-controller-promotion)** — *Establishing the singh.com forest root.*
* 🌐 **[View Phase 4.3: Network Infrastructure & Domain Verification](#phase-4-3-network-infrastructure-verification)** — *LAB1 segmentation, DHCP Scope, and Client Connectivity test.*
---
<a name="phase-4-1-server-role-configuration"></a>
## 🚀 Phase 4.1: Server Role Configuration

This module documents the initial deployment of **Active Directory Domain Services (AD DS)** and essential server features.

<details>
<summary><b>▶ Click to view detailed installation steps & screenshots</b></summary>
<br>

#### 1. Initialize Server Manager
Launching the Dashboard and selecting **Add Roles and Features** to begin infrastructure setup.
![Step 1](./Images/image%201.png)

---

#### 2. Role-Based Installation Type
Selecting **Role-based or feature-based installation**. This ensures the local server instance is provisioned with specific service capabilities for our domain environment.
![Step 2](./Images/image%202.png)

For Server selection click on Next
![Step 3](./Images/image%203.png)

---

#### 3. Active Directory Domain Services (AD DS) Setup
Provisioning the **AD DS** role. *Note:* I have deliberately deselected unnecessary roles like Web Server (IIS) to harden the server and reduce the attack surface.
![Step 3](./Images/image%204.png)

---

#### 4. Feature Selection & Migration Tools
Selecting **Windows Server Migration Tools** and **Wireless LAN services**. These utilities are essential for managing infrastructure mobility and future data transfers.
![Step 4](./Images/image%205.png)

---

#### 5. Dashboard Configuration Overview
Final verification of the Server Manager Dashboard. The interface now reflects the pending installation and integration of the selected core server roles.

Note: restart the system once to ensure your roles and features are added correctly.
![Step 5](./Images/image%2015.png)

</details>

This sub-module documents the initial configuration of the Windows Server environment, specifically focusing on the deployment of Active Directory Domain Services (AD DS).

<a name="phase-4-2-domain-controller-promotion"></a>
## 🌳 Phase 4.2: Domain Controller Promotion (singh.com)

After role installation, the server must be promoted to a Domain Controller to establish the forest root. This module documents the configuration of the **singh.com** identity infrastructure.

<details>
<summary><b>▶ Click to view Domain Promotion steps & screenshots</b></summary>

<br>

#### 1. Post-Deployment Configuration Request
Following the AD DS role installation, a notification in Server Manager indicates that additional configuration is required to "Promote this server to a domain controller."
![Step 6](./Images/image%206.png)

---

#### 2. Deployment Configuration: New Forest Creation
We select **"Add a new forest"** and define the Root Domain Name as `singh.com`. This initializes the top-level container for all future network objects.
![Step 7](./Images/image%207.png)

---

#### 3. Domain Controller Options & DSRM
Configuring the functional levels (Windows Server 2016) and setting the **Directory Services Restore Mode (DSRM)** password. This is a vital security credential for Active Directory recovery.
![Step 8](./Images/image%208.png)

---

#### 4. DNS Options & Delegation
The wizard prepares the DNS integration. A warning about delegation is standard here as we are creating the authoritative root zone for our private lab.
![Step 9](./Images/image%209.png)

---

#### 5. NetBIOS Name Assignment
The system verifies and assigns the NetBIOS name `SINGH`. This ensures legacy compatibility for naming services across the network.
![Step 10](./Images/image%2010.png)

---

#### 6. Prerequisites Validation
The 'Prerequisites Check' confirms the server meets all technical requirements for promotion. Once passed, we proceed with the actual promotion.
![Step 11](./Images/image%2011.png)

---

#### 7. Promotion Progress & Automation
PowerShell scripts execute in the background to configure the database (NTDS), logs, and SYSVOL folders required for AD operations.
![Step 12](./Images/image%2012.png)

---

#### 8. Successful Promotion & Final Result
The wizard confirms the server was successfully configured as a Domain Controller. The system then automatically reboots to apply the security changes.
![Step 13](./Images/image%2013.png)

---

#### 9. System Reboot into the Domain
The Windows Server initializes with its new identity. Upon logging in, the administrative account will now be part of the `SINGH` domain.
![Step 14](./Images/image%2014.png)

---

</details>

<a name="phase-4-3-network-segmentation"></a>
## 🌐 Phase 4.3: DHCP Scope & Network Segmentation (LAB1)

This module documents the isolation of the lab environment using a **LAN Segment (LAB1)** and the configuration of the **DHCP Server Role** to automatically provision IP addresses.

<details>
<summary><b>▶ Click to view Networking steps & screenshots</b></summary>

<br>

#### 1. Isolated LAN Segment Allocation (LAB1)
Both the Windows Server and the Windows Client must be assigned to the same isolated **LAN Segment (`LAB1`)**. This creates a private network that prevents lab traffic from conflicting with the host system's actual physical network.
![Step 25](./Images/image%2025.png)

---

#### 2. Configure Static IP on Domain Controller (IPAM)
A Domain Controller **must** have a static IP. We configure the server's network adapter with a fixed address to ensure reliable Identity Management and DNS services.
* **IPv4:** `192.168.10.1` (Lab Gateway)
* **DNS:** `127.0.0.1` (Self-reference)
![Step 33](./Images/image%2033.png)

---

#### 3. Initializing DHCP Scope Creation
Navigating to the **DHCP Manager** from Server Manager Tools. We begin the process of defining an **IPv4 Scope** to allow the client to automatically receive network configurations.
![Step 34](./Images/image%2034.png)

---

#### 4. Scope Name & IP Address Pool (grouped)
**Step 35 & 36:** We define the scope name as **`LAB1`** and establish the range of IP addresses that can be assigned to devices on this segmented network.
CLick on New scope and then Click on Next
* **Pool Range:** `192.168.10.100` – `192.168.10.200`
* **Subnet Mask:** `255.255.255.0`
![Step 35](./Images/image%2035.png)
![Step 36](./Images/image%2036.png)

---

#### 5. Confirming Scope Activation (grouped)
**Step 37 & 38:** We define the **Router (Default Gateway)** as `192.168.10.1` and activate the scope. The green checkmark in DHCP Manager confirms that the lab network is now active and ready.
In the Scope Name we enter random name and description
![Step 37](./Images/image%2037.png)
![Step 38](./Images/image%2038.png)

---

#### 6. Confirming Client IP Acquisition
The Windows Client Machine, assign to **LAB1** which automatically receives an IP address (e.g., `192.168.10.100`) from our DHCP server. We verify this using **`ipconfig /all`**.
![Step 40](./Images/image%2040.png)

---

#### 7. Final Domain Success Check: ADUC Verification
The final "Proof of Concept" is verified within **Active Directory Users and Computers (ADUC)**. We can confirm that the client machine (`DESKTOP-UHG2A68`) and clicking on it we see it is now a registered member of the **`singh.com/Domain Computers`** group.
![Final Verification](./Images/image%2041.png)
</details>

---
<br>
</details>
