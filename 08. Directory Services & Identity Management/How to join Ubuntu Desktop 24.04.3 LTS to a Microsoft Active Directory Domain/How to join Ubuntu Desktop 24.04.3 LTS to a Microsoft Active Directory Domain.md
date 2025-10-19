# How to join Ubuntu Desktop 24.04.3 LTS to a Microsoft Active Directory Domain.

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
