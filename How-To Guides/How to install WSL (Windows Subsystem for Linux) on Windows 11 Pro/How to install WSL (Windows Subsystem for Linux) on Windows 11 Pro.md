<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20WSL.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Windows%2011.png"/> <br>

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

## How to install WSL (Windows Subsystem for Linux) on Windows 11 Pro

### Table of Contents

&emsp; [1] Quick check, is CPU virtualization 'Enabled'? <br>
&emsp; [2] Enable Windows Features prior to WSL install. <br>
&emsp; [3] Reboot. <br>
&emsp; [4] Install WSL (Windows Subsystem for Linux). <br>
&emsp; [5] Launch WSL (Windows Subsystem for Linux). <br>
&emsp; [6] Helpful Linux (Ubuntu) Commands. <br>

&emsp; [#] Appendix <br>
&emsp; [#] Install Docker and Docker Compose (under WSL). <br>

#

### 📋 Prerequisites

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Windows 11 Pro</td>
    <td><a href="../How%20to%20install%20Windows%2011%20Pro/How%20to%20install%20Windows%2011%20Pro.md">How to install Windows 11 Pro</a></td>
  </tr> 
</table>

<br>

***

### [1] Quick check: is CPU virtualization 'Enabled'?

&emsp; Open the Windows Task Manager <br>
&emsp;&emsp; > Press '`Ctrl+Shift+Esc`'. <br>
&emsp;&emsp; > View '`Performance`' → '`CPU`' → look for '`Virtualization: Enabled`'. <br>

> ℹ️ If it says '*Disabled*', enable Intel VT-x/AMD-V (a.k.a. SVM) in your BIOS/UEFI (will require a reboot). <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20132826%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20132826%20v2.png" height="270"/>
</a><br>
<br>

***

### [2] Enable Windows Features prior to WSL install.

&emsp; PowerShell (***Run as Administrator***) <br>
```bash
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:HypervisorPlatform /all /norestart
```
<br>

***

### [3] Reboot.

&emsp; Be sure to reboot to allow kernel-level components to load on startup. <br>
<br>

***

### [4] Install WSL (Windows Subsystem for Linux).

&emsp; PowerShell (***As your standard user, NOT Administrator***) <br>
```bash
wsl --status
```

> ℹ️ By default, `wsl --install` uses the latest available version of Ubuntu. As of 2025/11/11, that is 24.04.3 LTS. <br>

> ℹ️ During the installation, you'll be prompted to create a user/password for the Linux subsystem environment. <br>

```bash
wsl --install
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20152603%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20152603%20v2.png" height="270"/>
</a><br>
<br>

***

### [5] Launch WSL (Windows Subsystem for Linux).

#

**[Option 1]** <br>

&emsp; Open a PowerShell or Command Prompt window and run: <br>
```bash
wsl
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20152828%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20152828%20v2.png" height="270"/>
</a><br>

#

**[Option 2]** <br>

&emsp;Open either the '*WSL*' or '*WSL Settings*' App: <br>
&emsp;&emsp; > Windows '`Start Menu`' <br>
&emsp;&emsp; > Search '`WSL`' or '`WSL Settings`' <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20153142%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20153142%20v2.png" height="270"/>
</a><br>
<br>

> ℹ️ If you opened the '*WSL Settings*' App, select '`Launch wsl.exe`' in the bottom left-hand corner. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20153143%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20153143%20v2.png" height="270"/>
</a><br>

#

<br>

***

### [6] Helpful Linux (Ubuntu) Commands.

&emsp; Verify Linux Distro / Version: <br>
```bash
lsb_release -a
```

&emsp; Update and Upgrade APT Software Packages: <br>
```bash
sudo apt update && sudo apt upgrade -y
```
<br>

## Appendix

***

### Install Docker and Docker Compose (under WSL).

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; **Verify WSL and Linux Versions** <br>

> ℹ️ It is important that you're using WSL version 2 and Linux distro Ubuntu. <br>

&emsp; Command Prompt: <br>
```bash
wsl -l -v
```

&emsp; WSL Command Prompt: <br>
```bash
lsb_release -a
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20152949%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20152949%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20153026%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20153026%20v2.png" height="270"/>
</a><br>

***

> ⚠️ **Warning**  
> 
> I do not recommend adding your user to the Docker group. Doing this will allow you to run Docker commands without 'sudo'; however, this is effectively giving your user root-level access (at all times) via Docker commands. This exposes you to many unintended security risks that I believe are not worth the trade-off of saving a few seconds to enter your 'sudo' user password for the first 'sudo' command you run. Keep in mind, you are only prompted for your 'sudo' user password for the first 'sudo' command you run within a terminal session; meaning, after you've run your first 'sudo' command and have successfully authenticated, you can run multiple following 'sudo' commands without being prompted for a password again.
>
> For those curious, this is the command I am referencing: `sudo usermod -aG docker $USER`
> 
> Risks: <br>
> 🛡️ Full root-level access: Being in the docker group gives root-equivalent access. <br>
> 🔓 Privilege escalation: Having root-equivalent access could allow the user to mount and modify the entire root filesystem. <br>
> 🧱 Bypasses user isolation: Docker doesn’t isolate users within containers. So this user would have root-equivalent access to all containers. <br>
> 🐛 Increased attack surface: If a non-privileged user or app is compromised, the attacker could take over the host using Docker. <br>

#

&emsp; **[Option 1] Install from Ubuntu's APT repository.**

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ This is the easiest method but may not pull the latest versions of Docker and Docker Compose from Docker's official APT repository. Please see '[Option 2]' below for steps on how to install Docker and Docker Compose from Docker's official APT repository. <br>

#### [1.1] Update your system/software packages.
```bash
sudo apt update && sudo apt upgrade -y
```

#### [1.2] Install Docker and Docker-Compose.
```bash
sudo apt install docker.io docker-compose -y
```
&emsp; docker.io installs the Docker Engine & CLI. <br>
&emsp; docker-compose installs the Python-based v1.x version of Compose (docker-compose with a hyphen). <br>
&emsp; 🧠 FYI: This installs Docker Compose v1, not the newer docker compose plugin (v2+). But for many use cases, it works just fine.

#### [1.3] Enable Docker to start at boot.
```bash
sudo systemctl enable docker
```

#### [1.4] Test Docker and Docker-Compose.
&emsp; Docker:
```bash
sudo docker version
```
&emsp; Docker Compose:
```bash
sudo docker-compose version
```

</details>

#

&emsp; **[Option 2] (Recommended) Install from Docker's official APT repository.**

<details>
  <summary>Expand for additional details.</summary>

#### [2.1] Update your system/software packages.
```bash
sudo apt update && sudo apt upgrade -y
```

#### [2.2] Install prerequisite packages.
```bash
sudo apt install ca-certificates curl gnupg lsb-release -y
```

#### [2.3] Add Docker’s official GPG key.
```bash
sudo mkdir -p /etc/apt/keyrings
```
```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

#### [2.4] Set up the Docker repository.
```bash
sudo echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### [2.5] Update your system/software packages again.
```bash
sudo apt update
```
&emsp; You should now see Docker packages coming from the Docker repo (e.g., https://download.docker.com).

#### [2.6] Install Docker Engine, CLI, Containerd, and Compose plugin
```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

#### [2.7] Enable Docker to start at boot.
```bash
sudo systemctl enable docker
```
&emsp; Check Docker service status:
```bash
sudo systemctl status docker
````
&emsp; Hit 'q' on your keyboard to exit the 'systemctl status' check. <br>

#### [2.8] Test Docker and Docker Compose.
&emsp; Docker:
```bash
sudo docker version
```
&emsp; Docker Compose:
```bash
sudo docker compose version
```

> ℹ️ `docker compose` (with a space, no hyphen '-') is the new plugin-based Compose (v2). You don’t need to install docker-compose separately.

<a href="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20152908%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-11-11%20152908%20v2.png" height="270"/>
</a><br>

</details>

</details>
