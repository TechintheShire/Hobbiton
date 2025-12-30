<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(4)%20-%20Longhorn.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(3)%20-%20MetalLB.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20RKE2%20NGINX.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

## How to deploy RKE2 with MetalLB, Ingress-NGINX, and Longhorn

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>

***
-->

### 📋 Prerequisites

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu 24.04.x LTS</td>
    <td><a href="../How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS.md">How to install Ubuntu Desktop 24.04.3 LTS</a></td>
  </tr>  
</table>

#

### 🌐 Reference Architecture Overview

This guide deploys a **3-node high-availability (HA)** Kubernetes cluster using:

| Component | Description |
|----------:|-------------|
| **RKE2** | Rancher Kubernetes Engine 2, Enterprise-grade Kubernetes distribution |
| **MetalLB** | Load Balancer for our Virtual IP Address Address (Endpoint) |
| **Ingress-NGINX** | Reverse Proxy (packaged with RKE2), routes Virtual IP Address (Endpoint) traffic by DNS/URL |
| **Longhorn** | Distributed block storage for Kubernetes workloads |
| **Rancher** | Web UI for RKE2 (optional but recommended) |

All nodes will run control-plane (management) + worker (running apps) roles. <br>

The network design in this guide uses **one Virtual IP Address (VIP)** to point all DNS entries to. From there, Ingress-NGINX (the built-in reverse proxy) routes requests to the correct app based on the DNS entry (URL). <br>

> ℹ️ In more advanced/production networks, you may separate “app traffic” and “storage traffic” (e.g., 10/25GbE for storage). This guide keeps everything on a single network for simplicity. Separating app and storage networks may be covered in a future update to this guide.

---

### 🧩 Cluster Variables (Edit these for your environment)

Pick values now and reuse them throughout this guide. <br>

> ✅ Tip: Keep these in a notes file so you can copy/paste throughout this guide. <br>

> ℹ️ I append `.spartan23.home` on my DNS entries because I am using Active Directory. Most users can simply use 'rancher' or 'longhorn' for DNS entries. <br>

| Variable | Example | Notes |
|---|---:|---|
| `VIP_IP` | `192.168.50.156` | MetalLB-advertised VIP used for Ingress |
| `NODE1_IP` | `192.168.50.157` | Control-plane + worker |
| `NODE2_IP` | `192.168.50.158` | Control-plane + worker |
| `NODE3_IP` | `192.168.50.159` | Control-plane + worker |
| `RANCHER_HOST` | `rancher.spartan23.home` | DNS name for Rancher UI |
| `LONGHORN_HOST` | `longhorn.spartan23.home` | DNS name for Longhorn UI |
| `LONGHORN_DISK` | `/dev/sdb` | A dedicated data disk per node for Longhorn (example) |
| `LONGHORN_MOUNT` | `/data/longhorn` | Mount point used by Longhorn (example) |
| `RKE2_TOKEN` | *(generated in step 4)* | Shared cluster token used on all nodes |

***

### [1] Prepare DNS (or /etc/hosts).

Create DNS records that point to your MetalLB VIP:

- `RANCHER_HOST` → `VIP_IP`
- `LONGHORN_HOST` → `VIP_IP`

> ℹ️ If you don’t have a DNS server, add the same mappings to `/etc/hosts` on **each** node (and on your workstation if you’ll browse from there). Replace `VIP_IP` with your MetalLB IP address. <br>
>
> Example: <br>
>
> ```
> VIP_IP  rancher
> VIP_IP  longhorn
> ```

<br>

***

### [2] Prepare Software for RKE2.

&emsp; Run these commands on ***[all nodes]***

Update and install packages: <br>
```bash
sudo apt update && sudo apt upgrade -y
```
```bash
sudo apt install -y curl vim git jq htop apt-transport-https ca-certificates
```

Disable swap (required for Kubernetes): <br>
```bash
sudo swapoff -a
```

> ⚠️ Misconfiguration within /etc/fstab can cause the system to fail to boot. <br>
> The command below makes a backup of the /etc/fstab file; then, comments out swap entries found in /etc/fstab file. <br>

```bash
sudo sed -i.bak '/ swap / s/^/#/' /etc/fstab || echo "No swap entry found in fstab"
```

<br>

***

### [3] Install RKE2 Binaries.

&emsp; Run this command on ***[all nodes]***

```bash
curl -sfL https://get.rke2.io | sudo sh -
```

<br>

***

### [4] Install (bootstrap) RKE2 (create the cluster).

&emsp; Run these commands on ***[node 1 only]***

Generate a strong token (save it for the next steps): <br>
```bash
openssl rand -hex 32
```

Example Output: <br>
```bash
85449a72f7fc19fa0169f276af1f1aad798cff6fc65e45242b4e8593e77ee3a1
```

Create the RKE2 config directory: <br>
```bash
sudo mkdir -p /etc/rancher/rke2
```

Create `/etc/rancher/rke2/config.yaml` on **node 1**:

> ℹ️ Replace the placeholders with your values (`RKE2_TOKEN`, `NODEx_IP`, and `VIP_IP`).

```bash
sudo tee /etc/rancher/rke2/config.yaml <<EOF
token: "<RKE2_TOKEN>"            # replace with the token you just generated above
tls-san:
  - <NODE1_IP>                   # replace with NODE1's IP address
  - <NODE2_IP>                   # replace with NODE2's IP address
  - <NODE3_IP>                   # replace with NODE3's IP address
  - <VIP_IP>                     # replace with your VIP_IP (MetalLB) IP address
write-kubeconfig-mode: "0644"
EOF
```

Example: <br>
```bash
sudo tee /etc/rancher/rke2/config.yaml <<EOF
token: "85449a72f7fc19fa0169f276af1f1aad798cff6fc65e45242b4e8593e77ee3a1"
tls-san:
  - 192.168.50.157
  - 192.168.50.158
  - 192.168.50.159
  - 192.168.50.156
write-kubeconfig-mode: "0644"
EOF
```

Start (bootstrap) RKE2 on node 1: <br>
```bash
sudo systemctl enable rke2-server --now
```

(Optional) Check the RKE2 service: <br>
> ℹ️ Exit with `Ctrl+C`.
```bash
sudo systemctl status rke2-server
```

Export kubeconfig and kubectl path (current shell session): <br>
```bash
export KUBECONFIG=/etc/rancher/rke2/rke2.yaml
export PATH=$PATH:/var/lib/rancher/rke2/bin
```
```bash
kubectl get nodes
```

(Optional but recommended) Persist kubectl access for your user: <br>
```bash
echo 'export KUBECONFIG=/etc/rancher/rke2/rke2.yaml' >> ~/.bashrc
echo 'export PATH=$PATH:/var/lib/rancher/rke2/bin' >> ~/.bashrc
source ~/.bashrc
```

<br>

***

### [5] Join nodes 2 and 3 to the RKE2 cluster.

&emsp; Run these commands on ***[node 2 and node 3]***

On **each** additional node, create the config directory: <br>
```bash
sudo mkdir -p /etc/rancher/rke2
```

Create `/etc/rancher/rke2/config.yaml`:

> ℹ️ Replace the placeholders with your values (`RKE2_TOKEN`, `NODEx_IP`, and `VIP_IP`).

> ⚠️ Notice the `server` line. This instructs RKE2 to join these nodes to an existing RKE2 cluster.

```bash
sudo tee /etc/rancher/rke2/config.yaml >/dev/null <<EOF
server: https://<NODE1_IP>:9345   # replace with NODE1's IP address (bootstrap node)
token: "<RKE2_TOKEN>"             # replace with the token you previously generated
tls-san:
  - <NODE1_IP>                    # replace with NODE1's IP address
  - <NODE2_IP>                    # replace with NODE2's IP address
  - <NODE3_IP>                    # replace with NODE3's IP address
  - <VIP_IP>                      # replace with your VIP_IP (MetalLB) IP address
write-kubeconfig-mode: "0644"
EOF
```

Example: <br>
```bash
sudo tee /etc/rancher/rke2/config.yaml >/dev/null <<EOF
server: https://192.168.50.157:9345
token: "85449a72f7fc19fa0169f276af1f1aad798cff6fc65e45242b4e8593e77ee3a1"
tls-san:
  - 192.168.50.157
  - 192.168.50.158
  - 192.168.50.159
  - 192.168.50.156
write-kubeconfig-mode: "0644"
EOF
```

Start RKE2 on node 2 and node 3: <br>
```bash
sudo systemctl enable rke2-server --now
```

(Optional) Check: <br>
```bash
sudo systemctl status rke2-server
```

Export kubeconfig: <br>
```bash
export KUBECONFIG=/etc/rancher/rke2/rke2.yaml
export PATH=$PATH:/var/lib/rancher/rke2/bin
```
```bash
kubectl get nodes
```

If the above worked, you can persist access to kubectl using the following commands: <br>
```bash
echo 'export KUBECONFIG=/etc/rancher/rke2/rke2.yaml' >> ~/.bashrc
echo 'export PATH=$PATH:/var/lib/rancher/rke2/bin' >> ~/.bashrc
source ~/.bashrc
```

At this point, all three nodes should report `Ready` and labeled as `control-plane`. <br>
```bash
kubectl get nodes
```

<br>

***

### [6] Networking Layer: MetalLB + Ingress-NGINX.

&emsp; Run these commands on ***[node 1 only]***

Install MetalLB: <br>
```bash
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.5/config/manifests/metallb-native.yaml
```
 
Wait for (check) MetalLB pods: <br>
```bash
kubectl get pods -n metallb-system
```

> ⚠️ Do NOT move to the next step until these pods are up and running. <br>

Deploy the MetalLB configuration: <br>

> ℹ️ Replace VIP_IP in all locations. <br>
> 
> Because we are using Ingress-NGINX (a reverse proxy), we only need one MetalLB IP address, even when running multiple Plex instances that all use the same internal port (32400). <br>
> 
> Ingress-NGINX routes traffic to the correct Plex server based on the DNS hostname (URL) being used, not by assigning a separate IP address to each app. This allows many services to safely share the same IP and ports (80/443) while still remaining completely independent. <br>
> 
> In other words — one IP can front many services. <br>

```bash
cat > metallb-ingress-vip.yaml <<EOF
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: ingress-pool
  namespace: metallb-system
spec:
  addresses:
    - <VIP_IP>-<VIP_IP>            # replace with your VIP_IP (MetalLB) IP address
---
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: ingress-l2adv
  namespace: metallb-system
spec:
  ipAddressPools:
    - ingress-pool
---
apiVersion: v1
kind: Service
metadata:
  name: rke2-ingress-nginx-lb
  namespace: kube-system
spec:
  type: LoadBalancer
  loadBalancerIP: <VIP_IP>         # replace with your VIP_IP (MetalLB) IP address
  selector:
    app.kubernetes.io/name: rke2-ingress-nginx
  ports:
    - name: http
      port: 80
      targetPort: 80
    - name: https
      port: 443
      targetPort: 443
EOF
```

Example: <br>
```bash
cat > metallb-ingress-vip.yaml <<EOF
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: ingress-pool
  namespace: metallb-system
spec:
  addresses:
    - 192.168.50.156-192.168.50.156
---
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: ingress-l2adv
  namespace: metallb-system
spec:
  ipAddressPools:
    - ingress-pool
---
apiVersion: v1
kind: Service
metadata:
  name: rke2-ingress-nginx-lb
  namespace: kube-system
spec:
  type: LoadBalancer
  loadBalancerIP: 192.168.50.156
  selector:
    app.kubernetes.io/name: rke2-ingress-nginx
  ports:
    - name: http
      port: 80
      targetPort: 80
    - name: https
      port: 443
      targetPort: 443
EOF
```

Deploy (start) MetalLB: <br>
```bash
kubectl apply -f metallb-ingress-vip.yaml
```

Quick verification: <br>
```bash
kubectl get ippools -n metallb-system
kubectl get l2advertisements -n metallb-system
kubectl get svc -n kube-system rke2-ingress-nginx-lb
```

<br>

***

### [7] Install Rancher (RKE2 UI) using Ingress-NGINX (Optional but recommended).

&emsp; Run these commands on ***[node 1 only]***

Install Helm: <br>
```bash
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```
Check:
```bash
helm version
```

Install cert-manager (for TLS): <br>
```bash
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.15.3/cert-manager.crds.yaml
```
```bash
helm repo add jetstack https://charts.jetstack.io
```
```bash
helm repo update
```
```bash
helm install cert-manager jetstack/cert-manager \
  --namespace cert-manager \
  --create-namespace \
  --version v1.15.3
```

Install Rancher: <br>
```bash
helm repo add rancher https://releases.rancher.com/server-charts/stable
helm repo update
```
```bash
kubectl create namespace cattle-system
```

> ℹ️ Replace `RANCHER_HOST` (Rancher DNS entry) and `BOOTSTRAP_PASSWORD`. <br>

> ℹ️ We will be changing the bootstrap password after initial login. <br>

```bash
helm install rancher rancher/rancher \
  --namespace cattle-system \
  --set hostname=<RANCHER_HOST> \
  --set replicas=3 \
  --set ingress.ingressClassName=nginx \
  --set ingress.tls.source=rancher \
  --set bootstrapPassword='<BOOTSTRAP_PASSWORD>'
```

Example: <br>
```bash
helm install rancher rancher/rancher \
  --namespace cattle-system \
  --set hostname=rancher.spartan23.home \
  --set replicas=3 \
  --set ingress.ingressClassName=nginx \
  --set ingress.tls.source=rancher \
  --set bootstrapPassword='Password123!'
```

Monitor deployment: <br>

> ℹ️ You want all `rancher-xxxx` pods in `Running` state.

```bash
kubectl get pods -n cattle-system
```

Check Service/Ingress: <br>
```bash
kubectl get svc -n cattle-system
kubectl get ingress -n cattle-system
```

Access Rancher UI: <br>
```text
https://<RANCHER_HOST>
```

Example: <br>
```bash
https://rancher.spartan23.home
```

> ✅ After first login, change the admin password (`BOOTSTRAP_PASSWORD`) and set your server URL (`https://<RANCHER_HOST>`).

Initial login: <br>
&emsp; Username: `admin` <br>
&emsp; Password: `Password123!` <br>
&emsp; Set server URL to your `https://<RANCHER_HOST>` (Example: `https://rancher.spartan23.home`) <br>

Be sure to update/change your admin password after initial login: <br>
&emsp; > Log into the Rancher UI (your URL above). <br>
&emsp; > Select `Users & Authentication`. <br>
&emsp; > Select the `three-dot` hamburger menu (on the right of the admin user) <br>
&emsp; > Select `Edit Config`. <br>
&emsp; > Update your password in the `New Password` and `Confirm Password` fields. <br>
&emsp; > Select `Save`. <br>

<br>

***

### [8] Prepare Software and Disks for Longhorn.

&emsp; Run these commands on ***[all nodes]***

Update and install software/packages required for Longhorn:
```bash
sudo apt install -y open-iscsi nfs-common
```
```bash
sudo systemctl enable --now iscsid || true
```
```bash
sudo systemctl enable --now open-iscsi || true
```
Check:
```bash
/usr/bin/iscsiadm --help
```

#### Disk and filesystem preparation

> ⚠️ These steps will **modify** a disk. Double-check the disk name first (example disk: `LONGHORN_DISK`).
>
> ✅ Recommendation: dedicate **one disk per node** for Longhorn data.

Inspect disks (DO NOT skip): <br>
```bash
lsblk
```

#

Create a single ext4 partition (in my example, I use `/dev/sdb`): <br>
```bash
sudo parted <LONGHORN_DISK> --script mklabel gpt mkpart primary ext4 0% 100%
```

Example:
```bash
sudo parted /dev/sdb --script mklabel gpt mkpart primary ext4 0% 100%
```

#

Make sure the kernel sees the new partition: <br>
```bash
sudo partprobe <LONGHORN_DISK>
```

Example:
```bash
sudo partprobe /dev/sdb
```

#

Create filesystem (example partition `/dev/sdb1`): <br>
```bash
sudo mkfs.ext4 <LONGHORN_DISK>1
```

Example:
```bash
sudo mkfs.ext4 /dev/sdb1
```

#

Create mount point: <br>
```bash
sudo mkdir -p <LONGHORN_MOUNT>
```

Example:
```bash
sudo mkdir -p /data/longhorn
```

#

Get the filesystem UUID (example `/dev/sdb1`): <br>
```bash
UUID=$(sudo blkid -s UUID -o value <LONGHORN_DISK>1)
```

Example:
```bash
UUID=$(sudo blkid -s UUID -o value /dev/sdb1)
```

Verify the UUID:
```bash
echo "Detected UUID: $UUID"
```

#

Add the filesystem/mount to fstab (example `/data/longhorn`):
```bash
echo "UUID=$UUID <LONGHORN_MOUNT> ext4 defaults,noatime 0 2" | sudo tee -a /etc/fstab
```

Example:
```bash
echo "UUID=$UUID /data/longhorn ext4 defaults,noatime 0 2" | sudo tee -a /etc/fstab
```

#

Mount and verify: <br>
```bash
sudo systemctl daemon-reload
```
```bash
sudo mount -a
```
```bash
df -h <LONGHORN_MOUNT>
```
Example:
```bash
df -h /data/longhorn
```

#

<br>

***

### [9] Install Longhorn.

&emsp; Run these commands on ***[node 1 only]***

```bash
helm repo add longhorn https://charts.longhorn.io
kubectl create namespace longhorn-system
```

Create Helm values: <br>
```bash
cat > longhorn.yaml <<'EOF'
service:
  ui:
    type: ClusterIP
defaultSettings:
  defaultReplicaCount: 3
  defaultDataPath: "<LONGHORN_MOUNT>"  # replace with your Longhorn mount path
EOF
```

Example:
```bash
cat > longhorn.yaml <<'EOF'
service:
  ui:
    type: ClusterIP
defaultSettings:
  defaultReplicaCount: 3
  defaultDataPath: "/data/longhorn"
EOF
```

Install: <br>
```bash
helm install longhorn longhorn/longhorn -n longhorn-system -f longhorn.yaml
kubectl get pods -n longhorn-system
```

***

### [10] Install Longhorn Ingress (TLS + Basic Authentication)

&emsp; Run these commands on ***[node 1 only]***

Generate basic-auth credentials (creates local file `longhorn-auth`): <br>
```bash
sudo apt install -y apache2-utils
```
```bash
htpasswd -c longhorn-auth admin
```
```bash
kubectl create secret generic longhorn-basic-auth --from-file=auth=longhorn-auth -n longhorn-system
```
```bash
rm longhorn-auth
```

Generate self-signed TLS cert for `LONGHORN_HOST`: <br>
```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout longhorn.key -out longhorn.crt -subj "/CN=<LONGHORN_HOST>"
```
Example:
```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout longhorn.key -out longhorn.crt -subj "/CN=longhorn.spartan23.home"
```
Add the self-signed TLS cert:
```bash
kubectl create secret tls longhorn-tls --cert=longhorn.crt --key=longhorn.key -n longhorn-system
```
```bash
rm longhorn.key longhorn.crt
```

Create the Ingress: <br>
```bash
cat > longhorn-ingress.yaml <<'EOF'
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: longhorn-ingress
  namespace: longhorn-system
  annotations:
    nginx.ingress.kubernetes.io/auth-type: basic
    nginx.ingress.kubernetes.io/auth-secret: longhorn-basic-auth
    nginx.ingress.kubernetes.io/auth-realm: "Authentication Required"
    nginx.ingress.kubernetes.io/ssl-redirect: "true"
spec:
  ingressClassName: nginx
  tls:
    - hosts:
        - <LONGHORN_HOST>        # replace with your Longhorn DNS entry
      secretName: longhorn-tls
  rules:
    - host: <LONGHORN_HOST>      # replace with your Longhorn DNS entry
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: longhorn-frontend
                port:
                  number: 80
EOF
```

Example:
```bash
cat > longhorn-ingress.yaml <<'EOF'
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: longhorn-ingress
  namespace: longhorn-system
  annotations:
    nginx.ingress.kubernetes.io/auth-type: basic
    nginx.ingress.kubernetes.io/auth-secret: longhorn-basic-auth
    nginx.ingress.kubernetes.io/auth-realm: "Authentication Required"
    nginx.ingress.kubernetes.io/ssl-redirect: "true"
spec:
  ingressClassName: nginx
  tls:
    - hosts:
        - longhorn.spartan23.home
      secretName: longhorn-tls
  rules:
    - host: longhorn.spartan23.home
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: longhorn-frontend
                port:
                  number: 80
EOF
```
```bash
kubectl apply -f longhorn-ingress.yaml
```
Check:
```bash
kubectl get ingress -n longhorn-system
```

Access Longhorn UI:
```bash
https://<LONGHORN_HOST>
```
Example:
```bash
https://longhorn.spartan23.home
```

By default, Longhorn is deployed using `/var/lib/longhorn` as its disk path (if not specified in `longhorn.yaml`). <br>

Because our Longhorn yaml included `defaultDataPath: "/data/longhorn"`, we don't have to worry about these steps below; however, if you need to change the default location for your Longhorn disk path, here is how it is done. <br>

In this example, we change the disk path from `/var/lib/longhorn` to `/data/longhorn`. <br>

Example: <br>
Access UI: `https://longhorn.spartan23.home`. <br>
&emsp; > Select `Nodes`. <br>
&emsp; > Select `Edit Node and Disks` under '*Operation*' for the respective node. <br>
&emsp; > For the disk / path `/var/lib/longhorn`, set `Scheduling` to `Disable` and `Eviction Requested` to `True`. <br>
&emsp; > Select `Add Disk`. <br>
&emsp; > Give your new disk / path a Name. <br>
&emsp; > Set the disk / path to `/data/longhorn`. <br>
&emsp; > Set `Storage Reserved` to  `8` Gi. <br>
&emsp; > Set `Scheduling` to `Enable` and leave `Eviction Requested` as `False`. <br>
&emsp; > Select `Save`. <br>
&emsp; > Monitor the eviction process by expanding the '`+`' sign on the left associated with the node. <br>
&emsp; > Once the disk / path `/var/lib/longhorn` shows '`0`' Replicas, you can go back into the `Edit Node and Disks` menu and select the `Delete` garbage-can icon. <br>

<br>

***

## 🎉 Congratulations, you're finished deploying a high-availability RKE2 cluster. Now we're ready to deploy apps!

Please see my guides on deploying applications (like PLEX, Emby, Jellyfin, Jellyseerr, SABnzbd, Radarr, Sonarr, Lidarr... and MORE!) into RKE2. <br>

<br>

***
## Appendix

### VM (Virtual Machine) | How to expand your VM’s virtual disk, disk partition, and ext4 filesystem.

<details>
  <summary>Expand for additional details.</summary>
<br>

This section covers how to expand your VM’s virtual disk, disk partition, and ext4 filesystem to provide more capacity for your PVCs (persistent volume claims) in Longhorn. These steps assume you followed this guide and used disk sdb (and filesystem sdb1) for your /data/longhorn mount. <br>

&emsp; > Expand the size of your virtual disk within your hypervisor (VMware, Proxmox, unRAID... etc.). <br>
&emsp; > SSH or log into your Ubuntu VM. <br>
&emsp; > Rescan your expanded disk and verify it sees the new capacity/size; in our example, `sdb`. <br>
```
echo 1 | sudo tee /sys/class/block/sdb/device/rescan
lsblk
```

> ℹ️ If the rescan does not allow Ubuntu to recognize the additional capacity, reboot and check again.
> ```
> lsblk
> ```

&emsp; > Resize the sdb1 partition on sdb. <br>
```bash
sudo parted /dev/sdb
```
```bash
print
```

&emsp; You will likely see the following message: <br>

<div style="user-select: none;">
<pre><codex>
Warning: Not all of the space available to /dev/sdb appears to be used, you can fix the GPT to use all of the space (an extra 134217728 blocks) or continue with the current setting?
Fix/Ignore?
</codex></pre>
</div>

&emsp; > Type: <br>
```bash
Fix
```

&emsp; > Hit `Enter`. <br>

Example output:
<div style="user-select: none;">
<pre><codex>
Model: VMware Virtual disk (scsi)
Disk /dev/sdb: 137GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  68.7GB  68.7GB  ext4         primary
</codex></pre>
</div>

&emsp; > In our example, we want to resize partition number '1'. <br>
```bash
resizepart 1 100%
```

&emsp; You will likely see the following message: <br>

<div style="user-select: none;">
<pre><codex>
Warning: Partition /dev/sdb1 is being used. Are you sure you want to continue?
</codex></pre>
</div>

&emsp; > Type: <br>
```bash
Yes
```

&emsp; > Hit `Enter`. <br>

```bash
quit
```

&emsp; > Extend the ext4 filesystem on sdb1. <br>
```bash
sudo resize2fs /dev/sdb1
```

&emsp; > Verify sdb1 now shows the correct capacity. <br>
```bash
lsblk
```

</details>
