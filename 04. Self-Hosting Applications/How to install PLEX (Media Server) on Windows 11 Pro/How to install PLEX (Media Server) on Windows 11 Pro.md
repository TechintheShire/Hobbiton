<a href="./Icons%20and%20Screenshots/20250805_095720.png">
  <img src="./Icons%20and%20Screenshots/20250805_095720.png" height="170"/>
</a>
<a href="./Icons%20and%20Screenshots/20250805_111419.png">
  <img src="./Icons%20and%20Screenshots/20250805_111419.png" height="170"/>
</a>

# How to install PLEX (Media Server) on Windows 11 Pro

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

## Recommended Operating System / Version
&emsp; Windows 11 Pro <br>

> ℹ️ **Note** <br>
> If you need help deploying Windows 11 Pro, please see my guide here, [How to install Windows 11 Pro](../../01.%20Operating%20Systems/How%20to%20install%20Windows%2011%20Pro/How%20to%20install%20Windows%2011%20Pro.md).
<br>

## Reasons for recommending Windows 11 Pro
&emsp; - Windows Operating Systems are widely in use and familiar for most users. <br>
&emsp; - Media management is typically easier in a Windows environment (managing folders, files, network shares, access, permissions... etc.). <br>
&emsp; - Using a Windows based Operating System provides integrations with VSS (Volume Shadow-copy Service), which gives you access to 'Previous Versions'. If you use TrueNAS Scale, you can provide this capability for your SMB shares!  <br>
&emsp; - Windows 11 Pro (vs Home) unlocks the following helpful features: <br>
&emsp;&emsp; - Remote Desktop connections. <br>
&emsp;&emsp; - Group Policy Editor, to disable automatic reboots caused by Windows Updates (see Appendix section in this guide). <br> 
&emsp;&emsp; - (Optional) Active Directory integration. <br>
&emsp; - Development Teams for library automation tools such as Radarr, Sonarr, Lidarr, and more... etc. officially support Windows. <br>
<br>

> ⚠️ **Warning**  
>
> Windows 11 has introduced an AI screen logging feature called 'Recall', which is a concern for both privacy and security.
>
> As of 2025/05, if you're using a standard x86-based system (Intel/AMD), Recall is not enabled, and you don't need to worry about it.
>
> At this time, the feature is only available / enabled under the following conditions: <br>
> &nbsp;- Copilot+ PCs, which use ARM-based Snapdragon X Elite/Plus chips. <br>
> &nbsp;- Devices running Windows 11 24H2 or later with NPU (Neural Processing Unit). <br>
>
> If in the future, this feature is enabled by default for all system types, we will strongly consider using a different operating system / platform; for example, Docker, which I also have a guide for. <br>
<br>

## Helpful Offical Links from PLEX
&emsp; General Requirements <br>
&emsp;&emsp; https://support.plex.tv/articles/200375666-plex-media-server-requirements/ <br>
&emsp; Recommended CPU(s) <br>
&emsp;&emsp; https://support.plex.tv/articles/201774043-what-kind-of-cpu-do-i-need-for-my-server/ <br>
&emsp; Hardware Acceleration (Transcoding) (CPU/GPU) <br>
&emsp;&emsp; https://support.plex.tv/articles/115002178853-using-hardware-accelerated-streaming/ <br>

<br>
<br>

***

## Install and Configure, Plex Media Server

### [1] Create a standard (non-administrator) user account on your Windows 11 Pro machine.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> If you are an advanced user with a Domain Controller running Active Directory in your environment, I would recommend skipping this step, which is creating a non-administrator local user. At this point, join this Windows 11 Pro machine to your Active Directory and use a non-administrator user within your Domain.

&emsp; Installing and running 'Plex Media Server' under a standard user account provides increased security and reduces overall risk to your environment in the event that your Windows machine or 'Plex Media Server' becomes compromised by malware. <br>

Create a standard (non-administrator) user following these steps: <br>
&emsp; > Log into an administrator-level account, if not already. <br>
&emsp; > Windows Start Menu <br>
&emsp; > Settings <br>
&emsp; > Accounts <br>
&emsp; > Scroll down to 'Other Users' <br>
&emsp; > To the right of 'Add other user' select 'Add account'. <br>
&emsp; > I recommend creating an 'non-microsoft' account. <br>
&emsp; > Select 'I don't have this person's sign-in information'. <br>
&emsp; > Select 'Add a user without a Microsoft account'. <br>
&emsp; > Follow the steps to create your new user. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123445%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123500%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123500%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123515%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123515%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123530%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123530%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123545%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123545%20v2.png" height="470"/>
</a><br>
<br>

Log into the non-administrator user account you just created.
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png" height="470"/>
</a><br>

</details>

### [2] Create a PLEX account.

<details>
  <summary>Expand for additional details.</summary>

<br>
&emsp;> Open https://www.plex.tv/ in your browser. <br>
&emsp;> Select 'Sign Up Free' and create your account. <br>
<br>

> ℹ️ **Note** <br>
> Here is a feature comparison between the 'free' vs 'PLEX Pass' licensing options offered by PLEX. <br>
> https://www.plex.tv/plans/#product-features
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20110000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20110000%20v2.png" height="470"/>
</a><br>

</details>

### [3] Download the 'Plex Media Server' .exe installer.

<details>
  <summary>Expand for additional details.</summary>

<br>
&emsp;> Open https://www.plex.tv/ in your browser. <br>
&emsp;> Select 'Download' > 'Plex Media Server' under 'Plex Pro Downloads'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120000%20v2.png" height="470"/>
</a><br>
<br>

&emsp;> Under the drop down menu, verify 'Windows' is selected. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120010%20v2.png" height="470"/>
</a><br>

&emsp;> Click the 'Choose Distribution' button. <br>
&emsp;> Select 'Windows 64-bit' to begin downloading the installer (PlexMediaServer-1.41.6.9685-d301f511a-x86_64.exe file). Your .exe version number will likely be different depending on the date/time of your download. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-19%20120020%20v2.png" height="470"/>
</a><br>
<br>

> ℹ️ **Note** <br>
> To check your Operating System type (64-bit vs 32-bit): <br>
> &emsp; > Windows Start Menu <br>
> &emsp; > Settings <br>
> &emsp; > System <br>
> &emsp; > About <br>
> &emsp; > View ‘System type’. <br>

</details>

### [4] Start the 'Plex Media Server' installer.

<details>
  <summary>Expand for additional details.</summary>

<br>
Start the 'Plex Media Server' installer by double-clicking or right-clicking the .exe, follow the installer steps. <br>
<br>

> ℹ️ **Note** <br>
> If you don't see file extensions like '.exe' on your file names and you would like to enable viewing them, follow these steps: <br>
>
> &gt; Windows Explorer <br>
> &gt; Select the three-dot hamburger menu <br>
> &gt; Select 'Options' <br>
> &gt; Select the 'View' tab <br>
> &gt; Scroll down and uncheck 'Hide extensions for known file types' <br>

&emsp; Once the 'Plex Media Server' installer has started, you can click through and accept all of the default options to complete the installation process. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120000%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120010%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120020%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120030%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120040%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120040%20v2.png" height="470"/>
</a><br>
<br>

&emsp; You can verify if the 'Plex Media Server' software has successfully started by checking the Windows 'System Tray' or 'Notification Area' to view the Plex icon. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120050%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120050%20v2.png" height="470"/>
</a><br>
<br>
</details>

### [5] Sign-in and initialize your new 'Plex Media Server'.

<details>
  <summary>Expand for additional details.</summary>

<br>
&emsp; Starting the 'Plex Media Server' application should automatically open a browser tab to the following URL; if it does not after a few seconds, open one manually: `https://app.plex.tv` <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120100%20v2.png" height="470"/>
</a><br>
<br>

&emsp; If you previously created and logged into your Plex account, select your account and give your new 'Plex Media Server' a few minutes to 'initialize'. <br>
 
&emsp; If after a few minutes, the 'initialization' process appears to be hanging, try refreshing the browser tab. If that doesn't work, try selecting 'Sign In' (upper right-hand corner) again and log in. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120110%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120110%20v2.png" height="470"/>
</a><br>
<br>

&emsp; Once you have successfully signed in, you should be greeted by a 'Server Setup' wizard. Select 'Got It!' to continue. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120120%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120120%20v2.png" height="470"/>
</a><br>
<br>

&emsp;> Assign a name for your Plex Media Server. In my example, my server will be named 'venom'. <br>
&emsp;> Confirm whether or not you want to enable access to your 'Plex Media Server' outside of your local LAN, meaning over the WAN/internet. *More on that later in this guide. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120130%20v2.png" height="470"/>
</a><br>
<br>

&emsp;> Next, you can determine whether or not to add media libraries, we'll be walking through this in more detail in a later step, so we'll skip this for now. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120140%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120140%20v2.png" height="470"/>
</a><br>
<br>

&emsp;> Select 'Done'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120150%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-20%20120150%20v2.png" height="470"/>
</a><br>
<br>
</details>

### [6] Activate (enable) Two-Factor Authentication (2FA).

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> <br>
> This step is optional but highly recommended. If you plan to expose your 'Plex Media Server' over the WAN/internet, this step should be considered manditory. <br>
> <br>
> My recommendation would be to use 'Google Authenticator', which is an easy to use TOTP (time-based one-time password) application. Mine is setup on my iPhone. <br>

&emsp; Navigate to the following location on your 'Plex Media Server': <br>
&emsp;&emsp; > Settings <br>
&emsp;&emsp; > Account <br>
&emsp;&emsp; > Select 'Edit' for 'Two-Factor Authentication'. <br>
&emsp;&emsp; > Follow the steps to enable 2FA. <br>
<br>
</details>

### [7] How to Add Libraries.
<details>
  <summary>Expand for additional details.</summary>

***

#### Locate and prepare your media files.
<details>
  <summary>Expand for additional details.</summary>
<br>

If you need some help or guidance on how to organize your media files, please see these two links from Plex. <br>

Naming and Organizing your Movie media files. <br>
https://support.plex.tv/articles/naming-and-organizing-your-movie-media-files/ <br>
<br>

Naming and Organizing your TV Show files. <br>
https://support.plex.tv/articles/naming-and-organizing-your-tv-show-files/ <br>
***
</details>

#### How to map a Network Drive.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; You can access network drives (shares) using either your NAS server's DNS hostname or IP address in the Windows Explorer address bar. <br>

&emsp; DNS hostname Example: <br>

 	\\apollo

&emsp; IP address Example: <br>

	\\192.168.50.191
<br>

> ⚠️ **Be Aware**  
>
> If you're having issues browsing or access SMB shares on your network, ensure 'Network discovery' and 'File and printer sharing' are enabled (set to 'On') under Settings > Network & internet > Advanced network settings . <br>
>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143546%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143546%20v2.png" height="470"/></a><br>
<br>

&emsp; I recommend following these steps to map a network drive: <br>
&emsp;&emsp; > Open Windows Explorer. <br>
&emsp;&emsp; > Navigate to the 'Network' section under the left side Navigation Pane. <br>
&emsp;&emsp; > Select your NAS server. <br>
&emsp;&emsp; > Right-click your SMB network share, then select 'Map network drive...'. <br>
&emsp;&emsp;&emsp; > Select (assign) a drive letter. <br>
&emsp;&emsp;&emsp; > Ensure 'Reconnect at sign-in' is selected. This will ensure the drive will get mapped (remapped) next time you log in. <br>
&emsp;&emsp;&emsp; > If needed, select 'Connect using different credentials'. <br>
&emsp;&emsp;&emsp; > Then select 'Finish', which will map the network drive. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143547%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143547%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143614%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143614%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143710%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143710%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143737%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143737%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143810%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143810%20v2.png" height="470"/>
</a><br>
<br>

&emsp; If the drive was successfully mapped, you should see a new Windows Explore window open and display the contents within the mapped network drive. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143829%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143829%20v2.png" height="470"/>
</a><br>
<br>

&emsp; You can also confirm the drive was successfully mapped by checking under 'This PC'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143900%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143900%20v2.png" height="470"/>
</a><br>
<br>

***
</details>

#### How to find your full UNC path.
<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Open Windows Explorer. <br>
&emsp; > Navigate to the 'Network' section under the left side Navigation Pane. <br>
&emsp; > Select your NAS server. <br>
&emsp; > Select you SMB network Share. <br>
&emsp; > If needed, navigate through any subdirectories. <br>
&emsp; > Then select/put your mouse cursor in the Windows Explore Address Bar, which should show you and allow you to right-click and copy the full UNC path for that location. <br>

Full UNC Path Example: <br>

	\\APOLLO\Media\TV Shows

> ⚠️ **Be Aware**  
>
> If you're having issues browsing or access SMB shares on your network, ensure 'Network discovery' and 'File and printer sharing' are enabled (set to 'On') under Settings > Network & internet > Advanced network settings . <br>
>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143546%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143546%20v2.png" height="470"/></a><br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112213%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112213%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112224%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112224%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112237%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112237%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112250%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112250%20v2.png" height="470"/>
</a><br>
<br>

&emsp; In this example, the syntax is as follows: <br>
&emsp;&emsp; \\\APOLLO\Media\TV Shows <br>
&emsp;&emsp; \\\NAS server\SMB network share\subdirectory <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112251%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20112251%20v2.png" height="470"/>
</a><br>

</details>

***

### [Add Library - Option 1]

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp;&emsp;&emsp; > From the default homepage, select 'More >'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120000%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Select the '+' sign next to your server's hostname. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120010%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > In this example, we'll add a 'Movies' library by selecting the 'Movies' icon/type. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120020%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Select 'Browse for Media Folder'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120030%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Select the folder where your Movie files are located. This can be on your local machine or on a mapped network drive. <br>
&emsp;&emsp;&emsp; > Select the appropriate drive letter and then browse to the folder/sub-folder where your Movie files are located, then select 'Add'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120040%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120040%20v2.png" height="470"/>
</a><br>

<br>

In following the example above, keep in mind, you can use local folders, mapped network drives, or full UNC network paths, see below. <br>
If you plan to run 'Plex Media Server' as a Windows Service (more on this in the Appendix section), you will need to use full UNC network paths. <br>

| Mapped Network Drive | Full UNC Network Path |
|----------|----------|
| Z:\Movies    | Syntax: \\\NAS Server\Network Share\Folder <br><br> \\\apollo\Media\Movies  |
| Example: <br> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120055%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120055%20v2.png" height="300"/></a> | Example: <br> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120110%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120110%20v2.png" height="300"/></a> |
<br>

&emsp;&emsp;&emsp; > When finished, select 'Add Library'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120050%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120050%20v2.png" height="470"/>
</a><br>
<br>

Once the library has been added, your Plex Media Server will start to scan the folder locations you specified and will organize, list, and add meta-data for each of the Movies / TV Shows in your respective library. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120100%20v2.png" height="470"/>
</a><br>
</details>

***

### [Add Library - Option 2]

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp;&emsp;&emsp; > Go to 'Settings'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120000%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Verify the appropriate 'Plex Media Server' is selected. <br>
&emsp;&emsp;&emsp; > In my example, my server name is 'venom'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120010%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Go to 'Manage' > 'Libraries' > Select 'Add Library'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120020%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > In this example, we'll add a 'TV Shows' library by selecting the 'TV Shows' icon/type. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120030%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp;&emsp; > Select 'Browse for Media Folder'. <br>
&emsp;&emsp;&emsp; > Select the folder where your TV Show files are located. This can be on your local machine or on a mapped network drive. <br>
&emsp;&emsp;&emsp; > Select the appropriate drive letter and then browse to the folder/sub-folder where your Movie files are located, then select 'Add'. <br>

Keep in mind, you can use local folders, mapped network drives, or full UNC network paths, see below. <br>
If you plan to run 'Plex Media Server' as a Windows Service (more on this in the Appendix section), you will need to use full UNC network paths. <br>

| Mapped Network Drive | Full UNC Network Path |
|----------|----------|
| Z:\Movies    | Syntax: \\\NAS Server\Network Share\Folder <br><br> \\\apollo\Media\Movies  |
| Example: <br> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120055%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120055%20v2.png" height="300"/></a> | Example: <br> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120110%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-21%20120110%20v2.png" height="300"/></a> |
<br>

&emsp;&emsp;&emsp; > When finished, select 'Add Library'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120040%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-22%20120040%20v2.png" height="470"/>
</a><br>
<br>
</details>

***

</details>

### [8] How to Remove Libraries.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> Deleting a library will not delete your actual folders / files. It simply removes the library (access to that media) from your 'Plex Media Server'. <br>

> ⚠️ **Warning**  
>
> Be aware, individual files within your library can be deleted! <br>
>
> To disable this, navigate to Settings > Library > Uncheck 'Allow media deletion' > Scroll down and select 'Save'. <br>
>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120015%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120015%20v2.png" height="470"/></a><br>

***

### [Remove Library - Option 1]

<details>
  <summary>Expand for additional details.</summary>

<br>
&emsp;&emsp;&emsp; From the default homepage (if your library is pinned to your Home/Dashboard page): <br>
&emsp;&emsp;&emsp;&emsp; > Hover over the lirbary you want to delete and select the '3-dot' hamburger menu. <br>
&emsp;&emsp;&emsp;&emsp; > Select 'Manage Library'. <br>
&emsp;&emsp;&emsp;&emsp; > Select 'Delete'. <br>     		
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-23%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-23%20120000%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-23%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-23%20120010%20v2.png" height="470"/>
</a><br>
</details>

***

### [Remove Library - Option 2]

<details>
  <summary>Expand for additional details.</summary>

<br>
&emsp;&emsp;&emsp; From the default homepage (if the library is NOT pinned to your Home/Dashboard page): <br>
&emsp;&emsp;&emsp;&emsp; > Scroll down and select 'More >' <br>
&emsp;&emsp;&emsp;&emsp; > Identifiy the server you want to delete the library from. <br>
&emsp;&emsp;&emsp;&emsp; > Under that server, hover over the lirbary you want to delete and select the '3-dot' hamburger menu. <br>
&emsp;&emsp;&emsp;&emsp; > Select 'Manage Library'. <br>
&emsp;&emsp;&emsp;&emsp; > Select 'Delete'. <br>     		
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120000%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120010%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-24%20120020%20v2.png" height="470"/>
</a><br>
</details>

***

### [Remove Library - Option 3]

<details>
  <summary>Expand for additional details.</summary>

<br>
&emsp;&emsp;&emsp; From the default homepage: <br>
&emsp;&emsp;&emsp;&emsp; > Go to 'Settings'. <br>
&emsp;&emsp;&emsp;&emsp; > Verify the appropriate 'Plex Media Server' is selected. <br>
&emsp;&emsp;&emsp;&emsp; > Under 'Manage', go to 'Libraries'. <br>
&emsp;&emsp;&emsp;&emsp; > Hover over the lirbary you want to delete and select the '3-dot' hamburger menu. <br>
&emsp;&emsp;&emsp;&emsp; > Select 'Delete'. <br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120000%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120010%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120020%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-25%20120030%20v2.png" height="470"/>
</a><br>
<br>
</details>

***

</details>

### [9] (Optional) Enable 'Remote Access'.

<details>
  <summary>Expand for additional details.</summary>

***

#### [Remote Access - Option 1 (UPnP)] 

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; If your router supports UPnP (Universal Plug and Play) and it is enabled, you should be able to 'Enable Remote Access' and the UPnP service should configure/map the necessary networking to access your 'Plex Media Server' externally over the WAN/internet without having to touch your firewall or manually forward ports. <br>
<br>

> ⚠️ **Warning**  
>
> Be aware, UPnP does not require authentication to configure these network settings, which is considered a security risk! If security is important to you, consider options 2 or 3. <br>

&emsp; > Settings <br>
&emsp; > Select 'Remote Access' under the Settings section <br>
&emsp; > Select 'Enable Remote Access' <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120000%20v2.png" height="470"/>
</a><br>
<br>

&emsp; If remote access has been enabled successfully, you should see a screen similar to the following. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120010%20v2.png" height="470"/>
</a><br>

***
</details>

***

#### [Remote Access - Option 2 (Manual Port-Forward on Firewall)]

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp;&emsp;&emsp; If your router doesn't support UPnP/NAT-PMP or you'd rather have more control over the port forwarding and network configuration, you can enable the 'manually specify public port' feature. The default port is 32400, which I recommend leaving. If you proceed with this option, you will need to manually configure your router's firewall to port-forward port 32400 to the IP address where your 'Plex Media Server' is running. Hopefully you've set a static IP address for your Plex Media Server; if not, pause here and do that now. <br>

&emsp; > On your router, Port-forward port 32400 to your Plex Media Server's IP address. <br>
&emsp; > In plex, navigate to the following location. <br>
&emsp; > Settings <br>
&emsp; > Select 'Remote Access' under the Settings section <br>
&emsp; > Select 'Enable Remote Access' <br>
&emsp; > Check 'Manually specify public port' and set/keep the port as default 32400 and select apply. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-26%20120020%20v2.png" height="470"/>
</a><br>

***
</details>

***

#### [Remote Access - Option 3 (Reverse Proxy)]

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; This option would be my ultimate recommendation. Routing access/traffic through a reverse proxy like 'Nginx Proxy Manager'. Using reverse proxies is more advanced and requires a deeper understanding of networking, DNS, and other concepts. I won't be covering that here in any detail as I have a seperate guide/tutorial on this (Reverse Proxies).
<br>
</details>

***

</details>

### [10] Configure 'Plex Media Server' Settings.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Various settings can be considered personal preference depending on your underlying hardware, use cases, or needs. I'll share what I use in general, but be sure to tailor your settings to your needs. <br>

&emsp; [General Settings] <br>
&emsp;&emsp; > Settings <br>
&emsp;&emsp; > Select 'General' under the Settings section. <br>
&emsp;&emsp; > Uncheck 'Send crash reports to Plex' (sorry plex, I do this for almost everything, trying to get a bit more privacy). <br>
&emsp;&emsp; > Select Save 'Changes' <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120000%20v2.png" height="470"/>
</a><br>
<br>

&emsp; [Library Settings] <br>
&emsp;&emsp; > Settings <br>
&emsp;&emsp; > Select 'Library' under Settings section. <br>
&emsp;&emsp; > Check 'Scan my library automatically'. <br>
&emsp;&emsp; > Check 'Scan my library periodically' with a Library scan interval of 'daily'. <br>
&emsp;&emsp; > Check 'Empty trash automatically after every scan'. <br>
&emsp;&emsp; > If you haven't already, uncheck 'Allow media deletion'. <br>
&emsp;&emsp; > Select 'Save Changes'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120010%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120010%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120020%20v2.png" height="470"/>
</a><br>
<br>

&emsp; [Network Settings] <br>
&emsp;&emsp; > Set 'Secure connections' to 'Required'. <br>
&emsp;&emsp;&emsp;&emsp; I encourage this, similar to enabling 2FA, to increase security. <br>
&emsp;&emsp; > Select 'Save Changes'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120030%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120040%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-27%20120040%20v2.png" height="470"/>
</a><br>
<br>

&emsp; [Transcoder Settings] <br>
&emsp;&emsp; These settings will be highly dependant on your hardware and personal preferences. <br>
&emsp;&emsp; > If you have hardware transcoding available via Intel Quick Sync or a dedicated NVIDIA/AMD GPU, I encourage enabling the following settings: <br>
&emsp;&emsp; > Enable 'Use hardware acceleration when available'. <br>
&emsp;&emsp; > Enable 'Use hardware-accelerated video encoding'. <br>
&emsp;&emsp; > Select 'Save Changes'. <br>

&emsp; [Scheduled Task Settings] <br>
&emsp;&emsp; > Change 'Time at which tasks start to run' to an appropriate time depending on your environment. <br>
&emsp;&emsp; > Change 'Time at which tasks stop running' to an appropriate time depending on your environment. <br>
&emsp;&emsp; > Select 'Save Changes'. <br>
<br>
</details>

<br>
<br>

***

## Upgrading 'Plex Media Server'

<details>
  <summary>Expand for additional details.</summary>
<br>

> ⚠️ **Alert**  
>
> If you are running PLEX as a Windows Service, set 'startup type' to 'disabled'. Otherwise, the Windows Service Control Manager (SCM) will quickly restart the previous code version instance preventing the new code version from loading. Yes, SCM is that quick and efficient! <br>
>
> Via Windows Services App: <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150732%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150732%20v2.png" height="470"/></a>
>
> Via NSSM: <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150733%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150733%20v2.png" height="470"/></a>

### [Option 1] Initiate the upgrade from the 'Notifications' / 'Server Notifications' area.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Here, in the notifications area (upper righthand corner), we can see 'Plex Media Server' reporting that an upgrade is available. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174118%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174118%20v2.png" height="470"/>
</a><br>

&emsp; If we click on the notification area, we can see which server (or servers) are reporting an available upgrade. In my example, I have two Plex Media Servers, one named Nova and the other Venom. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174133%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174133%20v2.png" height="470"/>
</a><br>

&emsp; If you select 'Server Update Available' for either server, it will bring to the upgrade page for that respective server. <br>
&emsp; If you'd like to continue with the upgrade, there are two steps: <br>
&emsp;&emsp; - Download the upgrade package (software). <br>
&emsp;&emsp; - Then install the upgrade, which we'll see in the following screenshots. <br>
&emsp; Select 'Download now' to continue. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174156%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174156%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174218%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174218%20v2.png" height="470"/>
</a><br>

&emsp; To continue with the upgrade, select 'Install now'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174235%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174235%20v2.png" height="470"/>
</a><br>

&emsp; While the upgrade is being performed, your 'Plex Media Server' will be unavailable. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174317%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174317%20v2.png" height="470"/>
</a><br>
<br>

&emsp; Once the upgrade is complete, it should automatically load your Plex Home page. <br>
&emsp; In my experience, the upgrade usually takes a few seconds to complete (not very long). <br>
&emsp; If your Plex Home page does not load automatically after a few seconds/minutes, select 'Retry connection', seen in the previous screenshot.
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174456%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174456%20v2.png" height="470"/>
</a><br>

</details>

### [Option 2] Initiate the upgrade from the 'Settings' area.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Here, in the notifications area (upper righthand corner), we can see 'Plex Media Server' reporting that an upgrade is available. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094410%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094410%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094426%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094426%20v2.png" height="470"/>
</a><br>
<br>

&emsp; Select 'Settings' in the upper right-hand corner. The icon looks like a wrench.
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094450%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094450%20v2.png" height="470"/>
</a><br>

&emsp; Ensure you've selected the appropriate server (if you have more than one).
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094506%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094506%20v2.png" height="470"/>
</a><br>

&emsp; Under 'Settings', select 'General'. Here you will see the ability to download the update package.
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094544%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094544%20v2.png" height="470"/>
</a><br>

&emsp; Select 'Download Updates' and the download will begin.
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094628%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094628%20v2.png" height="470"/>
</a><br>

&emsp; Once the download is complete, select 'Install Update' to begin the update.
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094653%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094653%20v2.png" height="470"/>
</a><br>
<br>

&emsp; While the upgrade is being performed, your 'Plex Media Server' will be unavailable. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094728%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094728%20v2.png" height="470"/>
</a><br>
<br>

&emsp; Once the upgrade is complete, it should automatically load your Plex Home page. <br>
&emsp; In my experience, the upgrade usually takes a few seconds to complete (not very long). <br>
&emsp; If your Plex Home page does not load automatically after a few seconds/minutes, select 'Retry connection', seen in the previous screenshot.
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094808%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094808%20v2.png" height="470"/>
</a><br>

</details>

### Helpful tips and troubleshooting.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ⚠️ **Remote Installation Warning** <br>
> 
> You may see a warning about installing software remotely. It is extremely rare that the Plex upgrade will require a local prompts; however, if this concerns you, I would Remote Desktop into your Windows 11 Pro machine where 'Plex Media Server' is running and initiate the upgrade there. You'll still be using the same web browser interface; however, you'll be logged in locally on the Windows desktop. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174251%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-26%20174251%20v2.png" height="470"/></a><br>

<br>

> ℹ️ **Note** <br>
>
> If you are running PLEX as a Windows Service, set 'startup type' to 'disabled'. Otherwise, the Windows Service Control Manager (SCM) will quickly restart the previous code version instance preventing the new code version from loading. Yes, SCM is that quick and efficient! <br>
>
> Via Windows Services App: <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150732%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150732%20v2.png" height="470"/></a>
>
> Via NSSM: <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150733%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-09-12%20150733%20v2.png" height="470"/></a>
>
> If you already initiated the upgrade before setting 'startup type' to 'disabled' you can restart the PLEX service to complete the upgrade.
> 
> Here you will notice, Plex Media Server is still running a previous version of the code. To fix this, we need to restart the Windows service running Plex Media Server. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094808%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094808%20v2.png" height="470"/></a><br>
> 
> Open and run the 'Services' app as Administrator. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094919%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20094919%20v2.png" height="470"/></a><br>
> 
> Find and restart the Windows service associated with your 'Plex Media Server'. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20095010%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20095010%20v2.png" height="470"/></a><br>
>
> You can also restart the Windows service using NSSM. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20095134%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-28%20095134%20v2.png" height="470"/></a><br>
> 
> Once you restart the associated Windows service, we can see 'Plex Media Server' running the latest/upgraded code. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20112400%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20112400%20v2.png" height="470"/></a><br>

</details>

</details>

<br>
<br>

***

## Uninstall 'Plex Media Server'

<details>
  <summary>Expand for additional details.</summary>
<br>

Use these steps to uninstall 'Plex Media Server': <br>

1. Stop the 'Plex Media Server' Process (if still running). <br>
&emsp; > Under the Windows notification area, right-click the 'Plex Media Server' icon and select exit to stop the 'Plex Media Server' process. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145516%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145516%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145639%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145639%20v2.png" height="470"/>
</a><br>
<br>

> ℹ️ **Note** <br>
> 
> If you are running 'Plex Media Server' as a Windows service, the active/running process will not show up in the Windows notification area. You will need to stop it via the Windows Services app or NSSM. I recommend using NSSM because we can stop and remove the Windows service all together. <br>
> 
> &emsp; Run the following NSSM commands to stop and remove the Windows service associated with your 'Plex Media Server'. <br>
> ```bash
> nssm status "plexmediaserver"
> ```
> ```bash
> nssm stop "plexmediaserver"
> ```
> ```bash
> nssm remove "plexmediaserver"
> ```
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150030%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150030%20v2.png" height="470"/></a><br>
> 
> &emsp; You can stop and disable (but not remove) a Windows service using the Windows Services app. <br>
>
> Right-click the Windows Services app and select 'Run as administrator'. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145801%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145801%20v2.png" height="470"/></a><br>
>
> Find and right-click the Windows service that is realted to your 'Plex Media Server'. Select 'Properties'.
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145930%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145930%20v2.png" height="470"/></a><br>
>
> Under the 'General' tab, select 'Stop' to stop the Windows service. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145931%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145931%20v2.png" height="470"/></a><br>
>
> Here, you can see the 'plexmediaserver' / 'Plex Media Server' Windows service stopping. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145932%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145932%20v2.png" height="470"/></a><br>
>
> Under the same 'General' tab, select the dropdown menu next to 'Startup type:' and select 'Disabled'.
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145933%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145933%20v2.png" height="470"/></a><br>
>
> Select 'Apply' to apply the settings we just configured. At this point, even if the Windows 11 Pro machine reboots, this service won't start autoamtically. If disabling the Windows service is sufficient for you're needs, proceed to the next step. If you'd prefer to remove/delete the Windows service, you'll need a tool like NSSM. NSSM can remove/delete the Windows service using the 'Service name:'. In this example, it would be 'plexmediaserver'. <br>
> <a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145934%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20145934%20v2.png" height="470"/></a><br>
<br>

2. Uninstall 'Plex Media Server' via the Windows Settings app. <br>
&emsp; > Navigate to 'Settings' > 'Apps' > 'Installed apps' . <br>
&emsp; > Scroll down until you see 'Plex Media Server <version number>' or search 'Plex Media Server' in the upper search bar. <br>
&emsp; > Select the three-dot hamburger menu on the right of the 'Plex Media Server' app, and select 'Uninstall'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150118%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150118%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150136%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150136%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150231%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150231%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150245%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150318%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150318%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150334%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150334%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150351%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150351%20v2.png" height="470"/>
</a><br>
<br>

3. Delete related 'Plex Media Server' Directories. <br>

&emsp; Even after uninstalling the 'Plex Media Server' app, there may be directories left behind that include configuration, cache, and metadata files. Depending on the size of your media collection, these folders could contain Gigabytes (GB) or more worth of data. <br>

Delete the following folders/directories: <br>
&emsp; C:\Users\<YourUsername>\AppData\Local\Plex Media Server <br>
&emsp; C:\Program Files\Plex <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150445%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150509%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150509%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150557%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150557%20v2.png" height="470"/>
</a><br>
<br>

Now empty your recycle bin. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150701%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150701%20v2.png" height="470"/>
</a><br>

4. Reboot your Windows 11 Pro machine. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150732%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-29%20150732%20v2.png" height="470"/>
</a><br>

</details>

<br>
<br>

***

# Appendix

## Disable automatic reboots caused by Windows Updates.

<details>
  <summary>Expand for additional details.</summary>
<br>

Following these steps will significantly reduce the risk of unexpected or unplanned outages and downtime for this Windows 11 machine and any Apps we decide to run on this machine. Windows Updates will still be downloaded and applied when they become available; however, you get to choose when to initiate the reboot. I typically Remote Desktop into the Windows 11 machine and selecting reboot when ready. If you run your Apps as a Windows 'service', this may not be as much of a conern; however, following these steps will give you much more control over when reboots occur. I'll be covering how to run Apps as a Windows 'service' in another tutorial. <br>
	
### [Option 1] Windows 11 | Standalone Windows Machine (no Workgroup / Domain)

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; - Log into an administrator-level user account. <br>
&emsp; - Open the 'Edit Group Policy' manager by following these steps: <br>
&emsp;&emsp; > Windows Start Menu  <br>
&emsp;&emsp; > Type/Search 'Edit Group Policy'. <br>
&emsp;&emsp; > Select/Open the 'Edit Group Policy' manager. <br>
&emsp;&emsp; > Navigate to the following location within the 'Edit Gorup Policy' manager: <br>
&emsp;&emsp;&emsp; > 'Computer Configuration' <br>
&emsp;&emsp;&emsp; > 'Administrative Templates' <br>
&emsp;&emsp;&emsp; > 'Windows Components' <br>
&emsp;&emsp;&emsp; > 'Windows Update' <br>
&emsp;&emsp;&emsp; > 'Legacy Policies' <br>
&emsp;&emsp;&emsp; > Right Click and Edit 'No auto-restart with logged on users for scheduled automatic updates installations'. <br>
&emsp;&emsp;&emsp; > Select 'Enable' <br>
&emsp;&emsp;&emsp; > Select 'Ok' or 'Apply'. <br>
This process is finished. Close the 'Group Policy Management' console at this time. <br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123830%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123830%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123845%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123845%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123900%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123900%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123915%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123915%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123930%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123930%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123945%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123945%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124000%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124000%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124015%20v2.png" height="470"/>
</a><br>

</details>

### [Option 2] Windows Server 2019 | Domain Controller w/Active Directory

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> For advanced users with their Windows 11 Pro server/machine joined to a Domain Controller/Active Directory.
> Setting this policy against the root of the domain will apply this setting against ALL Windows machines joined to the Domain, which is what I prefer in my environment. If you need to isolate specific machines/VMs, please adjust these steps as you see fit.

&emsp; - Log into your Domain Controller using an administrator-level account. <br>
&emsp; - Open the 'Group Policy Management Console' (GPMC) using the following steps: <br>
&emsp;&emsp; > Windows Start Menu <br>
&emsp;&emsp; > Type/Search ‘Group Policy Management’. <br>
&emsp;&emsp; > Select/Open the 'Group Policy Management' console. <br>			
&emsp;&emsp; > Create a new ‘Group Policy Object’ under your domain. <br>
&emsp;&emsp;&emsp; > Group Policy Management <br>
&emsp;&emsp;&emsp; > Forest: example_domain.home <br>
&emsp;&emsp;&emsp; > Domains <br>
&emsp;&emsp;&emsp; > Right click your ‘example_domain.home’ and select ‘Create a GPO in this domain, and Link it here…’ <br>
&emsp;&emsp;&emsp;&emsp; > Give your GPO (Group Policy Object) a name, I recommend something like “2025.08.02 Disable Auto Reboot for Updates”. <br>
&emsp;&emsp;&emsp;&emsp; > Right click your newly create GPO and select ‘Edit…’. <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Within the newly opened window ‘Group Policy Management Editor’, navigate to the following location. <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Computer Configuration <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Policies <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Administrative Templates <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Windows Components <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Windows Update. <br>
&emsp;&emsp;&emsp;&emsp;&emsp; > Find and open the policy ‘No auto-restart with logged on users for scheduled automatic updates installations’. <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; > Set the policy to Enabled by selecting the radio button. <br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; > Select 'Apply', then 'Ok' and you are finished. <br>
This process is finished. Close the 'Group Policy Management' console at this time. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124030%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124030%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124045%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124045%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124100%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124100%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124115%20v2.png" height="470"/>
</a><br>

&emsp; > Expand this window to make it easier to navigate through the next couple of steps. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png" height="470"/>
</a><br>

</details>

***

</details>

## Run 'Plex Media Server' as a Windows Service via NSSM (Non-Sucking Service Manager).

<details>
  <summary>Expand for additional details.</summary>
<br>

In this section, we'll cover how to run PLEX (Media Server) as a Windows Service using NSSM. <br>

⚠️ I would recommend starting this process without PLEX running. <br>
<br>

> ℹ️ Running PLEX as a Windows Service significantly improves stability and availability through two methods: <br>
> &nbsp;- PLEX will start at boot, which reduces downtime caused by unexpected reboots. <br>
> &nbsp;- The Windows Service Control Manager (SCM) will monitor and automatically restart PLEX if any crashes or unexpected stops are detected. <br>
<br>

&emsp; > Download the NSSM (Non-Sucking Service Manager) tool by visiting the following URL: <br>

```bash
https://nssm.cc/
```

&emsp; > Navigate to the 'Download' page by selecting Download on the left menu. <br>
&emsp; > Then download the NSSM .zip file. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20152840%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20152840%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20152929%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20152929%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Extract the .zip file to a location of your choosing. <br>

&emsp; I put this in a folder on my Desktop for easy access `C:\Users\artemis\Desktop\Toolkit\nssm-2.24`. <br>
&emsp; Here you can see that the .zip file will be extracted to `C:\Users\artemis\Desktop\Toolkit\nssm-2.24`. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153020%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153020%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153116%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153116%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153143%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153143%20v2.png" height="470"/>
</a><br>
<br>

&emsp; Here you can see the extracted folder. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153226%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153226%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Navigate into that folder to locate the 64-bit version of the .exe NSSM tool. ***Most OS's are 64-bit these days. <br>

&emsp; In my example, the 64-bit version of the .exe can be found in `C:\Users\artemis\Desktop\Toolkit\nssm-2.24\nssm-2.24\win64\nssm.exe`. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153308%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153308%20v2.png" height="470"/>
</a><br>
<br>

&emsp; I like to copy/move the 64-bit nssm.exe back to my `C:\Users\artemis\Desktop\Toolkit\nssm-2.24` folder for easier access. <br>

> ℹ️ There are ways to move this .exe file to C:\Program Files, modify permissions to the file, and add it you your system path for administrative / standard users; however, for my use cases and workflows, I believe that overcomplicates things. I simply keep the NSSM .exe in a folder on my desktop, run a Command Prompt (CMD) as Administrator, and run the tool from that folder (more on this in next steps).

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153338%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153338%20v2.png" height="470"/>
</a><br>
<br>

&emsp; From here, we can open and run a Command Prompt (CMD) as Administrator: <br>
&emsp;&emsp; > Right-click the Command Prompt (CMD) icon. <br>
&emsp;&emsp; > Right-click the 'Command Prompt' text. <br>
&emsp;&emsp; > Select 'Run as administrator'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153408%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153408%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > 'cd' (change directory) to the location where you're storing your nssm.exe file (tool). <br>

&emsp; Example: `cd "C:\Users\artemis\Desktop\Toolkit\nssm-2.24`

&emsp; > Verify you're in the correct folder (directory) by listing the folder (directory) contents. You should see the `nssm.exe` file: <br>

```bash
dir
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153504%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153504%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Start the NSSM tool and install PLEX as a Windows Service: <br>

```bash
nssm install "plexmediaserver"
```

&emsp; After running the command above, the NSSM GUI (graphical user interface) will open. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153609%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153609%20v2.png" height="470"/>
</a><br>
<br>

&emsp; In the NSSM GUI, configure the following options: <br>

&emsp;&emsp; > 'Application' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'Path': `C:\Program Files\Plex\Plex Media Server\Plex Media Server.exe` <br>
&emsp;&emsp;&emsp;&emsp; 'Startup directory': `C:\Program Files\Plex\Plex Media Server\` <br>
&emsp;&emsp;&emsp;&emsp; 'Arguments': Leave this blank. <br>

&emsp;&emsp; > 'Details' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'Display name': `Plex Media Server` <br>
&emsp;&emsp;&emsp;&emsp; 'Description': `Runs Plex Media Server as a Windows service using NSSM.` <br>

&emsp;&emsp; > 'Log on' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'This account': Enter your username <br>
&emsp;&emsp;&emsp;&emsp; 'Password': Enter your password <br>
&emsp;&emsp;&emsp;&emsp; 'Confirm': Re-enter your password for confirmation <br>
*In my example, I'm using an Active Directory/Domain user account, which is why I append '@spartan23.home' after my username. If you're not using an Active Directory/Domain user account, please ignore that syntax. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153651%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153651%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153710%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153710%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153822%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20153822%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp; > (Optional but useful) I/O tab: <br>
&emsp;&emsp;&emsp; > Create a 'Logs' folder. <br>
&emsp;&emsp;&emsp; > Create an output (plex_stdout.log) and error (plex_stderr.log) log files within the 'Logs' folder. <br>
&emsp;&emsp;&emsp; > Set the output and error log locations within the NSSM GUI. <br>
*In my example, I put these log files in the same Desktop folder that I put the NSSM .exe tool. <br>

Output log file: `C:\Users\artemis\Desktop\Toolkit\Logs\plex_stdout.log` <br>
Error log file: `C:\Users\artemis\Desktop\Toolkit\Logs\plex_stderr.log` <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154028%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154028%20v2.png" height="470"/><br>
<br>

&emsp; > Now select 'Install service'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154028%20v2%20(2).png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154028%20v2%20(2).png" height="470"/>
</a><br>
<br>

&emsp; If successful, you should see the "Service 'plexmediaserver' installed successfully!". <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154055%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154055%20v2.png" height="470"/>
</a><br>
<br>

&emsp; You can also see this 'success' message in the Command Prompt (CMD) window: <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154113%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154113%20v2.png" height="470"/>
</a><br>
<br>

&emsp; If we check under Windows Services, we can see a Windows Service was created; however, it has not been started. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154227%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154227%20v2.png" height="470"/>
</a><br>
<br>

&emsp; We have a few options to start our newly created service. <br>
&emsp; &emsp; Option 1, start the service via NSSM. <br>

```bash
nssm start "plexmediaserver"
```

&emsp;&emsp; Option 2, start the service via Windows Service tool. <br>
&emsp;&emsp; Option 3, reboot the Windows 11 Pro machine. <br>
<br>

&emsp; Option 1, start the service via NSSM. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154326%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154326%20v2.png" height="470"/>
</a><br>

&emsp; Option 2, start the service via Windows Service tool. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154250%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154250%20v2.png" height="470"/>
</a><br>

&emsp; Option 3, reboot the Windows 11 Pro machine. <br>

&emsp; Regardless of which method we used to start the service, we can check it's status via the Windows Services app. <br>
&emsp; In this example, we can see our 'Plex Media Server' service (which was created by NSSM), has a status of 'Running'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154346%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154346%20v2.png" height="470"/>
</a><br>

&emsp; Now that we've confirm the service is running, we can check if our 'Plex Media Server' is up and running. *Compare this to our intial screenshow were our 'Plex Media Server' was reporting 'currently unavailable'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154413%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154413%20v2.png" height="470"/>
</a><br>
<br>

&emsp; This screenshot is a quick reminder that if we are running 'Plex Media Server' as a service, we should be using full UNC paths and not mapped network drives (if our media is stored externally on a NAS). <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154446%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-17%20154446%20v2.png" height="470"/>
</a><br>

</details>
