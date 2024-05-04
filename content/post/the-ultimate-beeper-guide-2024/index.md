---
title: "The Ultimate Beeper-iMessage Guide: 2024"
date: 2024-03-24T01:00:00-04:00
lastmod: 2024-04-28T01:00:00-04:00
draft: false

description: "The One Guide to Rule Them All (for at least 2024)"
image: "featured-image.png"

tags: ["Beeper", "Beeper Mini", "iMessage", "BlueBubbles", "Virtual Machines"]
categories: ["guides"]

toc: true
---

Finally at long last, the one guide to iMessage on Android to rule them all, using Beeper Mini, the new Beeper beta app for Android, BlueBubbles, virtual machines, and much more. This guide will take you from the beginning and give you a fully working setup with iMessage with all your other chats in Beeper. This was made in collaboration with the amazing people on Matrix chat rooms (`#beepserv:beeper.com` and `#imessage:maunium.net`) that have not only contributed to these open source projects but also made guides that have been synthesized, updated, and simplified here for you.

## Beeper Mini (Phone Number Registration)
You may be fine only wanting to use Beeper Mini for iMessage chats and using your other apps for their respective DMs, so we’ll start with that first. There are now two ways of using Beeper Mini: beepserv-rewrite (Jailbreak required) or the new app that can be sideloaded (No Jailbreak!). Beeper no longer provides support for Beeper Mini/Beepserv in general. The new app that can be sideloaded on iPhones is made by [jjtech](https://github.com/JJTech0130) and no support will be given to users. Every since Apple's crackdown on Beeper, don't expect any real support as eveything is community maintained.

Before you get started either option
1. It is recommended to wipe your phone before you begin either option
2. **DO NOT SIGN INTO ANY APPLEID IN SETUP** -- signing in can cause instability in phone number registration. When setting up your iPhone after wiping, select "I don't have an AppleID" or any equivalent wording to make sure the iPhone has no AppleID after setup.
3. Disable your lock screen, there should be no PIN or fingerprint required to unlock the phone

### [Beepserv-rewrite](https://github.com/thatmarcel/beepserv-rewrite) by [thatmarcel](https://github.com/thatmarcel)
Let’s get the hard part out of the way

It is recommended that you follow a guide that matches your iPhone or iOS version at [https://ios.cfw.guide/get-started/](https://ios.cfw.guide/get-started/), they maintain updated guides for jailbreaking as projects come and go. **Do not use a video guide for jailbreaking, they are probably outdated!** Make sure you know the name of the Apple Silicon chip your iPhone has, as the guides will refer to it often (search your phone model on Wikipedia).

**Do your jailbreak**

You’re done? Good, let’s get Beepserv running.

1. Go to Settings → Messages → and make sure “iMessage” is toggled off
2. Go to [https://github.com/thatmarcel/beepserv-rewrite/releases](https://github.com/thatmarcel/beepserv-rewrite/releases) and download the latest release deb file on your iPhone. Choose the respective file if you are rootless or rootful (this may have come up during your jailbreak guide, check your guide and come back, it is always recommended to do a rootless jailbreak and is probably what you did)
3. Open the file with Safari and select Sileo in the share menu to install it, follow through the prompts
4. Open beepserv on your homescreen, that’s your Beeper Mini code! Save it somewhere to copy and paste later

It is recommended at this point to prevent your phone from sleeping/the screen from turning off and leave it charging in some corner permanently. This will hopefully prevent any crashes that could occur from the instability caused by the jailbreak and prevent the need to re-jailbreak because of an unexpected reboot. If this does happen, your messages will break.

### Create an App Password for Your “Main AppleID”
If you had tried to login with your AppleID in the past, you would have noticed that often Beeper Mini would require you to sign into your account again after only 30 minutes. This is not ideal and seems to be caused by 2FA on AppleIDs and Beeper Mini not handling it well. Luckily, Apple provides App Passwords for logins, so that 2FA isn’t needed and it would go into the regular password field for sign in. Beeper Mini offered this but If you had attempted to create an App Password inside of Beeper Mini when confirming 2FA, the issue would still occur. The solution is to create an App Password manually in iCloud.

1. Go to [https://appleid.apple.com/](https://appleid.apple.com/) and sign in
2. Go to Sign-In and Security → App Specific Password → Click the “+” → Give it a name
3. Put it in your password manager or note app in case your sign-in breaks, this rarely happens though using this method


### Using Beeper Mini
1. Download the APK at [https://mini.beeper.com/Beeper_Mini_v1.2.58.apk](https://mini.beeper.com/Beeper_Mini_v1.2.58.apk), latest version at the time of this post is 1.2.58 
    1. This version is important because it adds the ability to force re-register your phone number. If your phone number deregisters from iMessage, you won’t be able to receive iMessage texts and they will instead go to SMS. Using an App Password this will rarely break and will break less often over time as you re-register.
    2. Later in this guide we'll set up BlueBubbles which will notify you when your phone number deregisters
2. Enter your Beepserv code. If it fails to register your phone number, try again (Beepserv can fail to hook the right functions, doing it again forces it to use the fallback)
3. If you are asked to sign into Apple, use your Main AppleID and the App Password you created

Congrats! You have the ability to send iMessage texts on Android. If you want to continue with BlueBubbles and integration into the greater Beeper app, continue on.

## We Need macOS…
BlueBubbles is a client-server combo that also provides iMessage texts for any platform. They hook into the Messages app on macOS to provide this functionality. In doing so, their mobile app provides notifications for when an iMessage “alias” is deregistered, for example your phone number from Beeper Mini. With [mautrix/imessage](https://github.com/mautrix/imessage), we can have our iMessage chats in Beeper Cloud and even the new Beeper beta app for Android.

There are two options to do this:

1. Buy an old Mac Mini/Macbook/Macbook Air or any Mac device, ideally it should be able to run at least macOS Ventura
2. Run a virtual machine

This guide will continue with option 2, being free if you have an old computer lying around.

Note: Ventura is not required to use BlueBubbles but is required if you want to be able to receive and send edits as well as unsend messages.

## BlueBubbles

### Installing Proxmox and Running macOS Ventura
“Why use Proxmox?” We don’t actually need to, anything x86 with Linux should be fine but this makes VM creation more streamlined and if you want the PC to do anything else, and have the cores and memory to do it, you can just spin up another VM. [i12bretro](https://www.youtube.com/@i12bretro) has easy to follow guides as checklists that I recommend you follow. I’m copying his Ventura one here for your convenience and since Sonoma requires the AVX2 instruction set in order to boot. If you would like to use a different macOS version, you can find it on his website [here](https://i12bretro.github.io/tutorials/).

First install Proxmox Virtual Environment [here](https://www.proxmox.com/en/downloads) (you don’t need to pay, you can use the free version and ignore the prompts). Make a bootable USB and install the OS, you can then manage it headlessly with the web portal at `https://<IP-of-Proxmox-server>:8006` Then follow [these](https://i12bretro.github.io/tutorials/0775.html) steps:

1.  Download a MacOS Ventura .iso [Download](https://archive.org/search.php?query=MacOS%20collection&and[]=mediatype%3A%22software%22) OR create your own [https://youtu.be/JFMvUpdCMwo](https://youtu.be/JFMvUpdCMwo)
2.  Download KVM OpenCore bootloader [Download](https://github.com/thenickdude/KVM-Opencore/releases)
3.  Extract the downloaded KVM OpenCore bootloader .gz file
4.  Upload the Ventura and KVM OpenCore .iso files to the Proxmox ISO library
5.  Log into the ProxMox web UI
6.  Right click the ProxMox node name > Create VM
7.  Type MacOSVentura in the name field, set the VM ID to 1300 (unless 1300 is in use) > Next
8.  On the OS tab, set the Type field to Other and select the KVM OpenCore .iso in the ISO Image field > Next
9.  On the System tab, set the Graphic card field to VMware compatible, BIOS field to OVMF (UEFI), Uncheck the Pre-Enroll Keys checkbox, Check the Add EFI Disk checkbox, Machine field to q35 and the SCSI Controller to VirtIO SCSI > Next
10.  On the Hard Disk tab, set the Bus/Device field to VirtIO Block, Disk size field to 64, Cache field to Write back (unsafe) > Next
11.  On the CPU tab, set Cores field to 4, Type field to host > Next
12.  On the Memory tab, set the Memory to 4096 > Next
13.  On the Network tab, set the Model field to VMware vmxnet3 > Next
14.  Verify the summary and click Finish
15.  Click the MacOSVentura VM > Select Hardware from the left sub-navigation menu
16.  Click Add > CD/DVD Drive
17.  Select the MacOS Ventura .iso downloaded earlier > Click Create
18.  Select the MacOSVentura VM > Options > Boot Order
19.  Set the KVM OpenCore disk as the first boot option > Click OK
20.  Right click the ProxMox node name > Console
21.  Run the following commands in the terminal

    \# edit the VM conf file, change 1300 to the VM ID for the MacOSVentura VM  

     nano /etc/pve/qemu-server/1300.conf

22.  If running on an Intel CPU, add the following line to the bottom of the .conf file:

    args: -device isa-applesmc,osk="ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc" -smbios type=2 -device usb-kbd,bus=ehci.0,port=2 -global nec-usb-xhci.msi=off -global ICH9-LPC.acpi-pci-hotplug-with-bridge-support=off -cpu host,vendor=GenuineIntel,+invtsc,+hypervisor,kvm=on,vmware-cpuid-freq=on

23.  If running on an AMD CPU, add the following line to the bottom of the .conf file:

    args: -device isa-applesmc,osk="ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc" -smbios type=2 -device usb-kbd,bus=ehci.0,port=2 -global nec-usb-xhci.msi=off -global ICH9-LPC.acpi-pci-hotplug-with-bridge-support=off -cpu Haswell-noTSX,vendor=GenuineIntel,+invtsc,+hypervisor,kvm=on,vmware-cpuid-freq=on

24.  Press CTRL+W and search for ,media=cdrom
25.  Delete the ,media=cdrom from the two attached .iso files (KVM OpenCore and Ventura) and add cache=unsafe
26.  Press CTRL+O, Enter, CTRL+X to write the changes to the conf file
27.  Back in the Proxmox web UI, right click the MacOSVentura VM in the left navigation pane > Start
28.  Click console in the left sub-navigation menu
29.  At the OpenCore menu, select UEFI Shell > Press Enter
30.  Type the following in the UEFI shell:

    \# change to the Ventura.iso, the disk number may be different for you  

     fs0:\# launch the MacOS installer  

     System\\Library\\CoreServices\\boot.efi

31.  After a long initialization sequence the MAC OS Setup should start
32.  Select Disk Utility
33.  Select the VIRTIO Block Media > Click Erase
34.  Name the drive MacOS > Set the Format to APFS > Click Erase
35.  Click Done > Close Disk Utility
36.  Click Install macOS Ventura
37.  Click Continue > Click Agree > Click Agree again
38.  Select the MacOS disk > Click Install
39.  Wait while Mac OS installs files, the VM will reboot several times
40.  Select your Country > Click Continue
41.  Confirm your languages and keyboard layout > Click Continue
42.  Click Not Now on the Accessibility screen
43.  Click Continue on the Data & Privacy screen
44.  Select Not Now on the Migration Assistant screen
45.  Select Set Up Later and then Skip on the Apple ID screen
46.  Click Agree > Agree again
47.  Enter a name, user name, password > Click Continue
48.  Click Continue > Select Use or Don't Use for Location Services
49.  Pick a timezone > Click Continue
50.  Uncheck Share Mac Analytics with Apple > Click Continue
51.  Click Set Up Later on the Screen Time screen
52.  Uncheck the Enable Ask Siri box > Click Continue
53.  Pick a theme > Click Continue
54.  Welcome to MacOS 13 Ventura

You good? Great, let’s lie to Apple

### Activating iMessage on macOS
1. Follow [this guide](https://dortania.github.io/OpenCore-Post-Install/universal/iservices.html#using-gensmbios) 
    1. Make sure the ROM in your config.plist is the MAC address of the NIC you have set in Proxmox, you can go to Settings in macOS to see your MAC address of the NIC, this should still be all lowercase with no colons in your config.plist
2. Sign in with your Main AppleID
3. Sign into Messages with your Main AppleID


### Setting up BlueBubbles
You can also follow their instructions [here](https://bluebubbles.app/install/) and [here as well](https://docs.bluebubbles.app/private-api/installation) 

1. Download the latest release at [https://github.com/BlueBubblesApp/bluebubbles-server/releases](https://github.com/BlueBubblesApp/bluebubbles-server/releases) 
2. Open it and follow it’s instructions
3. Make sure you turn on the Private API, “Keep macOS Awake”, and “Startup with macOS”
4. Download the [BlueBubbles app for Android](https://play.google.com/store/apps/details?id=com.bluebubbles.messaging&hl=en_US&gl=US) 
5. Go through the setup and connection to your server
6. It is recommended to turn off your notification on Android except for errors, this way you are only notified of deregisters
7. Make sure the Private API is enabled in the Android app, if you go to the three dots → Settings → Your name under Profile → you should see all the aliases for your iMessage account, including your phone number from before (if not, force re-register!)
8. In the mobile app's settings, scroll to the bottom and sync your contacts to the BlueBubbles Server


## Self-Hosting the iMessage Bridge for Beeper Cloud
1. Download the latest Beeper Bridge Manager [here](https://github.com/beeper/bridge-manager/actions), put it into a folder somewhere, run `chmod +x bbctl-macos-amd64` in a terminal
2. Edit your paths with `sudo nano /etc/paths` and add the path to the folder with bbctl
3. Run `bbctl-macos-amd64 login <your-email-with-Beeper-Cloud>`
4. In your home directory, `git clone https://github.com/mautrix/imessage.git`
5. In the `imessage` directory, `bbctl-macos-amd64 run --param 'bluebubbles_url=http://localhost:1234' --param 'bluebubbles_password=<your-BlueBubbles-password>' --param 'imessage_platform=bluebubbles' sh-imessage`


And now finally… we're done.