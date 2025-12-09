<img src="./Icons%20and%20Screenshots/152025114633%20v2%20-%20(1)%20-%20Ubuntu.png"/> <br>

## How to install Ubuntu Server 24.04.3 LTS with software RAID (mdadm) and encryption.

<!--
YouTube <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
Rumble <br>
&emsp; [[ placeholder for embedded video and link ]] <br>
-->

### Table of Contents

&emsp; [1] Download a free copy of the Ubuntu Server 24.04.3 LTS ISO. <br>
&emsp; [2] Install Ubuntu Server 24.04.3 LTS. <br>

&emsp; [#] Appendix <br>
&emsp; [#] (Optional) How to install Ubuntu Desktop (GUI) for Ubuntu Server 24.04.3 LTS. <br>
&emsp; [#] (Optional) How to join Ubuntu Server 24.04.3 LTS to a Microsoft Active Directory Domain. <br>
<br>

***

### [1] Download a free copy of the Ubuntu Server 24.04.3 LTS ISO.

&emsp; Visit the following URL: <br>
```bash
https://ubuntu.com/download/server
```
&emsp; > Select '`Download`'. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20185715%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20185715%20v2.png" height="270"/>
</a><br>
<br>

***

### [2] Install Ubuntu Server 24.04.3 LTS.

&emsp; Installing Ubuntu Server 24.04.3 LTS with software RAID (mdadm) and encryption is typically done on bare-metal/physical servers. You will need to burn the Ubuntu Server ISO to a bootable USB drive. I recommend `Rufus`. <br>

# 

<details>
  <summary>Expand this section for additional details on <b><i>Rufus</i></b>.</summary>

***

> ℹ️ I recommend the 'Portable' version for simplicity. <br>

```bash
https://rufus.ie/en/#download
```
<br>

&emsp; Device: '`Select your USB`'. <br>
&emsp; Boot selection: '`ubuntu-24.04.3-live-server-amd64.iso`', use the 'SELECT' button to locate and select the ISO. <br>
&emsp; Under most circumstances, leave everything else at the default settings. <br>
&emsp; Select '`START`' to burn the Ubuntu Server ISO to your USB. <br>
<br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20185714%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20185714%20v2.png" height="270"/>
</a><br>

***

</details>

#

***
&emsp; > Boot from your Ubuntu Server 24.04.3 LTS ISO. <br>
&emsp; > When it's finished booting, you should see the following screen. <br>
&emsp; > Select your '`keyboard configuration`'. <br>
&emsp; > Then, select '`Done`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20185930%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20185930%20v2.png" height="270"/>
</a><br>

***
&emsp; > Select, '`Ubuntu Server`' for installation type. <br>
&emsp; > Then, select '`Done`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20185954%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20185954%20v2.png" height="270"/>
</a><br>

***
**(Optional) Set a static IP address.** <br>
&emsp; > Select your network adapter (then, hit '`Enter`'). <br>
&emsp; > Select '`Edit IPv4`' (then, hit '`Enter`'). <br>
&emsp; > Select '`Manual`' from the dropdown menu. <br>
&emsp; > Enter your relevant network information: <br>

> ℹ️ Be aware, subnet information is defined in CIDR notation (Classless Inter-Domain Routing) '`192.168.50.0/24`' instead of dotted decimal '`255.255.255.0`'. <br>

&emsp;&emsp; > '`Subnet`'. <br>
&emsp;&emsp; > '`Address`'. <br>
&emsp;&emsp; > '`Gateway`', typically your router. <br>
&emsp;&emsp; > '`Name servers`', any DNS servers within your environment or your router IP address. <br>
&emsp;&emsp; > '`Search domains`', (optional), used if you have a Domain Controller/Active Directory. <br>
&emsp; > Then, select '`Done`'.

> ℹ️ In my example, my network adapter is named '`ens192`'. Your network adapter may have a different name. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190031%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190031%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190101%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190101%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190133%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190133%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190309%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190309%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Verify your IP address has been set correctly. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190336%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190336%20v2.png" height="270"/>
</a><br>

***
&emsp; > If you are using a proxy to access the internet, enter the relevant information. <br>
&emsp; > Otherwise, select '`Done`' to skip this section. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190352%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190352%20v2.png" height="270"/>
</a><br>

***
&emsp; > Ubuntu will verify it can reach a mirror (copy) of its official software repository. Give it a moment to check. <br>
&emsp; > Once you see '`This mirror location passed tests.`', select '`Done`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190416%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190416%20v2.png" height="270"/>
</a><br>

***
&emsp; > Because we plan on installing with software RAID (mdadm) and encryption, we'll select '`Custom storage layout`'. <br>
&emsp; > Then, select '`Done`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190541%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190541%20v2.png" height="270"/>
</a><br>

***
&emsp; Here’s the layout we’ll build, from the bottom up. <br>

&emsp; Summary: <br>
&emsp;&emsp; Partition the physical drives. <br>
&emsp;&emsp; Create RAID devices. <br>
&emsp;&emsp; Create an LVM Volume Group (including encryption). <br>
&emsp;&emsp; Create LVM Logical Volumes. <br>
&emsp;&emsp; Create a Ubuntu partition for /boot on our RAID 1 device. <br>
&emsp;&emsp; Create Ubuntu partitions for SWAP and / (root) on our LVM Logical Volumes. <br>

> ℹ️ [X] = Partition Used for RAID, [_] = Partition NOT Used for RAID. <br>

```text
                            +---------------------------+---------------------------+
                            |           SWAP            |          ext4 /           |
                            +---------------------------+---------------------------+
                            | LVM Logical Volume (lv-0) | LVM Logical Volume (lv-1) |
        +-----------------+ +---------------------------+---------------------------+
        |    ext4 /boot   | |    LVM Volume Group (vg0) with Encryption (LUKS)      |
        +-----------------+ +-------------------------------------------------------+
        |   RAID 1 (md0)  | |                    RAID 10 (md1)                      |
        +-----------------+ +-------------------------------------------------------+
Drive 1 | [X] Partition 1 | |                   [X] Partition 2                     |
        +-----------------+ +-------------------------------------------------------+
Drive 2 | [X] Partition 1 | |                   [X] Partition 2                     |
        +-----------------+ +-------------------------------------------------------+
Drive 3 | [_] Partition 1 | |                   [X] Partition 2                     |
        +-----------------+ +-------------------------------------------------------+
Drive 4 | [_] Partition 1 | |                   [X] Partition 2                     |
        +-----------------+ +-------------------------------------------------------+
```
<br>

&emsp; > Start by preparing the drives for the RAID 1 device. <br>

&emsp; > Select the '`free space`' on your first drive by hitting '`Enter`'. <br>
&emsp; > Select '`Add GPT Partition`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190648%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190648%20v2.png" height="270"/>
</a><br>

&emsp; > Enter the following variables: <br>

> ℹ️ These days bootloader / kernel / initramfs are getting larger and growing. It is strongly recommended to plan for and size a /boot partition multiple GiB (gibibytes) in size. <br>

&emsp;&emsp; > Size: Multiple GiB, size/plan accordingly. <br> 
&emsp;&emsp; > Format: '`Leave unformatted`'. <br>
&emsp; > Select '`Create`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190729%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190729%20v2.png" height="270"/>
</a><br>

&emsp; > Here you can see the partition we just created. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190808%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20190808%20v2.png" height="270"/>
</a><br>

&emsp; > Repeat the steps above until you have equally sized partitions across all of your drives. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191131%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191131%20v2.png" height="270"/>
</a><br>

&emsp; > Continue by preparing the drives for the RAID 10 device. <br>

&emsp; > Select the remaining '`free space`' on your first drive by hitting '`Enter`'. <br>
&emsp; > Select '`Add GPT Partition`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191236%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191236%20v2.png" height="270"/>
</a><br>

&emsp; > Enter the following variables: <br>
&emsp;&emsp; > Size: Leave blank, which will use/consume the max available capacity left on the drive. <br> 
&emsp;&emsp; > Format: '`Leave unformatted`'. <br>
&emsp; > Select '`Create`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191254%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191254%20v2.png" height="270"/>
</a><br>

&emsp; > Here you can see the partition we just created. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191326%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191326%20v2.png" height="270"/>
</a><br>

&emsp; > Repeat the steps above until you have equally sized partitions across all of your drives. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191420%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191420%20v2.png" height="270"/>
</a><br>

&emsp; > Now we're ready to create our RAID 1 device. <br>
&emsp; > Select '`Create software RAID (md)`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191439%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191439%20v2.png" height="270"/>
</a><br>

&emsp; > Enter the following variables: <br>
&emsp;&emsp; > Name: '`md0`'. <br>
&emsp;&emsp; > RAID Level: '`1 (mirrored)`', for RAID 1. <br>
&emsp;&emsp; > Select the smaller partition from drives 1 and 2. <br>
&emsp; > Select '`Create`'. <br>

> ℹ️ Ubuntu /boot only supports RAID 1 devices, which is why we leave two of the four partitions unused. <br>

<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191535%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191535%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191605%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191605%20v2.png" height="270"/>
</a><br>
<br>

&emsp; > Here you can see the RAID 1 device '`md0`' we just created. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191629%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191629%20v2.png" height="270"/>
</a><br>

&emsp; > Now we're ready to create our RAID 10 device. <br>
&emsp; > Select '`Create software RAID (md)`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191629%20(2)%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191629%20(2)%20v2.png" height="270"/>
</a><br>

&emsp; > Enter the following variables: <br>
&emsp;&emsp; > Name: '`md1`'. <br>
&emsp;&emsp; > RAID Level: '`10`', for RAID 10. <br>
&emsp;&emsp; > Select the larger partition from drives 1, 2, 3, and 4. <br>
&emsp; > Select '`Create`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191702%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191702%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191711%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191711%20v2.png" height="270"/>
</a><br>

&emsp; > Here you can see the RAID 10 device '`md1`' we just created. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191732%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191732%20v2.png" height="270"/>
</a><br>

&emsp; > Now we're ready to create the Ubuntu /boot partition on our RAID 1 device. <br>

&emsp; > Select the '`free space`' under RAID 1 device '`md0`'. <br>
&emsp; > Select '`Add GPT Partition`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191850%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191850%20v2.png" height="270"/>
</a><br>

&emsp; > Enter the following variables: <br>
&emsp;&emsp; > Size: Leave blank, which will use/consume the max available capacity on the RAID device. <br> 
&emsp;&emsp; > Format: '`ext4`'. <br>
&emsp;&emsp; > Mount: '`/boot`'. <br>
&emsp; > Select '`Create`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191923%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191923%20v2.png" height="270"/>
</a><br>

&emsp; > Here you can see the Ubuntu /boot partition we just created. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191944%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20191944%20v2.png" height="270"/>
</a><br>

&emsp; > Now we're ready to create our LVM Logical Volume Group. <br>

&emsp; > Select '`Create volume group (LVM)`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192003%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192003%20v2.png" height="270"/>
</a><br>

&emsp; > Enter the following variables: <br>
&emsp;&emsp; > Name: '`vg0`'. <br>
&emsp;&emsp; > Devices: Select '`md1`'. <br>
&emsp;&emsp; > Select '`Create encrypted volume`' and enter a passphrase (password). <br>

> ℹ️ This passphrase (password) will be used to unlock the encrypted LVM Volume Group and allow Ubuntu to continue booting. <br>

&emsp; > Select '`Create`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192106%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192106%20v2.png" height="270"/>
</a><br>

&emsp; > Here you can see the LVM Logical Volume Group '`vg0`' we just created. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192130%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192130%20v2.png" height="270"/>
</a><br>

&emsp; > Now we're ready to create our LVM Logical Volumes within the LVM Logical Volume Group. <br>
&emsp; > Start by creating a Logical Volume to be used for our Ubuntu SWAP partition. <br>

&emsp; > Select the '`free space`' under LVM Logical Volume Group '`vg0`'. <br>
&emsp; > Select '`Create Logical Volume`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192150%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192150%20v2.png" height="270"/>
</a><br>

&emsp; > This Logical Volume will be used for Ubuntu SWAP. <br>
&emsp; > Enter the following variables: <br>
&emsp;&emsp; > Name: '`lv-0`'. <br>
&emsp;&emsp; > Size: I recommend sizing SWAP to be the same size as your available system memory (DRAM). <br>
&emsp;&emsp; > Format: '`swap`'. <br>
&emsp; > Select '`Create`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192220%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192220%20v2.png" height="270"/>
</a><br>

&emsp; > Here you can see the Ubuntu SWAP partition we just created. <br>
&emsp; > Also notice, our LVM Logical Volume Group now has less available 'free space'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192251%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192251%20v2.png" height="270"/>
</a><br>

&emsp; > Now we will create another Logical Volume for our Ubuntu / (root) partition. <br>

&emsp; > Select the remaining '`free space`' under LVM Logical Volume Group '`vg0`'. <br>
&emsp; > Select '`Create Logical Volume`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192311%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192311%20v2.png" height="270"/>
</a><br>

&emsp; > This Logical Volume will be used for Ubuntu / (root). <br>
&emsp; > Enter the following variables: <br>
&emsp;&emsp; > Name: '`lv-1`'. <br>
&emsp;&emsp; > Size: Leave blank, which will use/consume the max available capacity on the Logical Volume. <br>
&emsp;&emsp; > Format: '`ext4`'. <br>
&emsp;&emsp; > Mount: '`/`'
&emsp; > Select '`Create`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192313%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192313%20v2.png" height="270"/>
</a><br>

&emsp; > Here you can see the Ubuntu / (root) partition we just created. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192334%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192334%20v2.png" height="270"/>
</a><br>

&emsp; > Review your 'Custom storage layout' to be sure everything looks good. <br>
&emsp; > When ready, select '`Done`'. <br>
&emsp; > Confirm you are ready to proceed by selecting '`Continue`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192430%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192430%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192445%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192445%20v2.png" height="270"/>
</a><br>

&emsp; > Enter your profile configuration information. <br>
&emsp; > Then, select '`Done`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192520%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192520%20v2.png" height="270"/>
</a><br>

&emsp; > (Optional) Choose whether or not to enable Ubuntu Pro. <br>
&emsp; > I select '`Skip for now`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192533%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192533%20v2.png" height="270"/>
</a><br>

&emsp; > Select '`Install OpenSSH server`'. <br>
&emsp; > Then, select '`Done`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192554%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192554%20v2.png" height="270"/>
</a><br>

&emsp; > (Optional) If there are any software packages that you'd like to pre-install from Ubuntu's APT repository, select them here. <br>
&emsp; > Then, select '`Done`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192610%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192610%20v2.png" height="270"/>
</a><br>

&emsp; > Allow the install to run and wait for it to complete. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192635%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192635%20v2.png" height="270"/>
</a><br>

&emsp; > When you see '`Installation complete!`', you can select '`Reboot Now`'. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192732%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192732%20v2.png" height="270"/>
</a><br>

&emsp; > Remove the bootable USB drive we used for installation, then hit '`Enter`' to continue rebooting. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192756%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192756%20v2.png" height="270"/>
</a><br>

&emsp; > Once the Ubuntu server starts to boot, you'll notice it pauses/halts, until you enter the appropriate passphrase (password) to unlock the encrypted LVM Logical Volume we created earlier. <br>
&emsp; > Once you've unlocked the LVM Logical Volume, boot will continue. <br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192839%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192839%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192926%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20192926%20v2.png" height="270"/>
</a><br>
<a href="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20193035%20v2.png">
  <img src="./Icons%20and%20Screenshots/Screenshot%202025-10-20%20193035%20v2.png" height="270"/>
</a><br>

***

## Appendix

### (Optional) How to install Ubuntu Desktop (GUI) for Ubuntu Server 24.04.3 LTS.

<details>
  <summary>Expand for additional details.</summary>
<br>

&emsp; Run the following commands to install Ubuntu Desktop (GUI) for Ubuntu Server 24.04.3 LTS. <br>
&emsp; This will result in Ubuntu Server booting into the Desktop (GUI). <br>
```bash
sudo apt update && sudo apt upgrade -y
```
```bash
sudo apt install ubuntu-desktop -y
```
```bash
sudo apt install ubuntu-restricted-extras -y
```

</details>

### (Optional) How to join Ubuntu Server 24.04.3 LTS to a Microsoft Active Directory Domain.

<details>
  <summary>Expand for additional details.</summary>
<br>

These steps assume your Active Directory (Domain Controller) is already properly setup and running. I'm using Windows Server 2019 and these steps worked every time for me.

[1] Update and upgrade software packages. <br>
```bash
sudo apt update && sudo apt upgrade -y
```
```bash
sudo shutdown -r now
```

> ℹ️ Always reboot after kernel updates on Server to ensure consistency before joining the domain. <br>

[2] Install the software dependencies needed to join your Ubuntu Server to an Active Directory (AD) domain. <br>
```bash
sudo apt install -y realmd sssd sssd-tools adcli samba-common-bin oddjob oddjob-mkhomedir packagekit libnss-sss libpam-sss
```

> ℹ️ libnss-sss and libpam-sss ensure AD users can be resolved and authenticated via SSSD (these may come preinstalled on Desktop, but not always on Server). <br>

[3] Verify DNS resolution. <br>
&emsp; Before discovery, confirm your DNS is resolving the domain correctly: <br>
```bash
nslookup yourdomain.com
nslookup dc1.yourdomain.com
```
&emsp; Example: <br>
```bash
nslookup spartan23.home
nslookup owl.spartan23.home
```

[4] Discover your domain. This command uses DNS (and SRV records). <br>
```bash
realm discover yourdomain.com
```
&emsp; Example: <br>
```bash
realm discover spartan23.home
```

[5] Join your domain. This does require an administrator-level account. <br>
```bash
sudo realm join yourdomain.com -U "Administrator"
```
&emsp; Example: <br>
```bash
sudo realm join spartan23.home -U "Administrator"
```

[6] Verify you have successfully joined the domain <br>
```bash
realm list
```
&emsp; Expected Output: <br>
```bash
spartan23.home
  type: kerberos
  realm-name: SPARTAN23.HOME
  domain-name: spartan23.home
  configured: kerberos-member
  server-software: active-directory
  client-software: sssd
  required-package: sssd-tools
  required-package: sssd
  required-package: libnss-sss
  required-package: libpam-sss
  required-package: adcli
  required-package: samba-common-bin
  login-formats: %U@spartan23.home
  login-policy: allow-realm-logins
```

[7] If you've successfully joined the domain, you should be able to run the following command to pull user and group permissions for that Active Directory (AD) user. <br>
```bash
id yourdomain\\username
```
&emsp; Example: <br>
```bash
id spartan23.home\\thomas
```

[8] Modify the 'PAM Configuration' to allow Ubuntu to create a home directory (/home/username) and persist your domain user's settings. To do this, we edit the 'PAM Configuration' files. <br>
<br>
&emsp; Create a backup of the '*common-session*' and '*common-session-noninteractive*' PAM configuration files: <br>
```bash
sudo cp /etc/pam.d/common-session /etc/pam.d/common-session_$(date +%Y.%m.%d_%H-%M-%S)
```
```bash
sudo cp /etc/pam.d/common-session-noninteractive /etc/pam.d/common-session-noninteractive_$(date +%Y.%m.%d_%H-%M-%S)
```
&emsp; Add the following line at the end of both files: <br>
```bash
session required pam_mkhomedir.so skel=/etc/skel/ umask=0022
```
Edit the two PAM configuration files: <br>

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

```bash
sudo nano /etc/pam.d/common-session
```
```bash
sudo nano /etc/pam.d/common-session-noninteractive
```

[9] Enable 'sudo' rights for your domain user. <br>
&emsp; Create a new file where we'll specify our sudo permissions for this domain user. <br>
```bash
sudo touch /etc/sudoers.d/username
```
&emsp; Example: <br>
```bash
sudo touch /etc/sudoers.d/thomas
```
&emsp; Use nano to open and edit our newly created file. <br>

> ℹ️ To save changes in nano, select `Ctrl+x`, then `y`, then `Enter`. <br>

```bash
sudo nano /etc/sudoers.d/username
```
&emsp; Example: <br>
```bash
sudo nano /etc/sudoers.d/thomas
```
&emsp; Add this line of text to the file we just created. <br>
```bash
user@yourdomain.com ALL=(ALL:ALL) ALL
```
&emsp; Example:
```bash
thomas@spartan23.home ALL=(ALL:ALL) ALL
```

[10] (Recommended) Restart Services <br>
```bash
sudo systemctl restart sssd
sudo systemctl restart realmd
```

[11] Now you can log in using a domain user! These are the two formats you can use: <br>

```bash
DOMAIN\username
```
```bash
username@domain.com
```
&emsp; Example: <br>
```bash
ssh "thomas@spartan23.home"@hera
```

</details>
