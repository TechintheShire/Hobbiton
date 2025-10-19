<a href="./Icons%20and%20Screenshots/20250805_110313.png">
  <img src="./Icons%20and%20Screenshots/20250805_110313.png" height="170"/>
</a>

<a href="./Icons%20and%20Screenshots/20250805_100334.png">
  <img src="./Icons%20and%20Screenshots/20250805_100334.png" height="170"/>
</a>

# How to install Docker and Docker Compose

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>

***
-->

### Prerequisits

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu Desktop 24.04.x LTS</td>
  </tr>
</table>

> ℹ️ If you need help installing Ubuntu, please see our guide here: [How to install Ubuntu Desktop 24.04.3 LTS](../../01.%20Operating%20Systems/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS.md).

***
## Install and Configure, Docker / Docker Compose

> ⚠️ **Warning**  
> 
> I do not recommend adding your user to the Docker group. Doing this will allow you to run Docker commands without 'sudo'; however, this is effectively giving your user root-level access (at all times) via Docker commands. This exposes you to many unintended security risks that I believe are not worth the trade-off of saving a few seconds to enter your 'sudo' user password for the first 'sudo' command you run. Keep in mind, you are only prompted for your 'sudo' user password for the first 'sudo' command you run within a terminal session; meaning, after you've run your first 'sudo' command and have successfully authenticated, you can run multiple following 'sudo' commands without being prompted for a password again.
>
> For those curious, this is the command I am referencing: sudo usermod -aG docker $USER
> 
> Risks: <br>
> 🛡️ Full root-level access: Being in the docker group gives root-equivalent access. <br>
> 🔓 Privilege escalation: Having root-equivalent access could allow the user to mount and modify the entire root filesystem. <br>
> 🧱 Bypasses user isolation: Docker doesn’t isolate users within containers. So this user would have root-equivalent access to all containers. <br>
> 🐛 Increased attack surface: If a non-privileged user or app is compromised, the attacker could take over the host using Docker. <br>

***
### [Option 1] Install from Ubuntu's apt repository. 

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ This is the easiest method but may not pull the latest versions of Docker and Docker Compose from Docker's official APT repository. Please see '[Option 2]' below for steps on how to install Docker and Docker Compose from Docker's official APT repository. <br>

#### [1.1] Update your system/software packages.

    sudo apt update && sudo apt upgrade -y

#### [1.2] Install Docker and Docker-Compose.

    sudo apt install docker.io docker-compose -y

&emsp; docker.io installs the Docker Engine & CLI. <br>
&emsp; docker-compose installs the Python-based v1.x version of Compose (docker-compose with a hyphen). <br>
&emsp; 🧠 FYI: This installs Docker Compose v1, not the newer docker compose plugin (v2+). But for many use cases, it works just fine.

#### [1.3] Enable Docker to start at boot.

    sudo systemctl enable docker

#### [1.4] Test Docker and Docker-Compose.

&emsp; Docker:

    sudo docker version

&emsp; Docker Compose:

    sudo docker-compose version

</details>

***
### [Option 2] Install from Docker's official apt repository.

<details>
  <summary>Expand for additional details.</summary>
<br>

#### [2.1] Update your system/software packages.

    sudo apt update && sudo apt upgrade -y

#### [2.2] Install prerequisite packages.

    sudo apt install ca-certificates curl gnupg lsb-release -y

#### [2.3] Add Docker’s official GPG key.

```bash
sudo mkdir -p /etc/apt/keyrings
```
```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

#### [2.4] Set up the Docker repository.

    sudo echo \
      "deb [arch=$(dpkg --print-architecture) \
      signed-by=/etc/apt/keyrings/docker.gpg] \
      https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

#### [2.5] Update your system/software packages again.

    sudo apt update

&emsp; You should now see Docker packages coming from the Docker repo (e.g., https://download.docker.com).

#### [2.6] Install Docker Engine, CLI, Containerd, and Compose plugin

    sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

#### [2.7] Enable Docker to start at boot.

    sudo systemctl enable docker

&emsp; Check Docker service status:

    sudo systemctl status docker

&emsp; Hit 'q' on your keyboard to exit the systemctl status check. <br>

#### [2.8] Test Docker and Docker Compose.

&emsp; Docker:

    sudo docker version

&emsp; Docker Compose:

    sudo docker compose version

> ℹ️ `docker compose` (with a space, no hyphen '-') is the new plugin-based Compose (v2). You don’t need to install docker-compose separately.

</details>
