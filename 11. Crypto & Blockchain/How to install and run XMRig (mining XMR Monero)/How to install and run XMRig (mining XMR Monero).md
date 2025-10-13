<a href="./Icons%20and%20Screenshots/20250805_110313.png">
  <img src="./Icons%20and%20Screenshots/20250805_110313.png" height="170"/>
</a>
<a href="./Icons%20and%20Screenshots/20250915_001213.png">
  <img src="./Icons%20and%20Screenshots/20250915_001213.png" height="170"/>
</a>

# How to install and run XMRig (mining XMR Monero)

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

## Recommended Operating System / Software

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu Desktop 24.04.x LTS</td>
  </tr>
  <tr>
    <td align="right">Mining Software</td>
    <td>XMRig | https://xmrig.com/</td>
  </tr>
</table>

> ℹ️ **Note** If you need help installing Ubuntu, please see our guide here: [How to install Ubuntu Desktop 24.04.2 LTS](../../01.%20Operating%20Systems/How%20to%20install%20Ubuntu%20Desktop%2024.04.2%20LTS/How%20to%20install%20Ubuntu%20Desktop%2024.04.2%20LTS.md).
<br>

✅ With this setup: <br>
- XMRig runs as a background service. <br>
- It restarts automatically on crash. <br>
- It auto-starts at boot. <br>
- Updating is done with one command. <br>
<br>

## ⛏️ Step 1: Install XMRig

<details>
  <summary>Expand for additional details.</summary>

### Update System

```bash
sudo apt update && sudo apt upgrade -y
```

### Install Dependencies

```bash
sudo apt install git build-essential cmake automake libtool autoconf libhwloc-dev libuv1-dev libssl-dev -y
```

### Clone XMRig

```bash
git clone https://github.com/xmrig/xmrig.git
```
```bash
cd xmrig
```

***

### (Optional) Modify the donation level.

Edit the donate.h file to disable the default donation: <br>

Open the src/donate.h file with a text editor: <br>

```bash
nano src/donate.h
```
> ℹ️ To save changes in nano, select `Ctrl+x`, then `Shift+Y`, then `Enter`. <br>
<br>

Locate the line that defines the default donation level: <br>
&emsp; `constexpr const int kDefaultDonateLevel = 1;` <br>
&emsp; `constexpr const int kMinimumDonateLevel = 1;` <br>
<br>

Change the value from 1 to 0: <br>
&emsp; `constexpr const int kDefaultDonateLevel = 0;` <br>
&emsp; `constexpr const int kMinimumDonateLevel = 0;` <br>
<br>

***

### Build the XMRig Binary (application software)

```bash
mkdir build && cd build
```
```bash
cmake ..
```
```bash
make -j$(nproc)
```
<br>

XMRig binary will be at: <br>
`~/xmrig/build/xmrig`

</details>

## ⛏️ Step 2: Create an XMRig Config File

<details>
  <summary>Expand for additional details.</summary>
<br>

Go to the following URL:
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

> ℹ️ Your config file will start off looking like the following. Once you start XMRig, it'll automatically update your configuration file (see example further down).

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
<br>

Run XMRig with the following commands and verify you're seeing Hash Rate from your rig in the pool:
```bash
cd ~/xmrig/build/
```
```bash
./xmrig -c config.json
```

Example of udpated `config.json` file after running XMRig: <br>
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

</details>

## ⛏️ Step 3: Create a Systemd Service to run XMRig as a Service

<details>
  <summary>Expand for additional details.</summary>
<br>

Once you've confirmed your able to successfully run the XMRig software and it is producing Hash Rate within the pool, we can run XMRig as a service. <br>

Running XMRig as a service has the following benefits. <br>
&emsp; - Auto-start on boot; Mining starts automatically when the machine boots, even if you don’t log in. <br>
&emsp; - Automatic restarts on crash; If XMRig crashes, systemd can restart it automatically. <br>
&emsp; - Significantly reduces downtime and missed mining time. <br>
&emsp; - Cleaner process management; You don’t need to keep an open terminal session (whether that's via the Desktop or remote SSH session). <br>
&emsp; - systemctl start xmrig, stop, status, and journalctl -u xmrig give you full control and logs. <br>
&emsp; - Centralized logging; All XMRig output goes to journalctl, so you don’t lose logs when closing terminals. <br>
<br>

```bash
sudo nano /etc/systemd/system/xmrig.service
```
<br>

Paste: <br>
🔑 Replace userName / groupName with your Linux username. <br>

Syntax:
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
<br>

Example:
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

</details>

## ⛏️ Step 4: Enable & Start the XMRig Service

<details>
  <summary>Expand for additional details.</summary>

### Reload systemd

```bash
sudo systemctl daemon-reexec
```

### Enable at boot

```bash
sudo systemctl enable xmrig.service
```

### Start miner

```bash
sudo systemctl start xmrig.service
```

### Check status/logs

```bash
systemctl status xmrig.service
```
```bash
journalctl -fu xmrig.service
```

</details>

## ⛏️ Step 5: Create an automated Upgrade Script

<details>
  <summary>Expand for additional details.</summary>
<br>

Create a script to update XMRig + restart service: <br>
```bash
sudo nano /usr/local/bin/xmrig-update.sh
```
<br>

Paste: <br>

Syntax: <br>
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
<br>

Example:
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
<br>

Make it executable: <br>
```bash
sudo chmod +x /usr/local/bin/xmrig-update.sh
```
<br>

Now you can just run: <br>
```bash
xmrig-update.sh
```

</details>
