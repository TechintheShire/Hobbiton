<a href="./Icons%20and%20Screenshots/20250805_110313.png">
  <img src="./Icons%20and%20Screenshots/20250805_110313.png" height="170"/>
</a>

# How to install Ubuntu Desktop 24.04.2 LTS

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
-->

### [1] Download a free copy/ISO of Ubuntu Desktop 24.04.2 LTS.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Open https://ubuntu.com/download/desktop in your browser. <br>
&emsp; > Select 'Download'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120001%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120001%20v2.png" height="470"/>
</a><br>

&emsp; > Your ISO should look similar to the following. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120045%20v2.png" height="470"/>
</a><br>

</details>

### [2] Install Ubuntu Desktop 24.04.2 LTS on your target machine.

<details>
  <summary>Expand for additional details.</summary>

***
> ℹ️ If you are installing Ubuntu on a physical machine, you will need to burn the Ubuntu ISO to a bootable USB. I recommend using Rufus, https://rufus.ie/en/ . <br>

<details><summary> Expand this section for steps on using Rufus. </summary>
<br>

&emsp; > Download Rufus. In my example, I use the 'portable' version for Windows x64 (64-bit). <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120600%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120600%20v2.png" height="470"/>
</a><br>

&emsp; > Here is what the downloaded .exe looks like. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120615%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120615%20v2.png" height="470"/>
</a><br>

&emsp; > Double-click the .exe to start Rufus. <br>
&emsp; > I recommend allowing Rufus to check for updates. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120630%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120630%20v2.png" height="470"/>
</a><br>

&emsp; > If Rufus finds updates, select 'Yes' to accept and install them. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120645%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120645%20v2.png" height="470"/>
</a><br>

&emsp; > Select your ISO, in our case, the Ubuntu Desktop ISO. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120700%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120700%20v2.png" height="470"/>
</a><br>

&emsp; > Once all of your desired settings are in place and you're ready to burn the ISO to your USB, select 'START'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120715%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120715%20v2.png" height="470"/>
</a><br>

&emsp; > I select 'OK' here to proceed with the recommended write mode. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120730%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120730%20v2.png" height="470"/>
</a><br>

&emsp; > **Read this warning carefully**, all data on your target USB will be overwritten. Select 'OK' to proceed. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120745%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120745%20v2.png" height="470"/>
</a><br>

&emsp; > You can monitor the process here. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120800%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120800%20v2.png" height="470"/>
</a><br>

&emsp; > Once complete, the tool should show a green status bar with 'READY'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120815%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120815%20v2.png" height="470"/>
</a><br>

&emsp; > From here, you'd close Rufus, safely eject your USB, insert the USB into your target machine, boot from the USB, and follow the installation instructions.

</details>

***

&emsp; In this guide, I'll be installing Ubuntu Desktop 24.04.2 LTS on a VMware ESXi Virtual Machine (VM). Whenever possible, I recommend Virtual Machines (VMs) because it enables you to take VM-level snapshots and roll back to a known good state in the event that any task goes wrong or breaks something. There are plenty of great hypervisors on the market. I encourage you to do your own research and find one that meets your needs. I would comfortably recommend Proxmox, XCP-NG, TrueNAS, and unRAID.

> ⚠️ **Issues with the 24.04.2 LTS installer**  
>
> For some reason, many users are experiencing unexpected behavior and failed installs for this version (24.04.2 LTS). I could not get the install to complete successfully until I selected the 'Do not connect to the internet' option. No matter what I tried, if this option wasn't selected, my install would fail towards the end. After selecting this option, every install I attempted (regardless of which options I chose throughout the installation process), it succeeded. <br>
>
> *More details around this option can be found later in this guide. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120215%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120215%20v2.png" height="470"/></a><br>

***
&emsp; > Boot from your Ubuntu ISO. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120100%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120115%20v2.png" height="470"/>
</a><br>

***
&emsp; > Depending on your situation, the ISO may boot into the desktop mode. If so, find and select 'install' Ubuntu. If the ISO boots directly into the installer/wizard, continue from here. <br>

&emsp; > Select your language. <br>
&emsp; > Then select, 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120130%20v2.png" height="470"/>
</a><br>

***
&emsp; > If you need any 'accessibility' features enabled, select them here. <br>
&emsp; > Then select 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120145%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select your keyboard layout. <br>
&emsp; > Then select 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120200%20v2.png" height="470"/>
</a><br>

***
&emsp; > ⚠️ The only way I could get this installation to complete successfully was to select '*Do not connect to the internet*'. For this reason, please select this option before continuing to avoid any installation issues. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120215%20v2.png" height="470"/>
</a><br>

***
&emsp; > In my process, I select 'Skip' here. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120230%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Install Ubuntu'. <br>
&emsp; > Then select, 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120245%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Interactive installation', which will allow us to customize our installation. <br>
&emsp; > Then select, 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120300%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Extended selection', which will install additional tools and utilities. <br>
&emsp; > Then select, 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120315%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Install third-party software for graphics and Wi-Fi hardware'. <br>
&emsp; > Select 'Download and install support for additional media formats'. <br>
&emsp; > Then select, 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120330%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120330%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select 'Erase disk and install Ubuntu'. <br>
&emsp; > Then select, 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120345%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120345%20v2.png" height="470"/>
</a><br>

***
> ⚠️ **'Use Active Directory' (join Active Directory) does not appear to work within the installer.**  
>
> If you use Active Directory in your environment and want to join your Ubuntu machine to it, please see the 'Appendix' section towards the end of this guide. In that section, I outline the manual steps to join Ubuntu Desktop 24.04.2 LTS to Active Directory.

&emsp; > Enter your account information and set your 'computer's name' (hostname). <br>
&emsp; > Then select, 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120400%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120400%20v2.png" height="470"/>
</a><br>

***
&emsp; > Select your timezone. <br>
&emsp; > Then select, 'Next'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120415%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120415%20v2.png" height="470"/>
</a><br>

***
&emsp; > Review your installation choices. <br>
&emsp; > If everything looks good, select 'Install' to proceed. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120430%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120430%20v2.png" height="470"/>
</a><br>

***
&emsp; > Here, you can monitor the installation progress. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120445%20v2.png" height="470"/>
</a><br>

***
&emsp; > Once the installation completes, you'll need to restart your Ubuntu machine. <br>
&emsp; > Select 'Restart now' to reboot. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120500%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120500%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120515%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120515%20v2.png" height="470"/>
</a><br>

***
&emsp; > Once the reboot is complete, you should see the login screen. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120530%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120530%20v2.png" height="470"/>
</a><br>

***

</details>

### [3] Post-install (Personalization and Customization)

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Ensure your OS/software is up to date by running the following commands. <br>

```bash
sudo apt update
```
```bash
sudo apt upgrade -y
```

> ℹ️ **Note** <br>
> If you prefer upgrading your OS/software via the Desktop/GUI, you can use the 'Software Updater'.
>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121000%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121000%20v2.png" height="470"/></a><br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121145%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121145%20v2.png" height="470"/></a><br>

&emsp; I like to install 'OpenSSH Server' to allow SSH logins. If you are concerned about security, there are methods to disable password logins for SSH and use SSH keys.

	sudo apt install -y openssh-server

From here, I recommend doing some post-install cleanup and configuration based on your personal preferences: <br>
&emsp; > Set when your screen 'blanks' / locks. <br>
&emsp;&emsp;&emsp; Settings > Power > Power Saving > Screen Blank <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121115%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121130%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Unpin any apps you don't want on your dash (taskbar). <br>
&emsp; > Pin any apps you would like on your dash. <br>
&emsp; > Set your desktop background. <br>
&emsp;&emsp;&emsp; Settings > Appearance > Background <br>
&emsp; > Set your Avatar (user) picture. <br>
&emsp;&emsp;&emsp; Settings > System > Users > Select 'Change Avatar' by hovering over your Avatar picture. <br>

</details>

### [4] Set a static IP address for your Ubuntu machine.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> If you plan on self-hosting any applications on this Ubuntu machine, it is recommended to set a static IP address to ensure easy and consistant access. <br>

> ℹ️ **Note** <br>
> It is recommended to modify your router's DHCP range to exclude any IP addresses you wish to assign as static. Doing so will help avoid 'IP address conflicts'. An 'IP address conflict' occurs when two servers/machines are assigned the same IP address. This situation can cause communication failures and disrupt network operations, leading to connectivity problems, intermittent network access, and poor performance. <br><br>
> Here is an example of what this would like under pfsense. My DHCP Server will only hand out addresses between 192.168.50.21 through 192.168.50.100, which allows me to safely use any IP address outside of this range as a static IP address: <br><br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120545%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20120545%20v2.png" height="470"/></a><br>

***

> ⚠️ **Verify your static IP address before setting it!!!**
>
> Before setting a static IP address, it is recommended to verify whether or not that IP address is already in use. Taking the time to check will help avoid any 'IP address conflicts'. <br>
>
> To check this, we do the following: <br>
> &emsp; > Ubuntu Start Menu (by default, in the lower left-hand corner). <br>
> &emsp; > Type/search for 'Terminal' to find and open the Terminal app. <br>
> &emsp; > In the terminal window, run the following command, replacing 111.222.333.444 with your IP address: <br>
>
	ping -c 4 111.222.333.444
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121230%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121230%20v2.png" height="470"/></a><br>
> If you get a reply, that means the IP address is in use and you should choose a different IP address. <br>
> If you do NOT get a reply, that IP address should be safe to use. <br>

***

#### [4A] [Option 1] Set your static IP address via Ubuntu Network Settings.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > System Menu (in the upper right-hand corner) <br>
&emsp; > Settings (gear icon) <br>
&emsp; > Network <br>
&emsp; > Network Settings (gear icon, under 'Wired') <br>
&emsp; > Select the 'IPv4' tab. <br>
&emsp; > Select the 'Manual' radio button. <br>
&emsp; > Fill out Address and DNS information. <br>
&emsp; > Select 'Apply'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121200%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121215%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121245%20v2.png" height="470"/>
</a><br>

</details>

#### [4B] [Option 2] Assign a "static" IP address via a DHCP Server (typically your router).

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; This method is often refered to as a 'DHCP static reservation'. This method tells your DHCP Server to assign a specific IP address any time it sees a specific MAC address. If we use this method, any time our DHCP Server sees the MAC address for our Ubuntu machine, it will assign the IP address that we specified. <br>

How to find MAC address via Settings: <br>
&emsp; > System Menu (in the upper right-hand corner) <br>
&emsp; > Settings (gear icon) <br>
&emsp; > Network <br>
&emsp; > Network Settings (gear icon, under 'Wired') <br>
&emsp; > Under the 'Details' tab, view 'Hardware Address' (MAC Address) <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121330%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121330%20v2.png" height="470"/>
</a><br>
<br>

How to find your MAC address via Terminal: <br>
&emsp; > Ubuntu Start Menu (by default, in the lower left-hand corner). <br>
&emsp; > Type/search for 'Terminal' to find and open the Terminal app. <br>
&emsp; > In the terminal window, run the following command. <br>

	ip address

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121315%20v2.png" height="470"/>
</a><br>
<br>

&emsp; Here is an example for pfsense. Your router's web interface will look different but the methodolgy is the same. By setting a static mapping on your DHCP Server, any time your DHCP Server sees this MAC address, it will assign the specified IP address. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121345%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121345%20v2.png" height="470"/>
</a><br>

</details>

</details>

### [5] Reboot your Ubuntu machine and verify your IP address and host name.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; This step is helpful to ensure your hostname / IP address are set and stay assigned correctly. <br>

Verify IP address via Terminal (CLI): <br>
&emsp; > Ubuntu Start Menu (by default, in the lower left-hand corner). <br>
&emsp; > Type/search for 'Terminal' to find and open the Terminal app. <br>
&emsp; > In the terminal window, run the following command. <br>

	ip address

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121300%20v2.png" height="470"/>
</a><br>
<br>

Verify hostname via Terminal (CLI): <br>
&emsp; > Ubuntu Start Menu (by default, in the lower left-hand corner). <br>
&emsp; > Type/search for 'Terminal' to find and open the Terminal app. <br>
&emsp; > In the terminal window, run the following command. <br>

	hostname

 <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121445%20v2.png" height="470"/>
</a><br>
<br>

Verify IP address via Settings: <br>
&emsp; > System Menu (in the upper right-hand corner) <br>
&emsp; > Settings (gear icon) <br>
&emsp; > Network <br>
&emsp; > Network Settings (gear icon, under 'Wired') <br>
&emsp; > Under the 'Details' tab, view 'IP Address'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121400%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121400%20v2.png" height="470"/>
</a><br>
<br>

Verify hostname via Settings: <br>
&emsp; > System Menu (in the upper right-hand corner) <br>
&emsp; > Settings (gear icon) <br>
&emsp; > System <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121430%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20121430%20v2.png" height="470"/>
</a><br>

</details>

***

# Appendix

### (Optional) How to join Ubuntu Desktop 24.04.2 LTS to a Microsoft Active Directory Domain.

<details>
  <summary>Expand for additional details.</summary>
<br>

These steps assume your Active Directory (Domain Controller) is already properly setup and running. I'm using Windows Server 2019 and these steps worked every time for me. <br>

[1] Update and upgrade your software packages.

```bash
sudo apt update && sudo apt upgrade -y
```

[2] Install the software dependancies needed to join your Ubuntu machine to an Active Directory (AD) domain. <br>

	sudo apt install -y realmd sssd sssd-tools adcli samba-common-bin oddjob oddjob-mkhomedir packagekit

[3] Discover your domain. This command uses DNS (and SRV records). <br>

	realm discover yourdomain.com

&emsp; Example: <br>
	
 	realm discover spartan23.home

[4] Join your domain. This does require an administrator-level account. <br>

	sudo realm join yourdomain.com -U 'Administrator'

&emsp; Example:

 	sudo realm join spartan23.home -U 'Administrator'

[5] Verify you have successfully joined the domain. <br>

	realm list

[6] If you've successfully joined the domain, you should be able to run the following command to pull user and group permissions for that Active Directory (AD) user. <br>

	id yourdomain\\username

&emsp; Example: <br>

	id spartan23.home\\thomas

[7] Modify the 'PAM Configuration' to allow Ubuntu to create a home directory (/home/username) and persist your domain user's settings. To do this, we edit the 'PAM Configuration' file. <br>

&emsp; Create a backup of the 'common-session' file before making edits. <br>

	sudo cp /etc/pam.d/common-session /etc/pam.d/common-session_$(date +%Y.%m.%d_%H-%M-%S)

&emsp; Use nano to open and edit the 'common-session' file. <br>

	sudo nano /etc/pam.d/common-session

&emsp; Add this line at the bottom of the 'common-session' file, if it’s not already present: <br>

	session required pam_mkhomedir.so skel=/etc/skel/ umask=0022

[8] Enable 'sudo' rights your domain user. <br>

&emsp; Create a new file where we'll specify our sudo permissions for this domain user. <br>

	sudo touch /etc/sudoers.d/username

&emsp; Example: <br>

	sudo touch /etc/sudoers.d/thomas

&emsp; Use nano to open and edit our newly created file. <br>

	sudo nano /etc/sudoers.d/username

&emsp; Example: <br>

 	sudo nano /etc/sudoers.d/thomas

&emsp; Add this line of text to the file we just created. <br>

	user@yourdomain.com ALL=(ALL:ALL) ALL

&emsp; Example: <br>

	thomas@spartan23.home ALL=(ALL:ALL) ALL

&emsp; Save and close the file. <br>
<br>

[9] Now you can login using a domain user! These are the two formats you can use: <br>

```bash
DOMAIN\username
```
```bash
username@domain.com
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20120809%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20120809%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20120850%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20120850%20v2.png" height="470"/>
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
