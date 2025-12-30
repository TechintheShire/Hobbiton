<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(2)%20-%20Emby.png"/> <br>
<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Windows%2011.png"/> <br>

## How to install Emby (Media Server) on Windows 11 Pro

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

### Table of Contents

&emsp; [1] Create a standard (non-administrator) user account on your Windows 11 Pro machine. <br>
&emsp; [2] Download the Emby 'portable' installer. <br>
&emsp; [3] Unzip (install) the Emby 'portable' installer. <br>
&emsp; [4] Set up and initialize your new Emby server. <br>
&emsp; [5] How to Add Libraries. <br>
&emsp; [6] How to Remove Libraries. <br>

&emsp; [#] Appendix <br>
&emsp; [#] Disable automatic reboots caused by Windows Updates. <br>
&emsp; [#] Run Emby (Media Server) as a Windows Service via NSSM (Non-Sucking Service Manager). <br>

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
    <td>Emby 'Portable Installation'</td>
	<td>https://emby.media/windows-server.html</td>
  </tr>
</table>

> ℹ️ Here is a feature comparison between the 'free' vs 'Premiere' licensing options offered by Emby. <br>
> https://emby.media/support/articles/Premiere-Feature-Matrix.html <br>

### Reasons for recommending Emby 'Portable Installation' vs the Windows .exe installer:
> ⚠️ The Emby Windows '.exe' installer forces you (is hard-coded) to install under the Administrator user's 'AppData' folder (C:\Users\Administrator\AppData), which can make it very challenging to operate and manage from a non-administrator (standard user) user account. This is why Emby 'portable' is being recommended. <br>

Emby '*portable*' provides the following benefits:
- No system-wide install
	- Runs out of the folder you extract it to; doesn’t register itself in Windows’ Programs & Features.
- Self-contained environment
	- All configuration, metadata, and binaries live in that one folder. Easy to back up, or move to another machine.
- Doesn’t require admin rights
	- Since it’s not installing system services or writing to Program Files, you can run it under a normal user account.
- Multiple instances possible
	- You can run different portable Emby servers side by side with different configs by extracting to different folders.
- Easier cleanup
	- To “uninstall,” you just delete the folder.

> ℹ️ User authentication for Emby (or Jellyfin) is handled locally on the Emby server itself. This means you can still access and watch your media if you were to lose your internet connection (or didn't have one readily available). PLEX on the other hand, authenticates against PLEX's Cloud Servers. This is good because PLEX is able to include official support for 2FA (Two-Factor Authentication) out of the box; however, this means you can't access or watch your media if you lose your internet connection. This is something to consider when comparing Emby (or Jellyfin) with PLEX. <br>

<br>

***
### [1] Create a standard (non-administrator) user account on your Windows 11 Pro machine.

> ℹ️ If you are an advanced user with a Domain Controller running Active Directory in your environment, I would recommend skipping this step, which is creating a non-administrator local user. At this point, join this Windows 11 Pro machine to your Active Directory and use a non-administrator user within your Domain. <br>

&emsp; Installing and running Emby media server under a standard user account provides increased security and reduces overall risk to your environment in the event that your Windows machine or Emby media server becomes compromised by malware. <br>

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

&emsp; > Log into the non-administrator user account you just created. This is where we'll install our Emby media server software. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png" height="270"/>
</a><br>
<br>

***
### [2] Download the Emby 'portable' installer.

&emsp; > Open https://emby.media/index.html in your browser. <br>
&emsp; > Under '`Emby Server`' > '`Computer`', select '*`Windows`*'. <br>
&emsp; > Scroll down, under the '`Portable Installation`' section, select '*`Windows x64`*' to download the latest portable installer. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20091224%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20091224%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20091257%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20091257%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092123%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092123%20v2.png" height="270"/>
</a><br>
<br>

***
### [3] Unzip (install) the Emby 'portable' installer.

To "install" Emby 'portable', you simply unzip the file (embyserver-win-x64-4.8.11.0.7z) to a location where you'd like to run Emby server from. <br>

I run Emby 'portable' from my Desktop. <br>
&emsp; Example: <br>
`C:\Users\artemis\Desktop\embyserver-win-x64-4.8.11.0\` <br>
<br>

&emsp; > Unzip the Emby 'portable installer' file (embyserver-win-x64-4.8.11.0.7z) to a location where you'd like to run Emby server from. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092331%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092331%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092357%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092357%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092429%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092429%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092459%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092459%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Start Emby by locating the `EmbyServer.exe` file where you unzipped the 'portable' file. <br>

&emsp; Example: <br>
`C:\Users\artemis\Desktop\embyserver-win-x64-4.8.11.0\EmbyServer.exe` <br>

> ℹ️ **Note** <br>
> If you don't see file extensions like '.exe' on your file names and you would like to enable viewing them, follow these steps: <br>
>
> &gt; Windows Explorer <br>
> &gt; Select the `three-dot` hamburger menu <br>
> &gt; Select '`Options`' <br>
> &gt; Select the '`View`' tab <br>
> &gt; Scroll down and uncheck '`Hide extensions for known file types`' <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092602%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092602%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Once you start Emby, it should auto-launch a web browser session. If not, manually try using one of these two links: <br>

`http://localhost:8096/web` <br>

`http://ipAddress:8096/web` <br>
&emsp; Example: <br>
`http://192.168.50.190:8096/web` <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092827%20V2%20(2).png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092827%20V2%20(2).png" height="270"/>
</a><br>
<br>

***
### [4] Set up and initialize your new Emby server.

&emsp; > Once you start Emby, it should auto-launch a web browser session. If not, manually try using one of these two links: <br>

`http://localhost:8096/web` <br>

`http://ipAddress:8096/web` <br>
&emsp; Example: <br>
`http://192.168.50.190:8096/web` <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092827%20V2%20(2).png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092827%20V2%20(2).png" height="270"/>
</a><br>
<br>

&emsp; > Select your preferred display language; I selected `English`, then select '`Next`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092827%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092827%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Create an Emby user by entering a username and password, then select '`Next`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092911%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092911%20v2.png" height="270"/>
</a><br>

You can create/add new libraries during the initialization of your Emby server; however, we're going to skip this step because we'll cover it later in this guide. <br>

&emsp; > Proceed by selecting '`Next`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092929%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092929%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Here you can choose whether or not to allow remote access for your Emby media server. <br>

> ⚠️ Emby currently does not offer a native/built-in solution for 2FA (2-factor authentication). For this reason, I disable this option. In the future, we'll have detailed steps on how to put Emby behind a 2FA/SSO like Authelia or Authentik; until then, we'll leave this disabled. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092951%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20092951%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Accept the 'Terms of Use', then select '`Next`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093011%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093011%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now wrap everything up by selecting '`Finish`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093038%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093038%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > You should be redirected to the login screen. Select your user, then sign in. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093102%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093102%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093123%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093123%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Once you're logged in, you'll be brought to the 'Home' page. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093145%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20093145%20v2.png" height="270"/>
</a><br>
<br>

(Optional) If you purchased an Emby 'Premiere' license, apply it with these steps. <br>
> ℹ️ **Note** <br>
> Here is a feature comparison between the 'free' vs 'Premiere' licensing options offered by Emby. <br>
> https://emby.media/support/articles/Premiere-Feature-Matrix.html

&emsp; > Select the '`Settings`' gear icon in the upper right-hand corner. <br>
&emsp; > Select '`Emby Premiere`' from the left-hand menu. <br>
&emsp; > Under '`Emby Premiere Key`', enter your key and select '`Save`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20095531%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20095531%20v2.png" height="270"/>
</a><br>
<br>

***
### [5] How to Add Libraries.

> ℹ️ **Note** <br>
> If you need some help or guidance on how to organize your media files, please see these two links from Emby. <br>
> Naming and Organizing your Movie media files. <br>
> https://emby.media/support/articles/Movie-Naming.html <br>
>
> Naming and Organizing your TV Show files. <br>
> https://emby.media/support/articles/TV-Naming.html <br>

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

> ℹ️ If you plan to run Emby as a Windows service, it is recommended to use full UNC paths. Mapped network drives (drive letters) are not accessible or mounted until a user manually logs in. <br>

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
&emsp;&emsp; > Then select/put your mouse cursor in the Windows Explorer Address Bar, which should show you and allow you to right-click and copy the full UNC path for that location. <br>

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

&emsp; > Select the '`Settings`' gear icon in the upper right-hand corner. <br>
&emsp; > Select '`Library`'. <br>
&emsp; > Select '`+ New Library`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20095630%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20095630%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Select the '`Content type`'; for example, Movies, TV Shows, Music... etc. <br>
&emsp; > Enter a '`Display name`' for your library. <br>
&emsp; > Then select '`+ Add`' under the 'Folders' section. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20100123%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20100123%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Enter the folder location where your media for that associated library is stored. In my examples, I'm using full UNC paths because I plan to run Emby as a Windows Service. Then select '`OK`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20100156%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20100156%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Once you're finished adding your folder(s), select '`OK`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20100307%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20100307%20v2.png" height="270"/>
</a><br>
<br>

Repeat these steps for any additional libraries you want to add. <br>

<br>

***
### [6] How to Remove Libraries.

> ℹ️ **Note** <br>
> Deleting a library will not delete your actual folders / files. It simply removes the library (access to that media) from your Emby server. <br>

&emsp; > To delete a library, start by selecting the '`Settings`' gear icon in the upper right-hand corner. <br>
&emsp; > Select '`Library`'. <br>
&emsp; > Hover over the library you wish to delete, select the newly visible `three-dot` hamburger menu. <br>
&emsp; > Select '`Remove`' to remove/delete the library. <br>
&emsp; > When prompted, confirm and select '`Remove`' to remove/delete the library. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20101735%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20101735%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20101753%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20101753%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20101810%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20101810%20v2.png" height="270"/>
</a><br>

<br>
<br>

***

## Appendix

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
&emsp;&emsp;&emsp;&emsp; > Right-click your newly created GPO and select '`Edit…`'. <br>
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
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png" height="270"/>
</a><br>

</details>

#

</details>

#

### Run Emby (Media Server) as a Windows Service via NSSM (Non-Sucking Service Manager).

<details>
  <summary>Expand for additional details.</summary>
<br>
	
In this section, we'll cover how to run Emby (Media Server) as a Windows Service using NSSM. <br>

> ⚠️ I would recommend starting this process without Emby running. <br>

> ℹ️ Running Emby as a Windows Service significantly improves stability and availability through two methods: <br>
> &nbsp;- Emby will start at boot, which reduces downtime caused by unexpected reboots. <br>
> &nbsp;- The Windows Service Control Manager (SCM) will monitor and automatically restart Emby if any crashes or unexpected stops are detected. <br>

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

&emsp; > 'cd' (change directory) to the location where you're storing your nssm.exe file (tool). <br>

&emsp; Example: `cd "C:\Users\artemis\Desktop\Toolkit\nssm-2.24`

&emsp; > Verify you're in the correct folder (directory) by listing the folder (directory) contents. You should see the `nssm.exe` file: <br>

```bash
dir
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153504%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153504%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Start the NSSM tool and install Emby as a Windows Service: <br>

```bash
nssm install "emby"
```

&emsp; After running the command above, the NSSM GUI (graphical user interface) will open. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20151708%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20151708%20v2.png" height="270"/>
</a><br>
<br>

&emsp; In the NSSM GUI, configure the following options: <br>

&emsp;&emsp; > 'Application' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'Path': `C:\Users\artemis\Desktop\embyserver-win-x64-4.8.11.0\system\EmbyServer.exe` <br>
&emsp;&emsp;&emsp;&emsp; 'Startup directory': `C:\Users\artemis\Desktop\embyserver-win-x64-4.8.11.0\system\` <br>
&emsp;&emsp;&emsp;&emsp; 'Arguments': Leave this blank. <br>

&emsp;&emsp; > 'Details' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'Display name': `Emby` <br>
&emsp;&emsp;&emsp;&emsp; 'Description': `Runs Emby as a Windows service using NSSM.` <br>

&emsp;&emsp; > 'Log on' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'This account': Enter your username <br>
&emsp;&emsp;&emsp;&emsp; 'Password': Enter your password <br>
&emsp;&emsp;&emsp;&emsp; 'Confirm': Re-enter your password for confirmation <br>

> ℹ️ In my example, I'm using an Active Directory/Domain user account, which is why I append '@spartan23.home' after my username. If you're not using an Active Directory/Domain user account, please ignore that syntax. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20151850%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20151850%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20152132%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20152132%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155224%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155224%20v2.png" height="270"/>
</a><br>
<br>

&emsp;&emsp; > (Optional but useful) I/O tab: <br>
&emsp;&emsp;&emsp; > Create a 'Logs' folder. <br>
&emsp;&emsp;&emsp; > Create an output (emby_stdout.log) and error (emby_stderr.log) log files within the 'Logs' folder. <br>
&emsp;&emsp;&emsp; > Set the output and error log locations within the NSSM GUI. <br>

> ℹ️ In my example, I put these log files in the same Desktop folder that I put the NSSM .exe tool. <br>

Output log file: `C:\Users\artemis\Desktop\Toolkit\Logs\emby_stdout.log` <br>
Error log file: `C:\Users\artemis\Desktop\Toolkit\Logs\emby_stderr.log` <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155325%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155325%20v2.png" height="270"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155420%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155420%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Now select '`Install service`'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155420%20v2%20(2).png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155420%20v2%20(2).png" height="270"/>
</a><br>
<br>

&emsp; If successful, you should see the "`Service 'Emby' installed successfully!`". <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155513%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155513%20v2.png" height="270"/>
</a><br>
<br>

&emsp; You can also see this 'success' message in the Command Prompt (CMD) window: <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155535%20v2.png">
	<img src="./Icons%20and%20Screenshots/Screenshot%202025-10-02%20155535%20v2.png" height="270"/>
</a><br>
<br>

&emsp; We have a few options to start our newly created service. <br>
&emsp; &emsp; Option 1, start the service via NSSM. <br>

```bash
nssm start "emby"
```

&emsp;&emsp; Option 2, start the service via Windows Service tool. <br>
&emsp;&emsp; Option 3, reboot the Windows 11 Pro machine. <br>
<br>

</details>

#
