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

Once MDT is installed, a Deployment Share is created. From the share, things such as Applications and Operating Systems may be imported, and these processes will generate PowerShell scripts to be used later. Example scripts will be included below.

In order to import the Operating System, an ISO must be mounted and include an install.wim file. Windows 10 Professional includes install.esd . The DISM utility needs to create install.wim. The below commands will do just that, in the /sources directory:

  ```dism /Get-WimInfo /WimFile:install.esd```

  ```dism /export-image /SourceImageFile:install.esd /SourceIndex:IndexNumber /DestinationImageFile:install.wim /Compress:max /CheckIntegrity```

When the standard Windows 10 installation media boots, it loads boot.wim - which is Windows PE. That particular build of Windows PE will then run setup.exe from the root folder. The setup.exe program than uses the Windows 10 images contained in install.wim to install Windows 10 to the target hard drive/SSD. This is why MDT needs to be leveraged for both media types.

**Task Sequencing**

The Task Sequence is the driving force behind an MDT/SCCM deployment. This is a sequence of events, that includes suchs tasks as:
  - Hardware configuration
  - Deploy OS images
  - Install applications
  - State restore
  - Configuration scripts

There are several templates that may be applied are:
  - Sysprep and Capture
  - Standard Client Task Sequence



**PowerShell** 

PowerShell is a fantastic scripting language. It is quite robust, and has a fairly intuitive Verb-Noun structure, such as:

```Get-Help Install-Module```





**Automation**

PowerShell scripts work well with Windows Task Scheduler and Group Policy. Task Scheduler employs different trigger mechanisms. 

Time-based triggers start tasks at specified times. This includes starting the task once at a specific time or starting the task multiple times on a daily, weekly, monthly, or monthly day-of-week schedule.

Event-based triggers start a task in response to certain system events. For example, event-based triggers can be set to start a task when the system starts up, when a user logs on to the local computer, or when the system becomes idle.

The ability to have the system initiate the update process at Login, for example, proves quite powerful on an ongoing basis.
