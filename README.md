# euca-kernel

Provides a single kernel/ramdisk for all Linux EMI. The EMI is initially booted using kernel / ramdisk. 

The ramdisk reads grub ( 1 or 2 ) :
 - grub.cfg
 - menu.lst
 - grub.conf

It will then kexec into the configured kernel. It will also erase partition 2 ( ephemeral disk ) and add it to partition 1 ( / )
