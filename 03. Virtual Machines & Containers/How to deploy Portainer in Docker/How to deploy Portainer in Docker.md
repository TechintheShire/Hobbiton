<a href="./Icons%20and%20Screenshots/20250805_110313.png">
  <img src="./Icons%20and%20Screenshots/20250805_110313.png" height="170"/>
</a>

<a href="./Icons%20and%20Screenshots/20250805_100334.png">
  <img src="./Icons%20and%20Screenshots/20250805_100334.png" height="170"/>
</a>

<a href="./Icons%20and%20Screenshots/20250812_161817.png">
  <img src="./Icons%20and%20Screenshots/20250812_161817.png" height="170"/>
</a>

# How to install Portainer on Ubuntu Desktop 24.04.x LTS

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
-->

## Prerequisits

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Ubuntu Desktop 24.04.x LTS</td>
  </tr>
  <tr>
    <td align="right">Container Runtime</td>
    <td>Docker (incl. Docker Compose)</td>
  </tr>
</table>

> ℹ️ **Note** <br>
> 
> If you need help deploying Ubuntu Desktop, please see my guide here, [How to install Ubuntu Desktop 24.04.2 LTS](../../01.%20Operating%20Systems/How%20to%20install%20Ubuntu%20Desktop%2024.04.2%20LTS/How%20to%20install%20Ubuntu%20Desktop%2024.04.2%20LTS.md). <br>
> If you need help deploying Docker/Docker Compose, please see my guide here, [How to install Docker and Docker Compose](../../03.%20Virtual%20Machines%20%26%20Containers/How%20to%20install%20Docker%20and%20Docker%20Compose/How%20to%20install%20Docker%20and%20Docker%20Compose.md). <br>

## Install and Configure, Portainer

### [1] Create a docker volume for Portainer.

```bash
sudo docker volume create portainer_data
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145044%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145044%20v2.png" height="470"/>
</a><br>

### [2] Deploy Portainer in Docker.

```bash
sudo docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145143%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145143%20v2.png" height="470"/>
</a><br>

### [3] Verify Portainer has been successfully deployed.

```bash
sudo docker ps
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145222%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145222%20v2.png" height="470"/>
</a><br>

### [4] Log into and initialize Portainer.

Open a web browser and visit ```https://localhost:9443``` . <br>

Create your initial administrator user, which will be used to log into portainer and manage portainer itself along with other docker containers running on this machine. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145333%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145333%20v2.png" height="470"/>
</a><br>
<br>

You'll be brought to a default landing page where you can start to import environments. In our example, we'll only be managing our local Docker instance. <br>

Select 'Get Started - Proceed using the local environment which Portainer is running in'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145357%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145357%20v2.png" height="470"/>
</a>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145450%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145450%20v2.png" height="470"/>
</a><br>
<br>

Now we can navigate to our containers dashboard to see Docker containers running on this machine. As you can see, the only running Docker container on this system is Portainer itself. As we add more, more will be listed here. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145545%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-12%20145545%20v2.png" height="470"/>
</a>
