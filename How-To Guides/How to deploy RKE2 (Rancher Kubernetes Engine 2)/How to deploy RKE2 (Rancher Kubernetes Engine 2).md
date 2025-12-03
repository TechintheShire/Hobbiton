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

***

### Table of Contents

&emsp; [1] Prepare DNS <br>
&emsp; [2] Prepare Software for RKE2 <br>
&emsp; [3] Install RKE2 Binaries <br>
&emsp; [4] Install (bootstrap) RKE2, Create the cluster <br>
&emsp; [5] Join nodes to the RKE2 cluster <br>
&emsp; [6] Networking Layer: MetalLB + Ingress-NGINX <br>
&emsp; [7] Install RKE2 (Rancher) UI with Ingress-NGINX <br>
&emsp; [8] Prepare Software and Disks for Longhorn <br>
&emsp; [9] Install Longhorn <br>

***

### 🌐 Environment Overview

This guide will deploy a 3-node high-availability cluster running all of our components, RKE2, MetalLB, Ingress-NGINX, and Longhorn. In a true production environment, it may be helpful (but not required) to spread some of these components across different sets of nodes depending on performance, scalability, or capacity needs. The network design will expose a single Virtual (floating) IP address that all our DNS (URL) records will be pointed to. Our Ingress-NGINX (reverse proxy) will sort and route traffic to the appropriate service/app based on the incoming DNS/URL. <br>

> ℹ️ If you need help deploying Ubuntu Desktop, please see my guide here, [How to install Ubuntu Desktop 24.04.3 LTS](../How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS/How%20to%20install%20Ubuntu%20Desktop%2024.04.3%20LTS.md). <br>

| Component | Description |
|-----------|-------------|
| **RKE2 (Rancher Kubernetes Engine 2)** | Enterprise-grade Kubernetes Distribution |
| **MetalLB** | Load Balancer for our Virtual IP Address (Endpoint) |
| **Ingress-NGINX** | Reverse Proxy (built-in w/RKE2), routes VIP (Endpoint) traffic by DNS/URL |
| **Longhorn** | Distributed Storage for Kubernetes |

### Node Layout

MetalLB (Load Balancer) will listen across all nodes with VIP (Endpoint): 192.168.50.156 <br>

| Node (hostname) | IP | Component |
|-----------------|----|-----------|
| rke2-n1 | 192.168.50.157 | RKE2 (Control-Plane + Worker) + MetalLB + Ingress-NGINX - Longhorn |
| rke2-n2 | 192.168.50.158 | RKE2 (Control-Plane + Worker) + MetalLB + Ingress-NGINX - Longhorn |
| rke2-n3 | 192.168.50.159 | RKE2 (Control-Plane + Worker) + MetalLB + Ingress-NGINX - Longhorn |

<br>

***

### [1] Prepare DNS

If you have a DNS server: <br>

Prepare a DNS record pointing 'rancher.spartan23.home' to '192.168.50.156'. <br>
Prepare a DNS record pointing 'longhorn.spartan23.home' to '192.168.50.156'. <br>

> ℹ️ My Ubuntu machines (nodes) are joined to a Microsoft Active Directory Domain, which is why you see '.spartan23.home' appended to my DNS records. You likely only need to use 'rancher', not 'rancher.spartan23.home'.

Otherwise, update each node's '/etc/hosts' file with these DNS entries. <br><br>

***

### [2] Prepare Software for RKE2

&emsp; ***[all nodes]***

Update and install software/packages: <br>
```bash
sudo apt update && sudo apt upgrade -y
```
```bash
sudo apt install -y curl vim git jq htop apt-transport-https ca-certificates
```

Disable swap (required for RKE2/(Kubernetes): <br>
```bash
sudo swapoff -a
```
```bash
sudo sed -i.bak '/ swap / s/^/#/' /etc/fstab || echo "No swap entry found in fstab"
```

<br>

***

### [3] Install RKE2 Binaries

&emsp; ***[all nodes]***

```bash
curl -sfL https://get.rke2.io | sudo sh -
```

<br>

***

### [4] Install (bootstrap) RKE2, Create the cluster

&emsp; ***[node 1, rke2-n1 only]***

Generate a strong randomized token: <br>
```bash
openssl rand -hex 32
```

Example Output: <br>
```bash
85449a72f7fc19fa0169f276af1f1aad798cff6fc65e45242b4e8593e77ee3a1
```

> ℹ️ Replace `<token>` in the syntax below with the token you just created above.

Create RKE2 config for rke2-n1: <br>
```bash
sudo mkdir -p /etc/rancher/rke2
```

Syntax for config.yaml: <br>

> ℹ️ Replace `<token>` with the token we previously generated.

```bash
sudo tee /etc/rancher/rke2/config.yaml <<EOF
token: "<token>"
tls-san:
  - 192.168.50.157
  - 192.168.50.158
  - 192.168.50.159
  - 192.168.50.156
write-kubeconfig-mode: "0644"
EOF
```
Example of config.yaml with our token: <br>
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

Start the RKE2 service: <br>
```bash
sudo systemctl enable rke2-server --now
```

(Optional) Check the RKE2 service: <br>

> ℹ️ Exit the status check with `Ctrl+c`.

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

<br>

***

### [5] Join nodes to the RKE2 cluster

&emsp; ***[nodes 2 and 3, rke2-n2 and rke2-n3]*** 

```bash
sudo mkdir -p /etc/rancher/rke2
```

> ℹ️ Notice the 'server' line.

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

Start the RKE2 service: <br>
```bash
sudo systemctl enable rke2-server --now
```

(Optional) Check the RKE2 service: <br>
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

At this point, rke2-n1, rke2-n2, rke2-n3 should all report 'Ready' and labeled as 'control-plane'. <br>
```bash
kubectl get nodes
```

<br>

***

### [6] Networking Layer: MetalLB + Ingress-NGINX

&emsp; ***[node 1, rke2-n1 only]***

Install MetalLB: <br>
```bash
kubectl apply -f https://raw.githubusercontent.com/metallb/metallb/v0.14.5/config/manifests/metallb-native.yaml
```

Monitor and wait for pods to deploy: <br>
```bash
kubectl get pods -n metallb-system
```

Create MetalLB IP pool: <br>

> ℹ️ Because our design uses a single Virtual (floating) IP, our "pool" starts and ends with 192.168.50.156.

> ℹ️ The only time we'd want to increase our IP pool is if we wanted to run multiple instances of the same service/app using the same port. <br>
> 
> For example, MetalLB pool addresses (range) specified as 192.168.50.155-192.168.50.156. <br>
> DNS record 'plex-instance-1' pointing to '192.168.50.155' using port 32400. <br>
> DNS record 'plex-instance-2' pointing to '192.168.50.156' using port 32400. <br>

```bash
cat > metallb-ip-pool.yaml <<EOF
apiVersion: metallb.io/v1beta1
kind: IPAddressPool
metadata:
  name: ingress-pool
  namespace: metallb-system
spec:
  addresses:
    - 192.168.50.156-192.168.50.156
EOF
```

Start MetalLB IP pool: <br>
```bash
kubectl apply -f metallb-ip-pool.yaml
```

Create MetalLB L2 Advertisement: <br>
```bash
cat > metallb-l2adv.yaml <<EOF
apiVersion: metallb.io/v1beta1
kind: L2Advertisement
metadata:
  name: ingress-l2adv
  namespace: metallb-system
spec:
  ipAddressPools:
    - ingress-pool
EOF
```

Start MetalLB L2 Advertisement: <br>
```bash
kubectl apply -f metallb-l2adv.yaml
```

Expose RKE2 Ingress-NGINX via MetalLB IP: <br>
```bash
cat > ingress-nginx-lb.yaml <<EOF
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

Start RKE2 Ingress-NGINX: <br>
```bash
kubectl apply -f ingress-nginx-lb.yaml
```

Verify: <br>

> ℹ️ External IP should be 192.168.50.156.

```bash
kubectl get svc -n kube-system rke2-ingress-nginx-lb
```

<br>

***

### [7] Install RKE2 (Rancher) UI with Ingress-NGINX

&emsp; ***[node 1, rke2-n1 only]***

Install Helm: <br>
```bash
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash
```
Check: <br>
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

Install RKE2 (Rancher) UI: <br>
```bash
helm repo add rancher https://releases.rancher.com/server-charts/stable
helm repo update
```
```bash
kubectl create namespace cattle-system
```
```bash
helm install rancher rancher/rancher \
  --namespace cattle-system \
  --set hostname=rancher.spartan23.home \
  --set replicas=3 \
  --set ingress.ingressClassName=nginx \
  --set ingress.tls.source=rancher \
  --set bootstrapPassword='Password123!'
```

Monitor: <br>

> ℹ️ You want all `rancher-xxxx` pods in `Running` state.

```bash
kubectl get pods -n cattle-system
```

Check the Service/Ingress: <br>
```bash
kubectl get svc -n cattle-system
kubectl get ingress -n cattle-system
```

Access Rancher (RKE2) UI: <br>

```bash
https://rancher.spartan23.home
```

> Initial login: <br>
> &emsp; Username: `admin` <br>
> &emsp; Password: `Password123!` <br>
> &emsp; Set server URL (use `https://rancher.spartan23.home`) <br>

> ℹ️ Be sure to update/change your admin password after initial login.  <br>
> 
> `https://rancher.spartan23.home`: <br>
> &emsp; > Select `Users & Authentication`. <br>
> &emsp; > Select the `three-dot` hamburger menu (on the right of the admin user) <br>
> &emsp; > Select `Edit Config`. <br>
> &emsp; > Update your password in the `New Password` and `Confirm Password` fields. <br>
> &emsp; > Select `Save`. <br>

<br>

***

### [8] Prepare Software and Disks for Longhorn

&emsp; ***[all nodes]***

Update and install software/packages required for Longhorn: <br>
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

> ℹ️ These next steps assume you have an available/free disk at /dev/sdb.

Mount `/data/longhorn` (all nodes):
Inspect disks first (DO NOT skip this)
```bash
lsblk
```

Create a single ext4 partition on /dev/sdb
```bash
sudo parted /dev/sdb --script mklabel gpt mkpart primary ext4 0% 100%
```

Make sure the kernel sees the new partition
```bash
sudo partprobe /dev/sdb
```

Create filesystem on the new partition
```bash
sudo mkfs.ext4 /dev/sdb1
```

Create mountpoint for Longhorn data
```bash
sudo mkdir -p /data/longhorn
```

Get the UUID for /dev/sdb1
```bash
UUID=$(sudo blkid -s UUID -o value /dev/sdb1)
```

(Optional but helpful for sanity)
```bash
echo "Detected UUID: $UUID"
```

Add fstab entry using the detected UUID
```bash
echo "UUID=$UUID /data/longhorn ext4 defaults,noatime 0 2" | sudo tee -a /etc/fstab
```

Mount and verify
```bash
sudo systemctl daemon-reload
```
```bash
sudo mount -a
```
```bash
df -h /data/longhorn
```

<br>

***

### [9] Install Longhorn

&emsp; ***[node 1, rke2-n1 only]***

```bash
helm repo add longhorn https://charts.longhorn.io
kubectl create namespace longhorn-system
```

Values:
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

Install:
```bash
helm install longhorn longhorn/longhorn -n longhorn-system -f longhorn.yaml
```
```bash
kubectl get pods -n longhorn-system
```

***

Ingress for Longhorn (TLS + Basic Auth) (rke2-n1 only): <br>

Generate credentials:
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

Generate TLS:
```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout longhorn.key -out longhorn.crt -subj "/CN=longhorn.spartan23.home"
```
```bash
kubectl create secret tls longhorn-tls --cert=longhorn.crt --key=longhorn.key -n longhorn-system
```
```bash
rm longhorn.key longhorn.crt
```

Ingress:

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
https://longhorn.spartan23.home
```

By default, Longhorn is deployed using `/var/lib/longhorn` as its disk path (if not specified in `longhorn.yaml`). <br>

If you need to change the disk path, use the following steps. <br>

In this example, we change the disk path from `/var/lib/longhorn` to `/data/longhorn`.

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

***

## 🎉 Congratulations, you're finished deploying a high-availability RKE2 cluster. Now we're ready to deploy apps!

Please see my guides on deploying applications (like PLEX, Emby, Jellyfin, Jellyseerr, SABnzbd, Radarr, Sonarr, Lidarr... and MORE!) into RKE2. <br>
