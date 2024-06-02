external SSD :
make a Arch Linux OS from the Virtual Machine

paru-bin repo /morganamilo/paru

AUR_helpers

-- 29/09/23 
the VBox Manager keeps failing to load present VMs
I think I will delete it and reinstall it

T A — 06/16/2023 11:54 AM
Install VMware, install a Linux distro on it, connect the drive to the vm, ensure it is not mounted, format it

T A — 06/15/2023 10:18 PM
The path is this:
bios loads firmware
bios selects a start disk, loads boot loader, jumps into it
boot loader loads kernel and init filesystem (probably cpio based)
kernel loads configuration and additional modules from initfs
kernel mounts root fs (your distro)
kernel runs init