<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

## How to install Ubuntu Desktop 24.04.3 LTS

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
-->

***

### Table of Contents

&emsp; [1] Download a free copy of the Ubuntu Desktop 24.04.3 LTS ISO. <br>
&emsp; [2] Install Ubuntu Desktop 24.04.3 LTS. <br>
&emsp; [3] (Optional) Set a static IP address. <br>
&emsp; [4] (Optional) Install OpenSSH server (openssh-server). <br>

&emsp; [#] Appendix <br>
&emsp; [#] (Optional) How to join Ubuntu Desktop 24.04.3 LTS to a Microsoft Active Directory Domain. <br>

***

### [1] Download a free copy of the Ubuntu Desktop 24.04.3 LTS ISO.

&emsp; Visit the following URL: <br>
```bash
https://ubuntu.com/download/desktop
```
&emsp; > Select '`Download`'. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20124204%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20124204%20v2.png" height="270"/>
</a><br>
<br>

***

### [2] Install Ubuntu Desktop 24.04.3 LTS.

&emsp; If you're installing Ubuntu Desktop 24.04.3 LTS on a Virtual Machine, mount the ISO to the Virtual Machine's CD/DVD drive. <br>

&emsp; If you're installing Ubuntu Desktop 24.04.3 LTS on a physical machine, you will need to burn the ISO to a bootable USB drive. I recommend `Rufus`. <br>

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
&emsp; Boot selection: '`ubuntu-24.04.3-desktop-amd64.iso`', use the 'SELECT' button to locate and select the ISO. <br>
&emsp; Under most circumstances, leave everything else default. <br>
&emsp; Select '`START`' to burn the Windows 11 ISO to your USB. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20125106%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20125106%20v2.png" height="270"/>
</a><br>

***

</details>

#

> ℹ️ In my example, I'm installing Ubuntu Desktop 24.04.3 LTS on a VMware Virtual Machine. <br>

&emsp; > Boot from your Ubuntu Desktop 24.04.3 LTS ISO: <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094516%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094516%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094621%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094621%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select your language, then '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094813%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094813%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select any accessibility aids, if needed; then '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094855%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094855%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select your keyboard layout, then '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094912%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094912%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select your method for connecting to the internet, then '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094932%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20094932%20v2.png" height="270"/>
</a><br>

***
&emsp; > If an update is available, select '`Update now`'. <br>
&emsp; > Then, select '`Close installer`'. <br> 
> ℹ️ Updating the installer will bring you back to the Ubuntu desktop. See the next step to restart the installer. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095003%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095003%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095033%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095033%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select/open the '`Install Ubuntu 24.04.3 LTS`' icon on the desktop to restart the Ubuntu Desktop installation process. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095055%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095055%20v2.png" height="270"/>
</a><br>

***
&emsp; > Reselect your desired '`language`', '`accessibility`', '`keyboard`', and '`internet connection`' settings. <br>

***
&emsp; > Select '`Interactive installation`', then '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095220%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095220%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Default selection`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095240%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095240%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select the following options: <br>
&emsp;&emsp; > '`Install third-party software for graphics and Wi-Fi hardware`'. <br>
&emsp;&emsp; > '`Download and install support for additional media formats`'. <br>
&emsp; > Then, select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095258%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095258%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select '`Erase disk and install Ubuntu`'. <br>
&emsp; > Then, select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095314%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095314%20v2.png" height="270"/>
</a><br>

***
&emsp; > Create an account for your Ubuntu machine. <br>
&emsp; > Assign a name (hostname) to your Ubuntu machine. <br>
&emsp; > Keep '`Require my password to log in`' checked. <br>
&emsp; > Select '`Next`'. <br>

> ℹ️ I skip steps on '`Use Active Directory`' here because most users won't be joining their Ubuntu machine to an existing Domain Controller/Active Directory. If that is something that is relevant to your environment (you have an existing Domain Controller/Active Directory), please see the Appendix section of this guide. <br>

> ℹ️ Assigning a name (hostname) will make identification, DNS, and self-hosting apps in the future easier. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095418%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095418%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select your timezone, then select '`Next`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095438%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095438%20v2.png" height="270"/>
</a><br>

***
&emsp; > Review your installation choices. <br>
&emsp; > When ready, select '`Install`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095454%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095454%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095511%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095511%20v2.png" height="270"/>
</a><br>

***
&emsp; > Once installation is complete, select '`Restart now`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095649%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095649%20v2.png" height="270"/>
</a><br>

***
&emsp; > When prompted, remove the installation media (ISO); then, hit '`ENTER`' on your keyboard. <br>

> ℹ️ Removing the installation media from your Ubuntu machine is as simple as 'disabling' the CD/DVD drive on your Virtual Machine or pulling the USB drive from your physical machine. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095719%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095719%20v2.png" height="270"/>
</a><br>

***
&emsp; > Once Ubuntu has finished rebooting, you'll see a login screen. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095816%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20095816%20v2.png" height="270"/>
</a><br>

***

### [3] (Optional) Set a static IP address.

> ℹ️ If you plan on self-hosting applications on this Ubuntu machine, it is recommended to set a static IP address to ensure easy and consistent access. <br>

&emsp; **[3.1] [Option 1] Set a static IP address via Ubuntu's Network Settings.** <br>

&emsp; > Open the '`System Menu`' (in the upper right-hand corner). <br>
&emsp; > Select '`Settings`' (gear icon). <br>
&emsp; > Select '`Network`'. <br>
&emsp; > Select '`Network Settings`' (gear icon, under 'Wired'). <br>
&emsp; > Select the '`IPv4`' tab. <br>
&emsp; > Select the '`Manual`' radio button. <br>
&emsp; > Fill out IP address and DNS information. <br>
&emsp; > Select '`Apply`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155223%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155223%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155248%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155248%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155405%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155405%20v2.png" height="270"/>
</a><br>
<br>

&emsp; **[3.2] [Option 2] Assign a "static" IP address via a 'DHCP static reservation' (typically your router).** <br>

&emsp;&emsp; Assigning a “static” IP via a DHCP reservation uses your machine’s network adapter MAC address. <br>

&emsp;&emsp; Find your MAC address with these steps. <br>
&emsp;&emsp;&emsp; > Open the '`System Menu`' (in the upper right-hand corner). <br>
&emsp;&emsp;&emsp; > Select '`Settings`' (gear icon). <br>
&emsp;&emsp;&emsp; > Select '`Network`'. <br>
&emsp;&emsp;&emsp; > Select '`Network Settings`' (gear icon, under 'Wired'). <br>
&emsp;&emsp;&emsp; > View the '`Details`' tab, looking for the '`Hardware Address`' (MAC address). <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155223%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155223%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155248%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155248%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp; > Here is an example of what assigning a "static" IP address via a 'DHCP static reservation' looks like on pfSense. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155438%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155438%20v2.png" width="360"/>
</a><br>
<br>

***

### [4] (Optional) Install OpenSSH server (openssh-server).

&emsp; > Open a command prompt (terminal). <br>
&emsp; > Run the following commands. <br>
```bash
sudo apt update
sudo apt upgrade -y
sudo apt install -y openssh-server
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155618%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-19%20155618%20v2.png" height="270"/>
</a><br>
<br>

<br>

***

## Appendix

### (Optional) How to join Ubuntu Desktop 24.04.3 LTS to a Microsoft Active Directory Domain.

<details>
  <summary>Expand for additional details.</summary>
<br>

These steps assume your Active Directory (Domain Controller) is already properly setup and running. I'm using Windows Server 2019 and these steps worked every time for me. <br>

[1] Update and upgrade your software packages.
```bash
sudo apt update && sudo apt upgrade -y
```

[2] Install the software dependencies needed to join your Ubuntu machine to an Active Directory (AD) domain. <br>
```bash
sudo apt install -y realmd sssd sssd-tools adcli samba-common-bin oddjob oddjob-mkhomedir packagekit
```

[3] Discover your domain. This command uses DNS (and SRV records). <br>
```bash
realm discover yourdomain.com
```
&emsp; Example: <br>
```bash
realm discover spartan23.home
```

[4] Join your domain. This does require an administrator-level account. <br>
```bash
sudo realm join yourdomain.com -U 'Administrator'
```
&emsp; Example:
```bash
sudo realm join spartan23.home -U 'Administrator'
```

[5] Verify you have successfully joined the domain. <br>
```bash
realm list
```

[6] If you've successfully joined the domain, you should be able to run the following command to pull user and group permissions for that Active Directory (AD) user. <br>
```bash
id yourdomain\\username
```
&emsp; Example: <br>
```bash
id spartan23.home\\thomas
```

[7] Modify the 'PAM Configuration' to allow Ubuntu to create a home directory (/home/username) and persist your domain user's settings. To do this, we edit the 'PAM Configuration' file. <br>
&emsp; Create a backup of the 'common-session' file before making edits. <br>
```bash
sudo cp /etc/pam.d/common-session /etc/pam.d/common-session_$(date +%Y.%m.%d_%H-%M-%S)
```
&emsp; Use nano to open and edit the 'common-session' file. <br>
```bash
sudo nano /etc/pam.d/common-session
```
&emsp; Add this line at the bottom of the 'common-session' file, if it’s not already present: <br>
```bash
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
```

[8] Enable 'sudo' rights your domain user. <br>
&emsp; Create a new file where we'll specify our sudo permissions for this domain user. <br>
```bash
sudo touch /etc/sudoers.d/username
```
&emsp; Example: <br>
```bash
sudo touch /etc/sudoers.d/thomas
```
&emsp; Use nano to open and edit our newly created file. <br>
```bash
sudo nano /etc/sudoers.d/username
```
&emsp; Example: <br>
```bash
sudo nano /etc/sudoers.d/thomas
```
&emsp; Add this line of text to the file we just created. <br>
```bash
user@yourdomain.com ALL=(ALL:ALL) ALL
```
&emsp; Example: <br>
```bash
thomas@spartan23.home ALL=(ALL:ALL) ALL
```
&emsp; Save and close the file. <br>
<br>

[9] Now you can log in using a domain user! These are the two formats you can use: <br>
```bash
DOMAIN\username
```
```bash
username@domain.com
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20120809%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20120809%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20120850%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20120850%20v2.png" height="270"/>
</a><br>
<br>

> ℹ️ **Note** <br>
>
> To SSH into a domain user account, use the following syntax:
>
> &emsp; ssh "domain-user@yourdomain.com"@hostname
>
> &emsp; ssh "domain-user@yourdomain.com"@ip_address
> 
> Example: <br>
> &emsp; ```ssh "thomas@spartan23.home"@viper```

</details>
