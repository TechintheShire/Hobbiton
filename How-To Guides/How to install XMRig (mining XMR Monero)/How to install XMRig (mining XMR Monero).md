<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20XMRig.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

## How to install XMRig (mining XMR Monero)

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

### Table of Contents

&emsp; [1] Install XMRig. <br>
&emsp; [2] Create an XMRig Config File. <br>
&emsp; [3] Create a Systemd Service to run XMRig as a Service. <br>
&emsp; [4] Enable and Start the XMRig Service. <br>
&emsp; [5] Create an automated Upgrade Script. <br>

#

### 🌐 Recommended Operating System / Software

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu Desktop 24.04.x LTS</td>
    <td><a href="../How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS.md">How to install Ubuntu Desktop 24.04.3 LTS</a></td>
  </tr>
  <tr>
    <td align="right">Mining Software</td>
    <td>XMRig</td>
    <td>https://xmrig.com/</td>
  </tr>
</table>

✅ With this setup: <br>
- XMRig runs as a background service. <br>
- It restarts automatically on crash. <br>
- It auto-starts at boot. <br>
- Updating is done with one command. <br>

<br>

***
### ⛏️ [1] Install XMRig.

&emsp; Update System: <br>

```bash
sudo apt update && sudo apt upgrade -y
```

&emsp; Install Dependencies: <br>

```bash
sudo apt install git build-essential cmake automake libtool autoconf libhwloc-dev libuv1-dev libssl-dev -y
```

&emsp; Clone XMRig: <br>

```bash
git clone https://github.com/xmrig/xmrig.git
```
```bash
cd xmrig
```

#

&emsp; **(Optional) Modify the donation level.** <br>

&emsp;&emsp; Open the `src/donate.h` file with a text editor: <br>

```bash
nano src/donate.h
```

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

&emsp; Locate the line that defines the default donation level: <br>
&emsp;&emsp; `constexpr const int kDefaultDonateLevel = 1;` <br>
&emsp;&emsp; `constexpr const int kMinimumDonateLevel = 1;` <br>

&emsp; Change the value from 1 to 0: <br>
&emsp;&emsp; `constexpr const int kDefaultDonateLevel = 0;` <br>
&emsp;&emsp; `constexpr const int kMinimumDonateLevel = 0;` <br>

#

&emsp; Build the XMRig Binary (application software): <br>

```bash
mkdir build && cd build
```
```bash
cmake ..
```
```bash
make -j$(nproc)
```

&emsp; XMRig binary will be at: `~/xmrig/build/xmrig` <br>
<br>

***
### ⛏️ [2] Create an XMRig Config File.

&emsp; Go to the following URL:

```bash
https://xmrig.com/wizard
```

&emsp; > Under 'Start', select 'New configuration'. <br>
&emsp;&emsp; > Enter your pool (I currently recommend `HashVault.pro`) and wallet address information. <br>
&emsp; > Select 'Backends' <br>
&emsp;&emsp;&emsp; Enabling `CPU` will enable mining using your CPU. <br>
&emsp;&emsp;&emsp; Enabling `OpenCL` will enable mining for AMD GPUs (not recommended as it is inefficient, power vs the extra hash rate). <br>
&emsp;&emsp;&emsp; Enabling `CUDA` will enable mining for NVIDIA GPUs (not recommended as it is inefficient, power vs the extra hash rate). <br>
&emsp; > Select 'Misc' and adjust Donation percentage if needed. <br>
&emsp; > Select 'Result'. <br>
&emsp;&emsp; > Download the generated `config.json` file. <br>

> ℹ️ Your config file will start off looking like the following. Once you start XMRig, it'll automatically update your configuration file (see example further down below).

```bash
{
    "autosave": true,
    "cpu": true,
    "opencl": false,
    "cuda": false,
    "pools": [
        {
            "url": "pool.hashvault.pro:443",
            "user": "<wallet address>", # I removed my wallet address for privacy.
            "keepalive": true,
            "tls": true
        }
    ]
}
```

&emsp; > Move this `config.json` file to your `~/xmrig/build` directory, within the same folder as the './xmrig' binary we created. <br>

&emsp; > Run XMRig with the following commands and verify you're seeing Hash Rate from your rig in the pool: <br>
```bash
cd ~/xmrig/build/
```
```bash
./xmrig -c config.json
```

&emsp; Example of updated `config.json` file after running XMRig: <br>

> ℹ️ This output is from a Proxmox Virtual Machine with 8x vCPUs. <br>

```bash
{
    "api": {
        "id": null,
        "worker-id": null
    },
    "http": {
        "enabled": false,
        "host": "127.0.0.1",
        "port": 0,
        "access-token": null,
        "restricted": true
    },
    "autosave": true,
    "background": false,
    "colors": true,
    "title": true,
    "randomx": {
        "init": -1,
        "init-avx2": -1,
        "mode": "auto",
        "1gb-pages": false,
        "rdmsr": true,
        "wrmsr": true,
        "cache_qos": false,
        "numa": true,
        "scratchpad_prefetch_mode": 1
    },
    "cpu": {
        "enabled": true,
        "huge-pages": true,
        "huge-pages-jit": false,
        "hw-aes": null,
        "priority": null,
        "memory-pool": false,
        "yield": true,
        "asm": true,
        "argon2-impl": null,
        "argon2": [0, 1, 2, 3, 4, 5, 6, 7],
        "cn": [
            [1, 0],
            [1, 1],
            [1, 2],
            [1, 3],
            [1, 4],
            [1, 5],
            [1, 6],
            [1, 7]
        ],
        "cn-heavy": [
            [1, 0],
            [1, 1],
            [1, 2],
            [1, 3]
        ],
        "cn-lite": [
            [1, 0],
            [1, 1],
            [1, 2],
            [1, 3],
            [1, 4],
            [1, 5],
            [1, 6],
            [1, 7]
        ],
        "cn-pico": [
            [2, 0],
            [2, 1],
            [2, 2],
            [2, 3],
            [2, 4],
            [2, 5],
            [2, 6],
            [2, 7]
        ],
        "cn/upx2": [
            [2, 0],
            [2, 1],
            [2, 2],
            [2, 3],
            [2, 4],
            [2, 5],
            [2, 6],
            [2, 7]
        ],
        "ghostrider": [
            [8, 0],
            [8, 1],
            [8, 2],
            [8, 3],
            [8, 4],
            [8, 5],
            [8, 6],
            [8, 7]
        ],
        "rx": [0, 1, 2, 3, 4, 5, 6, 7],
        "rx/wow": [0, 1, 2, 3, 4, 5, 6, 7],
        "cn-lite/0": false,
        "cn/0": false,
        "rx/arq": "rx/wow"
    },
    "opencl": {
        "enabled": false,
        "cache": true,
        "loader": null,
        "platform": "AMD",
        "adl": true
    },
    "cuda": {
        "enabled": false,
        "loader": null,
        "nvml": true
    },
    "log-file": null,
    "donate-level": 0,
    "donate-over-proxy": 1,
    "pools": [
        {
            "algo": null,
            "coin": null,
            "url": "pool.hashvault.pro:443",
            "user": "<wallet address>", # I removed my wallet address for privacy.
            "pass": null,
            "rig-id": null,
            "nicehash": false,
            "keepalive": true,
            "enabled": true,
            "tls": true,
            "sni": false,
            "tls-fingerprint": null,
            "daemon": false,
            "socks5": null,
            "self-select": null,
            "submit-to-origin": false
        }
    ],
    "retries": 5,
    "retry-pause": 5,
    "print-time": 60,
    "health-print-time": 60,
    "dmi": true,
    "syslog": false,
    "tls": {
        "enabled": false,
        "protocols": null,
        "cert": null,
        "cert_key": null,
        "ciphers": null,
        "ciphersuites": null,
        "dhparam": null
    },
    "dns": {
        "ip_version": 0,
        "ttl": 30
    },
    "user-agent": null,
    "verbose": 0,
    "watch": true,
    "pause-on-battery": false,
    "pause-on-active": false
}
```
<br>

***
### ⛏️ [3] Create a Systemd Service to run XMRig as a Service.

&emsp; Once you've confirmed you're able to successfully run the XMRig software and it is producing Hash Rate within the pool, we can run XMRig as a service. <br>

> ℹ️ Running XMRig as a service has the following benefits. <br>
> - Auto-start on boot; Mining starts automatically when the machine boots, even if you don’t log in. <br>
> - Automatic restarts on crash; If XMRig crashes, systemd can restart it automatically. <br>
> - Significantly reduces downtime and missed mining time. <br>
> - Cleaner process management; You don’t need to keep an open terminal session (via Desktop or remote SSH session). <br>
> - systemctl start xmrig, stop, status, and journalctl -u xmrig give you full control and logs. <br>
> - Centralized logging; All XMRig output goes to journalctl, so you don’t lose logs when closing terminals. <br>

```bash
sudo nano /etc/systemd/system/xmrig.service
```

&emsp; Paste the following into the `xmrig.service` file: <br>

&emsp; Syntax: <br>
&emsp; 🔑 Replace userName / groupName with your Linux username. <br>

```bash
[Unit]
Description=XMRig Monero Miner
After=network.target

[Service]
ExecStart=/home/userName/xmrig/build/xmrig -c /home/userName/xmrig/build/config.json
WorkingDirectory=/home/userName/xmrig/build
User=userName
Group=groupName # same as userName
Restart=always
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
```

&emsp; Example: <br>
```bash
[Unit]
Description=XMRig Monero Miner
After=network.target

[Service]
ExecStart=/home/xmrig-04/xmrig/build/xmrig -c /home/xmrig-04/xmrig/build/config.json
WorkingDirectory=/home/xmrig-04/xmrig/build
User=xmrig-04
Group=xmrig-04
Restart=always
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
```
<br>

***
### ⛏️ [4] Enable and Start the XMRig Service.

&emsp; Reload systemd: <br>

```bash
sudo systemctl daemon-reexec
```

&emsp; Enable the XMRig service at boot: <br>

```bash
sudo systemctl enable xmrig.service
```

&emsp; Start the XMRig service: <br>

```bash
sudo systemctl start xmrig.service
```

&emsp; Check status/logs: <br>

```bash
systemctl status xmrig.service
```
```bash
journalctl -fu xmrig.service
```
<br>

***
### ⛏️ [5] Create an automated Upgrade Script.

&emsp; Create a script to update XMRig + restart service: <br>

```bash
sudo nano /usr/local/bin/xmrig-update.sh
```

&emsp; Paste the following into the `xmrig-update.sh` file: <br>

&emsp; Syntax: <br>

```bash
#!/bin/bash
set -e

echo "[*] Updating XMRig..."
cd /home/YOURUSER/xmrig
git pull
cd build
make -j$(nproc)

echo "[*] Restarting XMRig service..."
sudo systemctl restart xmrig.service

echo "[✓] Update complete!"
```

&emsp; Example: <br>

```bash
#!/bin/bash
set -e

echo "[*] Updating XMRig..."
cd /home/xmrig-04/xmrig
git pull
cd build
make -j$(nproc)

echo "[*] Restarting XMRig service..."
sudo systemctl restart xmrig.service

echo "[✓] Update complete!"
```

&emsp; Make it executable: <br>

```bash
sudo chmod +x /usr/local/bin/xmrig-update.sh
```

&emsp; Now you can just run: <br>

```bash
xmrig-update.sh
```
