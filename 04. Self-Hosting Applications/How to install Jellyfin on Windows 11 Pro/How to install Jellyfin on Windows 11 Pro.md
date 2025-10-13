<a href="./Icons%20and%20Screenshots/20250805_095720.png">
  <img src="./Icons%20and%20Screenshots/20250805_095720.png" height="170"/>
</a>

<a href="./Icons%20and%20Screenshots/20250805_095853.png">
  <img src="./Icons%20and%20Screenshots/20250805_095853.png" height="170"/>
</a>

# How to install Jellyfin on Windows 11 Pro

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
<br>
-->

## Recommended Operating System / Version
&emsp; Windows 11 Pro <br>

> ℹ️ If you need help deploying Windows 11 Pro, please see my guide here, [How to install Windows 11 Pro](../../01.%20Operating%20Systems/How%20to%20install%20Windows%2011%20Pro/How%20to%20install%20Windows%2011%20Pro.md).

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

***

## Install and Configure, Jellyfin

> ⚠️ Jellyfin currently does not offer a native/built-in solution for 2FA (Two-Factor Authentication). For this reason, I would not recommend exposing your Jellyfin server over the WAN (outside of your local network/LAN). In the future, we'll have detailed steps on how to put Jellyfin behind a 2FA/SSO like Authelia or Authentik. <br>

### [1] Create a standard (non-administrator) user account on your Windows 11 Pro machine and login.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> If you are an advanced user with a Domain Controller running Active Directory in your environment, I would recommend skipping this step, which is creating a non-administrator local user. At this point, join this Windows 11 Pro machine to your Active Directory and use a non-administrator user within your Domain.

&emsp; Installing and running Jellyfin under a standard user account provides increased security and reduces overall risk to your environment in the event that your Windows machine or Jellyfin becomes compromised by malware. <br>

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

&emsp; > Log into the non-administrator user account you just created.

<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20123600%20v2.png" height="470"/>
</a><br>

</details>

### [2] Download the Jellyfin .exe installer.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; > Open https://jellyfin.org in your browser. <br>
&emsp; > Select '*Downloads*'. <br>
&emsp; > Select '*Server*', '*Windows*', then '*Downloads*'. <br>
&emsp; > Select '*AMD64*'. <br>
&emsp; > Select the '.exe' hyperlink to start the installer download. <br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 183437 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 183437 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 183538 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 183538 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184641 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184641 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184701 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184701 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184722 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184722 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184846 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184846 v2.png" height="470"/><br>

</details>

### [3] Start the Jellyfin installer.

<details>
  <summary>Expand for additional details.</summary>

<br>
&emsp; Start the Jellyfin installer by double-clicking or right-clicking the .exe, follow the installer steps. <br>
<br>

> ℹ️ **Note** <br>
> If you don't see file extensions like '.exe' on your file names and you would like to enable viewing them, follow these steps: <br>
>
> &gt; Windows Explorer <br>
> &gt; Select the three-dot hamburger menu <br>
> &gt; Select 'Options' <br>
> &gt; Select the 'View' tab <br>
> &gt; Scroll down and uncheck 'Hide extensions for known file types' <br>

&emsp; Once the Jellyfin installer has started, you can click through and accept all of the default options to complete the installation process. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184846 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184846 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184919 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184919 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184935 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184935 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184949 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 184949 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185006 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185006 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185027 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185027 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185049 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185049 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185105 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185105 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185121 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185121 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185143 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185143 v2.png" height="470"/><br>

</details>

### [4] Create a local Jellyfin user account and initialize your new Jellyfin server.

<details>
  <summary>Expand for additional details.</summary>
<br>
	
&emsp; Unfortunately, the Jellyfin installer does not add Jellyfin to the Windows application list, pin it to start, or pin it to your taskbar. <br>

&emsp; To start Jellyfin, we need to browse to the following location and start the .exe. Before we start Jellyfin, I recommend pinning the .exe to the Start Menu for quicker/easier access in the future. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185228 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185228 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185244 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185244 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185300 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185300 v2.png" height="470"/><br>

&emsp; Now we can start Jellyfin. Double-click or right-click and select open for the jellyfin.exe . <br>
&emsp; Starting the Jellyfin application will open a Command Prompt window associated with the application, leave it alone, don't close it. If needed, simply minimize it. <br>
&emsp; You may be prompted to allow Jellyfin through your Windows Firewall, select 'Allow'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185316 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185316 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185339 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185339 v2.png" height="470"/><br>

&emsp; Now that the Jellyfin application has been started, we can open a browser tab to the following URL: `http://venom:8096` or `http://192.168.50.230:8096`; replace with your DNS hostname or IP address depending on your environment. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185404 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185404 v2.png" height="470"/><br>

&emsp; > Select your default language, then select 'Next'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185420 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185420 v2.png" height="470"/><br>

&emsp; > Create a local Jellyfin user account for your Jellyfin server, then select 'Next'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185454 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185454 v2.png" height="470"/><br>

&emsp; > Here we have the option to start adding media/libraries; however, we'll skip this step by selecting 'Next' as we'll cover creating libraries in more detail in later steps. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185517 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185517 v2.png" height="470"/><br>

&emsp; > From here, we'll continue following the default prompts until we are greeted by the login screen. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185533 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185533 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185559 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185559 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185613 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185613 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185635 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185635 v2.png" height="470"/><br>

&emsp; After initially logging in, you'll notice a 'Nothing here' message displayed on the Home page. This is expected as we haven't added any media/libraries to this Jellyfin server. <br> 

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185635 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-30 185635 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234314 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234314 v2.png" height="470"/><br>

</details>

### [5] How to Add Libraries.
<details>
  <summary>Expand for additional details.</summary>

***

> ℹ️ **Note** <br>
> If you need some help or guidance on how to organize your media files, please see these two links from Jellyfin. <br>
> Naming and Organizing your Movie media files. <br>
> https://jellyfin.org/docs/general/server/media/movies <br>
>
> Naming and Organizing your TV Show files. <br>
> https://jellyfin.org/docs/general/server/media/shows <br>

&emsp; Depending on your setup, you may be using Mapped Network Drives or Full UNC Paths. Expand the sections below for additional guidance, if needed. <br>

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
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143710%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143710%20v2.png" height="470"/>
</a><br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143737%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-07-22%20143737%20v2.png" height="470"/>
</a><br>
<br>

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

In my example, I plan to run Jellyfin as a Windows service in the future. For that reason, I'll be using full UNC paths for my folders. <br>

&emsp; > Navigate to your Jellyfin Dashboard by either selecting the User Menu in the upper right-hand corner or the upper left-hand corner hamburger menu, then select 'Dashboard'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234427 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234427 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234541 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234541 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234603 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234603 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234500 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234500 v2.png" height="470"/><br>

&emsp; > Once you are on the Dashboard, you can select 'Libraries' > then 'Libraries' again. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234647 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-31 234647 v2.png" height="470"/><br>

&emsp; > Now we can select 'Add Media Library'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-07-31 235004 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-07-31 235004 v2.png" height="470"/><br>

&emsp; > In this example, I'll show you how to add a 'Movies' library. I'll be using a full UNC path; however, you may use a local folder, mapped network drive... etc. depending on your configuration. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-08-01 000303 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-08-01 000303 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-08-01 000323 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-08-01 000323 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101525 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101525 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101647 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101647 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101711 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101711 v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101743 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101743 v2.png" height="470"/><br>

&emsp; > Once you've added all your libraries, you will see them under the 'Libraries' page. Jellyfin will scan your library and start organizing associated meta-data. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101839 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101839 v2.png" height="470"/><br>

This screenshot shows the same activity of your libraries being scanned and organized but from the Dashboard under 'Running tasks'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101955 v2.png"><img src="./Icons%20and%20Screenshots/Screenshot 2025-08-01 101955 v2.png" height="470"/><br>

***

</details>

### [6] How to Remove Libraries.

<details>
  <summary>Expand for additional details.</summary>
<br>

> ℹ️ **Note** <br>
> Deleting a library will not delete your actual folders / files. It simply removes the library (access to that media) from your Jellyfin server. <br>

&emsp; > To delete a library, start by selecting the 3-line hamburger menu in the upper left-hand corner. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142020%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142020%20v2.png" height="470"/><br>

&emsp; > Select 'Dashboard'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142037%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142037%20v2.png" height="470"/><br>

&emsp; > Select 'Libraries', then 'Libraries' again. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142113%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142113%20v2.png" height="470"/><br>

&emsp; > Hover over and select the 3-dot hamburger menu for the library you want to remove (delete). <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142141%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142141%20v2.png" height="470"/><br>

&emsp; > Select 'Remove'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142140%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142140%20v2.png" height="470"/><br>

&emsp; > Select 'Delete'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142205%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-01%20142205%20v2.png" height="470"/><br>

***

</details>

### [7] Recommended Jellyfin Settings.

<details>
  <summary>Expand for additional details.</summary>
<br>

Most of the settings in Jellyfin will depend on your personal preference. I only recommend (per library), setting the following: <br>
&emsp; > Set preferred download language, I used `English`. <br>
&emsp; > Set Country/Region, I used `United States`. <br>
&emsp; > Enable 'Save artwork into media folders'. <br>
<br>

&emsp; > Select the three-line hamburger menu in the upper left-hand corner. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111158%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111158%20v2.png" height="470"/><br>

&emsp; > Select 'Dashboard'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111218%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111218%20v2.png" height="470"/><br>

&emsp; > Select the 'Libraries' drop down menu/section, then select 'Libraries' again. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111300%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111300%20v2.png" height="470"/><br>

&emsp; > For any library you want to update the settings for, select the 3-dot hamburger menu, then select 'Manage Library'.
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111327%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111327%20v2.png" height="470"/><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111342%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111342%20v2.png" height="470"/><br>

&emsp; > Set your preferred download language, I used `English`. <br>
&emsp; > Set Country/Region, I used `United States`. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111449%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111449%20v2.png" height="470"/><br>

&emsp; > Enable 'Save artwork into media folders'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111557%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-04%20111557%20v2.png" height="470"/><br>

</details>

<br>
<br>

***

## Upgrading Jellyfin

<details>
  <summary>Expand for additional details.</summary>
<br>

Jellyfin does not currently support in-app upgrades from the web interface. To update Jellyfin, you need to manually update it depending on your operating system or how it was installed. <br>

&emsp; > Go to https://jellyfin.org/downloads/ <br>
&emsp; > Download the latest Windows installer (.exe) <br>
&emsp; > Shutdown Jellyfin from the Dashboard webpage interface. <br>
&emsp; > Run the Windows installer (.exe) — it will automatically upgrade the existing installation while preserving settings and libraries. <br>

</details>


***

## Uninstall Jellyfin

<details>
  <summary>Expand for additional details.</summary>

***

⚠️ If you're running Jellyfin as a Windows service, stop and disable the Windows service associated with your Jellyfin server before proceeding. <br>

[Option 1] Stop and remove the Windows service using NSSM. <br>

<details>
  <summary>Expand for additional details.</summary>
<br>
	
&emsp; > Run the following NSSM commands in a command prompt terminal to stop and remove the Windows service associated with your Jellyfin server. <br>
```bash
nssm status "jellyfin"
```
```bash
nssm stop "jellyfin"
```
```bash
nssm remove "jellyfin"
```
<!-- screenshot of NSSM command prompt commands -->
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160714%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160714%20v2.png" height="470"/></a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160901%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160901%20v2.png" height="470"/></a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160916%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160916%20v2.png" height="470"/></a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160930%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160930%20v2.png" height="470"/></a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160947%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160947%20v2.png" height="470"/></a><br>

</details>

[Option 2] Stop and disable the Windows service using the Windows Services app.

<details>
  <summary>Expand for additional details.</summary>
<br>
	
&emsp; You can stop and disable (but not remove) a Windows service using the Windows Services app. <br>

&emsp; > Right-click the Windows Services app and select 'Run as administrator'. <br>
&emsp; > Find and right-click the Windows service that is realted to your Jellyfin server. Select 'Properties'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160511%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160511%20v2.png" height="470"/></a><br>

&emsp; > Under the 'General' tab, select 'Stop' to stop the Windows service. <br>
&emsp; > Under the same 'General' tab, select the dropdown menu next to 'Startup type:' and select 'Disabled'. <br>
&emsp; > Select 'Apply' to apply the settings we just configured. At this point, even if the Windows 11 Pro machine reboots, this service won't start autoamtically. If disabling the Windows service is sufficient for you're needs, proceed to the next step. If you'd prefer to remove/delete the Windows service, you'll need a tool like NSSM. NSSM can remove/delete the Windows service using the 'Service name:'. In this example, it would be 'jellyfin'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160601%20v2.png"><img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160601%20v2.png" height="470"/></a><br>
<br>

</details>

***

&emsp; > Shutdown Jellyfin from the Dashboard interface. <br>
&emsp;&emsp; > Select the 3-line hamburger menu in the upper left-hand corner. <br>
&emsp;&emsp; > Select 'Dashboard'. <br>
&emsp;&emsp; > Select 'Shutdown'. <br>
&emsp;&emsp; > Confirm the shutdown request by select 'Shutdown'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160311%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160311%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160325%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160325%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160339%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160339%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160354%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160354%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Uninstall Jellyfin via the Windows Settings app. <br>
&emsp;&emsp; > Navigate to 'Settings' > 'Apps' > 'Installed apps' . <br>
&emsp;&emsp; > Scroll down until you see 'Jellyfin' or search 'Jellyfin' in the upper search bar. <br>
&emsp;&emsp; > Select the three-dot hamburger menu on the right of the 'Jellyfin' app, and select 'Uninstall'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161015%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161039%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161039%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161110%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161110%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161125%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161125%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161152%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161152%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161214%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161214%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161232%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161232%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161254%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161254%20v2.png" height="470"/>
</a><br>

<br>

&emsp; > Delete related Jellyfin Directories. <br>

&emsp;&emsp; Even after uninstalling the Jellyfin app, there may be directories left behind that include configuration, cache, and metadata files. Depending on the size of your media collection, these folders could contain Gigabytes (GB) or more worth of data. <br>

&emsp; > Delete the following folders/directories: <br>
&emsp;&emsp; `C:\Users\<YourUsername>\AppData\Local\Jellyfin` <br>
&emsp;&emsp; `C:\Program Files\Jellyfin` <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161341%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161341%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161413%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161413%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Now empty your recycle bin. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161511%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20161511%20v2.png" height="470"/>
</a><br>

&emsp; > Reboot your Windows 11 Pro machine. <br>

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

> ℹ️ For advanced users with their Windows 11 Pro server/machine joined to a Domain Controller/Active Directory. Setting this policy against the root of the domain will apply this setting against ALL Windows machines joined to the Domain, which is what I prefer in my environment. If you need to isolate specific machines/VMs, please adjust these steps as you see fit.

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
<br>

&emsp; > Expand this window to make it easier to navigate through the next couple of steps. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124130%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124145%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124200%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124215%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124230%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124245%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124300%20v2.png" height="470"/>
</a>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-06-17%20124315%20v2.png" height="470"/>
</a>

</details>

***

</details>

## Run Jellyfin as a Windows Service via NSSM (Non-Sucking Service Manager).

<details>
  <summary>Expand for additional details.</summary>
<br>

In this section, we'll cover how to run Jellyfin (Media Server) as a Windows Service using NSSM. <br>

⚠️ I would recommend shutting down Jellyfin before starting this process. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20154526%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20154526%20v2.png" height="470"/>
</a><br>
<br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20154543%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20154543%20v2.png" height="470"/>
</a><br>
<br>

> ℹ️ Running Jellyfin as a Windows Service significantly improves stability and availability through two methods: <br>
> &nbsp;- Jellyfin will start at boot, which reduces downtime caused by unexpected reboots. <br>
> &nbsp;- The Windows Service Control Manager (SCM) will monitor and automatically restart Jellyfin if any crashes or unexpected stops are detected. <br>
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
<br>

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

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155154%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155154%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > 'cd' (change directory) to the location where you're storing your nssm.exe file (tool). <br>

&emsp; Example: `cd "C:\Users\artemis\Desktop\Toolkit\nssm-2.24`

&emsp; > Verify you're in the correct folder (directory) by listing the folder (directory) contents. You should see the `nssm.exe` file: <br>

```bash
dir
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155248%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155248%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Start the NSSM tool and install Jellyfin as a Windows Service: <br>

```bash
nssm install "jellyfin"
```

&emsp; After running the command above, the NSSM GUI (graphical user interface) will open. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155323%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155323%20v2.png" height="470"/>
</a><br>
<br>

&emsp; In the NSSM GUI, configure the following options: <br>

&emsp;&emsp; > 'Application' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'Path': `C:\Program Files\Jellyfin\Server\jellyfin.exe` <br>
&emsp;&emsp;&emsp;&emsp; 'Startup directory': `C:\Program Files\Jellyfin\Server` <br>
&emsp;&emsp;&emsp;&emsp; 'Arguments': Leave this blank. <br>

&emsp;&emsp; > 'Details' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'Display name': `Jellyfin` <br>
&emsp;&emsp;&emsp;&emsp; 'Description': `Runs Jellyfin as a Windows service using NSSM.` <br>

&emsp;&emsp; > 'Log on' tab: <br>
&emsp;&emsp;&emsp;&emsp; 'This account': Enter your username <br>
&emsp;&emsp;&emsp;&emsp; 'Password': Enter your password <br>
&emsp;&emsp;&emsp;&emsp; 'Confirm': Re-enter your password for confirmation <br>
*In my example, I'm using an Active Directory/Domain user account, which is why I append '@spartan23.home' after my username. If you're not using an Active Directory/Domain user account, please ignore that syntax. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155350%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155350%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155438%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155438%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155516%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155516%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155647%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155647%20v2.png" height="470"/>
</a><br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155724%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155724%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp; > (Optional but useful) I/O tab: <br>
&emsp;&emsp;&emsp; > Create a 'Logs' folder. <br>
&emsp;&emsp;&emsp; > Create an output (jellyfin_stdout.log) and error (jellyfin_stderr.log) log files within the 'Logs' folder. <br>
&emsp;&emsp;&emsp; > Set the output and error log locations within the NSSM GUI. <br>
*In my example, I put these log files in the same Desktop folder that I put the NSSM .exe tool. <br>

Output log file: `C:\Users\artemis\Desktop\Toolkit\Logs\jellyfin_stdout.log` <br>
Error log file: `C:\Users\artemis\Desktop\Toolkit\Logs\jellyfin_stderr.log` <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155851%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155851%20v2.png" height="470"/>
</a><br>
<br>

&emsp; > Now select 'Install service'. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155851%20v2%20(2).png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155851%20v2%20(2).png" height="470"/>
</a><br>
<br>

&emsp; If successful, you should see the "Service 'jellyfin' installed successfully!". <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155931%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155931%20v2.png" height="470"/>
</a><br>
<br>

&emsp; You can also see this 'success' message in the Command Prompt (CMD) window: <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155947%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20155947%20v2.png" height="470"/>
</a><br>
<br>

&emsp; We have a few options to start our newly created service. <br>
&emsp; &emsp; Option 1, start the service via NSSM. <br>

```bash
nssm start "jellyfin"
```

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160015%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160015%20v2.png" height="470"/>
</a><br>
<br>

&emsp;&emsp; Option 2, start the service via Windows Service tool. <br>
&emsp;&emsp; Option 3, reboot the Windows 11 Pro machine. <br>
<br>

&emsp; Now that we've confirm the service is running, we can check if our 'Jellyfin' is up and running. Open a browser tab to the following URL: `http://venom:8096` or `http://192.168.50.230:8096`; replace with your DNS hostname or IP address depending on your environment. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160115%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-08-05%20160115%20v2.png" height="470"/>
</a><br>
<br>

</details>
