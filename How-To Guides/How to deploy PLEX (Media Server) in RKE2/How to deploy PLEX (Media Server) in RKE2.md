<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(5)%20-%20PLEX.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(4)%20-%20Longhorn.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(3)%20-%20MetalLB.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20RKE2%20NGINX.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

## How to deploy PLEX (Media Server) in RKE2

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>

***
-->

<!--

***

### Table of Contents

&emsp; []  <br>
&emsp; []  <br>
&emsp; []  <br>

&emsp; [#]  <br>
-->

### 📋 Prerequisites

<table>
  <tr>
    <td align="right">Operating Environment</td>
    <td>RKE2 (Rancher Kubernetes Engine 2)</td>
    <td><a href="../How%20to%20deploy%20RKE2%20(Rancher%20Kubernetes%20Engine%202)/How%20to%20deploy%20RKE2%20(Rancher%20Kubernetes%20Engine%202).md">How to deploy RKE2 with MetalLB, Ingress-NGINX, and Longhorn</a></td>
  </tr>
</table>

### 🧾 Assumptions

- The PLEX app /config (Library, Metadata, Databases... etc.) will be stored in a Longhorn PVC (persistent volume claim). <br>
- Media files (Movies / TV Shows) will be stored on an external SMB NAS share. In my example, hosted by TrueNAS Scale. <br>

> ⚠️ It is NOT recommended to store large sets of media files in Longhorn. Doing so makes uploading media files to PLEX very complex and makes integration with other applications such as SABnzbd, Radarr, Sonarr... etc. not possible due to the way the app is isolated in a container. In a future update to this guide, we may consider cephfs, which would allow us to consolidate media storage onto our RKE2 nodes; keep a lookout. <br>

### 🌐 Environment Overview
- MetalLB (Load Balancer) will listen on Virtual IP (Endpoint): 192.168.50.156. <br>
- DNS Record rke2-plex.spartan23.home pointing to 192.168.50.156. <br>
- When our DNS Record (URL) rke2-plex.spartan23.home hits 192.168.50.156, the Ingress-NGINX running in RKE2 will route traffic to our PLEX service/app. <br>
<br>

<!--
### 🏷️ Metadata Capacity Estimate 
-->

***

### [1] Install software dependencies.

```bash
sudo apt update && sudo apt upgrade -y
```
```bash
sudo apt install -y cifs-utils keyutils
```

<br>

***
### [2] Create a username/password security file for our SMB share.

> ⚠️ Unfortunately, mount.cifs does not support hashed passwords. For this reason, we need to store our username/password in a plain text file. If you're the only user on this machine, it shouldn't be an issue. We will be securing the text file by only allowing root access. However, anyone else with an account that has 'sudo' privileges on your machine could read your plain text username/password file. <br>

&emsp; > Create a directory to store our username/password security file. <br>
```bash
sudo mkdir -p /etc/creds
```

&emsp; > Create a credentials file. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">sudo touch /etc/creds/creds-userName</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">sudo touch /etc/creds/creds-artemis</code></pre>
    </td>
  </tr>
</table>

&emsp; > Edit the credentials file, adding username and password information, see below. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">sudo nano /etc/creds/creds-userName</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">sudo nano /etc/creds/creds-artemis</code></pre>
    </td>
  </tr>
</table>

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

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

&emsp; > Modify permissions to this file so that only 'root' can access it. This makes it much more secure. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Syntax: <br>
      <pre><code class="language-bash">sudo chmod 600 /etc/creds/creds-userName</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">sudo chmod 600 /etc/creds/creds-artemis</code></pre>
    </td>
  </tr>
</table>

<br>

***
### [3] Create mount directories for our SMB share(s).

```bash
mkdir -p ~/plex
```
```bash
mkdir -p ~/plex/media
```

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

<br>

***
### [4] Mount SMB share(s).

&emsp; > Identify your user ID and group ID. <br>
```bash
id -u <user>
```
```bash
id -g <group (typically the same as user)>
```

> ℹ️ If you are using Active Directory, you can use the following command. My domain user is 'artemis' or 'artemis@spartan23.home'. <br>
> 
> `id spartan23.home\\artemis` <br>

&emsp; > This command (below) is used to test and ensure you can successfully mount your SMB share before we modify our /etc/fstab file. <br>

> ⚠️ **Warning** <br>
>
> Do not skip this step!!! You should make sure your mount commands and permissions are working as expected before modifying the /etc/fstab. Misconfiguration within the fstab file could cause the system to fail to boot. <br>

&emsp; Syntax: <br>
```bash
sudo mount -t cifs //nasServer/smbShare /home/user/plex/media/nasServer_smbShare -o credentials=/etc/creds/creds-userName,uid=userID,gid=groupID,vers=3.1.1
```
&emsp; Example: <br>
```bash
sudo mount -t cifs //apollo/Media /home/rke2@spartan23.home/plex/media/apollo_Media -o credentials=/etc/creds/creds-artemis,uid=1171601103,gid=1171600513,vers=3.1.1
```

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

&emsp; > Make a backup copy of the fstab file before making any edits. Misconfiguration within the fstab file could cause the system to fail booting. <br>
```bash
sudo cp /etc/fstab /etc/fstab_$(date +%Y.%m.%d_%H-%M-%S)
```
```bash
ll /etc/ | grep -i fstab*
```

&emsp; > Edit the fstab file. <br>
```bash
sudo nano /etc/fstab
```

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

&emsp; > Add the following line at the bottom of your fstab (replacing any variables to match your environment, see syntax below for additional guidance). <br>

&emsp; Syntax: <br>
```bash
//fileserver/shareName /path/to/mountPoint cifs credentials=/etc/creds/creds-userName,uid=userID,gid=groupID,vers=3.1.1,_netdev,nofail 0 0
```
&emsp; Example: <br>
```bash
//apollo/Media /home/rke2@spartan23.home/plex/media/apollo_Media cifs credentials=/etc/creds/creds-artemis,uid=1171601103,gid=1171600513,vers=3.1.1,_netdev,nofail 0 0
```

&emsp; > Verify the fstab was successfully modified by running the following mount commands. <br>
```bash
sudo systemctl daemon-reload
```
```bash
sudo mount -a
```

&emsp; > To truly test that things are working properly, reboot your Ubuntu machine and verify the SMB shares successfully mounted to the directory you specified. If you have multiple SMB shares you'd like to mount, simply repeat the steps above for each respective SMB share. <br>

<br>

***
### [5] Deploy PLEX.

Create a Kubernetes namespace for PLEX: <br>
```bash
kubectl create namespace plex
```

> ℹ️ Explaining the sections of this .yaml: <br>
> `kind: PersistentVolumeClaim` = tells RKE2 where to store PLEX's /config (Library, Metadata, Databases... etc.) data. <br>
> `kind: Deployment` = tells RKE2 the image and configuration for the container. <br>
> `kind: Service` = tells RKE2 (specifically MetalLB) how to find the container within the cluster via the DNS record. <br>

Create a deployment configuration .yaml file for PLEX: <br>
```bash
cat > plex.yaml <<'EOF'
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: plex-config-pvc
  namespace: plex
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: longhorn
  resources:
    requests:
      storage: 16Gi
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: plex
  namespace: plex
spec:
  replicas: 1
  selector:
    matchLabels:
      app: plex
  template:
    metadata:
      labels:
        app: plex
    spec:
      containers:
        - name: plex
          image: lscr.io/linuxserver/plex:latest
          env:
            - name: PUID
              value: "1171601103"                     # replace with your user's UID
            - name: PGID
              value: "1171600513"                     # replace with your user's GID
            - name: TZ
              value: "America/New_York"               # https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List
            - name: PLEX_CLAIM
              value: "claim-Zy7RFT3zSvyJ3wfT_HSZ"     # replace with your PLEX claim token
          ports:
            - containerPort: 32400
              name: web
          volumeMounts:
            - name: plex-config
              mountPath: /config
            - name: plex-apollo-media     # match 'volume mount name' with your 'volume name' (below)
              mountPath: /apollo_Media    # update, this is the mount/path inside the container
      volumes:
        - name: plex-config               
          persistentVolumeClaim:
            claimName: plex-config-pvc
        - name: plex-apollo-media         # match 'volume name' with your 'volume mount name' (above)
          hostPath:
            path: "/home/rke2@spartan23.home/plex/media/apollo_Media"      # update, this is the mount/path on your host 
            type: Directory
---
apiVersion: v1
kind: Service
metadata:
  name: plex
  namespace: plex
spec:
  type: ClusterIP
  ports:
    - name: web
      port: 32400
      targetPort: 32400
      protocol: TCP
  selector:
    app: plex
EOF
```

Deploy PLEX: <br>
```bash
kubectl apply -f plex.yaml
```

Create an ingress configuration .yaml file for PLEX: <br>
```bash
cat > plex-ingress.yaml <<EOF
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: plex-ingress
  namespace: plex
  annotations:
    nginx.ingress.kubernetes.io/backend-protocol: "HTTP"
    nginx.ingress.kubernetes.io/proxy-read-timeout: "3600"
    nginx.ingress.kubernetes.io/proxy-send-timeout: "3600"
spec:
  ingressClassName: nginx
  rules:
    - host: rke2-plex.spartan23.home     # this should match the DNS record you previously created
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: plex
                port:
                  number: 32400
EOF
```

Deploy ingress for PLEX: <br>
```bash
kubectl apply -f plex-ingress.yaml
```

Check/Monitor Deployment:
```bash
kubectl get pods -n plex
```
```bash
kubectl get ingress -n plex
```

Access PLEX UI:
```bash
https://rke2-plex.spartan23.home/web
```
<br>

***
### [6] Configure PLEX media server Settings.

&emsp; PLEX includes a wide range of settings that can be customized to your hardware and personal preferences. Below are the only settings that I strongly recommend configuring regardless of your hardware specs or personal preferences: <br>

&emsp; This setting prevents you or others from accidentally deleting media via your PLEX clients (Web Browser, iPhone/Android, Roku, etc.): <br>
&emsp;&emsp; [Library Settings] <br>
&emsp;&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp;&emsp; > Select '`Library`' under Settings section. <br>
&emsp;&emsp;&emsp;&emsp; > Uncheck '`Allow media deletion`'. <br>
&emsp;&emsp;&emsp; > Select '`Save Changes`'. <br>

&emsp; These settings will save significant amounts of storage capacity: <br>
&emsp;&emsp; [Library Settings] <br>
&emsp;&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp;&emsp; > Select '`Library`' under Settings section. <br>
&emsp;&emsp;&emsp;&emsp; > Set '`Generate video preview thumbnails`' to '`never`'. <br>
&emsp;&emsp;&emsp;&emsp; > Set '`Generate chapter thumbnails`' to '`never`'. <br>
&emsp;&emsp;&emsp; > Select '`Save Changes`'. <br>
<br>

***
### Helpful Commands/Scenarios

#

&emsp; **Upgrade PLEX**

<details>
  <summary>Expand for additional details.</summary>
<br>

```bash
kubectl apply -f plex.yaml
```
```bash
kubectl rollout restart deployment/plex -n plex
```

</details>

#

&emsp; **Expand PLEX's PVC (Persistent Volume Claim)** <br>

<details>
  <summary>Expand for additional details.</summary>
<br>

In your .yaml file for PLEX, modify `storage: 16Gi` to `storage: 24Gi`. <br>
Verify that Longhorn allows PVC expansion: <br>
```bash
kubectl get storageclass longhorn -o yaml | grep -i allowVolumeExpansion
```
Redeploy PLEX: <br>
```bash
kubectl apply -f plex.yaml
```
Restart PLEX:
```bash
kubectl rollout restart deployment/plex -n plex
```

</details>

#
