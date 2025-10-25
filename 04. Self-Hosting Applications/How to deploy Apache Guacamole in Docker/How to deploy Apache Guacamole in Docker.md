<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(3)%20-%20Apache%20Guacamole.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20Docker.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

# How to deploy Apache Guacamole in Docker

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

## Recommended Operating System / Docker Image

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu Desktop 24.04.x LTS</td>
  </tr>
  <tr>
    <td align="right">Container Runtime</td>
    <td>Docker (incl. Docker Compose)</td>
  </tr>
  <tr>
    <td align="right">Docker Image</td>
    <td>boschkundendienst https://github.com/boschkundendienst/guacamole-docker-compose</td>
  </tr>
</table>

Using `boschkundendienst/guacamole-docker-compose` gives you a production-ready, "batteries-included" deployment of Guacamole. This makes it especially valuable for homelab users, sysadmins, or small teams who want Guacamole up and running quickly without diving deep into manual config. <br>

Instead of manually configuring guacd + webapp + DB + SSL + proxy, you get: <br>
&emsp; > Preconfigured docker-compose stack <br>
&emsp; > Database auto-init <br>
&emsp; > SSL (self-signed or bring-your-own) <br>
&emsp; > Session recording <br>
&emsp; > Stable, pinned versions <br>

> ℹ️ **Note** <br>
> 
> If you need help deploying Ubuntu Desktop, please see my guide here, [How to install Ubuntu Desktop 24.04.3 LTS](../../01.%20Operating%20Systems/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS.md). <br>
> If you need help deploying Docker/Docker Compose, please see my guide here, [How to install Docker and Docker Compose](../../03.%20Virtual%20Machines%20%26%20Containers/How%20to%20install%20Docker%20and%20Docker%20Compose/How%20to%20install%20Docker%20and%20Docker%20Compose.md). <br>

## Deploy Apache Guacamole in Docker

***

### [1] Clone boschkundendienst's GitHub repository to your local machine.

&emsp; > The following commands will clone `boschkundendienst`'s GitHub repository to your local machine and navigate into the 'guacamole-docker-compose' directory. <br>
```bash
git clone "https://github.com/boschkundendienst/guacamole-docker-compose.git" && cd guacamole-docker-compose
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20161014%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20161014%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20161037%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20161037%20v2.png" height="270"/>
</a><br>

***

### [2] Make a backup copy of the docker-compose.yml file. 
```bash
cp docker-compose.yml docker-compose.yml_$(date +%Y.%m.%d_%H-%M-%S)
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164341%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164341%20v2.png" height="270"/>
</a><br>

***

### [3] Secure the docker-compose.yml file.

&emsp; > Because we'll be required to enter a password in plain text within the docker-compose.yml file, I recommend securing the file with the following command(s). The first command changes file ownership to the root user. The second command makes sure only the root user can read this file. That way, if anyone wanted to read this file, they'd need 'sudo' (root) permissions. <br>
```bash
sudo chown root:root docker-compose.yml && sudo chmod 600 docker-compose.yml
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164421%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164421%20v2.png" height="270"/>
</a><br>

***

### [4] Modify the docker-compose.yml file.

&emsp; > Modify/add passwords for `POSTGRES_PASSWORD:` and `POSTGRESQL_PASSWORD:` in the docker-compose.yml file. <br>
> ℹ️ To save changes in nano, select `Ctrl+x`, then `Shift+Y`, then `Enter`. <br>
```bash
sudo nano docker-compose.yml
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164422%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164422%20v2.png" height="270"/>
</a><br>
<br>

Example of `POSTGRES_PASSWORD:`. Don't forget to scroll down and also enter a password for `POSTGRESQL_PASSWORD:`:
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164600%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164600%20v2.png" height="270"/>
</a><br>

***

### [5] Deploy Apache Guacamole in Docker.

&emsp; > Run the 'prepare' script, then deploy Apache Guacamole using Docker Compose.
```bash
sudo ./prepare.sh
```
```bash
sudo docker compose up -d
```
> ℹ️ **Note** If the command above fails, try the following: 
> ```bash
> sudo docker-compose up -d
> ```
>
> `docker-compose` = Using Ubuntu repos. <br>
> `docker compose` = Using Official Docker repos.

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164719%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164719%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164919%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20164919%20v2.png" height="270"/>
</a><br>

***

### [6] Log in to Apache Guacamole.
```bash
https://ipAddress:8443/
```
Default username is `guacadmin` <br>
Default password is `guacadmin` <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165333%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165333%20v2.png" height="270"/>
</a><br>

&emsp; > Update/change the default password for guacadmin. <br>
&emsp;&emsp; > Select the dropdown menu for 'guacadmin' in the upper right-hand corner. <br>
&emsp;&emsp; > Select '`Settings`'. <br>
&emsp;&emsp; > Select '`Preferences`'. <br>
&emsp;&emsp; > Scroll down to view '`CHANGE PASSWORD`'. Here is where you can enter the relevant current and new password information. <br>
&emsp;&emsp; > When finished, select '`Update Password`'. <br>
&emsp;&emsp; > [*Optional*] Log out and then log back in with your new guacadmin password. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165349%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165349%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165430%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165430%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165442%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165442%20v2.png" height="270"/>
</a><br>

&emsp; > [*Optional*] Create a 'standard' (non-admin) level account for daily use. <br>
&emsp;&emsp; > Select the dropdown menu for 'guacadmin' in the upper right-hand corner. <br>
&emsp;&emsp; > Select '`Settings`'. <br>
&emsp;&emsp; > Select '`Users`'. <br>
&emsp;&emsp; > Select '`New User`'. <br>
&emsp;&emsp;&emsp; > Enter your desired username and password information. <br>
&emsp;&emsp;&emsp; > Enable the following permissions: <br>
&emsp;&emsp;&emsp;&emsp; > '`Create new connections`' <br>
&emsp;&emsp;&emsp;&emsp; > '`Create new connection groups`' <br>
&emsp;&emsp;&emsp;&emsp; > '`Change own password`' <br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165547%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165547%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165603%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165603%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165633%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165633%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165701%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-09%20165701%20v2.png" height="270"/>
</a><br>

***

### [7] Created new 'connections' and 'connection groups'.

> ℹ️ **Note**
>
> To exit or interact with a session, use the following keys: <br>
> `Ctrl+alt+Shift` for Windows. <br>
> `control+command+shift` for MAC. <br>

***

#### RDP

<details>
  <summary>Expand for additional details.</summary>
<br>
  
&emsp;&emsp; > Select the dropdown menu in the upper right-hand corner. <br>
&emsp;&emsp; > Select 'Settings'. <br>
&emsp;&emsp; > Select 'Connections'. <br>
&emsp;&emsp; > Select 'New Connection', fill out the following information. <br>
&emsp;&emsp;&emsp;&emsp; EDIT CONNECTION <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Name: `connectionName` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Protocol: `RDP` <br>
&emsp;&emsp;&emsp;&emsp; PARAMETERS > Network <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Hostname: `hostname` or `ip address` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Port: `3389` <br>
&emsp;&emsp;&emsp;&emsp; PARAMETERS > Authentication <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Username: `userName` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Password: `somePassword` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; (Optional) Domain: `yourDomain` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Security mode: `NLA (Network Level Authentication)` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `Ignore sever certificate` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `&emsp;&emsp;&emsp;&emsp; ` <br>
&emsp;&emsp;&emsp;&emsp; PARAMETERS > Performance <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `Enable wallpaper` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `Enable theming` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `Enable font smoothing (ClearType)`	<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `Enable full-window drag` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `Enable desktop composition (Aero)`	<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `Enable menu animations` <br>
&emsp;&emsp; > Scroll down, select `Save`. <br>

</details>

***

#### SSH / SFTP

<details>
  <summary>Expand for additional details.</summary>
<br>

<!-- in the future, add the option for using SSH keys only -->

&emsp;&emsp; > Select the dropdown menu in the upper right-hand corner. <br>
&emsp;&emsp; > Select 'Settings'. <br>
&emsp;&emsp; > Select 'Connections'. <br>
&emsp;&emsp; > Select 'New Connection', fill out the following information. <br>
&emsp;&emsp;&emsp;&emsp; EDIT CONNECTION <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Name: `connectionName` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Protocol: `SSH` <br>
&emsp;&emsp;&emsp;&emsp; PARAMETERS > Network <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Hostname: `hostname` or `ip address` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Port: `22` <br>
&emsp;&emsp;&emsp;&emsp; PARAMETERS > Authentication <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Username: `userName` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Password: `somePassword` <br>
&emsp;&emsp;&emsp;&emsp; PARAMETERS > Display <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Color scheme: `Green on black` <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Font size: `10` <br>
&emsp;&emsp;&emsp;&emsp; PARAMETERS > SFTP <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; Select `Enable SFTP` <br>
&emsp;&emsp; > Scroll down, select `Save`. <br>

</details>

***
