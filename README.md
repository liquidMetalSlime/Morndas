# Morndas

This is a very, very small scale Lab aimed at recreating an enterprise network

# Necessities~ 
- VirtualBox *(VMWare packages were out of date at the time)*
- A Windows Desktop ISO, 10 is used for this; found [HERE](https://www.microsoft.com/en-us/software-download/windows10ISO)
  [WIN10-ISO site as of 2025-04-29](https://github.com/liquidMetalSlime/Morndas/blob/main/daImages/windowsISOsite.png)
- A Windows Server 2016 and up, found [HERE](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2016)
  [WIN-SVR-2016 site as of 2025-04-29](https://github.com/liquidMetalSlime/Morndas/blob/main/daImages/windowsISOsite.png)
- Google

# Installing VirtualBox

For Arch, follow the [ArchWiki](https://wiki.archlinux.org/title/VirtualBox).
For Debian, follow the [Debian Wiki](https://wiki.debian.org/VirtualBox).
Alternatively, don't listen to me and go straight to the [source](https://www.virtualbox.org/manual/ch02.html).

For *me*, on **6.14.2-arch1-1**:
```bash
# Firstly, check for updates
pacman -Syyu
# Then, once finished, if updates were installed, reboot.
reboot
# Lastly, installing
pacman -Syy virtualbox virtualbox-host-modules-arch
```
# Creating the Virtual Machines (VM)

This should be an equivalent process; unless you want to be fancy.

- **Name and Operating System**
1. Name both of the VMs after your favorite snack
2. Folder can remain as is, unless you want it somewhere else of course.
3. The '/path/to/your/iso'. Likely in your Downloads folder.
4. Edition *really* only matters for the Windows Server, at which point you
can decide, at least for 2016, two things, whether you want a purely
command-line server or Desktop 'Experience'; and whether you want a
*Standard* Edition or *Datacenter* Edition of the server. The differences between
the two is 'minimal',  this small lab takes place on Datacenter Edition (Desktop Experience).
Differences *Standard*, *Datacenter*, and *Datacenter: Azure Edition* can be found [HERE](https://learn.microsoft.com/en-us/windows-server/get-started/editions-comparison?pivots=windows-server-2025) 
5.


- **Unattended Install**
1. Credentials (user/pswd) can be whatever you want,
2. Product Keys can be ignored, as always.
3. *I* didn't care about a *Hostname* at the time, you may; or not. 
4. *I* didn't care about *Domain Names* at the time, you may; or not.




## next

