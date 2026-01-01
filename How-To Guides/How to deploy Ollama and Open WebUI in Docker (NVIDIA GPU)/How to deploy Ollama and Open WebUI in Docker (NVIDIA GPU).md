<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(5)%20-%20NVIDIA.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(4)%20-%20Open%20WebUI.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(3)%20-%20Ollama.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20Docker.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

## How to deploy Ollama and Open WebUI in Docker (NVIDIA GPU)

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>

***
-->

### Table of Contents

&emsp; [1] GPU Setup; NVIDIA <br>
&emsp; [2] Create a Shared Docker Network <br>
&emsp; [3] Deploy Ollama (Backend) <br>
&emsp; [4] Deploy Open WebUI (Frontend) <br>
&emsp; [5] Managing Models with Ollama <br>
&emsp; [6] Upgrading Ollama and Open WebUI <br>
&emsp; [7] Troubleshooting (Common Issues & Fixes) <br>

#

### 📋 Prerequisites

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu Server/Desktop 22.04.x LTS</td>
    <td><a href="../How%20to%20install%20Ubuntu%20Desktop%2022.04.5%20LTS/How%20to%20install%20Ubuntu%20Desktop%2022.04.5%20LTS.md">How to install Ubuntu Desktop 22.04.5 LTS</a></td>
  </tr>
  <tr>
    <td align="right">Container Runtime</td>
    <td>Docker (incl. Docker Compose)</td>
    <td><a href="../How%20to%20install%20Docker%20and%20Docker%20Compose/How%20to%20install%20Docker%20and%20Docker%20Compose.md">How to install Docker and Docker Compose</a></td>
  </tr> 
  <tr>
    <td align="right">Supported GPUs</td>
    <td>NVIDIA</td>
    <td>https://docs.ollama.com/gpu#nvidia</td>
  </tr>
</table>

> ⚠️ Ubuntu 22.04 is strongly recommended when using the `NVIDIA Container Toolkit`. Ubuntu 24.04 is claimed to be supported; however, there are many known issues and functionality/stability concerns. <br>

### 🌐 Recommended Docker Images

<table>  
  <tr>
    <td align="right">Frontend Interface / Client Application</td>
    <td>Open WebUI</td>
    <td>https://github.com/open-webui/open-webui</td>
  </tr>
  <tr>
    <td align="right">Model Runtime / Backend Engine</td>
    <td>Ollama</td>
    <td>https://hub.docker.com/r/ollama/ollama</td>
  </tr>
</table>

> ℹ️ The official documentation uses `docker run` commands. I used '*ChatGPT*' and '*Copilot*' to help me convert those commands into Docker Compose yaml files as I prefer using Docker Compose. <br>

<br>

***

### [1] GPU Setup; NVIDIA

#

&emsp; **[1.1] Install NVIDIA Driver**

> ℹ️ Ubuntu ships with a **meta-package** to help list/display available drivers for NVIDIA GPUs within Ubuntu's APT repository. For this reason, we can list and then install our driver without needing to download anything external. <br>

&emsp; List available NVIDIA drivers: <br>
```bash
ubuntu-drivers devices
```
&emsp; Example Output: <br>

> ℹ️ non-free ≠ costs money, it simply means, “This driver is proprietary (from NVIDIA), not open-source.” <br>

```bash
wraith@wraith:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:03.1/0000:06:00.0 ==
modalias : 
pci:v000010DEd00001E89sv00001043sd00008732bc03sc00i00
vendor : NVIDIA Corporation 
model : TU104 [GeForce RTX 2060] 
driver : nvidia-driver-535-server-open - distro non-free 
driver : nvidia-driver-470 - distro non-free 
driver : nvidia-driver-535-server - distro non-free 
driver : nvidia-driver-570-server - distro non-free 
driver : nvidia-driver-550-open - distro non-free 
driver : nvidia-driver-580-server - distro non-free 
driver : nvidia-driver-470-server - distro non-free 
driver : nvidia-driver-580-open - distro non-free 
driver : nvidia-driver-570-server-open - distro non-free 
driver : nvidia-driver-570-open - distro non-free 
driver : nvidia-driver-550 - distro non-free 
driver : nvidia-driver-570 - distro non-free 
driver : nvidia-driver-545 - distro non-free 
driver : nvidia-driver-535 - distro non-free 
driver : nvidia-driver-580-server-open - distro non-free 
driver : nvidia-driver-450-server - distro non-free 
driver : nvidia-driver-580 - distro non-free recommended     # 'recommended' WOULD BE THE DRIVER YOU WANT TO INSTALL.
driver : nvidia-driver-545-open - distro non-free 
driver : nvidia-driver-535-open - distro non-free 
driver : xserver-xorg-video-nouveau - distro free builtin
```
&emsp; Install the 'recommended' NVIDIA driver listed from your output: <br>
> ℹ️ For my machine `nvidia-driver-580` was recommended. <br>
```bash
sudo apt install -y nvidia-driver-580
```

#

&emsp; **[1.2] Reboot and Verify**

&emsp; Reboot: <br>
```bash
sudo shutdown -r now
```
&emsp; Verify your NVIDIA driver: <br>
```bash
nvidia-smi
```
&emsp; Example Output: <br>
```bash
Thu Sep 18 13:30:11 2025       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 580.65.06              Driver Version: 580.65.06      CUDA Version: 13.0     | # See 'Driver Version: 580.65.06'
+-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 2060        Off |   00000000:06:00.0  On |                  N/A |
|  0%   45C    P8             13W /  170W |      39MiB /   6144MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI              PID   Type   Process name                        GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A            1781      G   /usr/lib/xorg/Xorg                       24MiB |
|    0   N/A  N/A            2054      G   /usr/bin/gnome-shell                      5MiB |
+-----------------------------------------------------------------------------------------+
```

#

&emsp; **[1.3] Install NVIDIA Container Toolkit**

&emsp; Add the NVIDIA Container Toolkit repository: <br>
```bash
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | \
sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit.gpg
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/libnvidia-container/$distribution/libnvidia-container.list | \
sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit.gpg] https://#g' | \
sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
sudo apt update
```
&emsp; Install the NVIDIA Container Toolkit: <br>
```bash
sudo apt install -y nvidia-container-toolkit
```
&emsp; Verify the NVIDIA Container Toolkit installation: <br>
```bash
nvidia-container-cli --version
```

#

&emsp; **[1.4] (Optional) Install CUDA Toolkit**

&emsp; Benefits of using NVIDIA CUDA Toolkit: <br>
<table>
  <tr>
    <td align="right">Inference Speed</td>
    <td>🚀 Much faster</td>
  </tr>
  <tr>
    <td align="right">Resource Efficiency</td>
    <td>🧠 Lower CPU usage</td>
  </tr>
  <tr>
    <td align="right">Model Scalability</td>
    <td>📈 Handles larger models</td>
  </tr>
    <tr>
    <td align="right">UI Responsiveness</td>
    <td>⚡ Snappier Open WebUI experience</td>
  </tr>
    <tr>
    <td align="right">Advanced Optimizations</td>
    <td>🔥 Flash Attention support</td>
  </tr>
</table>	

&emsp; Verify your NVIDIA GPU is CUDA-capable: <br>
```bash
lspci | grep -i nvidia
```
&emsp; Add the NVIDIA CUDA Toolkit repository: <br>
```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/3bf863cc.pub
sudo add-apt-repository "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/ /"
sudo apt update
```
&emsp; Install the NVIDIA CUDA Toolkit: <br>
```bash
sudo apt install -y nvidia-cuda-toolkit
```
&emsp; Verify the NVIDIA CUDA Toolkit installation: <br>
```bash
nvcc --version
```
<br>

***

### [2] Create a Shared Docker Network

&emsp; Create a Docker network to be used by Ollama and Open WebUI: <br>
```bash
sudo docker network create ollama-net
```
&emsp; This network lets Ollama and Open WebUI communicate internally. <br>
<br>

***

### [3] Deploy Ollama (Backend)

&emsp; Create directories for Ollama: <br>
```bash
mkdir -p ~/ollama/ollama
```
&emsp; cd (Change Directory) into our base-Ollama directory: <br>
```bash
cd ~/ollama
```
&emsp; Create a Docker Compose file for Ollama: <br>
```bash
nano docker-compose.yml
```
<br>

&emsp; Copy and paste the following into your docker-compose.yml file. <br>
&emsp; NVIDIA GPU Example: <br>
> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>
```bash
services:
  ollama:
    image: ollama/ollama
    container_name: ollama
    ports:
      - "11434:11434"
    volumes:
      - /home/username/ollama/ollama:/root/.ollama
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]
    restart: unless-stopped
    networks:
      - ollama-net

networks:
  ollama-net:
    external: true
```
<br>

&emsp; Deploy Ollama: <br>
```bash
sudo docker compose up -d
```
&emsp; Verify Docker container 'ollama' is running: <br>
```bash
sudo docker ps
```
<br>

***

### [4] Deploy Open WebUI (Frontend)

&emsp; Create directories for Open WebUI: <br>
```bash
mkdir -p ~/open-webui/data
```
&emsp; cd (Change Directory) into our base-Open WebUI directory: <br>
```bash
cd ~/open-webui
```
&emsp; Create a Docker Compose file for Open WebUI: <br>
```bash
nano docker-compose.yml
```
<br>

&emsp; Copy and paste the following into your docker-compose.yml file: <br>
&emsp; NVIDIA GPU Example: <br>
> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>
```bash
services:
  open-webui:
    image: ghcr.io/open-webui/open-webui:cuda
    container_name: open-webui
    volumes:
      - /home/username/open-webui/data:/app/backend/data
    ports:
      - "3000:8080"
    environment:
      - OLLAMA_BASE_URL=http://ollama:11434
    restart: unless-stopped
    networks:
      - ollama-net
    deploy:
      resources:
        reservations:
          devices:
            - driver: nvidia
              count: all
              capabilities: [gpu]

networks:
  ollama-net:
    external: true
```
<br>

&emsp; Deploy Open WebUI: <br>
```bash
sudo docker compose up -d
```
&emsp; Verify Docker container 'open-webui' is running: <br>
```bash
sudo docker ps
```
<br>

&emsp; Access the UI: <br>
```bash
http://localhost:3000
```
```bash
http://<ip-address>:3000
```
<br>

***

### [5] Managing Models with Ollama

> ℹ️ Models can also be managed via Open WebUI → Admin Panel → Settings → Connections (or Models). <br>

&emsp; List models: <br>
```bash
sudo docker exec ollama ollama list
```
&emsp; Pull a model Example: <br>
```bash
sudo docker exec ollama ollama pull tinyllama:1.1b
```
&emsp; List model information (ex. quantization) Example: <br>
```bash
sudo docker exec ollama ollama show tinyllama:1.1b
```
&emsp; Remove a model Example: <br>
```bash
sudo docker exec ollama ollama rm tinyllama:1.1b
```
<br>

&emsp; To open a CLI session directly within the ollama Docker container:
```bash
sudo docker exec -it ollama bash
```
&emsp; While in the CLI session, you no longer need the `sudo docker exec` prefix. You can use `ollama <command>`. <br>
> ℹ️ Use `/bye` and/or `exit` to exit out of the CLI session. <br>
<br>

***

### [6] Upgrading Ollama and Open WebUI

&emsp; Upgrade Ollama (NVIDIA GPU): <br>
```bash
sudo docker pull ollama/ollama
cd ~/ollama
sudo docker compose down
sudo docker compose up -d
```
&emsp; Upgrade Open WebUI (NVIDIA GPU): <br>
```bash
sudo docker pull ghcr.io/open-webui/open-webui:cuda
cd ~/open-webui
sudo docker compose down
sudo docker compose up -d
```
<br>

***

### [7] Troubleshooting (Common Issues & Fixes)

| Issue                                   | Cause                                         | Fix                                                                                                                                     |
| --------------------------------------- | --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Docker can’t see GPU**                | Missing container toolkit (NVIDIA)            | Re-run install for `nvidia-container-toolkit` and restart Docker                                                                        |
| **`nvidia-smi` not found in container** | Container missing NVIDIA runtime mounts       | Ensure you’re using the `nvidia` driver block and `--gpus all` runtime if manual                                                        |
| **UI loads but models don’t respond**   | Backend Ollama not reachable                  | Confirm network `ollama-net` exists and `OLLAMA_BASE_URL` set correctly                                                                 |
| **High CPU usage / no GPU load**        | Model running on CPU fallback                 | For NVIDIA, verify `nvidia-smi` shows active process                                                                                    |
| **Open WebUI crashes on startup**       | Missing database directory or permissions     | Ensure `~/open-webui/data` exists and is writable by Docker user                                                                        |

> 💡 Tip: Verify GPU usage directly inside the container: <br>
> NVIDIA → `sudo docker exec -it ollama nvidia-smi` <br>

> ✅ Summary
> - Ubuntu 22.04 LTS remains the most stable base for NVIDIA GPUs.
> - Use ollama/ollama for NVIDIA.
> - Verify with nvidia-smi.
