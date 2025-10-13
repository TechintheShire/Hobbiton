<a href="./Icons%20and%20Screenshots/20250805_095720.png">
  <img src="./Icons%20and%20Screenshots/20250805_095720.png" height="170"/>
</a><br>

# How to install Windows 11 Pro

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

## Install and Configure, Windows 11 Pro

> ℹ️ The ISO used in this guide is Windows 11 24H2. <br>

> ⚠️ **Windows 11 'Recall' Feature**  
>
> Windows 11 has introduced an AI screen logging feature called 'Recall', which is a concern for both privacy and security. <br>
>
> As of 2025/05, if you're using a standard x86-based system (Intel/AMD), Recall is not enabled, and you don't need to worry about it. <br>
>
> At this time, the feature is only available / enabled under the following conditions: <br>
> &nbsp;- Copilot+ PCs, which use ARM-based Snapdragon X Elite/Plus chips. <br>
> &nbsp;- Devices running Windows 11 24H2 or later with NPU (Neural Processing Unit). <br>
>
> If in the future, this feature is enabled by default for all system types, we will strongly consider using a different operating system / platform overall. <br>

### [1] Download a free copy/ISO of Windows 11.

<details>
  <summary>Expand for additional details.</summary>
<br>
	
&emsp; > Open https://www.microsoft.com/en-us/software-download/windows11 in your browser. <br>
&emsp; > Scroll to the bottom of the page. <br>
&emsp; > Using the drop down menu, select the appropriate ISO and download. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121500%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121500%20v2.png" height="470"/>
</a><br>
<br>

&emsp;> Your ISO should look similar to the following. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121515%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121515%20v2.png" height="470"/>
</a><br>

</details>

### [2] Install Windows 11 (Pro) on your target machine.

<details>
  <summary>Expand for additional details.</summary>
<br>

***
> ℹ️ If you are installing Windows 11 (Pro) on a physical machine, you will need to burn the Windows ISO to a bootable USB. <br>
>
> I recommend using Rufus, https://rufus.ie/en/ . <br>

<details><summary> Expand this section for steps on using Rufus. </summary>
<br>

&emsp; > Download Rufus. In my example, I use the 'portable' version for Windows x64 (64-bit). <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124120%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124120%20v2.png" height="470"/>
</a><br>

&emsp; > Here is what the downloaded .exe looks like. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124135%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124135%20v2.png" height="470"/>
</a><br>

&emsp; > Double-click the .exe to start Rufus. <br>
&emsp; > I recommend allowing Rufus to check for updates. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124150%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124150%20v2.png" height="470"/>
</a><br>

&emsp; > If Rufus finds updates, select 'Yes' to accept and install them. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124205%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124205%20v2.png" height="470"/>
</a><br>

&emsp; > Select your ISO, in our case, the Windows 11 ISO. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124220%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124220%20v2.png" height="470"/>
</a><br>

&emsp; > Once all of your desired settings are in place and you're ready to burn the ISO to your USB, select 'START'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124235%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124235%20v2.png" height="470"/>
</a><br>

&emsp; > Select or deselect your desired 'Customize Windows installation?' settings, then select 'OK'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124250%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124250%20v2.png" height="470"/>
</a><br>

&emsp; > Read this warning carefully, all data on your target USB will be overwritten. Select 'OK' to proceed. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124305%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124305%20v2.png" height="470"/>
</a><br>

&emsp; > You can monitor the process here. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124320%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124320%20v2.png" height="470"/>
</a><br>

&emsp; > Once complete, the tool should show a green status bar with 'READY'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124335%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124335%20v2.png" height="470"/>
</a><br>

&emsp; > From here, you'd close Rufus, safely eject your USB, insert the USB into your target machine, boot from the USB, and follow the installation instructions.

</details>

***

In this guide, I'll be installing Windows 11 Pro on a VMware ESXi Virtual Machine (VM). Whenever possible, I recommend Virtual Machines (VMs) because it enables you to take VM-level snapshots and roll back to a known good state in the event that any task goes wrong or breaks something. This goes for installs, updates, or even general changes. There are plenty of great hypervisors on the market. I encourage you to do your own research and find one that meets your needs. I would comfortably recommend Proxmox, XCP-NG, TrueNAS, and unRAID.

***
&emsp; > Boot from your Windows 11 ISO. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121530%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121530%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121545%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121545%20v2.png" height="470"/>
</a><br>

***
&emsp; > Begin following the installation wizard. <br>

> ℹ️ I prefer initially installing Windows 11 without a Microsoft account (more on this later in this tutorial). <br>
>
> I used the following Guide from 'tom's HARDWARE' to accomplish this: <br>
> https://www.tomshardware.com/how-to/install-windows-11-without-microsoft-account .

***
&emsp; > Select your language settings, then 'Next'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122000%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select your keyboard settings, then 'Next'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122015%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Install Windows 11'. <br> 
&emsp; > Accept (check) the warning that proceeding with this selection will wipe the entire target disk. <br>
&emsp; > Then, select 'Next'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122030%20v2.png" height="470"/>
</a><br>

***
&emsp; > Here you can enter your Windows product key (license) or select 'I don't have a product key' to continue the installation process. <br>

> ℹ️ From a technical perspective, Windows 11 Pro can be run without a product key (license); however, I encourage you to do your research regarding Microsoft's stance and EULA on this topic.

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122045%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Windows 11 Pro' for your image, then 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122100%20v2.png" height="470"/>
</a><br>

***
&emsp; > 'Accept' the license agreement and terms. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122115%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select the target disk, where you want to install the Windows 11 Pro Operating System. <br>
&emsp; > Then, select 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122130%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Install' once you are ready to proceed and install Windows 11 Pro. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122145%20v2.png" height="470"/>
</a><br>

***
&emsp; > Now, give Windows 11 Pro some time to install. <br>
&emsp; > The install process will reboot your machine multiple times! <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122200%20v2.png" height="470"/>
</a><br>

***

> ⚠️ **Pause Here!!!**  
>
> Please read below before continuing.
>
> I prefer initially installing Windows 11 without a Microsoft account. The next few steps will outline this process.
>
> I used the following Guide from 'tom's HARDWARE' to accomplish this: <br>
https://www.tomshardware.com/how-to/install-windows-11-without-microsoft-account <br>
>
> If the method I have outlined here doesn't work, please see 'tom's HARDWARE' guide for additional methods and guidance. <br>

&emsp; > Once you see the "choose a country" screen, we are going to run through a series of steps to disable the requirement to continue the installation with an internet connection / Microsoft account. Once complete, we'll be able to finish the installation process using (creating) a local user (administrator) account. <br>

&emsp; > On this screen, hit 'Shift + F10' to open a Command Prompt (seen in the next screenshot). <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122215%20v2.png" height="470"/>
</a><br>

***
&emsp; > Running the following command will automatically reboot your machine, which is expected. <br>
&emsp; > In the Command Prompt, type the following and hit 'Enter'. <br>
	
 	OOBE\BYPASSNRO

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122230%20v2.png" height="470"/>
</a><br>

***
&emsp; > When the "choose a country" screen comes back up, we need to disable our internet connection / network connectivity for the Windows 11 Pro machine (see the next screenshot for an example). <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122300%20v2.png" height="470"/>
</a><br>

&emsp; > In my example, I simply disable the NIC (network interface card) on my Virtual Machine. <br>
&emsp; > Once you completed this step, continue with the installation process. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122245%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select your keyboard layout / input method. <br>
&emsp; > Select 'Yes' to continue. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122315%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Skip' when asked to add a second keyboard. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122330%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122330%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'I don't have internet'. <br>
&emsp; > From this point forward, we'll be able to continue the installation using / creating a local user (administrator) instead of being forced to sign into a Microsoft account. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122345%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122345%20v2.png" height="470"/>
</a><br>

***
&emsp; > Over the next few screens / steps, create your local user account (administrator) and answer the necessary security / recovery / privacy questions. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122400%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122400%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122415%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122415%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122430%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122430%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122445%20v2.png" height="470"/>
</a><br>

***
&emsp; > Once you see the Windows desktop, the installation is complete!!! <br>
&emsp; > Before we continue, we need to re-enable our internet / network connection. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122500%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122500%20v2.png" height="470"/>
</a><br>

&emsp; > In my example, I simply re-enable the NIC on my Virtual Machine. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122515%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122515%20v2.png" height="470"/>
</a><br>

&emsp; > Here you can see, I now have internet / network access. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122530%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122530%20v2.png" height="470"/>
</a><br>

</details>

### [3] Post-install (Personalization and Customization)

<details>
  <summary>Expand for additional details.</summary>
<br>

From here, I recommend doing some post-install cleanup and configuration based on your personal preferences: <br>
&emsp; > Taskbar / Taskbar Settings <br>
&emsp; > Startup Program settings via 'Task Manager' <br>
&emsp; > Display, Power, and Sleep Options via 'Control Panel' <br>

</details>

### [4] Set a static IP address for your Windows 11 Pro machine.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> If you plan on self-hosting any applications on this Windows 11 Pro machine, it is recommended to set a static IP address to ensure easy and consistant access. 

> ℹ️ **Note** <br>
> It is recommended to modify your router's DHCP range to exclude any IP addresses you wish to assign as static. Doing so will help avoid 'IP address conflicts'. An 'IP address conflict' occurs when two devices connected to the same network are assigned the same IP address. This situation can cause communication failures and disrupt network operations, leading to connectivity problems, intermittent network access, and poor performance. <br><br>
> Here is an example of what this would like under pfsense. My DHCP Server will only hand out addresses between 192.168.50.21 through 192.168.50.100, which allows me to safely use any IP address outside of this range as a static IP address: <br><br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120545%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120545%20v2.png" height="470"/></a><br>

***

> ⚠️ **Verify your static IP address before setting it!!!**
>
> Before setting a static IP address, it is recommended to verify whether or not that IP address is already in use. Taking the time to check will help avoid any 'IP address conflicts'. <br>
>
> To check this, we do the following: <br>
> &emsp; > Windows Start Menu <br>
> &emsp; > Type/search for 'cmd' or 'Command Prompt' to find and open the Command Prompt app. <br>
> &emsp; > In the Command Prompt window, run the following command, replacing 111.222.333.444 with your IP address: <br>
>
	ping 111.222.333.444
>
> If you get a reply, that means the IP address is in use and you should choose a different IP address. <br>
> If you do NOT get a reply, that IP address should be safe to use. <br>

***

#### [4A] [Option 1] Set your static IP address via Windows 11 Network Settings.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > Network & internet <br>
&emsp; > Ethernet <br>
&emsp; > Select 'Edit' next to 'IP assignment' and enter your networking information. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122545%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20122545%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123000%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123015%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123016%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123016%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123030%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123045%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123100%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123115%20v2.png" height="470"/>
</a><br>

</details>

#### [4B] [Option 2] Assign a "static" IP address via a DHCP Server (typically your router).

<details>
  <summary>Expand for additional details.</summary>
<br>

This method is often refered to as a 'DHCP static reservation'. This method tells your DHCP Server to assign a specific IP address any time it sees a specific MAC address. If we use this method, any time our DHCP Server sees the MAC address for our Windows 11 Pro machine, it will assign the IP address that we specified. <br>

How to find MAC address via Settings. <br>
&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > Network & internet <br>
&emsp; > Ethernet <br>
&emsp; > Scroll down and view 'Physical address (MAC)' <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123130%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123145%20v2.png" height="470"/>
</a><br>

How to find your MAC address via Command Prompt. <br>
&emsp; > Windows Start Menu <br>
&emsp; > Type/Search for 'cmd' or 'Command Prompt' to find and open the Command Prompt app. <br>
&emsp; > In Command Prompt, run the following command and look for 'Physical address (MAC)': <br>

	ipconfig /all

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123200%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123215%20v2.png" height="470"/>
</a><br>

Here is an example for pfsense. Your router's web interface will look different but the methodolgy is the same. By setting a static mapping on your DHCP Server, any time your DHCP Server sees this MAC address, it will assign the specified IP address. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123230%20v2.png" height="470"/>
</a><br>

</details>

***

</details>

### [5] Set a unique hostname for your Windows 11 Pro machine.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > System <br>
&emsp; > About <br>
&emsp; > Select 'Rename this PC' and enter a new hostname. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123245%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123300%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123315%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123330%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123330%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123345%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123345%20v2.png" height="470"/>
</a><br>

</details>

### [6] Reboot your Windows 11 Pro machine and verify your IP address and host name.

<details>
  <summary>Expand for additional details.</summary>
<br>

This step is helpful to ensure your hostname / IP address are set and stay assigned correctly. <br>

Verify via Settings. <br>

&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > Network & internet <br>
&emsp; > Ethernet <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123115%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > System <br>
&emsp; > About <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123415%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123415%20v2.png" height="470"/>
</a><br>

Verify via 'Command Prompt' by running these commands.

&emsp; > Windows Start Menu <br>
&emsp; > Type/Search for 'cmd' or 'Command Prompt' to find and open the Command Prompt app. <br>

	ipconfig 

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123430%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123430%20v2.png" height="470"/>
</a><br>

	hostname

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123400%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123400%20v2.png" height="470"/>
</a><br>

</details>

### [7] Create a standard (non-administrator) user.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> If you are an advanced user with a Domain Controller running Active Directory in your environment, I would recommend skipping this step, which is creating a non-administrator local user. At this point, join this Windows 11 Pro machine to your Active Directory and use a non-administrator user within your Domain.

The install process we followed earlier in this guide initially sets us up with a local administrator-level account. To increase our security posture, I recommend creating a standard (non-administrator) level user account for daily operations and running our Apps. Running applications from an administrative account can cause security risks if the Windows Operating System or Apps we're running become compromised by malware. Running your applications within a user account/profile that only has standard permissions, will limit what changes can be made on the machine if anything were to become compromised by malware. <br>

Create a standard (non-administrator) user following these steps: <br>
&emsp; > Log into an administrator-level account, if not already. <br>
&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > Accounts <br>
&emsp; > Scroll down to 'Other Users' <br>
&emsp; > To the right of 'Add other user' select 'Add account'. <br>
&emsp; > I recommend creating an 'non-microsoft' account. <br>
&emsp; > Select 'I don't have this person's sign-in information'. <br>
&emsp; > Select 'Add a user without a Microsoft account'. <br>
&emsp; > Follow the steps to create your new user. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123445%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123500%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123500%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123515%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123515%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123530%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123530%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123545%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123545%20v2.png" height="470"/>
</a><br>
<br>

Log into the non-administrator user account you just created and perform similar cleanup and customization steps we did previously with our administrator account.

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png" height="470"/>
</a><br>

</details>

### [8] Enable RDP Remote Desktop.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > System <br>
&emsp; > Remote Desktop <br>
&emsp; > Select to enable Remote Desktop <br>
If prompted, enter your admin username/password/pin as needed. <br>
&emsp; > Select 'Confirm' to enable Remote Desktop <br>
&emsp; > Once enabled, open 'Remote Desktop users' where we will add our RDP user. <br>
If prompted, enter your admin username/password/pin as needed. <br>
<br>
Verify RDP is working by logging in via RDP. <br>
Continue the guide / tutorial from your RDP session! <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123615%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123615%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123630%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123630%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123645%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123645%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123700%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123700%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123715%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123715%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123730%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123730%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123745%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123745%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123800%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123800%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123815%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123815%20v2.png" height="470"/>
</a><br>

</details>

***

<br>

# Appendix

## Disable automatic reboots caused by Windows Updates.

<details>
  <summary>Expand for additional details.</summary>
<br>

Following these steps will significantly reduce the risk of unexpected or unplanned outages and downtime for this Windows 11 machine and any Apps we decide to run on this machine. Windows Updates will still be downloaded and applied when they become available; however, you get to choose when to initiate the reboot. I typically Remote Desktop into the Windows 11 machine and selecting reboot when ready. If you run your Apps as a Windows 'service', this may not be as much of a conern; however, following these steps will give you much more control over when reboots occur. I'll be covering how to run Apps as a Windows 'service' in another tutorial. <br>
	
### [Option 1] Windows 11 | Standalone Windows Machine (no Workgroup / Domain)

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; - Log into an administrator-level user account. <br>
&emsp; - Open the 'Edit Group Policy' manager by following these steps: <br>
&emsp;&emsp; > Windows Start Menu  <br>
&emsp;&emsp; > Type/Search 'Edit Group Policy'. <br>
&emsp;&emsp; > Select/Open the 'Edit Group Policy' manager. <br>
&emsp;&emsp; > Navigate to the following location within the 'Edit Gorup Policy' manager: <br>
&emsp;&emsp;&emsp; > 'Computer Configuration' <br>
&emsp;&emsp;&emsp; > 'Administrative Templates' <br>
&emsp;&emsp;&emsp; > 'Windows Components' <br>
&emsp;&emsp;&emsp; > 'Windows Update' <br>
&emsp;&emsp;&emsp; > 'Legacy Policies' <br>
&emsp;&emsp;&emsp; > Right Click and Edit 'No auto-restart with logged on users for scheduled automatic updates installations'. <br>
&emsp;&emsp;&emsp; > Select 'Enable' <br>
&emsp;&emsp;&emsp; > Select 'Ok' or 'Apply'. <br>
This process is finished. Close the 'Group Policy Management' console at this time. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123830%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123830%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123845%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123845%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123900%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123900%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123915%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123915%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123930%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123930%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123945%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123945%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124000%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124015%20v2.png" height="470"/>
</a><br>

</details>

### [Option 2] Windows Server 2019 | Domain Controller w/Active Directory

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ For advanced users with their Windows 11 Pro server/machine joined to a Domain Controller/Active Directory. Setting this policy against the root of the domain will apply this setting against ALL Windows machines joined to the Domain, which is what I prefer in my environment. If you need to isolate specific machines/VMs, please adjust these steps as you see fit.

&emsp; - Log into your Domain Controller using an administrator-level account. <br>
&emsp; - Open the 'Group Policy Management Console' (GPMC) using the following steps: <br>
&emsp;&emsp; > Windows Start Menu <br>
&emsp;&emsp; > Type/Search ‘Group Policy Management’. <br>
&emsp;&emsp; > Select/Open the 'Group Policy Management' console. <br>			
&emsp;&emsp; > Create a new ‘Group Policy Object’ under your domain. <br>
&emsp;&emsp;&emsp; > Group Policy Management <br>
&emsp;&emsp;&emsp; > Forest: example_domain.home <br>
&emsp;&emsp;&emsp; > Domains <br>
&emsp;&emsp;&emsp; > Right click your ‘example_domain.home’ and select ‘Create a GPO in this domain, and Link it here…’ <br>
&emsp;&emsp;&emsp;&emsp; > Give your GPO (Group Policy Object) a name, I recommend something like “2025.08.02 Disable Auto Reboot for Updates”. <br>
&emsp;&emsp;&emsp;&emsp; > Right click your newly create GPO and select ‘Edit…’. <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Within the newly opened window ‘Group Policy Management Editor’, navigate to the following location. <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Computer Configuration <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Policies <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Administrative Templates <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Windows Components <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Windows Update. <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Find and open the policy ‘No auto-restart with logged on users for scheduled automatic updates installations’. <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; > Set the policy to Enabled by selecting the radio button. <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; > Select 'Apply', then 'Ok' and you are finished. <br>
This process is finished. Close the 'Group Policy Management' console at this time. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124030%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124045%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124100%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124115%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Expand this window to make it easier to navigate through the next couple of steps. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png" height="470"/>
</a>

</details>

</details>

## How to join Windows 11 Pro to a Microsoft Active Directory Domain.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ This section assumes you already have a Domain Controller / Active Directory up and running.

&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > Search 'domain', then select 'Access work or school'. <br>
&emsp; > Select 'Connect' <br>
&emsp; > Select 'Join this device to a local Active Directory domain' <br>
&emsp; > Enter your domain information, then select 'Next'. <br>
&emsp; > Enter an Administrator-level account and password that is authorized to join Windows machines to the domain. <br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120000%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120015%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120030%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120045%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120100%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120115%20v2.png" height="470"/>
</a><br>

</details>
