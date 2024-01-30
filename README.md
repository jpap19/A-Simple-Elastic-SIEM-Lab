<h1>A Simple Elastic SIEM Lab</h1>

<h2>Description</h2>
In this activity, we are going to set up a home lab for Elastic Stack Security Information and Event Management (SIEM) using the Elastic Web portal and a Kali Linux VM. 
We will generate security events on the Kali VM, set up an agent to forward data to the SIEM, query and analyze the logs in the SIEM.
<br />

<h2>Resources And Links To Download Required Softwares:</h2>

- <b>VMware SandBox</b>    https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html
- <b>Windows 10 ISO</b>    https://www.microsoft.com/en-us/software-download/windows10
- <b>cloud.elastic</b>     https://cloud.elastic.co/registration
- <b>kali</b>              https://www.kali.org/get-kali/#kali-virtual-machines.
- <b>Basic Linux Knowledge is needed</b>

<h2>Program walk-through:</h2>

<p align="center">
 
 The links provided here above can be used to download required softwares. The implementation will be in done in 6 Steps:

STEP 1: Set up a free Elastic account and Install the Kali VM.

STEP 2: Configure the Elastic Agent on the Linux VM to collect the logs and forward it to the SIEM.

STEP 3: Generate security events on the Kali VM.

STEP 4: Query to find the security events in the Elastic SIEM.

STEP 5: Create a Dashboard to visualize security events.

STEP 6: Create alerts for security events.

STEP 1 Set up a free Elastic account and Install the Kali VM:
Go to the link provided here above, download and install VMware SANDBOX, then download windows 10 ISO and save in a folder on the computer. VMware  will be used to setup and run virtual machine, Windows 10 ISO  will be installed on the virtual machine.
 
1.1 Set up a free Elastic account: <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/VmwareInstalled.png" height="150%" width="100%" alt="Nessus Essential Home Lab"/>
<br />
<br />
1.2 Install the Kali VM: <br/>

<img src="https://github.com/jpap19/NessusHomeLab/blob/main/Images/WindowsInstalledOnVM.png" height="150%" width="150%" alt="Nessus Essential Home Lab"/>
<br />
<br />



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
