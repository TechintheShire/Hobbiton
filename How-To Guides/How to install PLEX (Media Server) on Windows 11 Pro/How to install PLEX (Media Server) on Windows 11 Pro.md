<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20PLEX.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Windows%2011.png"/> <br>

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

## How to install PLEX (Media Server) on Windows 11 Pro

### Table of Contents

&emsp; [1] Create a standard (non-administrator) user account on your Windows 11 Pro machine. <br>
&emsp; [2] Create a PLEX account. <br>
&emsp; [3] Download the PLEX .exe installer. <br>
&emsp; [4] Start the PLEX .exe installer. <br>
&emsp; [5] Sign in and initialize PLEX. <br>
&emsp; [6] Activate (enable) Two-Factor Authentication (2FA). <br>
&emsp; [7] How to Add Libraries. <br>
&emsp; [8] How to Remove Libraries. <br>
&emsp; [9] (Optional) Enable 'Remote Access'. <br>
&emsp; [10] Configure PLEX media server Settings. <br>

&emsp; [#] Appendix <br>
&emsp; [#] Upgrading PLEX <br>
&emsp; [#] Uninstalling PLEX <br>
&emsp; [#] Disable automatic reboots caused by Windows Updates. <br>
&emsp; [#] Run PLEX (Media Server) as a Windows service via NSSM (Non-Sucking Service Manager). <br>

#

### 📋 Prerequisites

<table>
  <tr>
    <td align="right">Operating System</td>
    <td>Windows 11 Pro</td>
    <td><a href="../How%20to%20install%20Windows%2011%20Pro/How%20to%20install%20Windows%2011%20Pro.md">How to install Windows 11 Pro</a></td>
  </tr> 
</table>

### 🌐 Recommended Software

<table>
  <tr>
    <td align="right">Media Server Software</td>
    <td>Plex Media Server</td>
    <td>https://www.plex.tv/</td>
  </tr>
</table>

### 🧠 Reasons for recommending Windows 11 Pro
&emsp; - Windows Operating Systems are widely in use and familiar for most users. <br>
&emsp; - Media management is typically easier in a Windows environment (managing folders, files, network shares, access, permissions... etc.). <br>
&emsp; - Using a Windows based Operating System provides integrations with VSS (Volume Shadow-copy Service), which gives you access to '*Previous Versions*'. If you use TrueNAS Scale, you can provide this capability for your SMB shares!  <br>
&emsp; - Windows 11 Pro (vs Home) unlocks the following helpful features: <br>
&emsp;&emsp; - Remote Desktop connections. <br>
&emsp;&emsp; - Group Policy Editor, to disable automatic reboots caused by Windows Updates (see Appendix section in this guide). <br> 
&emsp;&emsp; - (Optional) Active Directory integration. <br>
&emsp; - Development Teams for library automation tools such as Radarr, Sonarr, Lidarr, and more... etc. officially support Windows. <br>

### Helpful Official Links from PLEX
&emsp; General Requirements <br>
&emsp;&emsp; https://support.plex.tv/articles/200375666-plex-media-server-requirements/ <br>
&emsp; Recommended CPU(s) <br>
&emsp;&emsp; https://support.plex.tv/articles/201774043-what-kind-of-cpu-do-i-need-for-my-server/ <br>
&emsp; Hardware Acceleration (Transcoding) (CPU/GPU) <br>
&emsp;&emsp; https://support.plex.tv/articles/115002178853-using-hardware-accelerated-streaming/ <br>
&emsp; Naming and Organizing your Movie media files <br>
&emsp;&emsp;https://support.plex.tv/articles/naming-and-organizing-your-movie-media-files/ <br>
&emsp; Naming and Organizing your TV Show files <br>
&emsp;&emsp; https://support.plex.tv/articles/naming-and-organizing-your-tv-show-files/ <br>
<br>

***
### [1] Create a standard (non-administrator) user account on your Windows 11 Pro machine.

> ℹ️ If you are an advanced user with a Domain Controller running Active Directory in your environment, I would recommend skipping this step, which is creating a non-administrator local user. At this point, join this Windows 11 Pro machine to your Active Directory and use a non-administrator user within your Domain. <br>

&emsp; Installing and running PLEX media server under a standard user account provides increased security and reduces overall risk to your environment in the event that your Windows machine or PLEX media server becomes compromised by malware. <br>

Create a standard (non-administrator) user following these steps: <br>
&emsp; > Log into an administrator-level account, if not already. <br>
&emsp; > Windows '`Start Menu`'. <br>
&emsp; > '`Settings`'. <br>
&emsp; > '`Accounts`'. <br>
&emsp; > Scroll down to '`Other Users`'. <br>
&emsp; > To the right of 'Add other user' select '`Add account`'. <br>
&emsp; > I recommend creating a non-Microsoft account. <br>
&emsp; > Select '`I don't have this person's sign-in information`'. <br>
&emsp; > Select '`Add a user without a Microsoft account`'. <br>
&emsp; > Follow the steps to create your new user. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123445%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123500%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123500%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123515%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123515%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123530%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123530%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123545%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123545%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Log into the non-administrator user account you just created. This is where we'll install our PLEX media server software. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png" height="270"/>
</a><br>

***

### [2] Create a PLEX account.

&emsp; > Open https://www.plex.tv/ in your browser. <br>
&emsp; > Select '`Sign Up Free`' and create your account. <br>

> ℹ️ Here is a feature comparison between the '*free*' vs '*PLEX Pass*' licensing options offered by PLEX. <br>
> https://www.plex.tv/plans/#product-features

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20110000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20110000%20v2.png" height="270"/>
</a><br>

***

### [3] Download the PLEX .exe installer.

&emsp; > Open https://www.plex.tv/ in your browser. <br>
&emsp; > Select '`Download`' > '`Plex Media Server`' under '*Plex Pro Downloads*'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120000%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Under the dropdown menu, verify '`Windows`' is selected. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120010%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Click the '`Choose Distribution`' button. <br>
&emsp; > Select '`Windows 64-bit`' to begin downloading the installer (PlexMediaServer-1.41.6.9685-d301f511a-x86_64.exe file). Your .exe version number will likely be different depending on the date/time of your download. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120020%20v2.png" height="270"/>
</a><br>
<br>

> ℹ️ To check your Operating System type (64-bit vs 32-bit): <br>
> &emsp; > Windows '`Start Menu`'. <br>
> &emsp; > '`Settings`'. <br>
> &emsp; > '`System`'. <br>
> &emsp; > '`About`'. <br>
> &emsp; > View '`System type`'. <br>

***

### [4] Start the PLEX .exe installer.

&emsp; > Start the PLEX media server installer by double-clicking or right-clicking the .exe, follow the installer steps, using the default options. <br>

> ℹ️ If you don't see file extensions like '.exe' on your file names and you would like to enable viewing them, follow these steps: <br>
> &emsp; > Windows Explorer <br>
> &emsp; > Select the '`three-dot`' hamburger menu <br>
> &emsp; > Select '`Options`' <br>
> &emsp; > Select the '`View`' tab <br>
> &emsp; > Scroll down and ***uncheck*** '`Hide extensions for known file types`' <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120000%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120010%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120020%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120030%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120040%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120040%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Verify the installation was successful by checking the Windows '*System Tray*' or '*Notification Area*' and viewing the PLEX icon. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120050%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120050%20v2.png" height="270"/>
</a><br>

***

### [5] Sign in and initialize PLEX.

&emsp; Starting the PLEX media server software should automatically open a browser tab to URL `https://app.plex.tv` where it'll ask you to sign into your PLEX account. <br>

&emsp; If it doesn't, manually open a browser tab to one of the following URLs:
```bash
https://localhost:32400/web
```
```bash
https://<ipAddress>:32400/web
``` 

> ℹ️ Regardless of which URL you use, you will likely be redirected to '*https://app.plex.tv*'. Once you are done signing in, you should be redirected back to your original URL (*https://localhost:32400/web* or *https://ipAddress:32400/web*). <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120100%20v2.png" height="270"/>
</a><br>
<br>

&emsp; If you previously created and logged into your PLEX account, select your account and give your new PLEX media server a few minutes to 'initialize'. <br>
 
&emsp; If after a few minutes, the 'initialization' process appears to be hanging, try refreshing the browser tab. If that doesn't work, try selecting '`Sign In`' (upper right-hand corner) again and log in. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120110%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120110%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Once you have successfully signed in, you should be greeted by a 'Server Setup' wizard. <br>

&emsp; > Select '`Got It!`' to continue. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120120%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120120%20v2.png" height="270"/>
</a><br>
<br>

&emsp;> Assign a name to your PLEX media server. This name can be different from your Windows 11 Pro hostname; however, I keep it the same for simplified identification and network DNS. <br>
&emsp;> Confirm whether or not you want to enable remote access to your PLEX media server outside of your local LAN, meaning over the WAN/internet. *More on that later in this guide. <br>
&emsp;> Then, select '`Next`'. <br>

> ℹ️ In my example, my PLEX media server will be named '*venom*'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120130%20v2.png" height="270"/>
</a><br>
<br>

&emsp;> Here we can begin to add media libraries. Because we'll be covering this in more detail in a later step, we'll skip this for now. <br>
&emsp;> Select '`Next`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120140%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120140%20v2.png" height="270"/>
</a><br>
<br>

&emsp;> Select '`Done`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120150%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120150%20v2.png" height="270"/>
</a><br>

***

### [6] Activate (enable) Two-Factor Authentication (2FA).

> ℹ️ This step is optional but highly recommended. If you plan to expose your PLEX media server over the WAN/internet, this step should be considered mandatory. My recommendation would be to use 'Google Authenticator', which is an easy to use TOTP (time-based one-time password) application. Mine is set up on my iPhone. <br>

&emsp; > '`Settings`' <br>
&emsp; > '`Account`' <br>
&emsp; > Select '`Edit`' for '*Two-Factor Authentication*'. <br>
&emsp; > Follow the steps to enable 2FA. <br>

***

### [7] How to Add Libraries.

&emsp; > Confirm whether you will store your media files locally on your PLEX media server or an external NAS SMB share. <br>
&emsp; > If storing on an external NAS SMB share, confirm whether you will use **'*mapped network drives*'** or **'*full UNC paths*'**. <br>

> ℹ️ If you plan to run your PLEX media server as a Windows service, use full UNC paths. Mapped network drives (drive letters) are not accessible or mounted until a user manually logs in. <br>

#

&emsp; **How to map a network drive.** <br>

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; You can access network drives (shares) using either your NAS server's DNS hostname or IP address in the Windows Explorer address bar. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      DNS hostname Example: <br>
      <pre><code class="language-bash">\\apollo</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">\\192.168.50.191</code></pre>
    </td>
  </tr>
</table>

> ⚠️ If you're having issues browsing or accessing SMB shares on your network, ensure '`Network discovery`' and '`File and printer sharing`' are enabled (set to 'On') under '`Settings`' > '`Network & internet`' > '`Advanced network settings`' . <br>
>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143546%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143546%20v2.png" height="270"/></a><br>

&emsp; Steps to map a network drive: <br>
&emsp;&emsp; > Open Windows Explorer. <br>
&emsp;&emsp; > Navigate to the '`Network`' section under the left side Navigation Pane. <br>
&emsp;&emsp; > Select your NAS server. <br>
&emsp;&emsp; > Right-click your SMB network share, then select '`Map network drive...`'. <br>
&emsp;&emsp;&emsp; > Select (assign) a drive letter. <br>
&emsp;&emsp;&emsp; > Ensure '`Reconnect at sign-in`' is selected. This will ensure the drive will get mapped (remapped) next time you log in. <br>
&emsp;&emsp;&emsp; > If needed, select '`Connect using different credentials`'. <br>
&emsp;&emsp;&emsp; > Then select '`Finish`', which will map the network drive. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143547%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143547%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143614%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143614%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143710%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143710%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143737%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143737%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143810%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143810%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143829%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143829%20v2.png" height="270"/>
</a><br>
<br>

&emsp; You can also confirm the drive was successfully mapped by checking under '`This PC`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143900%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143900%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **How to identify your full UNC path.** <br>

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ If you plan to run PLEX as a Windows service, it is recommended to use full UNC paths. Mapped network drives (drive letters) are not accessible or mounted until a user manually logs in. <br>

&emsp; You can access network drives (shares) using either your NAS server's DNS hostname or IP address in the Windows Explorer address bar. <br>
<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      DNS hostname Example: <br>
      <pre><code class="language-bash">\\apollo</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Example: <br>
      <pre><code class="language-bash">\\192.168.50.191</code></pre>
    </td>
  </tr>
</table>

> ⚠️ If you're having issues browsing or accessing SMB shares on your network, ensure '`Network discovery`' and '`File and printer sharing`' are enabled (set to 'On') under '`Settings`' > '`Network & internet`' > '`Advanced network settings`' . <br>
>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143546%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143546%20v2.png" height="270"/></a><br>

&emsp; Steps to identify your full UNC path: <br>
&emsp;&emsp; > Open Windows Explorer. <br>
&emsp;&emsp; > Navigate to the '`Network`' section under the left side Navigation Pane. <br>
&emsp;&emsp; > Select your NAS server. <br>
&emsp;&emsp; > Select your SMB network Share. <br>
&emsp;&emsp; > If needed, navigate through any subdirectories. <br>
&emsp;&emsp; > Then select/put your mouse cursor in the Windows Explore Address Bar, which should show you and allow you to right-click and copy the full UNC path for that location. <br>

<table>
  <tr>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Full UNC Path Syntax: <br>
      <pre><code class="language-bash">\\NAS server\SMB network share\subdirectory</code></pre>
    </td>
    <td>
      <img src="placeholder.png" width="475" height="0" alt="">
      Full UNC Path Example: <br>
      <pre><code class="language-bash">\\APOLLO\Media\TV Shows</code></pre>
    </td>
  </tr>
</table>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112213%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112213%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112224%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112224%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112237%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112237%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112250%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112250%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112251%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112251%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Add Library - Option 1] From the default homepage.** <br>

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > From the default homepage, select '`More >`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120000%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Select the '`+`' sign next to your server's hostname. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120010%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > In this example, we'll add a 'Movies' library by selecting the '`Movies`' icon/type. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120020%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Select '`Browse for Media Folder`'. <br>
&emsp; > Select the folder where your Movie files are located (e.g., local machine, mapped network drive, full UNC network path). <br>
&emsp; > Then, select '`Add`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120030%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120040%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120040%20v2.png" height="270"/>
</a><br>
<br>

> ℹ️ If you plan to run your PLEX media server as a Windows service (more on this in the Appendix section), you will need to use full UNC network paths. <br>

| Mapped Network Drive | Full UNC Network Path |
|----------|----------|
| Z:\Movies    | Syntax: \\\NAS Server\Network Share\Folder <br><br> \\\apollo\Media\Movies  |
| Example: <br> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120055%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120055%20v2.png" height="300"/></a> | Example: <br> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120110%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120110%20v2.png" height="300"/></a> |

&emsp; > When finished, select '`Add Library`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120050%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120050%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Once the library has been added, your PLEX will start to scan the folder locations you specified and will organize, list, and add meta-data for each of the Movies / TV Shows in your respective library. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120100%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Add Library - Option 2] From Settings.** <br>

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Go to '`Settings`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120000%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Verify the appropriate PLEX media server is selected. <br>
&emsp; > In my example, my server name is 'venom'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120010%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Go to '`Manage`' > '`Libraries`' > Select '`Add Library`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120020%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > In this example, we'll add a 'TV Shows' library by selecting the '`TV Shows`' icon/type. <br>
&emsp; > Select '`Browse for Media Folder`'. <br>
&emsp; > Select the folder where your TV Show files are located (e.g., local machine, mapped network drive, full UNC network path). <br>
&emsp; > Then, select '`Add`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120030%20v2.png" height="270"/>
</a><br>
<br>

> ℹ️ If you plan to run your PLEX media server as a Windows service (more on this in the Appendix section), you will need to use full UNC network paths. <br>

| Mapped Network Drive | Full UNC Network Path |
|----------|----------|
| Z:\Movies    | Syntax: \\\NAS Server\Network Share\Folder <br><br> \\\apollo\Media\Movies  |
| Example: <br> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120055%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120055%20v2.png" height="300"/></a> | Example: <br> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120110%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120110%20v2.png" height="300"/></a> |

&emsp; > When finished, select '`Add Library`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120040%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120040%20v2.png" height="270"/>
</a><br>

</details>

#

***

### [8] How to Remove Libraries.

> ℹ️ Deleting a library will not delete your actual folders / files. It simply removes the library (access to that media) from your PLEX media server. <br>

> ⚠️ Individual files within your library can be deleted! <br>
>
> To disable this, navigate to '`Settings`' > '`Library`' > ***Uncheck*** '`Allow media deletion`' > Scroll down and select '`Save`'. <br>
>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120015%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120015%20v2.png" height="270"/></a><br>

#

&emsp; **[Remove Library - Option 1] From the default homepage, for a pinned library.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; From the default homepage (if your library is pinned to your Home/Dashboard page): <br>
&emsp;&emsp; > Hover over the library you want to delete and select the '`three-dot`' hamburger menu. <br>
&emsp;&emsp; > Select '`Manage Library`'. <br>
&emsp;&emsp; > Select '`Delete`'. <br>     		

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-23%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-23%20120000%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-23%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-23%20120010%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Remove Library - Option 2] From the default homepage, for an unpinned library.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; From the default homepage (if the library is NOT pinned to your Home/Dashboard page): <br>
&emsp;&emsp; > Scroll down and select '`More >`' <br>
&emsp;&emsp; > Identify the server you want to delete the library from. <br>
&emsp;&emsp; > Under that server, hover over the library you want to delete and select the '`three-dot`' hamburger menu. <br>
&emsp;&emsp; > Select '`Manage Library`'. <br>
&emsp;&emsp; > Select '`Delete`'. <br>     		

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120000%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120010%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120020%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Remove Library - Option 3] From Settings.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; From the default homepage: <br>
&emsp;&emsp; > Go to '`Settings`'. <br>
&emsp;&emsp; > Verify the appropriate PLEX media server is selected. <br>
&emsp;&emsp; > Under '`Manage`', go to '`Libraries`'. <br>
&emsp;&emsp; > Hover over the library you want to delete and select the '`three-dot`' hamburger menu. <br>
&emsp;&emsp; > Select '`Delete`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120000%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120010%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120020%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120030%20v2.png" height="270"/>
</a><br>

</details>

#

***

### [9] (Optional) Enable 'Remote Access'.

#

&emsp; **[Remote Access - Option 1 (UPnP/NAT-PMP)]**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; If your router supports UPnP/NAT-PMP (Universal Plug and Play/NAT Port Mapping Protocol) and it is enabled, you should be able to 'Enable Remote Access' on your PLEX media server and the UPnP/NAT-PMP service should configure/map the necessary networking to access your PLEX media server externally over the WAN/internet without having to touch your firewall or manually forward ports. <br>

> ⚠️ Be aware, UPnP/NAT-PMP does not require authentication to configure these network settings, which should be considered a security risk! If security is important to you, consider options 2 or 3 below. <br>

&emsp; > '`Settings`'. <br>
&emsp; > Select '`Remote Access`'. <br>
&emsp; > Select '`Enable Remote Access`'. <br>
&emsp; > If UPnP/NAT-PMP is supported and enabled on your router, your router should automatically configure the necessary port forwarding. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120000%20v2.png" height="270"/>
</a><br>
<br>

&emsp; If remote access has been enabled successfully, you should see a screen similar to the following. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120010%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Remote Access - Option 2 (Manual Port-Forward on Firewall)]**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Manually configuring port forwarding provides better security, better control, and reduces the attack surface on your firewall.

&emsp; > On your router's firewall, port-forward port 32400 to your PLEX media server's IP address. <br>
&emsp; > Then, on your PLEX media server, navigate to the following location. <br>
&emsp;&emsp; > '`Settings`'. <br>
&emsp;&emsp; > Select '`Remote Access`'. <br>
&emsp;&emsp; > Select '`Enable Remote Access`'. <br>
&emsp;&emsp; > Check '`Manually specify public port`' and set/keep the port as default '`32400`' and select '`Apply`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120020%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Remote Access - Option 3 (Reverse Proxy)]**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; I believe the best option is to route your access/traffic through a reverse proxy like 'Nginx Proxy Manager'. I'll cover reverse proxies in a separate guide. <br>

</details>

#

***

### [10] Configure PLEX media server Settings.

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

## Appendix

***

### Upgrading PLEX

<details>
  <summary>Expand for additional details.</summary>

#

> ℹ️ If you are running your PLEX media server as a Windows service, set '`startup type`' to '`disabled`'. Otherwise, the Windows Service Control Manager (SCM) will quickly restart the previous code version instance preventing the new code version from loading. Yes, SCM is that quick and efficient! <br>

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Via Windows Services App: <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150732%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150732%20v2.png" height="270"/></a>

&emsp; Via NSSM: <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150733%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150733%20v2.png" height="270"/></a>

</details>

#

> ℹ️ If you already initiated the upgrade before setting '`startup type`' to '`disabled`' you can restart the Windows service associated with your PLEX media server to complete the upgrade. <br>

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Here you will notice, the PLEX media server is still running a previous version of the code. To fix this, we need to restart the Windows service associated with the PLEX media server. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094808%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094808%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Open and run the 'Services' app as Administrator. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094919%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094919%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Find and restart the Windows service associated with the PLEX media server. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20095010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20095010%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > You can also restart the Windows service using NSSM. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20095134%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20095134%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Once you restart the associated Windows service, we can see our PLEX media server is running the latest/upgraded code. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20112400%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20112400%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Option 1] Initiate the upgrade from the 'Notifications' / 'Server Notifications' area.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > View the notifications area (upper right-hand corner). <br>
&emsp; > Here we can see our PLEX media server reporting an upgrade is available. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174118%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174118%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Select the notification area to see which server(s) are reporting an available upgrade. <br>

> ℹ️ In my example, I have two PLEX media servers, one named 'nova' and the other 'venom'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174133%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174133%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Select '`Server Update Available`' for the server you want to upgrade. <br>
&emsp; > Select '`Download now`'. <br>
&emsp; > Then, select '`Install now`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174156%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174156%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174218%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174218%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174235%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174235%20v2.png" height="270"/>
</a><br>
<br>

&emsp; While the upgrade is being performed, your PLEX media server will be unavailable. <br>
&emsp; The upgrade should only take a few seconds/minutes. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174317%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174317%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Once the upgrade is complete, it should automatically load your PLEX media server's Home page. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174456%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174456%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Option 2] Initiate the upgrade from the 'Settings' area.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > View the notifications area (upper right-hand corner). <br>
&emsp; > Here we can see our PLEX media server reporting an upgrade is available. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094410%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094410%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094426%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094426%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Select '`Settings`' in the upper right-hand corner. The icon looks like a wrench. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094450%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094450%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Ensure you've selected the appropriate server (if you have more than one). <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094506%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094506%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Under '`Settings`', select '`General`'. Here you will see the ability to download the update package. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094544%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094544%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Select '`Download Updates`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094628%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094628%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Then, select '`Install Update`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094653%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094653%20v2.png" height="270"/>
</a><br>
<br>

&emsp; While the upgrade is being performed, your PLEX media server will be unavailable. <br>
&emsp; The upgrade should only take a few seconds/minutes. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094728%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094728%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Once the upgrade is complete, you should see the updated code version. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094808%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094808%20v2.png" height="270"/>
</a><br>

</details>

#

</details>

***

### Uninstalling PLEX

<details>
  <summary>Expand for additional details.</summary>

#

&emsp; **Stop the PLEX media server Process (if still running).** <br>
&emsp;&emsp; > Under the Windows notification area, right-click the PLEX media server icon and select exit to stop the PLEX media server process. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145516%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145516%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145639%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145639%20v2.png" height="270"/>
</a><br>
<br>

> ℹ️ If you are running PLEX as a Windows service, the active/running process will not show up in the Windows notification area. You will need to stop it via the Windows Services app or NSSM. I recommend using NSSM because we can stop and remove the Windows service; whereas, the Windows Services app can only stop/disable the Windows service. <br>

&emsp; **[Option 1] Stop and remove the PLEX Windows service via NSSM.**

<details>
  <summary>Expand for additional details.</summary>
<br>

```bash
nssm status "plexmediaserver"
```
```bash
nssm stop "plexmediaserver"
```
```bash
nssm remove "plexmediaserver"
```
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150030%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150030%20v2.png" height="270"/></a><br>

</details>

&emsp; **[Option 2] Stop/disable the PLEX Windows service via the Windows Services app.**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Use the following steps to stop/disable the Windows service associated with your PLEX media server via the Windows Services app. <br>

&emsp; > Right-click the Windows Services app and select 'Run as administrator'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145801%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145801%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Find and right-click the Windows service that is related to your 'Plex Media Server'. Select 'Properties'.

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145930%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145930%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Under the 'General' tab, select 'Stop' to stop the Windows service. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145931%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145931%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Here, you can see the 'plexmediaserver' / 'Plex Media Server' Windows service stopping. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145932%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145932%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Under the same 'General' tab, select the dropdown menu next to 'Startup type:' and select 'Disabled'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145933%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145933%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Select 'Apply' to apply the settings we just configured. At this point, even if the Windows 11 Pro machine reboots, this service won't start automatically. If disabling the Windows service is sufficient for your needs, proceed to the next step. If you'd prefer to remove/delete the Windows service, you'll need a tool like NSSM. NSSM can remove/delete the Windows service using the 'Service name:'. In this example, it would be 'plexmediaserver'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145934%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145934%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **Uninstall PLEX via the Windows Settings app.** <br>
&emsp; > Windows '`Start Menu`'. <br>
&emsp; > '`Settings`'. <br>
&emsp; > '`Apps`'. <br>
&emsp; > '`Installed apps`'. <br>
&emsp; > Scroll down until you see '`Plex Media Server <version number>`' or search '`Plex Media Server`' in the upper search bar. <br>
&emsp; > Select the '`three-dot`' hamburger menu on the right of the '`Plex Media Server`' app, and select '`Uninstall`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150118%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150118%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150136%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150136%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150231%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150231%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150245%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150318%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150318%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150334%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150334%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150351%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150351%20v2.png" height="270"/>
</a><br>

#

&emsp; **Delete related 'Plex Media Server' Directories.** <br>

&emsp; Even after uninstalling the 'Plex Media Server' app, there may be directories left behind that include configuration, cache, and metadata files. Depending on the size of your media collection, these folders could contain Gigabytes (GB) or more worth of data. <br>

&emsp; > Delete the following folders/directories: <br>
&emsp;&emsp;&emsp; '`C:\Users\<YourUsername>\AppData\Local\Plex Media Server`' <br>
&emsp;&emsp;&emsp; '`C:\Program Files\Plex`' <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150445%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150509%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150509%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150557%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150557%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now empty your recycle bin. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150701%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150701%20v2.png" height="270"/>
</a><br>

#

&emsp; **Reboot your Windows 11 Pro machine.** <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150732%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150732%20v2.png" height="270"/>
</a><br>

#

</details>

***

### Disable automatic reboots caused by Windows Updates.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ These steps prevent Windows Updates from automatically rebooting your machine when a user is logged in. <br>

#

&emsp; **[Option 1] Windows 11 | Standalone Windows Machine (no Workgroup / Domain)**

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Log into an administrator-level user account. <br>
&emsp; > Open the '`Edit Group Policy`' manager: <br>
&emsp;&emsp; > Windows Start Menu  <br>
&emsp;&emsp; > Type/Search '`Edit Group Policy`'. <br>
&emsp;&emsp; > Select/Open the '`Edit Group Policy`' manager. <br>
&emsp;&emsp; > Navigate to the following location within the 'Edit Group Policy' manager: <br>
&emsp;&emsp;&emsp; > '`Computer Configuration`' <br>
&emsp;&emsp;&emsp; > '`Administrative Templates`' <br>
&emsp;&emsp;&emsp; > '`Windows Components`' <br>
&emsp;&emsp;&emsp; > '`Windows Update`' <br>
&emsp;&emsp;&emsp; > '`Legacy Policies`' <br>
&emsp;&emsp;&emsp; > Find and edit the policy '`No auto-restart with logged on users for scheduled automatic updates installations`'. <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Enable`' <br>
&emsp;&emsp;&emsp;&emsp; > Select '`Ok`' or '`Apply`'. <br>

Close the '`Group Policy Management`' console. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123830%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123830%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123845%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123845%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123900%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123900%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123915%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123915%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123930%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123930%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123945%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123945%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124000%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124015%20v2.png" height="270"/>
</a><br>

</details>

#

&emsp; **[Option 2] Windows Server 2019 | Domain Controller w/Active Directory**

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ For advanced users with their Windows 11 Pro server/machine joined to a Domain Controller/Active Directory. Setting this policy against the root of the domain will apply this setting against ALL Windows machines joined to the Domain, which is what I prefer in my environment. If you need to isolate specific machines/VMs, please adjust these steps as you see fit.

&emsp; > Log into your Domain Controller. <br>
&emsp; > Open the '`Group Policy Management`' console: <br>
&emsp;&emsp; > Windows Start Menu <br>
&emsp;&emsp; > Type/Search '`Group Policy Management`'. <br>
&emsp;&emsp; > Select/Open the '`Group Policy Management`' console. <br>			
&emsp;&emsp;&emsp; > Expand '`Forest: example_domain.home`'. <br>
&emsp;&emsp;&emsp; > Expand '`Domains`'. <br>
&emsp;&emsp;&emsp; > Right-click your 'example_domain.home' and select '`Create a GPO in this domain, and Link it here…`'. <br>
&emsp;&emsp;&emsp;&emsp; > Give your GPO (Group Policy Object) a name, I recommend something like “2025.08.02 Disable Auto Reboot for Updates”. <br>
&emsp;&emsp;&emsp;&emsp; > Right-click your newly create GPO and select '`Edit…`'. <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Within the '`Group Policy Management Editor`', navigate to the following location: <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Computer Configuration`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Policies`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Administrative Templates`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Windows Components`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > '`Windows Update`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Find and edit the policy '`No auto-restart with logged on users for scheduled automatic updates installations`'. <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; > Select '`Enable`' <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; > Select '`Ok`' or '`Apply`'. <br>

Close the '`Group Policy Management`' console. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124030%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124045%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124100%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124115%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Expand this window to make it easier to navigate through the next couple of steps. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png" height="270"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png" height="270"/>
</a>

</details>

#

</details>

***

### Run PLEX (Media Server) as a Windows service via NSSM (Non-Sucking Service Manager).

<details>
  <summary>Expand for additional details.</summary>
<br>

In this section, we'll cover how to run PLEX (Media Server) as a Windows service using NSSM. <br>

> ⚠️ I would recommend starting this process without PLEX running. <br>

> ℹ️ Running PLEX as a Windows service significantly improves stability and availability through two methods: <br>
> &emsp; - PLEX will start at boot, which reduces downtime caused by unexpected reboots. <br>
> &emsp; - The Windows Service Control Manager (SCM) will monitor and automatically restart PLEX if any crashes or unexpected stops are detected. <br>

&emsp; > Download the NSSM (Non-Sucking Service Manager) tool by visiting the following URL: <br>

```bash
https://nssm.cc/
```

&emsp; > Navigate to the '`Download`' page by selecting Download on the left menu. <br>
&emsp; > Then download the NSSM .zip file. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20152840%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20152840%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20152929%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20152929%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Extract the .zip file to a location of your choosing. <br>

&emsp; I put this in a folder on my Desktop for easy access `C:\Users\artemis\Desktop\Toolkit\nssm-2.24`. <br>
&emsp; Here you can see that the .zip file will be extracted to `C:\Users\artemis\Desktop\Toolkit\nssm-2.24`. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153020%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153116%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153116%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153143%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153143%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Here you can see the extracted folder. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153226%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153226%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Navigate into that folder to locate the 64-bit version of the .exe NSSM tool. ***Most OSes are 64-bit these days. <br>

&emsp; In my example, the 64-bit version of the .exe can be found in `C:\Users\artemis\Desktop\Toolkit\nssm-2.24\nssm-2.24\win64\nssm.exe`. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153308%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153308%20v2.png" height="270"/>
</a><br>
<br>

&emsp; I like to copy/move the 64-bit nssm.exe back to my `C:\Users\artemis\Desktop\Toolkit\nssm-2.24` folder for easier access. <br>

> ℹ️ In a future update to this guide, we'll cover how to safely add nssm-2.24.exe to our system path and lock it down to 'administrator-only' permissions. For now, we'll run the tool from a subdirectory on our desktop. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153338%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153338%20v2.png" height="270"/>
</a><br>
<br>

&emsp; From here, we can open and run a Command Prompt (CMD) as Administrator: <br>
&emsp;&emsp; > Right-click the Command Prompt (CMD) icon. <br>
&emsp;&emsp; > Right-click the '`Command Prompt`' text. <br>
&emsp;&emsp; > Select '`Run as administrator`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153408%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153408%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > '`cd`' (change directory) to the location where you're storing your nssm.exe file (tool). <br>

&emsp; Example: `cd "C:\Users\artemis\Desktop\Toolkit\nssm-2.24`

&emsp; > Verify you're in the correct folder (directory) by listing the folder (directory) contents. You should see the `nssm.exe` file: <br>

```bash
dir
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153504%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153504%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Start the NSSM tool and install PLEX as a Windows service: <br>

```bash
nssm install "plexmediaserver"
```

&emsp; After running the command above, the NSSM GUI (graphical user interface) will open. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153609%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153609%20v2.png" height="270"/>
</a><br>
<br>

&emsp; In the NSSM GUI, configure the following options: <br>

&emsp;&emsp; > **[Application]** tab: <br>
&emsp;&emsp;&emsp;&emsp; Path: `C:\Program Files\Plex\Plex Media Server\Plex Media Server.exe` <br>
&emsp;&emsp;&emsp;&emsp; Startup directory: `C:\Program Files\Plex\Plex Media Server\` <br>
&emsp;&emsp;&emsp;&emsp; Arguments: Leave this blank. <br>

&emsp;&emsp; > **[Details]** tab: <br>
&emsp;&emsp;&emsp;&emsp; Display name: `Plex Media Server` <br>
&emsp;&emsp;&emsp;&emsp; Description: `Runs Plex Media Server as a Windows service using NSSM.` <br>

&emsp;&emsp; > **[Log on]** tab: <br>
&emsp;&emsp;&emsp;&emsp; This account: Enter your username <br>
&emsp;&emsp;&emsp;&emsp; Password: Enter your password <br>
&emsp;&emsp;&emsp;&emsp; Confirm: Re-enter your password for confirmation <br>

> ℹ️ In my example, I'm using an Active Directory/Domain user account, which is why I append '@spartan23.home' after my username. If you're not using an Active Directory/Domain user account, please ignore that syntax. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153651%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153651%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153710%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153710%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153822%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153822%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp; > (Optional but useful) I/O tab: <br>
&emsp;&emsp;&emsp; > Create a 'Logs' folder. <br>
&emsp;&emsp;&emsp; > Create an output (plex_stdout.log) and error (plex_stderr.log) log files within the 'Logs' folder. <br>
&emsp;&emsp;&emsp; > Set the output and error log locations within the NSSM GUI. <br>

> ℹ️ In my example, I put these log files in the same Desktop folder that I put the NSSM .exe tool. <br>

Output log file: `C:\Users\artemis\Desktop\Toolkit\Logs\plex_stdout.log` <br>
Error log file: `C:\Users\artemis\Desktop\Toolkit\Logs\plex_stderr.log` <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154028%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154028%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now select '`Install service`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154028%20v2%20(2).png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154028%20v2%20(2).png" height="270"/>
</a><br>
<br>

&emsp; If successful, you should see the "`Service 'plexmediaserver' installed successfully!`". <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154055%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154055%20v2.png" height="270"/>
</a><br>
<br>

&emsp; You can also see this 'success' message in the Command Prompt (CMD) window: <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154113%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154113%20v2.png" height="270"/>
</a><br>
<br>

&emsp; If we check under Windows Services, we can see a Windows service was created; however, it has not been started. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154227%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154227%20v2.png" height="270"/>
</a><br>
<br>

&emsp; We have a few options to start our newly created service. <br>
&emsp; &emsp; Option 1, start the service via NSSM. <br>
```bash
nssm start "plexmediaserver"
```
&emsp;&emsp; Option 2, start the service via Windows Service tool. <br>
&emsp;&emsp; Option 3, reboot the Windows 11 Pro machine. <br>

&emsp; Option 1, start the service via NSSM. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154326%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154326%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Option 2, start the service via Windows Service tool. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154250%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154250%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Option 3, reboot the Windows 11 Pro machine. <br>

&emsp; Regardless of which method we used to start the service, we can check its status via the Windows Services app. <br>
&emsp; In this example, we can see our 'Plex Media Server' service (which was created by NSSM), has a status of 'Running'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154346%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154346%20v2.png" height="270"/>
</a><br>
<br>

&emsp; Now that we've confirm the service is running, we can check if our 'Plex Media Server' is up and running. *Compare this to our initial screenshow where our 'Plex Media Server' was reporting 'currently unavailable'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154413%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154413%20v2.png" height="270"/>
</a><br>
<br>

&emsp; This screenshot is a quick reminder that if we are running 'Plex Media Server' as a service, we should be using full UNC paths and not mapped network drives (if our media is stored externally on a NAS). <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154446%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154446%20v2.png" height="270"/>
</a><br>

</details>
