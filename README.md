# EDR-Home-Lab-Attack-and-Defense
## Summary
This lab focuses on recreating a realistic cyberattack scenario alongside endpoint detection and response processes. Following Eric Capuano's online guide, I will use virtual machines to represent both the threat actor and the victim systems. The attack VM will employ the Sliver C2 framework to target a Windows endpoint, while the Windows machine will run LimaCharlie as its EDR solution.

Guide: https://blog.ecapuano.com/p/so-you-want-to-be-a-soc-analyst-intro

## The Setup
### Windows 11 Machine (Victim)
The first step to the lab is setting up both VMs using VMware Workstation and creating two VMs, one for Ubuntu Server and one for Windows 11. The attack machine will run on Ubuntu Server, and the endpoint will run on Windows 11. For the lab to work correctly, it is important to remove all the security capabilities from the Windows 11 VM (The Victim). I will be installing Silver on the VM with Ubuntu installed on it, which will be the primary attacking tool used, and LimaCharlie will be set up on the Windows 11 machine as an EDR solution. LimaCharlie will have a sensor linked to the Windows 11 machine and will be importing the Sysmon logs.

<hspac>
<img width="1920" height="1032" alt="Screenshot 2025-12-01 170714" src="https://github.com/user-attachments/assets/9199a523-f09a-4be0-97d8-8d54633e6396" />
- By enabling Microsoft Windows Defender Antivirus setting in Group Policy Editor will ensure that Antivirus will not run and scan the computer for malware and other potentially unwanted software.
<img width="1920" height="1032" alt="Screenshot 2025-12-01 170829" src="https://github.com/user-attachments/assets/b342dff4-8c0d-4f87-9d1e-6e2405faa5d0" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 171314" src="https://github.com/user-attachments/assets/b77f7504-9e32-43e1-b244-fbe248ebeecd" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 172548" src="https://github.com/user-attachments/assets/e043f90f-f0cb-486c-83d4-ca4f55164e06" />

### Windows 11 Machine (Victim)
<img width="1920" height="1020" alt="Screenshot 2025-12-01 173014" src="https://github.com/user-attachments/assets/d8be21a6-c2cd-4c4e-bb72-ef5ae3020b13" />
<img width="1920" height="1020" alt="Screenshot 2025-12-01 173153" src="https://github.com/user-attachments/assets/56b16170-3d42-4fba-8cab-3f2f6be85b2e" />

## Ubuntu Machine (Attacker)
<img width="1920" height="1032" alt="Screenshot 2025-12-01 174112" src="https://github.com/user-attachments/assets/d7bf2199-52de-4e71-93bd-fff3c3a0fc0c" />

## The Attack
Generate our payload on Sliver, and implant the malware into the Windows host machine.
<img width="1920" height="1032" alt="Screenshot 2025-12-01 174711" src="https://github.com/user-attachments/assets/638469cf-7e24-4286-8d79-dab1098d570a" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 175302" src="https://github.com/user-attachments/assets/749c8e5a-4b9f-44cb-9d9c-c3fef308b6b8" />
<img width="1103" height="759" alt="Screenshot 2025-12-01 175518" src="https://github.com/user-attachments/assets/b27c664a-ed24-48eb-8104-cfa56a113928" />
<img width="1103" height="759" alt="Screenshot 2025-12-01 175816" src="https://github.com/user-attachments/assets/72b3ee65-bc43-4f8a-b710-3f811f24a025" />

- We are now interacting directly with the C2 session on the Windows 11 VM.
<img width="1103" height="759" alt="Screenshot 2025-12-01 175952" src="https://github.com/user-attachments/assets/02a1df1a-ccb2-45ae-b87c-0a900d6f151d" />
<img width="1920" height="1020" alt="Screenshot 2025-12-01 180033" src="https://github.com/user-attachments/assets/c8c3eb85-5deb-4a18-841a-a00206fb5e00" />
<img width="1920" height="1020" alt="Screenshot 2025-12-01 180127" src="https://github.com/user-attachments/assets/9f628792-46f2-4c88-9f6c-3acf4dd18aec" />
<img width="1920" height="1020" alt="Screenshot 2025-12-01 180144" src="https://github.com/user-attachments/assets/d42e9de8-fbfa-4b63-840b-c0991ac11f70" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 180214" src="https://github.com/user-attachments/assets/33723031-1227-4d47-a9cd-dd4bc615d387" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 180229" src="https://github.com/user-attachments/assets/5c595367-6664-43e8-b868-d6b68798cb8e" />

- On the host machine we can look inside our LimaCharlie SIEM and see telemetry from the attacker. We can identify the payload thats running and see the IP its connected to.
<hspac>
<img width="1920" height="1032" alt="Screenshot 2025-12-01 180329" src="https://github.com/user-attachments/assets/1c60cd63-f699-49c0-a395-b0dd850bf2cf" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 180356" src="https://github.com/user-attachments/assets/0bbe3a08-50ac-46d0-86cd-7712d60f8b25" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 180451" src="https://github.com/user-attachments/assets/7153ecd1-b800-4df7-a0aa-3b69daf4e298" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 180527" src="https://github.com/user-attachments/assets/15c4a5db-266b-4a87-9bc0-f1de24e571ec" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 180551" src="https://github.com/user-attachments/assets/090ba954-f496-4810-9de4-21146d010024" />

<hspac>
- Item not found on VirusTotal doesn't mean that the file is innocent, just that it has never been seen before by VirusTotal, which makes sense because we just created this payload. 
<img width="904" height="972" alt="Screenshot 2025-12-01 180605" src="https://github.com/user-attachments/assets/960b6147-0696-4557-bd46-3cbf28cf32d9" />
<img width="1920" height="1032" alt="Screenshot 2025-12-01 180728" src="https://github.com/user-attachments/assets/4601dea7-e582-406c-8c56-30a9e6414f0e" />








