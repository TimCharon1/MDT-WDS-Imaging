<h1>MDT and WDS Imaging Lab</h1>
This tutorial outlines the steps to build and test a Microsoft Deployment Toolkit (MDT) and Windows Deployment Services (WDS) environment in a virtual lab using free tools. This simulates a real-world imaging and deployment system used by IT Configuration Technicians.

<br/>

- Microsoft Deployment Toolkit (MDT)
- Windows Deployment Services (WDS)
- Windows Server 2019
- Windows 10/11 ISO
- VirtualBox or Hyper-V

<h2>Operating Systems Used</h2>

- Windows Server 2019 (Evaluation)
- Windows 10 / 11 (ISO image only)

<h2>List of Prerequisites</h2>

- Host system with at least 8GB RAM and 50GB free space
- Internet connection to download ISOs and tools
- Virtualization platform (VirtualBox or Hyper-V)
- Basic understanding of Windows and virtual machines

---

<h2>Day 1 (3 Hours): Build the Lab and Set Up MDT</h2>

<h3>Hour 1: Set Up Your Lab Environment</h3>

📁 Install and prepare your environment:

1. **Install virtualization software:**
   - [VirtualBox](https://www.virtualbox.org/wiki/Downloads) *(Windows Home OK)*
   - Or enable Hyper-V on Windows Pro
   - ![image](https://github.com/user-attachments/assets/fc71a9f5-61dc-4593-8d69-624c51aff79e)


2. **Download software:**
   - [Windows Server 2019 ISO](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019)
   - [Windows 10 or 11 ISO](https://www.microsoft.com/software-download/)
   - [Windows ADK + WinPE](https://learn.microsoft.com/en-us/windows-hardware/get-started/adk-install)
   - [Microsoft Deployment Toolkit (MDT)](https://www.microsoft.com/en-us/download/details.aspx?id=54259)

3. **Create two VMs:**
   - `MDT-SERVER`: Windows Server 2019, 4GB RAM, 40GB disk
   - `CLIENT-1`: Blank VM for PXE booting
  
   - ![image](https://github.com/user-attachments/assets/107b7ef8-4158-4af6-8d31-39424c30c574)
   - ![image](https://github.com/user-attachments/assets/74911df4-6f85-4dc9-88af-12f682a00b23)



---

<h3>Hour 2: Install MDT and Create Deployment Share</h3>

🛠️ Install and configure MDT:

1. **Install tools (in this order) on `MDT-SERVER`:**
   - Windows ADK
   - WinPE Add-on
   - Microsoft Deployment Toolkit (MDT)

2. **Launch Deployment Workbench:**
   - Create a Deployment Share: `C:\DeploymentShare`

3. **Import Windows OS image:**
   - Use the Windows 10/11 ISO
   - Add it under “Operating Systems” in MDT

4. **Create Task Sequence:**
   - Use "Standard Client Task Sequence"
   - Select imported OS
   - Leave admin password blank for now

---

<h3>Hour 3: Create Boot Media and Configure PXE Boot</h3>

🌐 Generate and prepare PXE boot environment:

1. **Update Deployment Share** to generate:
   - `LiteTouchPE_x64.wim`
   - `LiteTouchPE_x64.iso`

2. **Install Windows Deployment Services (WDS)**:
   - Add WDS role to Server
   - Use default install path `C:\RemoteInstall`

3. **Configure PXE boot in WDS:**
   - Add `LiteTouchPE_x64.wim` as a boot image

4. **Set `CLIENT-1` to boot from network (PXE)**:
   - In VirtualBox: Move “Network” to top in boot order

---

<h2>Day 2 (3 Hours): Deploy and Customize Images</h2>

<h3>Hour 4: PXE Boot the Client and Deploy</h3>

🚀 Deploy the OS via PXE:

1. **Boot CLIENT-1**
2. **Press F12 for PXE boot**
3. **MDT Wizard launches:**
   - Select Task Sequence
   - Configure basic settings (name, timezone)
4. **Watch Windows deploy fully automated**

---

<h3>Hour 5: Customize the Deployment</h3>

🧩 Add applications and system tweaks:

1. **Add Chrome or Firefox:**
   - Right-click Applications → New Application
   - Silent install command: `ChromeSetup.exe /silent /install`

2. **Add custom settings:**
   - Wallpaper
   - Auto-login
   - Registry keys

3. **Add GPO files or scripts (optional)**

---

<h3>Hour 6: Optional Stretch Goals</h3>

🧪 Try advanced features:

- Create Task Sequence for **Windows 11**
- Import real-world **OEM drivers**
- Use Sysprep + DISM to **capture a custom image**
- Enable logging to track deployments
- Join PC to domain during deployment

---

<h2>📥 Tools and Downloads</h2>

- VirtualBox: https://www.virtualbox.org/wiki/Downloads  
- Windows Server 2019 Evaluation: https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019  
- Windows 10/11 ISO: https://www.microsoft.com/software-download/  
- Windows ADK + WinPE Add-on: https://learn.microsoft.com/en-us/windows-hardware/get-started/adk-install  
- Microsoft Deployment Toolkit (MDT): https://www.microsoft.com/en-us/download/details.aspx?id=54259

---

<h2>💡 Skills Demonstrated</h2>

- Operating system deployment (MDT)
- PXE boot configuration (WDS)
- Application packaging and silent installs
- VM-based testing and lab simulation
- Real-world imaging workflow for enterprise systems

> 🧠 Perfect for aspiring IT Configuration Technicians, Help Desk, or Sysadmins.

