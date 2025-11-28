# EDR-Home-Lab-Attack-and-Defense
## Summary
This lab focuses on recreating a realistic cyberattack scenario alongside endpoint detection and response processes. Following Eric Capuano's online guide, I will use virtual machines to represent both the threat actor and the victim systems. The attack VM will employ the Sliver C2 framework to target a Windows endpoint, while the Windows machine will run LimaCharlie as its EDR solution.

Guide: https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-intro

## The Setup
### Windows 11 Machine (Victim)
The first step to the lab is setting up both VMs using VMware Workstation and creating two VMs, one for Ubuntu Server and one for Windows 11. The attack machine will run on Ubuntu Server, and the endpoint will run on Windows 11. For the lab to work correctly, it is important to remove all the security capabilities from the Windows 11 VM (The Victim). I will be installing Silver on the VM with Ubuntu installed on it, which will be the primary attacking tool used, and LimaCharlie will be set up on the Windows 11 machine as an EDR solution. LimaCharlie will have a sensor linked to the Windows 11 machine and will be importing the Sysmon logs.

<hspac>
<img width="1228" height="889" alt="Screenshot 2025-11-28 122256" src="https://github.com/user-attachments/assets/d6eb0f50-7649-4304-87c9-a58afc169d6c" />

- By enabling Microsoft Windows Defender Antivirus setting in Group Policy Editor will ensure that Antivirus will not run and scan the computer for malware and other potentially unwanted software.

<hspac>
<img width="1228" height="889" alt="image" src="https://github.com/user-attachments/assets/6854c77e-ddca-4b84-abf7-ae0ede0d84af" />

<img width="1228" height="889" alt="image" src="https://github.com/user-attachments/assets/dfcd1637-a04d-4f69-b335-cdc0175fe57d" />

### Downloading Sysmon and SwiftOnSecurity's Sysmon Config
<img width="1228" height="889" alt="image" src="https://github.com/user-attachments/assets/4971f8d3-e76e-4bd6-8045-88a0fd723907" />

### Installing LimaCharlie 
<img width="1594" height="575" alt="image" src="https://github.com/user-attachments/assets/4ca490a1-38bc-430b-87ab-e3bd47124e92" />
<img width="1608" height="531" alt="image" src="https://github.com/user-attachments/assets/8ad3bf03-df69-44fe-8427-cdc65bc14fff" />

### SSH into Ubuntu Server Machine and Downloading Sliver C2
<img width="1260" height="845" alt="image" src="https://github.com/user-attachments/assets/0e6ef4bd-8f44-4fd4-b876-fa5b30ae78b9" />

## The Attack
### Generate the C2 Payload
<img width="1260" height="845" alt="image" src="https://github.com/user-attachments/assets/72f657c9-bd6d-4f83-a2af-3d86c6e1e0ec" />
<img width="1228" height="889" alt="image" src="https://github.com/user-attachments/assets/44399813-789b-4c86-9557-460917afad3b" />
<img width="1260" height="845" alt="image" src="https://github.com/user-attachments/assets/0e324cee-77f1-45bb-922a-d5575a4ed6ac" />









