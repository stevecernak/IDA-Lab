# IDA-Lab
Documentation describing my Hyper-V lab setup to explore Deployment Workbench and related technologies.

**Introduction**

The author is looking to demonstrate proficiency in:
  - Microsoft Deployment Toolkit (MDT)
  - Task Sequencing 
  - PowerShell
  - Automation
  
There is no particular aversion to Microsoft Endpoint Configuration Manager (MECM), however, my previous experience was with SCCM. I have significant experience creating Low Touch Interaction (LTI) media to be deployed via Windows Deployment Services (WDS) via the Smart Deploy commercial wrapper.
  
**Microsoft Deployment Toolkit**

The Microsoft Deployment Toolkit (MDT) is a free tool for automating Windows and Windows Server operating system deployment, leveraging the Windows Assessment and Deployment Kit (ADK) for Windows 10. In order to support a full Task Sequence, the  Windows PE (Pre-Installation Environemnt) add-on is required.

The ADK, the add-on, and MDT was installed on Windows Server 2016 installation, primarily because of the age of my HP Z420. This server is named LAB. The device was modified to include a 4th hard disk, an SSD, which was placed below the CD-ROM. Three 1 TB HDDs were added to a storage pool, with the equivalent of RAID 5, to LAB as to allow for one disk to fail (my equipment is old). These disks were virtualized so as for the three disks to be accesible from D: .  

**Task Sequencing**

**PowerShell** 

PowerShell is a fantastic scripting language. This is for a few 

**Automation**
