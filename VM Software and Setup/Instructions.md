In order to set up a VM for use with my school, you need the following software:

 - [Windows 10 64-bit](https://www.microsoft.com/en-in/software-download/windows10)
 - [Oracle VirtualBox](https://www.virtualbox.org/)
 - DyKnow Vision and Monitor 5.8 (Mirror located here, otherwise available on a mirror from [the web archive)](http://web.archive.org/web/20151005050322/https://support.dyknow.com/hc/en-us/articles/201672607-5-8-Client-Installation-Guide) (select the 64-bit version for "Monitor/Vision Bundle Customers")
 - (Requirement of DyKnow 5.8) [Microsoft Visual C++ Redistributable for Visual Studio 2012 x86 and x64](https://www.microsoft.com/en-us/download/details.aspx?id=30679)
 - [Google Chrome offline x64](https://www.google.com/chrome/eula.html?system=true&standalone=1&platform=win64)

# Installing for N00bs:

1.) Install VirtualBox and create a new Virtual Machine in VirtualBox and give it a reasonable amount of space. From personal experience, around 60 GB is a good size to go with. If needed, it can always be [expanded](https://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/) later. Under the Virtual Machine settings assign it at least 2 GB of memory and 2 CPU cores, and enable PAE/NX, VT-x/AMD-V, and Nested Paging. Additionally, enable 3D and 2D video acceleration and give it 256 MB of Video Memory.

2.) Install Windows 10 and the VirtualBox Guest Additions. Make sure that everything works properly, including resizing the display, fullscreen modes, and shared folders.

3.) Install Microsoft Visual C++ Redistributable for Visual Studio 2012 x86 and x64. Yes, you need both versions, as they are required for DyKnow.

4.) Setting up the NAT network to trick the VM into believing that it is on school property, allowing the use of DyKnow once installed. To do this, open a command prompt and run `cd "C:\Program Files\Oracle\Virtualbox"` and then run `VBoxManage modifyvm "<vmname>" --natnet1 "172.16.1/24"`. Additionally, make sure that your VM type is set to "NAT", not "NAT Network".

5.) Install Google Chrome, and if needed, sign into [Office 365](https://login.microsoftonline.com) and download and install Office 2016. Make sure that you set up all microsoft applications using your school-provided email. The purpose of installing all of this software in a Virtual Machine is to completely isolate it from the host and give it a "school-only" use.

6.) Disable Windows Defender. Windows Defender has a tendency to use up a large amount of CPU time, slowing down the virtual machine and making it very frustrating to use. First, open Windows Defender settings from Cortana and disable all of the options provided. Then open `gpedit.msc`, and under `Computer Configuration\Adminstrative Templates\Windows Components\` set "Turn off Windows Defender" to "Enabled".

7.) Install DyKnow 5.8 using the downloaded `.msi`. After it installs, restart the Virtual Machine and, while connected to any wifi (now that it thinks that it is on school wifi), open DyKnow and click on "Communication Settings" on the login page. For "Communications String", type in "dyknow://<dyknow-server>", where you can find <dyknow-server> by checking these same communication options on any regular school computer. Click the button labelled "Test", and if it tells you that the connection was successful, then click OK and log in with your regular username and password. This will enable the "Ad-hoc" mode on DyKnow in order to have teachers see this device under your name.

# Things to keep in mind:

1.) DyKnow, DyKnow's blocking, and DyKnow's screen viewer are all sandboxed to your Virtual Machine. This means that anything you open inside of your Virtual Machine is visible to teachers, and everything you open outside of it is not.

2.) You're still on school internet (if you've managed to get in; this is left as an exercise to the reader until I have concrete instructions). Act responsibly. Even if teachers can't see anything, SysAdmins can see *everything* you do while connected to their network. So don't do anything stupid.

3.) Teachers aren't stupid. If you sit there laughing at something on your computer screen and your screen hasn't changed in the past hour, or if they see you breaking out of the Virtual Machine, you're in for a bad time. Check where teachers are, and *focus* if they're watching you or anywhere where they could catch a glimpse of your screen. If they can't see it, you're in the clear for the most part

4.) Due to the changes that were made to the NAT network in step 4, the Virtual Machine will always think that it is connected to school internet. This also means (tested using Wireshark) that it will at the very least, try communicating with the DyKnow servers. It is up to your school's DyKnow Admin whether or not to permit teachers to watch you, but using this method, you can assume that teachers *can and will* watch you at home if you turn on the Virtual Machine. Therefore, either disconnect the network from the VM before starting it up at home, or don't use it at home.
