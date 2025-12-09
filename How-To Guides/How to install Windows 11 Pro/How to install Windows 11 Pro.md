
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Windows%2011.png"/> <br>

## How to install Windows 11 Pro

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

### Table of Contents

&emsp; [1] Download a free copy of the Windows 11 ISO. <br>
&emsp; [2] Install Windows 11 Pro. <br>
&emsp; [3] (Optional) Set a static IP address. <br>
&emsp; [4] (Optional) Enable 'Network discovery and file sharing'. <br>
&emsp; [5] (Optional) Create a non-Administrator user account. <br>

&emsp; [#] Appendix <br>
&emsp; [#] Disable automatic reboots caused by Windows Updates. <br>
&emsp; [#] How to join Windows 11 Pro to a Microsoft Active Directory Domain. <br>
<br>

***

### [1] Download a free copy of the Windows 11 ISO.

> ℹ️ This guide was written using the 25H2 version, '`Win11_25H2_English_x64.iso`'. <br>

&emsp; Visit the following URL: <br>
```bash
https://www.microsoft.com/en-us/software-download/windows11
```
&emsp; > Scroll down to the '*Download Windows 11 Disk Image (ISO) for x64 devices*' section. <br>
&emsp; > Select '`Windows 11 (multi-edition ISO for x64 devices)`' from the drop-down menu. <br>
&emsp; > Select '`Confirm`'. <br>
&emsp; > Select '`English (United States)`', or another language if needed. <br>
&emsp; > Select '`Confirm`'. <br>
&emsp; > Select '`64-bit Download`' to download the Windows 11 ISO. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132129%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132129%20v2.png" height="270"/>
</a><br>
<br>

***

### [2] Install Windows 11 Pro.

&emsp; If you're installing Windows 11 on a Virtual Machine, mount the ISO to the Virtual Machine's CD/DVD drive. <br>

&emsp; If you're installing Windows 11 on a physical machine, you will need to burn the ISO to a bootable USB drive. I recommend `Rufus`. <br>

# 

<details>
  <summary>Expand this section for additional details on <b><i>Rufus</i></b>.</summary>

***

> ℹ️ I recommend the 'Portable' version for simplicity. <br>

```bash
https://rufus.ie/en/#download
```
<br>

&emsp; Device: '`Select your USB`'. <br>
&emsp; Boot selection: '`Win11_25H2_English_x64.iso`', use the 'SELECT' button to locate and select the ISO. <br>
&emsp; Under most circumstances, leave everything else at the default. <br>
&emsp; Select '`START`' to burn the Windows 11 ISO to your USB. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132130%20v2.png" height="270"/>
</a><br>

***

</details>

#

> ℹ️ In my example, I'm installing Windows 11 Pro on a VMware Virtual Machine. <br>

&emsp; > Boot from your Windows 11 ISO: <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132328%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132328%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132351%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132351%20v2.png" height="270"/>
</a><br>

***
&emsp; > Begin following the installation wizard. <br>
&emsp; > Select your language settings, then '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132425%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132425%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select your keyboard settings, then '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132616%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132616%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Install Windows 11`'. <br> 
&emsp; > Accept (check) '`I agree everything will be deleted including files, apps, and settings`'. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132640%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132640%20v2.png" height="270"/>
</a><br>

***
&emsp; > Here you can enter your Windows product key (license). <br>
&emsp; > Select '`I don't have a product key`'. <br>

> ℹ️ From a technical perspective, Windows 11 Pro can be run without a product key (license); however, I encourage you to do your research regarding Microsoft's stance and EULA on this topic.

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132658%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132658%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Windows 11 Pro`' for your image, then '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132727%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132727%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Accept`' to the license agreement and terms. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132742%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132742%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select the target disk, where you want to install the Windows 11 Pro Operating System. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132811%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132811%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Install`' once you are ready to proceed and install Windows 11 Pro. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132830%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132830%20v2.png" height="270"/>
</a><br>

***
&emsp; > Now, allow time for Windows 11 Pro to install. <br>
&emsp; > The install process will reboot your machine multiple times! <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132848%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20132848%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select your country/region, then select '`Yes`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133524%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133524%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select your keyboard layout / input method. <br>
&emsp; > Select '`Yes`' to continue. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133555%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133555%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Skip`' when asked to add a second keyboard. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133612%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133612%20v2.png" height="270"/>
</a><br>

***
&emsp; > Assign a name (hostname) to your Windows 11 Pro machine. <br>
&emsp; > Select '`Next`'. <br>

> ℹ️ Assigning a name (hostname) will make identification, DNS, and self-hosting apps in the future easier. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133819%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133819%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Set up for personal use`'. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133908%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20133908%20v2.png" height="270"/>
</a><br>

***
&emsp; > Windows will take a few minutes to perform updates. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20134132%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20134132%20v2.png" height="270"/>
</a><br>

***
> ⚠️ Unfortunately, Microsoft is now intentionally blocking Microsoft Account bypass options like '`OOBE\BYPASSNRO`' / '`ipconfig /release`'. For this reason, I recommend signing into or creating a Microsoft account. Post-install, we can create a non-Administrator account that does not need to be tied to a Microsoft account. We'll use the non-Administrator account to install/run our self-hosted applications for better security and isolation. <br>

&emsp; > Select '`Sign in`' to sign into your existing or to create a Microsoft account. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20134820%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20134820%20v2.png" height="270"/>
</a><br>

***
&emsp; > If you have an existing Microsoft account, sign in. <br>
&emsp; > If you need to create a Microsoft account, follow the next few steps. <br>
&emsp;&emsp;&emsp; > Select '`Create one!`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20134845%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20134845%20v2.png" height="270"/>
</a><br>

***
> ℹ️ Microsoft no longer requires an '`@hotmail.com`' email address. Choose an email provider of your choice to create a Microsoft account. <br>

&emsp; > Enter your email address. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20135734%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20135734%20v2.png" height="270"/>
</a><br>

***
&emsp; > Create a password for your new Microsoft account. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140001%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140001%20v2.png" height="270"/>
</a><br>

***
&emsp; > Enter your first and last name. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140033%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140033%20v2.png" height="270"/>
</a><br>

***
&emsp; > Enter your Country/region and Birthdate. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140110%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140110%20v2.png" height="270"/>
</a><br>

***
&emsp; > Enter the code sent to your specified Microsoft account email address. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140324%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140324%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Create PIN`'. <br>
&emsp; > Create a PIN. <br>
&emsp; > Select '`OK`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140440%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140440%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140507%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140507%20v2.png" height="270"/>
</a><br>

***
&emsp; > Choose your privacy settings. <br>
&emsp; > Select '`Accept`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140608%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140608%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Set up a new PC`'. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140734%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20140734%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Skip`' for the 'Let's customize your experience'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141755%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141755%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Skip`' for integrating your mobile device. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141820%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141820%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Not now`' for syncing browsing data associated with your Microsoft account. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141849%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141849%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Decline Microsoft 365`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141907%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141907%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Decline`' for Microsoft 365 cloud storage. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141923%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20141923%20v2.png" height="270"/>
</a><br>

***
&emsp; > Turn off '`Yes, set up my email`' for Outlook. <br>
&emsp; > Select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142043%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142043%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Skip`' for Game Pass. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142104%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142104%20v2.png" height="270"/>
</a><br>

***
&emsp; > Microsoft will finish setup. <br>
&emsp; > Once you see the Windows desktop, installation is complete!!! <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142224%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142224%20v2.png" height="270"/>
</a><br>
<br>

***

### [3] (Optional) Set a static IP address.

> ℹ️ If you plan on self-hosting applications on this Windows 11 Pro machine, it is recommended to set a static IP address to ensure easy and consistent access. <br>

&emsp; **[3.1] [Option 1] Set a static IP address via Windows 11 Network Settings.** <br>

&emsp;&emsp; > Windows Start Menu <br>
&emsp;&emsp; > Settings <br>
&emsp;&emsp; > Select '`Network & internet`'. <br>
&emsp;&emsp; > Select '`Ethernet`'. <br>
&emsp;&emsp; > Select '`Edit`' next to '*IP assignment*'. <br>
&emsp;&emsp; > Select '`Manual`' from the dropdown menu. <br>
&emsp;&emsp; > Enable '`IPv4`' and enter your networking information. <br>
&emsp;&emsp; > When finished, select '`Save`'. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142501%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142501%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142534%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142534%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142641%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142641%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142712%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142712%20v2.png" height="270"/>
</a><br>

&emsp; **[3.2] [Option 2] Assign a "static" IP address via a 'DHCP static reservation' (typically your router).** <br>

&emsp;&emsp; Assigning a “static” IP via a DHCP reservation uses your machine’s network adapter MAC address. <br>

&emsp;&emsp; Find your MAC address with these steps. <br>
&emsp;&emsp;&emsp; > Windows Start Menu <br>
&emsp;&emsp;&emsp; > Settings <br>
&emsp;&emsp;&emsp; > Select '`Network & internet`'. <br>
&emsp;&emsp;&emsp; > Select '`Ethernet`'. <br>
&emsp;&emsp;&emsp; > View 'Physical address (MAC)'. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20143322%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20143322%20v2.png" height="270"/>
</a><br>

&emsp;&emsp; > Here is an example of what assigning a "static" IP address via a 'DHCP static reservation' looks like on pfSense. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123200%20v2.png" width="360"/>
</a><br>
<br>

***

### [4] (Optional) Enable 'Network discovery and file sharing'.

> ℹ️ If you plan on mounting network drives or using SMB shares with this Windows 11 Pro machine, you should enable 'Network discovery and file sharing'. <br>

&emsp; > Open 'File Explorer'. <br>
&emsp; > Select '`Network`'. <br>
&emsp; > Select the '`Network discovery and file sharing are turned off [...] Click to change...`' banner. <br>
&emsp; > Select '`Turn on network discovery and file sharing`'. <br>
&emsp; > Select '`Yes, turn on network discovery and file sharing`'. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142818%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142818%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142835%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142835%20v2.png" height="270"/>
</a><br>

&emsp; > Now you can see devices on your network. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142915%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20142915%20v2.png" height="270"/>
</a><br>
<br>

***

### [5] (Optional) Create a non-Administrator user account.

&emsp; **[5.1] Create a non-Administrator user account.** <br>

> ℹ️ If you plan on self-hosting applications on this Windows 11 Pro machine, it is recommended to create a non-Administrator user account. Doing so will increase your security posture by reducing what changes or actions can be run on your machine if it were compromised by malware. <br>

> ℹ️ If you are an advanced user with a Domain Controller running Active Directory in your environment, I would recommend skipping this step. At this point, join this Windows 11 Pro machine to your Active Directory and use a non-Administrator user within your Domain.

&emsp; Create a standard (non-Administrator) user following these steps: <br>
&emsp;&emsp; > Log into an Administrator-level account, if not already. <br>
&emsp;&emsp; > Windows Start Menu <br>
&emsp;&emsp; > Settings <br>
&emsp;&emsp; > Select '`Accounts`'. <br>
&emsp;&emsp; > Select '`Other users`'. <br>
&emsp;&emsp; > Select '`Add account`'. <br>
&emsp;&emsp; > Select '`I don't have this person's sign-in information`'. <br>
&emsp;&emsp; > Select '`Add a user without a Microsoft account`'. <br>
&emsp;&emsp; > Enter your user information and fill out the security questions. <br>
&emsp;&emsp; > Select '`Next`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20143503%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20143503%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20143610%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20143610%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20143648%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20143648%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20144028%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20144028%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20144100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20144100%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Here you can see the standard (non-Administrator) user account. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20144248%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20144248%20v2.png" height="270"/>
</a><br>
<br>

&emsp; **[5.2] Enable Remote Desktop access for your non-Administrator user account.** <br>

> ℹ️ During this process, you will be prompted to enter your Administrator user credentials, which is expected. <br>

&emsp; > Login on your non-Administrator user account. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20144446%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-17%20144446%20v2.png" height="270"/>
</a><br>

&emsp; Enable Remote Desktop access for your non-Administrator user account following these steps: <br>
&emsp;&emsp; > Windows Start Menu <br>
&emsp;&emsp; > Settings <br>
&emsp;&emsp; > Select '`System`'. <br>
&emsp;&emsp; > Select '`Remote Desktop`'. <br>
&emsp;&emsp; > Turn on '`Remote Desktop`'. <br>
&emsp;&emsp; > Select '`Confirm`'. <br>
&emsp;&emsp; > Select '`Remote Desktop users`'. <br>
&emsp;&emsp; > Select '`Add`'. <br>
&emsp;&emsp; > Enter your non-Administrator user's account name. <br>
&emsp;&emsp; > Select '`Check Names`'. <br>
&emsp;&emsp; > Select '`OK`'. <br>
&emsp;&emsp; > Verify your non-Administrator user is listed, then select '`OK`'. <br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123615%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123615%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123630%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123630%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123700%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123700%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123715%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123715%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123745%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123745%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123800%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123800%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123815%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123815%20v2.png" height="270"/>
</a><br>
<br>

<br>

***

## Appendix

### Disable automatic reboots caused by Windows Updates.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ These steps prevent Windows Updates from automatically rebooting your machine when a user is logged in. <br>

&emsp; **[Option 1] Windows 11 | Standalone Windows Machine (no Workgroup / Domain)**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Log into an administrator-level user account. <br>
&emsp; > Open the '`Edit Group Policy`' manager: <br>
&emsp;&emsp; > Windows Start Menu  <br>
&emsp;&emsp; > Type/Search '`Edit Group Policy`'. <br>
&emsp;&emsp; > Select/Open the '`Edit Group Policy`' manager. <br>
&emsp;&emsp; > Navigate to the following location within the 'Edit Group Policy' manager: <br>
&emsp;&emsp;&emsp; > '`Computer Configuration`' <br>
&emsp;&emsp;&emsp; > '`Administrative Templates`' <br>
&emsp;&emsp;&emsp; > '`Windows Components`' <br>
&emsp;&emsp;&emsp; > '`Windows Update`' <br>
&emsp;&emsp;&emsp; > '`Legacy Policies`' <br>
&emsp;&emsp;&emsp; > Find and edit the policy '`No auto-restart with logged on users for scheduled automatic updates installations`'. <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Enable`' <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Ok`' or '`Apply`'. <br>

Close the '`Group Policy Management`' console. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123830%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123830%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123845%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123845%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123900%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123900%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123915%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123915%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123930%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123930%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123945%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123945%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124000%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124015%20v2.png" height="270"/>
</a><br>

</details>

&emsp; **[Option 2] Windows Server 2019 | Domain Controller w/Active Directory**

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ For advanced users with their Windows 11 Pro server/machine joined to a Domain Controller/Active Directory. Setting this policy against the root of the domain will apply this setting against ALL Windows machines joined to the Domain, which is what I prefer in my environment. If you need to isolate specific machines/VMs, please adjust these steps as you see fit.

&emsp; > Log into your Domain Controller. <br>
&emsp; > Open the '`Group Policy Management`' console: <br>
&emsp;&emsp; > Windows Start Menu <br>
&emsp;&emsp; > Type/Search '`Group Policy Management`'. <br>
&emsp;&emsp; > Select/Open the '`Group Policy Management`' console. <br>			
&emsp;&emsp;&emsp; > Expand '`Forest: example_domain.home`'. <br>
&emsp;&emsp;&emsp; > Expand '`Domains`'. <br>
&emsp;&emsp;&emsp; > Right-click your 'example_domain.home' and select '`Create a GPO in this domain, and Link it here…`'. <br>
&emsp;&emsp;&emsp;&emsp; > Give your GPO (Group Policy Object) a name, I recommend something like “2025.08.02 Disable Auto Reboot for Updates”. <br>
&emsp;&emsp;&emsp;&emsp; > Right-click your newly create GPO and select '`Edit…`'. <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Within the '`Group Policy Management Editor`', navigate to the following location: <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Computer Configuration`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Policies`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Administrative Templates`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Windows Components`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Windows Update`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Find and edit the policy '`No auto-restart with logged on users for scheduled automatic updates installations`'. <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; > Select '`Enable`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; > Select '`Ok`' or '`Apply`'. <br>

Close the '`Group Policy Management`' console. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124030%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124045%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124100%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124115%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Expand this window to make it easier to navigate through the next couple of steps. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png" height="270"/>
</a>

</details>

***

</details>

### How to join Windows 11 Pro to a Microsoft Active Directory Domain.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ This section assumes you already have a Domain Controller / Active Directory up and running.

&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > Search '`domain`', then select '`Access work or school`'. <br>
&emsp; > Select '`Connect`' <br>
&emsp; > Select '`Join this device to a local Active Directory domain`' <br>
&emsp; > Enter your domain information, then select '`Next`'. <br>
&emsp; > Enter an Administrator-level account and password that is authorized to join Windows machines to the domain. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120015%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120030%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120045%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120100%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-18%20120115%20v2.png" height="270"/>
</a><br>

</details>
