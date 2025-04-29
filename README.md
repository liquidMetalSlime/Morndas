# Morndas


This is a very, very small scale Lab aimed at recreating an enterprise network




## Necessities~ 
- VirtualBox (VMWare packages were out of date at the time)
- A Windows Desktop ISO, 10 is used for this; found [HERE](https://www.microsoft.com/en-us/software-download/windows10ISO)
- A Windows Server 2016 and up, found [HERE](https://www.microsoft.com/en-us/evalcenter/download-windows-server-2016)
- Google



## Setting Up

1. **VirtualBox Installation**
Installations for VirtualBox can be grabbed [HERE](https://www.virtualbox.org/wiki/Downloads).
Or if you enjoy Linux here and there, using Arch, follow the [ArchWiki](https://wiki.archlinux.org/title/VirtualBox) on this. 

For *me*, on **6.14.2-arch1-1**:
```bash
# Firstly, check for updates
pacman -Syyu
# Then, once finished, if updates were installed, reboot.
reboot
# Lastly, installing
pacman -Syy virtualbox virtualbox-host-modules-arch
```
And it magically works.


