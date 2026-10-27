<img src="./Media/152025114633%20v2%20-%20(2)%20-%20Docker.png"/> <br>
<img src="./Media/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

# How to Install Docker and Docker Compose on Ubuntu

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>

Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>

***
-->

Current Guide Version: 1.0 <br>
Last Verified: August 2026 <br>

> [!IMPORTANT]
> **Supported Platforms**
>
> ✅ Ubuntu Desktop 22.04 LTS <br>
> ✅ Ubuntu Desktop 24.04 LTS <br>
> ⏳ Ubuntu Desktop 26.04 LTS <br>
> ⏳ Ubuntu Server 

| Guide Version | Date | Changes |
|---|---|---|
| 1.0 | August 2026 | Initial guide, validated for `Ubuntu Desktop 22.04 LTS` and `24.04 LTS`. |

## 📋 Prerequisites

Before you begin, make sure you have:
- A supported version of Ubuntu:
  - [How to Install Ubuntu Desktop 22.04 LTS](../How%20to%20Install%20Ubuntu%20Desktop%2022.04%20LTS/How%20to%20Install%20Ubuntu%20Desktop%2022.04%20LTS.md)
  - [How to Install Ubuntu Desktop 24.04 LTS](../How%20to%20Install%20Ubuntu%20Desktop%2024.04%20LTS/How%20to%20Install%20Ubuntu%20Desktop%2024.04%20LTS.md)
- A user account with `sudo` privileges.
- An active internet connection.

> [!NOTE]
> To install Docker / Docker Compose directly from Docker's APT Repository, please see [dockerdocs - Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/#install-using-the-apt-repository).

> [!TIP]
> If you need the ability to run Docker commands without `sudo`, please see [Docker rootless mode](https://docs.docker.com/engine/security/rootless/).

> [!CAUTION]
> Do NOT add your user account to the `docker` group via `sudo usermod -aG docker "$USER"`. Doing so allows that user to control the root-owned Docker daemon and effectivly grants root-level access to the host, which is a significant security risk!

---
---

## 🔥 Quick Start Installation

<details>
  <summary>Expand for the condensed Ubuntu APT commands.</summary>
<br>

```bash
sudo apt update
sudo apt install -y \
  docker.io \
  docker-compose-v2 \
  docker-buildx
sudo systemctl enable --now docker
sudo docker version
sudo docker compose version
sudo docker buildx version
sudo docker run --rm hello-world
```

</details>

---
---

## [1] 🔄 Update the Ubuntu APT package index

```bash
sudo apt update
```

## [2] 📦 Install Docker Engine, Docker Compose v2, and Docker Buildx

```bash
sudo apt install -y \
  docker.io \
  docker-compose-v2 \
  docker-buildx
```

- `docker.io` installs Docker Engine and the Docker CLI.
- `docker-compose-v2` installs the Compose v2 CLI plugin used by `docker compose`.
- `docker-buildx` installs the Docker Buildx CLI plugin.

## [3] 🚀 Enable and start Docker

```bash
sudo systemctl enable --now docker
```

## [4] ✅ Verify the Docker service

```bash
sudo systemctl is-active docker
sudo systemctl is-enabled docker
```

Expected results: `active` / `enabled`.

## [5] 🔍 Verify the installed components

```bash
sudo docker version
sudo docker compose version
sudo docker buildx version
```

## [6] 🧪 Run a test container

```bash
sudo docker run --rm hello-world
```

The test container should display a message confirming that Docker is working correctly.

## 🎉 Installation Complete!

Congratulations! You've successfully installed and verified Docker and Docker Compose. Your system is now ready to run Docker containers!
