<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(3)%20-%20PLEX.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20Docker.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

## How to deploy PLEX in Docker

***

### Table of Contents

&emsp; [01] Create a PLEX account. <br>
&emsp; [02] Create application directories and mount points for PLEX / Docker. <br>
&emsp; [03] Create directories and mount points for PLEX media file storage. <br>
&emsp; [04] Create and prepare a Docker Compose yaml (.yml) file for PLEX. <br>
&emsp; [05] Deploy PLEX in Docker. <br>
&emsp; [06] Sign in and initialize PLEX. <br>
&emsp; [07] Activate (enable) Two-Factor Authentication (2FA). <br>
&emsp; [08] How to Add Libraries. <br>
&emsp; [09] How to Remove Libraries. <br>
&emsp; [10] (Optional) Enable 'Remote Access'. <br>
&emsp; [11] Configure PLEX media server Settings. <br>

&emsp; [#] Appendix <br>
&emsp; [#] Upgrading PLEX (Docker version) <br>
&emsp; [#] Uninstall PLEX <br>

***

### Recommended Operating System / Docker Image
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
    <td>LinuxServer.io https://github.com/linuxserver/docker-plex</td>
  </tr>
</table>

> ℹ️ **Note** <br>
> 
> If you need help deploying Ubuntu Desktop, please see my guide here, [How to install Ubuntu Desktop 24.04.3 LTS](../../01.%20Operating%20Systems/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS.md). <br>
> If you need help deploying Docker/Docker Compose, please see my guide here, [How to install Docker and Docker Compose](../../03.%20Virtual%20Machines%20%26%20Containers/How%20to%20install%20Docker%20and%20Docker%20Compose/How%20to%20install%20Docker%20and%20Docker%20Compose.md). <br>
> 
> PLEX offers an official Docker image, if you're interested in exploring that option, https://github.com/plexinc/pms-docker <br>

### Helpful Official Links from PLEX
&emsp; General Requirements <br>
&emsp;&emsp; https://support.plex.tv/articles/200375666-plex-media-server-requirements/ <br>
&emsp; Recommended CPU(s) <br>
&emsp;&emsp; https://support.plex.tv/articles/201774043-what-kind-of-cpu-do-i-need-for-my-server/ <br>
&emsp; Hardware Acceleration (Transcoding) (CPU/GPU) <br>
&emsp;&emsp; https://support.plex.tv/articles/115002178853-using-hardware-accelerated-streaming/ <br>
&emsp; Naming and Organizing your Movie media files <br>
&emsp;&emsp;https://support.plex.tv/articles/naming-and-organizing-your-movie-media-files/ <br>
&emsp; Naming and Organizing your TV Show files <br>
&emsp;&emsp; https://support.plex.tv/articles/naming-and-organizing-your-tv-show-files/ <br>

***
### [1] Create a PLEX account.

&emsp; > Open https://www.plex.tv/ in your browser. <br>
&emsp; > Select 'Sign Up Free' and create your account. <br>

> ℹ️ Here is a feature comparison between the 'free' vs 'PLEX Pass' licensing options offered by PLEX. <br>
> https://www.plex.tv/plans/#product-features

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161117%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161117%20v2.png" height="270"/>
</a><br>

***
### [2] Create application directories and mount points for PLEX / Docker.

For the commands listed throughout this guide, we'll be using Ubuntu's terminal. <br>
&emsp; > Open the '`Show Apps`' menu (by default, in the bottom left-hand corner). <br>
&emsp; > Use the search bar to search '`terminal`'. <br>
&emsp; > Open a terminal session. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161159%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161159%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161223%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161223%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161239%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161239%20v2.png" height="270"/>
</a><br>

<br>

&emsp; > cd (Change Directory) back to your user's home directory. <br>
```bash
cd ~ && pwd
```
&emsp; > Create base application directories for PLEX. <br>
```bash
mkdir -p ~/plex
mkdir -p ~/plex/config
mkdir -p ~/plex/media
```
&emsp; config → is where we'll store PLEX’s application/config data. <br>
&emsp; media → is where we'll store all our Movies, TV, Music, etc. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161359%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161359%20v2.png" height="270"/>
</a><br>

&emsp; These screenshots show what the directory structure should look like. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161436%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161436%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161454%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161454%20v2.png" height="270"/>
</a><br>

***
### [3] Create directories and mount points for PLEX media file storage.

#

&emsp; **[Option 1] Store your media files locally, under the ~/plex/media directory.**

<details>
  <summary>Expand for additional details.</summary>
<br>

```bash
mkdir -p ~/plex/media/movies
mkdir -p ~/plex/media/tv
mkdir -p ~/plex/media/music
```

&emsp; This way your directory tree looks like: <br>

~/plex/ <br>
&emsp; ├── config/ <br>
&emsp; └── media/ <br>
&emsp;&emsp;&emsp;&emsp; ├── movies/ <br>
&emsp;&emsp;&emsp;&emsp; ├── tv/ <br>
&emsp;&emsp;&emsp;&emsp; └── music/ <br>

</details>

#

&emsp; **[Option 2] Mount your media files from an external NAS SMB share, under the ~/plex/media directory.**

<details>
  <summary>Expand for additional details.</summary>
<br>

This section will cover mounting your NAS SMB share(s) to your Ubuntu machine when it boots (or reboots!!!). <br>

> ⚠️ Unfortunately, mount.cifs does not support hashed passwords. For this reason, we need to store our username/password in a plain text file. If you're the only user on this machine, it shouldn't be an issue. We will be securing the text file by only allowing root access. However, anyone else with an account that has 'sudo' privileges on your machine could read your plain text username/password file. <br>

&emsp; > Upgrade Ubuntu and related Software packages. <br>
```bash
sudo apt update && sudo apt upgrade -y
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161608%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161608%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Install software dependencies that will allow us to mount SMB shares. <br>
```bash
sudo apt install cifs-utils keyutils
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161841%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161841%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Create a credentials file. This file will be used to securely store our username and password for the SMB share. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">sudo touch /etc/samba/creds-userName</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">sudo touch /etc/samba/creds-artemis</code></pre>
    </td>
  </tr>
</table>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161948%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20161948%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Edit the credentials file, adding username and password information, see below. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">sudo nano /etc/samba/creds-userName</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">sudo nano /etc/samba/creds-artemis</code></pre>
    </td>
  </tr>
</table>

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162020%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Add your user's information to this 'creds-userName' file. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">username=yourUsername
password=somePassword</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">username=artemis
password=somePassword</code></pre>
    </td>
  </tr>
</table>

> ℹ️ If you are using Active Directory, be aware of how you specify your domain information; For example, my Active Directory domain is 'spartan23.home'. When I tried using 'spartan23.home', my mount commands wouldn't work; however, when using 'spartan23', they did. <br>
> 
> Example: <br>
> ```bash
> username=artemis
> password=somePassword
> domain=spartan23
> ```
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162055%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162055%20v2.png" height="270"/></a><br>
<br>

&emsp; > Modify permissions to this file so that only 'root' can access it. This makes it much more secure. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">sudo chmod 600 /etc/samba/creds-userName</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">sudo chmod 600 /etc/samba/creds-artemis</code></pre>
    </td>
  </tr>
</table>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162337%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162337%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Create a subdirectory under ~/plex/media for any SMB shares you want to mount to your Ubuntu machine. This way, you can expand and add more SMB shares in the future, if needed. <br>

> ℹ️ My NAS server's name is 'apollo' and the SMB share is 'Media'. <br>

<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">mkdir -p ~/plex/media/nasServer_smbShare</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">mkdir -p ~/plex/media/apollo_Media</code></pre>
    </td>
  </tr>
</table>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162426%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162426%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > This command is used to test and ensure you can successfully mount your SMB share before we modify our /etc/fstab file. <br>

> ⚠️ **Warning** <br>
>
> Do not skip this step!!! You should make sure your mount commands and permissions are working as expected before modifying the /etc/fstab. Misconfiguration within the fstab file could cause the system to fail booting. <br>

&emsp; Syntax: <br>
```bash
sudo mount -t cifs //nasServer/smbShare /home/user/plex/media/nasServer_smbShare -o credentials=/etc/samba/creds-userName,uid=$(id -u),gid=$(id -g),vers=3.1.1
```
&emsp; Example: <br>
```bash
sudo mount -t cifs //apollo/Media /home/artemis@spartan23.home/plex/media/apollo_Media -o credentials=/etc/samba/creds-artemis,uid=$(id -u),gid=$(id -g),vers=3.1.1
```
<br>

&emsp; > If the mount command is successful, verify that you can view the data within the SMB share mounted to your Ubuntu machine. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">ll ~/plex/media/nasServer_smbShare</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">ll ~/plex/media/apollo_Media</code></pre>
    </td>
  </tr>
</table>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162531%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162531%20v2.png" height="270"/>
</a><br>
<br>

Now you're ready to edit the /etc/fstab file, which controls what filesystems partitions are mounted during boot, whether they're local filesystem partitions or, in our case, external SMB shares. <br>

&emsp; > I recommend making a backup copy of the fstab file before making any edits. Misconfiguration within the fstab file could cause the system to fail booting. <br>
```bash
sudo cp /etc/fstab /etc/fstab_$(date +%Y.%m.%d_%H-%M-%S)
```
```bash
ll /etc/ | grep -i fstab*
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162730%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162730%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162833%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20162833%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now we're ready to edit the fstab file. <br>
```bash
sudo nano /etc/fstab
```

> ℹ️ To save changes in nano, select `Ctrl+x`, then `Shift+Y`, then `Enter`. <br>

&emsp; > Add the following line at the bottom of your fstab (replacing any variables to match your environment, see syntax below for additional guidance). <br>

> ⚠️ Unfortunately, /etc/fstab does NOT support `uid=$(id -u)` `gid=$(id -g)` variables. They must be entered manually. To find your 'user ID' and 'group ID', run the following commands: 
> ```bash
> id -u
> ```
> ```bash
> id -g
> ```
&emsp; Syntax: <br>
```bash
//fileserver/shareName /path/to/mountPoint cifs credentials=/etc/samba/creds-userName,uid=userID,gid=groupID,vers=3.1.1,_netdev,nofail 0 0
```
&emsp; Example: <br>
```bash
//apollo/Media /home/artemis@spartan23.home/plex/media/apollo_Media cifs credentials=/etc/samba/creds-artemis,uid=1171601103,gid=1171600513,vers=3.1.1,_netdev,nofail 0 0
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163139%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163139%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163313%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163313%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now we can verify the fstab was successfully modified by running the following mount commands.
```bash
sudo systemctl daemon-reload
```
```bash
sudo mount -a
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163356%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163356%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > To truly test that things are working properly, reboot your Ubuntu machine and verify the SMB shares successfully mounted to the directory you specified. If you have multiple SMB shares you'd like to mount, simply repeat the steps above for each respective SMB share. <br>

</details>

#

***
### [4] Create and prepare a Docker Compose yaml (.yml) file for PLEX.

&emsp; > Create a Docker Compose yaml (.yml) file. <br>

> ℹ️ **Note** <br>
> 
> Make sure your Docker Compose yaml (.yml) file is named appropriately. <br>
>
> Supported filenames: <br>
> &emsp; docker-compose.yml <br>
> &emsp; docker-compose.yaml <br>
> &emsp; compose.yml <br>
> &emsp; compose.yaml <br>

```bash
cd ~/plex
```
```bash
touch docker-compose.yml
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163626%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163626%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Edit the Docker Compose yaml (.yml) file using nano. *Note: If you're using Ubuntu Desktop, you can also open this file with Ubuntu's text editor, which may be easier. <br>
```bash
nano docker-compose.yml
```

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163722%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163722%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Copy and paste the syntax below into your Docker Compose yaml (.yml) file replacing variables depending on your environment. <br>

&emsp; Draft Syntax: <br>
```bash
---
services:
  plex:
    image: lscr.io/linuxserver/plex:latest
    container_name: plex
    network_mode: host
    environment:
      - PUID=userID      # find by running 'id -u'
      - PGID=groupID     # find by running 'id -g'
      - TZ=Etc/UTC       # https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List
      - VERSION=docker
      - PLEX_CLAIM=      # optional https://www.plex.tv/claim
    volumes:
      - /path/to/plex/config:/config
      - /path/to/tvseries:/tv
      - /path/to/movies:/movies
    restart: unless-stopped
```

> ℹ️ PLEX Claim tokens usually expire within 4-5 minutes. I'd recommend waiting to generate your PLEX Claim token until you're ready to quickly copy/paste the token into your yaml (.yml) file, save it, and then deploy PLEX via the Docker Compose command. <br>

```bash
https://www.plex.tv/claim
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163901%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163901%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163937%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20163937%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Here is an example of my Docker Compose yaml (.yml) file: <br>
<!-- include a config/mapping for transcode to land on SMB share? -->
```bash
---
services:
  plex:
    image: lscr.io/linuxserver/plex:latest
    container_name: plex
    network_mode: host
    environment:
      - PUID=1171601103
      - PGID=1171600513
      - TZ=America/New_York
      - VERSION=docker
      - PLEX_CLAIM=claim-r1zMSK-x7F38-bUbr1Gs
    volumes:
      - /home/artemis@spartan23.home/plex/config:/config
      - /home/artemis@spartan23.home/plex/media:/media_plex
    restart: unless-stopped
```

***
### [5] Deploy PLEX in Docker.
  
&emsp; > Ensure you're in the same directory where the docker-compose.yml file was created. <br>
```bash
cd ~/plex
```
&emsp; > Run the following command to deploy PLEX into Docker. This command will search within the directory it was run for a file named 'docker-compose.yml' (or other supported filenames, as previously outlined) and deploy the specified configuration. <br>
```bash
sudo docker compose up -d
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164135%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164135%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > View your new PLEX container in Docker by running the following command. <br>
```bash
sudo docker ps
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164202%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164202%20v2.png" height="270"/>
</a><br>

***
### [6] Sign in and initialize PLEX.

&emsp; > Open a web browser tab to the following URL:
```bash
https://ipAddress:32400/web
``` 

> ℹ️ You will be redirected to `https://app.plex.tv` and asked to sign in with your PLEX account. Once that is done, you should be redirected back to the URL above. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164418%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164418%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164443%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164443%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Once you have successfully signed in, you should be greeted by a 'Server Setup' wizard. <br>
&emsp; > Select '`Got It!`' to continue. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164513%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164513%20v2.png" height="270"/>
</a><br>

&emsp;> Assign a name for your PLEX media server. In my example, my server will be named 'viper'. <br>
&emsp;> Confirm whether or not you want to enable access to your PLEX media server outside of your local LAN, meaning over the WAN/internet. *More on that later in this guide. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164537%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164537%20v2.png" height="270"/>
</a><br>

&emsp;> Next, you can determine whether or not to add media libraries, we'll be walking through this in more detail in a later step, so we'll skip this for now. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164554%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164554%20v2.png" height="270"/>
</a><br>

&emsp;> Select 'Done' and have fun! <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164607%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164607%20v2.png" height="270"/>
</a><br>

***
### [7] Activate (enable) Two-Factor Authentication (2FA).

> ℹ️ I recommend using 'Google Authenticator', which is an easy to use TOTP (time-based one-time password) application. Mine is setup on my iPhone. <br>

&emsp; Navigate to the following location on your PLEX media server: <br>
&emsp;&emsp; > Settings <br>
&emsp;&emsp; > Account <br>
&emsp;&emsp; > Select 'Edit' for 'Two-Factor Authentication'. <br>
&emsp;&emsp; > Follow the steps to enable 2FA. <br>

***
### [8] How to Add Libraries.

#

&emsp; **[Add Library - Option 1] From the default homepage.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp;&emsp;&emsp; > From the default homepage, select '`More >`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164810%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164810%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Select the '`+`' sign next to your server's hostname. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164826%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164826%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > In this example, we'll add a 'Movies' library by selecting the '`Movies`' icon/type. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164906%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164906%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Select '`Browse for Media Folder`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164907%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164907%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Select the folder where your Movie files are located, then select '`Add`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164943%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20164943%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > When finished, select '`Add Library`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165040%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165040%20v2.png" height="270"/>
</a><br>
<br>

Once the library has been added, PLEX will start to scan the folder locations you specified and will organize, list, and add metadata for each of the Movies / TV Shows in your respective library. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165101%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165101%20v2.png" height="270"/>
</a><br>
</details>

#

&emsp; **[Add Library - Option 2] From Settings.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp;&emsp;&emsp; > Go to '`Settings`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165139%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165139%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Verify the appropriate PLEX media server is selected. <br>
&emsp;&emsp;&emsp; > In my example, my server name is 'viper'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165154%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165154%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Go to '`Manage`' > '`Libraries`' > Select '`Add Library`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165230%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > In this example, we'll add a 'TV Shows' library by selecting the '`TV Shows`' icon/type. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165249%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165249%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Select '`Browse for Media Folder`'. <br>
&emsp;&emsp;&emsp; > Select the folder where your TV Show files are located, then select '`Add`'. <br>
&emsp;&emsp;&emsp; > When finished, select '`Add Library`'. <br>

Once the library has been added, PLEX will start to scan the folder locations you specified and will organize, list, and add metadata for each of the Movies / TV Shows in your respective library. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165350%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165350%20v2.png" height="270"/>
</a><br>

</details>

#

***
### [9] How to Remove Libraries.

> ℹ️ Deleting a library will not delete your actual media folders / files. It simply removes the library (access to that media) from your PLEX media server. <br>

> ⚠️ **Warning**  
>
> Be aware, individual files within your library can be deleted! <br>
>
> To disable this, navigate to Settings > Library > Uncheck 'Allow media deletion' > Scroll down and select 'Save'. <br>
>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-09-04%20092557%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-09-04%20092557%20v2.png" height="270"/></a><br>

#

&emsp; **[Remove Library - Option 1] From the default homepage, for a pinned library.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp;&emsp;&emsp; From the default homepage (if your library is pinned to your Home/Dashboard page): <br>
&emsp;&emsp;&emsp;&emsp; > Hover over the lirbary you want to delete and select the '`three-dot`' hamburger menu. <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Manage Library`'. <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Delete`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165545%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165545%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165604%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165604%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Remove Library - Option 2] From the default homepage, for an unpinned library.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp;&emsp;&emsp; From the default homepage (if the library is NOT pinned to your Home/Dashboard page): <br>
&emsp;&emsp;&emsp;&emsp; > Scroll down and select '`More >`' <br>
&emsp;&emsp;&emsp;&emsp; > Identify the server you want to delete the library from. <br>
&emsp;&emsp;&emsp;&emsp; > Under that server, hover over the library you want to delete and select the '`three-dot`' hamburger menu. <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Manage Library`'. <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Delete`'. <br>     		

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165640%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165640%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165713%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165713%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165743%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165743%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Remove Library - Option 3] From Settings**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp;&emsp;&emsp; From the default homepage: <br>
&emsp;&emsp;&emsp;&emsp; > Go to '`Settings`'. <br>
&emsp;&emsp;&emsp;&emsp; > Verify the appropriate PLEX media server is selected. <br>
&emsp;&emsp;&emsp;&emsp; > Under '`Manage`', go to '`Libraries`'. <br>
&emsp;&emsp;&emsp;&emsp; > Hover over the lirbary you want to delete and select the '`three-dot`' hamburger menu. <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Delete`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165806%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165806%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165824%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165824%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165849%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165849%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165904%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-03%20165904%20v2.png" height="270"/>
</a><br>
<br>

</details>

#

***

### [10] (Optional) Enable 'Remote Access'.

#

&emsp; **[Remote Access - Option 1 (UPnP/NAT-PMP)]**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; If your router supports UPnP/NAT-PMP (Universal Plug and Play/NAT Port Mapping Protocol) and it is enabled, you should be able to 'Enable Remote Access' in PLEX and the UPnP/NAT-PMP service should configure/map the necessary networking to access your PLEX media server externally over the WAN/internet without having to touch your firewall or manually forward ports. <br>

> ⚠️ Be aware, UPnP/NAT-PMP does not require authentication to configure these network settings, which should be considered a security risk! If security is important to you, consider options 2 or 3 below. <br>

&emsp; > '`Settings`'. <br>
&emsp; > Select '`Remote Access`'. <br>
&emsp; > Select '`Enable Remote Access`'. <br>
&emsp; > If UPnP/NAT-PMP is supported and enabled on your router, your router should automatically configure the necessary port forwarding. <br>

</details>

#

&emsp; **[Remote Access - Option 2 (Manual Port-Forward on Firewall)]**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Manually configuring port forwarding provides better security, better control, and reduces the attack surface on your firewall.

&emsp; > On your router, port-forward port 32400 to your PLEX media server's IP address. <br>
&emsp; > In PLEX, navigate to the following location. <br>
&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp; > Select '`Remote Access`'. <br>
&emsp;&emsp; > Select '`Enable Remote Access`'. <br>
&emsp;&emsp; > Check '`Manually specify public port`' and set/keep the port as default '`32400`' and select '`Apply`'. <br>

</details>

#

&emsp; **[Remote Access - Option 3 (Reverse Proxy)]**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; I believe the best option is to route your access/traffic through a reverse proxy like 'Nginx Proxy Manager'. I'll cover reverse proxies in a separate guide. <br>

</details>

#

***
### [11] Configure PLEX media server Settings.

&emsp; Various settings can be considered personal preference depending on your underlying hardware, use cases, or needs. I'll share what I use in general, but be sure to tailor your settings to your needs. <br>

&emsp; [General Settings] <br>
&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp; > Select '`General`' under the Settings section. <br>
&emsp;&emsp; > Uncheck '`Send crash reports to Plex`' (sorry Plex, I do this for almost everything, trying to get a bit more privacy). <br>
&emsp;&emsp; > Select Save '`Changes`'. <br>

&emsp; [Library Settings] <br>
&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp; > Select '`Library`' under Settings section. <br>
&emsp;&emsp; > Check '`Scan my library automatically`'. <br>
&emsp;&emsp; > Check '`Scan my library periodically`' with a Library scan interval of '`daily`'. <br>
&emsp;&emsp; > Check '`Empty trash automatically after every scan`'. <br>
&emsp;&emsp; > If you haven't already, uncheck '`Allow media deletion`'. <br>
&emsp;&emsp; > Select '`Save Changes`'. <br>

&emsp; [Network Settings] <br>
&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp; > Select '`Network`'. <br>
&emsp;&emsp; > Set '`Secure connections`' to '`Required`'. <br>
&emsp;&emsp;&emsp;&emsp; I encourage this, similar to enabling 2FA, to increase security. <br>
&emsp;&emsp; > Select '`Save Changes`'. <br>

&emsp; [Transcoder Settings] <br>
&emsp;&emsp; These settings will be highly dependent on your hardware and personal preferences. <br>
&emsp;&emsp; > If you have hardware transcoding available via Intel Quick Sync or a dedicated NVIDIA/AMD GPU: <br>
&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp; > Select '`Transcoder`'. <br>
&emsp;&emsp; > Enable '`Use hardware acceleration when available`'. <br>
&emsp;&emsp; > Enable '`Use hardware-accelerated video encoding`'. <br>
&emsp;&emsp; > Select '`Save Changes`'. <br>

&emsp; [Scheduled Task Settings] <br>
&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp; > Select '`Scheduled Tasks`'. <br>
&emsp;&emsp; > Change '`Time at which tasks start to run`' to an appropriate time depending on your environment. <br>
&emsp;&emsp; > Change '`Time at which tasks stop running`' to an appropriate time depending on your environment. <br>
&emsp;&emsp; > Select '`Save Changes`'. <br>
<br>

## Appendix

***

### Upgrading PLEX (Docker version)

<details>
  <summary>Expand for additional details.</summary>
<br>

In this section, we'll cover how to upgrade our PLEX Docker container using Docker Compose. <br>

&emsp; > Here, we can see an update is available for our PLEX Docker container. <br>

> ⚠️ **Warning**
> 
> Do not upgrade PLEX from within the PLEX Web UI. This could break dependencies within the Docker container/image itself. It is recommended to upgrade Docker containers using updated base images from the Docker container provider, in our case Linuxserver.io . <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115254%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115254%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115319%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115319%20v2.png" height="270"/>
</a><br>
<br>
 
&emsp; > Navigate to the directory where your 'docker-compose.yml' file is stored. <br>
```bash
cd ~/plex
```
&emsp; > Verify your docker-compose.yml configuration looks good. Verify image: '`lscr.io/linuxserver/plex:latest`' is set to '`latest`'. <br>
```bash
cat docker-compose.yml
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115420%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115420%20v2.png" height="270"/>
</a><br>
<br>

Here is an example of my Docker-Compose yaml (.yml) file: <br>
```bash
---
services:
  plex:
    image: lscr.io/linuxserver/plex:latest
    container_name: plex
    network_mode: host
    environment:
      - PUID=1171601103
      - PGID=1171600513
      - TZ=America/New_York
      - VERSION=docker
      - PLEX_CLAIM=
    volumes:
      - /home/artemis@spartan23.home/plex/config:/config
      - /home/artemis@spartan23.home/plex/media:/media_plex
    restart: unless-stopped
```
<br>

&emsp; > Recreate / redeploy the PLEX container with the new image. <br>
```bash
sudo docker pull lscr.io/linuxserver/plex:latest
```
```bash
sudo docker compose up -d plex
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115515%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115515%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now we can see PLEX is successfully upgraded. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115602%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115602%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115628%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-05%20115628%20v2.png" height="270"/>
</a><br>
<br>

</details>

***

### Uninstall PLEX

<details>
  <summary>Expand for additional details.</summary>
<br>

In this section, we'll cover how to uninstall our PLEX Docker container. <br>

&emsp; > Check running containers, looking for the name of your PLEX container. If you followed the guide above, we named our PLEX container, 'plex'. <br>
```bash
sudo docker ps
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131536%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131536%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Stop the PLEX container. <br>
```bash
sudo docker stop plex
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131613%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131613%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Remove (uninstall) the PLEX container. This only removes the Docker container itself, your directories and files are not removed at this point. <br>
```bash
sudo docker rm plex
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131646%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131646%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > List the Docker images on your system, looking for the PLEX image(s). <br>
```bash
sudo docker image ls
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131812%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131812%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Remove (delete) any PLEX images. <br>
```bash
sudo docker rmi lscr.io/linuxserver/plex
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131854%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20131854%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Remove or comment-out the SMB share mounts in the /etc/fstab . <br>
```bash
sudo nano /etc/fstab
```
Example: <br>
This is the line I removed/commented out in my /etc/fstab file. <br>
&emsp; `//apollo/Media /home/artemis@spartan23.home/plex/media/apollo_Media cifs credentials=/etc/samba/creds-artemis,uid=1171601103,gid=1171600513,vers=3.1.1,_netdev,nofail 0 0` <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132001%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132001%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132019%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132019%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Remove any related SMB share password files. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">sudo rm /etc/samba/creds-userName</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">sudo rm /etc/samba/creds-artemis</code></pre>
    </td>
  </tr>
</table>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132448%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132448%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now reboot your Ubuntu machine. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132228%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132228%20v2.png" height="270"/>
</a><br>

&emsp; > Verify that your SMB share(s) are no longer mounted. In my example, the following command shows an empty (no SMB share(s) mounted) to the directory, `ll ~/plex/media/apollo_Media/`. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132308%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132308%20v2.png" height="270"/>
</a><br>

> ⚠️ **Be Aware**
>
> DO NOT run the following command unless you are absolutely sure your SMB share is no longer mounted underneath `~/plex/media/nasServer_smbShare`. The following command runs a forced and recursive delete, meaning it will delete the base directory and any subdirectories or files underneath. If your SMB share were still mounted within a subdirectory, you may end up permanently deleting data on your SMB share.
>
> RUN THE FOLLOWING COMMAND AT YOUR OWN RISK!!!

```bash
sudo rm -fr plex/
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132618%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-09-07%20132618%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now you're finished removing/uninstalling PLEX. <br>

</details>
