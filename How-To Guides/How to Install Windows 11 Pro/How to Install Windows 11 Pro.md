<img src="./Media/152025114633%20v2%20-%20(1)%20-%20Windows%2011.png"/> <br>

# How to Install Windows 11 Pro

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>

Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

Current Guide Version: 1.0 <br>
Last Verified: August 2026 <br>

> [!IMPORTANT]
> **Supported Platforms**
>
> ✅ Windows 11 Pro 25H2 (`Win11_25H2_English_x64.iso`) <br>
> ⏳ Windows 11 Pro 26H2

> [!IMPORTANT]
> For Windows 11 Minimum System Requirements, see [Microsoft's Windows 11 System Requirements](https://www.microsoft.com/en-us/windows/windows-11-specifications).

| Guide Version | Date | Changes |
|---|---|---|
| 1.0 | August 2026 | Initial guide, validated Windows 11 Pro 25H2 (`Win11_25H2_English_x64.iso`). |

## [1] 💿 Download the Windows 11 ISO.

- Download the Windows 11 ISO using your `🌐 web browser`.

```bash
https://www.microsoft.com/en-us/software-download/windows11
```

- Scroll down to the "***Download Windows 11 Disk Image (ISO) for x64 devices***" section.
- Select `Windows 11 (multi-edition ISO for x64 devices)` from the drop-down menu. 
- Select `Confirm`. 
- Select `English (United States)`, or another language if needed. 
- Select `Confirm`. 
- Select `64-bit Download` to download the Windows 11 ISO. 

<a href="./Media/Screenshot%202025-10-17%20132129%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132129%20v2.png" height="270"/>
</a><br>

## [2] ⬇️ Install Windows 11 Pro.

> [!TIP]
> If you are installing Windows on a physical machine, I recommend writing the ISO to a bootable USB drive using `Rufus`.
> ```bash
> https://rufus.ie/en/#download
> ```

- Boot from your Windows 11 ISO.

<a href="./Media/Screenshot%202025-10-17%20132328%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132328%20v2.png" height="370"/>
</a><br>

<a href="./Media/Screenshot%202025-10-17%20132351%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132351%20v2.png" height="370"/>
</a><br>
<br>

- Begin following the installation wizard.
- Select your language settings, then `Next`.

<a href="./Media/Screenshot%202025-10-17%20132425%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132425%20v2.png" height="370"/>
</a><br>
<br>

-  Select your keyboard settings, then `Next`.

<a href="./Media/Screenshot%202025-10-17%20132616%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132616%20v2.png" height="370"/>
</a><br>
<br>

- Select `Install Windows 11`.
- Accept (check) `I agree everything will be deleted including files, apps, and settings`.
- Select `Next`.

<a href="./Media/Screenshot%202025-10-17%20132640%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132640%20v2.png" height="370"/>
</a><br>
<br>

- Here you can enter your Windows product key (license). 
- For this guide, I'll select `I don't have a product key`. 

> [!NOTE]
> From a technical perspective, Windows 11 Pro can be run without a product key (license); however, I encourage you to do your research regarding Microsoft's stance and EULA on this topic.

<a href="./Media/Screenshot%202025-10-17%20132658%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132658%20v2.png" height="370"/>
</a><br>
<br>

- Select your Windows 11 edition, then `Next`.
  
<a href="./Media/Screenshot%202025-10-17%20132727%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132727%20v2.png" height="370"/>
</a><br>
<br>

- Read the Microsoft license terms, then select `Accept` to proceed.

<a href="./Media/Screenshot%202025-10-17%20132742%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132742%20v2.png" height="370"/>
</a><br>
<br>

- Select the target disk, where you want to install the Windows 11 Operating System.
- Select `Next`.

> [!WARNING]
> Installing Windows 11 may permanently erase existing data on the selected disk. Make sure you've selected the correct disk before proceeding!

> [!TIP]
> If you are installing Windows 11 on a KVM/QEMU-based hypervisor, such as Proxmox or unRAID, you may need to load VirtIO drivers before Windows can detect virtual hardware such as disks and network adapters.
>
> https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/

<a href="./Media/Screenshot%202025-10-17%20132811%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132811%20v2.png" height="370"/>
</a><br>
<br>

- Select `Install` once you are ready to proceed and install Windows 11.
  
<a href="./Media/Screenshot%202025-10-17%20132830%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132830%20v2.png" height="370"/>
</a><br>
<br>

- Allow Windows 11 to complete the installation. 
- The installation process will reboot your machine multiple times! 

<a href="./Media/Screenshot%202025-10-17%20132848%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20132848%20v2.png" height="370"/>
</a><br>
<br>

- Once the installation has completed, you can continue with Windows 11 setup.
- Select your country/region, then select `Yes`.

<a href="./Media/Screenshot%202025-10-17%20133524%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20133524%20v2.png" height="370"/>
</a><br>
<br>

- Select your keyboard layout / input method.
- Select `Yes` to continue.

<a href="./Media/Screenshot%202025-10-17%20133555%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20133555%20v2.png" height="370"/>
</a><br>
<br>

- Select `Skip` when asked to add a second keyboard.

<a href="./Media/Screenshot%202025-10-17%20133612%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20133612%20v2.png" height="370"/>
</a><br>
<br>

- Assign a name (hostname) to your Windows 11 Pro machine. 
- Select `Next`. 

> [!NOTE]
> Assigning a name (hostname) will make identification, DNS, and self-hosting apps easier in the future. 

<a href="./Media/Screenshot%202025-10-17%20133819%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20133819%20v2.png" height="370"/>
</a><br>
<br>

- Select `Set up for personal use`.
- Select `Next`.
<a href="./Media/Screenshot%202025-10-17%20133908%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20133908%20v2.png" height="370"/>
</a><br>
<br>

- Windows will take a few minutes to perform updates.
<a href="./Media/Screenshot%202025-10-17%20134132%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20134132%20v2.png" height="370"/>
</a><br>
<br>

> [!WARNING]
> Unfortunately, Microsoft is now intentionally blocking Microsoft Account bypass methods like '`OOBE\BYPASSNRO`' / '`ipconfig /release`'. For this reason, I recommend signing into or creating a Microsoft account. Post-install, we can create a non-Administrator account that does not need to be tied to a Microsoft account. We'll use the non-Administrator account to install/run our self-hosted applications for better security and isolation.

- Select `Sign in`.
<a href="./Media/Screenshot%202025-10-17%20134820%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20134820%20v2.png" height="370"/>
</a><br>
<br>

- ***Option 1***: If you have an existing Microsoft account, enter your sign in information and select `Next`.
- ***Option 2***: If you need to create a Microsoft account, select `Create one!`.
  - In this guide, I'll create a Microsoft account.
<a href="./Media/Screenshot%202025-10-17%20134845%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20134845%20v2.png" height="370"/>
</a><br>
<br>

> [!NOTE]
> Microsoft no longer requires an `@hotmail.com` email address. Choose an email provider of your choice to create a Microsoft account.

- Enter your email address.
- Select `Next`.
<a href="./Media/Screenshot%202025-10-17%20135734%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20135734%20v2.png" height="370"/>
</a><br>
<br>

- Create a password for your new Microsoft account.
- Select `Next`.
<a href="./Media/Screenshot%202025-10-17%20140001%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20140001%20v2.png" height="370"/>
</a><br>
<br>

- Enter your first and last name.
- Select `Next`.
<a href="./Media/Screenshot%202025-10-17%20140033%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20140033%20v2.png" height="370"/>
</a><br>
<br>

- Enter your Country/region and Birthdate.
- Select `Next`.
<a href="./Media/Screenshot%202025-10-17%20140110%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20140110%20v2.png" height="370"/>
</a><br>
<br>

- Enter the verification code sent to your email address.
- Select `Next`.
<a href="./Media/Screenshot%202025-10-17%20140324%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20140324%20v2.png" height="370"/>
</a><br>
<br>

- Select `Create PIN`.
- Create a PIN.
- Select `OK`.
<a href="./Media/Screenshot%202025-10-17%20140440%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20140440%20v2.png" height="370"/>
</a><br>
<a href="./Media/Screenshot%202025-10-17%20140507%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20140507%20v2.png" height="370"/>
</a><br>
<br>

- Choose your privacy settings.
- Select `Accept`.
<a href="./Media/Screenshot%202025-10-17%20140608%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20140608%20v2.png" height="370"/>
</a><br>
<br>

- Select `Set up a new PC`.
- Select `Next`.
<a href="./Media/Screenshot%202025-10-17%20140734%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20140734%20v2.png" height="370"/>
</a><br>
<br>

- Select `Skip` for the 'Let's customize your experience'.
<a href="./Media/Screenshot%202025-10-17%20141755%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20141755%20v2.png" height="370"/>
</a><br>
<br>

- Select `Skip` for integrating your mobile device.
<a href="./Media/Screenshot%202025-10-17%20141820%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20141820%20v2.png" height="370"/>
</a><br>
<br>

- Select `Not now` for syncing browsing data associated with your Microsoft account.
<a href="./Media/Screenshot%202025-10-17%20141849%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20141849%20v2.png" height="370"/>
</a><br>
<br>

- Select `Decline Microsoft 365`.
<a href="./Media/Screenshot%202025-10-17%20141907%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20141907%20v2.png" height="370"/>
</a><br>
<br>

- Select `Decline` for Microsoft 365 cloud storage.
<a href="./Media/Screenshot%202025-10-17%20141923%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20141923%20v2.png" height="370"/>
</a><br>
<br>

- Turn off `Yes, set up my email` for Outlook.
- Select `Next`.
<a href="./Media/Screenshot%202025-10-17%20142043%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20142043%20v2.png" height="370"/>
</a><br>
<br>

- Select `Skip` for Game Pass.
<a href="./Media/Screenshot%202025-10-17%20142104%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20142104%20v2.png" height="370"/>
</a><br>
<br>

- Microsoft will finish setup.
- Once you see the Windows desktop, installation is complete!!! <br>
<a href="./Media/Screenshot%202025-10-17%20142224%20v2.png">
  <img src="./Media/Screenshot%202025-10-17%20142224%20v2.png" height="370"/>
</a><br>

## 🎉 Congratulations!

You've successfully installed **Windows 11 Pro**! Your system is now ready for configuration, customization, and installing your favorite applications.

**Happy computing!** 🚀

<!--
***

# Appendix

## How to Disable Automatic Reboots caused by Windows Updates

<details>
  <summary>Expand for additional details.</summary>
<br>

- Guide for `How to Disable Automatic Reboots caused by Windows Updates` under development.

</details>

## How to Join Windows to a Microsoft Active Directory Domain

<details>
  <summary>Expand for additional details.</summary>
<br>

- Guide for `How to Join Windows to a Microsoft Active Directory Domain` under development.

</details>
-->
