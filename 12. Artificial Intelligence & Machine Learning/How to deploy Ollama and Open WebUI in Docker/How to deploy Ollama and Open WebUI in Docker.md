<a href="./Icons%20and%20Screenshots/20251007_115914.png">
  <img src="./Icons%20and%20Screenshots/20251007_115914.png" height="170"/>
</a>

<a href="./Icons%20and%20Screenshots/20250805_100334.png">
  <img src="./Icons%20and%20Screenshots/20250805_100334.png" height="170"/>
</a>

<a href="./Icons%20and%20Screenshots/20251007_114425.png">
  <img src="./Icons%20and%20Screenshots/20251007_114425.png" height="170"/>
</a>

<a href="./Icons%20and%20Screenshots/20251007_115237.png">
  <img src="./Icons%20and%20Screenshots/20251007_115237.png" height="170"/>
</a>

# How to deploy Ollama and Open WebUI in Docker

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>

***
-->

### Recommended Operating System / Docker Image(s) 

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu Server/Desktop 22.04.x LTS</td>
  </tr>
  <tr>
    <td align="right">Container Runtime</td>
    <td>Docker (incl. Docker Compose)</td>
  </tr>
  <tr>
    <td align="right">Frontend Interface / Client Application</td>
    <td>Open WebUI <br> https://github.com/open-webui/open-webui</td>
  </tr>
  <tr>
    <td align="right">Model Runtime / Backend Engine</td>
    <td>Ollama <br> https://github.com/ollama/ollama <br> https://hub.docker.com/r/ollama/ollama</td>
  </tr>
</table>

> ⚠️ Ubuntu 22.04 is strongly recommended because provides official support for the NVIDIA Container Toolkit, which allows us to share our NVIDIA GPU wiht Docker containers. Official support for Ubuntu 24.04 is still under development. <br>

> ℹ️ If you need help deploying Docker/Docker Compose, please see my guide here, [How to install Docker and Docker Compose](../../03.%20Virtual%20Machines%20%26%20Containers/How%20to%20install%20Docker%20and%20Docker%20Compose/How%20to%20install%20Docker%20and%20Docker%20Compose.md). <br>

### My Hardware Specs

&emsp; I share this information to prove that you don't need an expensive or complex build to get started with running and leanring AI. <br>

<table>
  <tr>
    <td align="right">Motherboard</td>
    <td>ASUS TUF B450M-PLUS GAMING</td>
    <td><code>sudo dmidecode -t baseboard</code></td>
  </tr>
<tr>
<td align="right">Processor</td>
<td>AMD Ryzen 7 1700 8C/16T, 3.0 GHz (3.7 GHz Boost)</td>
<td><code>sudo dmidecode -t processor</code><br> <code>lscpu</code></td> 
</tr>
<tr>
<td align="right">DRAM Memory</td>
<td>64 GiB DRAM Memory 2133 MT/s (4x 16 GiB DIMMs)</td>
<td><code>sudo dmidecode -t memory</code></td>
</tr>
<tr>
<td align="right">VRAM GPU</td>
<td>NVIDIA GeForce RTX 2060 6 GiB VRAM</td>
<td><code>nvidia-smi</code><br> <code>sudo lshw -C display</code><br> <code>lspci | grep -i vga</code></td>
</tr>
  <tr>
<td align="right">Storage</td>
<td>4x 500GB SATA SSDs in a RAID 10 via Linux software RAID (mdadm)</td>
<td><code>cat /proc/mdstat</code></td>
</tr>
</table>
<br>

## [1] Prepare your NVIDIA GPU and Software

### [1.1] Install NVIDIA Driver
***

&emsp; Verify which NVIDIA drivers are available on your system; install the 'recommended' version. If you're using a recent version of Ubuntu, NVIDIA drivers are pre-bundled with the OS and can be installed using `apt`. <br>
<br>

&emsp; List the available drivers on your system. <br>
```bash
ubuntu-drivers devices
```
&emsp; Example Output: <br>
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
driver : nvidia-driver-580 - distro non-free recommended     # THIS WOULD BE THE DRIVER I WOULD WANT TO INSTALL ON MY SYSTEM.
driver : nvidia-driver-545-open - distro non-free 
driver : nvidia-driver-535-open - distro non-free 
driver : xserver-xorg-video-nouveau - distro free builtin
```
<br>

&emsp; Install the recommended NVIDIA driver for your GPU. In my case, it was `nvidia-driver-580`.
```bash
sudo apt install -y nvidia-driver-580
```
<br>

### [1.2] Reboot
***

&emsp; Reboot and verify the NVIDIA driver installed successfully. <br> 
<br>

&emsp; List your NVIDIA GPU information, look for 'Driver Version'. <br>
```bash
nvidia-smi
```
&emsp; Example Output:
```bash
wraith@wraith:~$ nvidia-smi
Thu Sep 18 13:30:11 2025       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 580.65.06              Driver Version: 580.65.06      CUDA Version: 13.0     |
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
<br>

### [1.3] Install the NVIDIA Container Toolkit
***

&emsp; Because we're using Docker, we'll want to install the NVIDIA Container Toolkit, which will allow us to share our GPU with Docker containers. <br>
<br>

&emsp; Install the NVIDIA Container Toolkit repository. <br>
```bash
curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit.gpg
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/libnvidia-container/$distribution/libnvidia-container.list | \
  sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit.gpg] https://#g' | \
  sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
```
```bash
sudo apt update
```
<br>

&emsp; Install the NVIDIA Container Toolkit. <br>
```bash
sudo apt install -y nvidia-container-toolkit
```
<br>

### [1.4] (Optional but Recommended) Install the NVIDIA CUDA Toolkit
***

&emsp; Benefits of using NVIDIA CUDA Toolkit <br>

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
    </tr>
    <tr>
    <td align="right">Advanced Optimizations</td>
    <td>🔥 Flash Attention support</td>
  </tr>
</table>	
</br>

&emsp; Verify your NVIDIA GPU is CUDA-capable. <br>
```bash
lspci | grep -i nvidia
```
<br>

&emsp; Add the NVIDIA CUDA Toolkit repository. <br>
```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/cuda-ubuntu2204.pin
```
```bash
sudo mv cuda-ubuntu2204.pin /etc/apt/preferences.d/cuda-repository-pin-600
```
```bash
sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/3bf863cc.pub
```
```bash
sudo add-apt-repository "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu2204/x86_64/ /"
```
```bash
sudo apt update
```
<br>

&emsp; Install the NVIDIA CUDA Toolkit.
```bash
sudo apt install nvidia-cuda-toolkit
```
<br>

&emsp; Verify the NVIDIA CUDA Toolkit installed successfully.
```bash
nvcc --version
```
<br>

## [2] Create a shared Docker network for Ollama and Open WebUI to use.

&emsp; This command creates a Docker network, which will be shared by Ollama and Open WebUI for API communication. <br>
```bash
sudo docker network create ollama-net
```
<br>

## [3] Deploy Ollama (Backend) in Docker

&emsp; Create directories/mount points for our Ollama Docker container. <br>
```bash
mkdir -p ~/ollama
```
```bash
mkdir -p ~/ollama/ollama
```
```bash
cd ~/ollama
```
<br>

&emsp; Create a Docker Compose yml (yaml) file for Ollama.
```bash
touch docker-compose.yml
```
<br>

&emsp; Open the Docker Compose yml file and paste the example below.
```bash
nano docker-compose.yml
```
> ℹ️ To save changes in nano, select `Ctrl+x`, then `Shift+Y`, then `Enter`. <br>

&emsp; Example File: <br>
> ℹ️ Be sure to replace the /home/user directory with your own. <br>
```bash
services:
  ollama:
    image: ollama/ollama
    container_name: ollama
    ports:
      - "11434:11434"
    volumes:
      - /home/thomas@spartan23.home/ollama/ollama:/root/.ollama
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
```
cd ~/ollama
```
```bash
sudo docker compose up -d
```
```bash
sudo docker ps
```
<br>

## [4] Install Open WebUI (Frontend)

&emsp; Create directories/mount points for our Open WebUI Docker container. <br>
```bash
mkdir -p ~/open-webui
```
```bash
mkdir -p ~/open-webui/data
```
```bash
cd ~/open-webui
```
<br>

&emsp; Create a Docker Compose yml (yaml) file for Open WebUI.
```bash
touch docker-compose.yml
```
<br>

&emsp; Open the Docker Compose yml file and paste the example below.
```bash
nano docker-compose.yml
```
> ℹ️ To save changes in nano, select `Ctrl+x`, then `Shift+Y`, then `Enter`. <br>

&emsp; Example File: <br>
> ℹ️ Be sure to replace the /home/user directory with your own. <br>
```bash
services:
  open-webui:
    image: ghcr.io/open-webui/open-webui:cuda
    container_name: open-webui
    volumes:
      - /home/thomas@spartan23.home/open-webui/data:/app/backend/data
    ports:
      - ${OPEN_WEBUI_PORT-3000}:8080
    environment:
      - 'OLLAMA_BASE_URL=http://ollama:11434'
      - 'WEBUI_SECRET_KEY='
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
cd ~/open-webui
```
```bash
sudo docker compose up -d
```
<br>

&emsp; Access Open WebUI via one of the following URLs: <br>
`http://localhost:3000` <br>
`http://ipAddress:3000/` <br>
<br>

&emsp; Example: <br>
`http://192.168.50.20:3000/` <br>
<br>

&emsp; Once Open WebUI has loaded, you will be prompted to create an administrator account (username / password). <br>
<br>

## [5] Managing Models with Ollama

&emsp; Available models: https://ollama.com/library <br>
<br>

> ℹ️ **Note** You can also manage Ollama models within Open WebUI. <br>
> &emsp; > Select your user profile icon in the upper right-hand of the screen (or bottom left-hand of the screen). <br>
> &emsp; > Select 'Admin Panel'. <br>
> &emsp; > Select the 'Settings' tab along the top. <br>
> &emsp; > Select 'Connections' from the menu on the left. <br>
> &emsp; > Locate your Ollama API. On the right, select the 'downward arrow over the flat line' to 'Manage' Ollama models. <br>
<br>

&emsp; Because we're using Docker to host Ollama, we need to pass any Ollama CLI commands through Docker and into the Ollama Docker container. <br>
<br> 

&emsp; List models currently on your system: <br>
```bash
sudo docker exec ollama ollama list
```
<br>

&emsp; Pull (download) new models: <br>
&emsp; Syntax: <br>
```bash
sudo docker exec ollama ollama pull <model>:<tag>
```
&emsp; Example Command: <br>
```bash
sudo docker exec ollama ollama pull tinyllama:1.1b
```
<br>

&emsp; Remove (delete) a model from your system: <br>
&emsp; Syntax: <br>
```bash
sudo docker exec ollama ollama rm <model>:<tag>
```
&emsp; Example Command: <br>
```bash
sudo docker exec ollama ollama rm tinyllama:1.1b
```
<br>
<br>

## Upgrade Ollama

```bash
sudo docker pull ollama/ollama
```
```bash
cd ~/ollama
```
```bash
sudo docker compose down
```
```bash
sudo docker compose up -d
```
<br>

## Upgrade Open WebUI

```bash
sudo docker pull ghcr.io/open-webui/open-webui:cuda
```
```bash
cd ~/open-webui
```
```bash
sudo docker compose down
```
```bash
sudo docker compose up -d
```
<br>

## "Uninstall" Ollama

TBD... <br>
<br>

## "Uninstall" Open WebUI

TBD... <br>
<br>
