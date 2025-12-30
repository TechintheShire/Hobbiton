<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

## How to join Ubuntu Desktop 22.04.5 LTS to a Microsoft Active Directory Domain.

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
-->

### 📋 Prerequisites

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu Desktop 22.04.x LTS</td>
    <td><a href="../How%20to%20install%20Ubuntu%20Desktop%2022.04.5%20LTS/How%20to%20install%20Ubuntu%20Desktop%2022.04.5%20LTS.md">How to install Ubuntu Desktop 22.04.5 LTS</a></td>
  </tr>
</table>

> ℹ️ These steps assume your Active Directory (Domain Controller) is already properly set up and running. I'm using *Windows Server 2019* and these steps have worked for me every time. <br>
<br>

***
### [1] Update and upgrade your software packages.

```bash
sudo apt update && sudo apt upgrade -y
```
<br>

***
### [2] Install the software dependencies needed to join your Ubuntu machine to an Active Directory (AD) domain. <br>

```bash
sudo apt install -y realmd sssd-ad sssd-tools libnss-sss libpam-sss adcli samba-common-bin smbclient cifs-utils krb5-user
```
<br>

&emsp; When prompted to enter your realm, use the following syntax: <br>

```bash
YOURDOMAIN.COM
```

&emsp; Example: <br>

```bash
SPARTAN23.HOME
```
<br>

***
### [3] Discover your domain. This command uses DNS (and SRV records). <br>

```bash
realm discover yourdomain.com
```

&emsp; Example: <br>

```bash
realm discover spartan23.home
```
<br>

***
### [4] Join your domain. This does require an administrator-level account. <br>

```bash
sudo realm join yourdomain.com -U 'Administrator'
```

&emsp; Example:

```bash
sudo realm join spartan23.home -U 'Administrator'
```
<br>

***
### [5] Verify you have successfully joined the domain. <br>

```bash
realm list
```
<br>

***
### [6] If you've successfully joined the domain, you should be able to run the following command to pull user and group permissions for that Active Directory (AD) user. <br>

```bash
id yourdomain\\username
```

&emsp; Example: <br>

```bash
id spartan23.home\\thomas
```
<br>

***
### [7] Modify the 'PAM Configuration' to allow Ubuntu to create a home directory (/home/username) and persist your domain user's settings. To do this, we edit the 'PAM Configuration' file. <br>

&emsp; Create a backup of the 'common-session' file before making edits. <br>

```bash
sudo cp /etc/pam.d/common-session /etc/pam.d/common-session_$(date +%Y.%m.%d_%H-%M-%S)
```

&emsp; Use nano to open and edit the 'common-session' file. <br>

```bash
sudo nano /etc/pam.d/common-session
```

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

&emsp; Add this line at the bottom of the 'common-session' file, if it’s not already present: <br>

```bash
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
```
<br>

***
### [8] Enable 'sudo' rights your domain user. <br>

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

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

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

***
### [9] Now you can login using a domain user! These are the two formats you can use: <br>

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
> &emsp; ```ssh "thomas@spartan23.home"@viper"```
