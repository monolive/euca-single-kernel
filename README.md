# euca-kernel

Provides a single kernel/ramdisk for all Linux EMI. The EMI is initially booted using kernel / ramdisk. 

The ramdisk reads grub ( 1 or 2 ) :
 - grub.cfg
 - menu.lst
 - grub.conf

It will then kexec into the configured kernel. It will also erase partition 2 ( ephemeral disk ) and add it to partition 1 ( / )

Both scripts are modified version of Scott Moser scripts. https://code.launchpad.net/~smoser/+junk/kexec-loader

##  Requirements

The ramdisk is generated on top of ubuntu. You will need to have the following package available as part of your image
 - kexec-tools
 - ( provides growpart )

## How to 
1. Check out code

2. Copy all files from conf directory to /etc/initramfs-tools/
<pre><code>
cp -ax kexec-loader/conf/* /etc/initramfs-tools
</code></pre>

3. Update initramfs
<pre><code>
update-initramfs -c -k `uname -r`
</code></pre>

4. Bundle / upload / register - kernel / initramdisk pair

## Todo 
Clean up kexec-loader script ( some part of script are not neccesary )
Create a conf file for growroot ( to enable it or not ) 


