## notes

## Kernel stuff

> uname -r — prints the kernel version

## hardware stuff

> lscpu shows the architecture

Lsmem or free -m shows memory

> lshw gives. A detailed report on the machine

## to figure out what boot loader the system has

> ls -l /sbin/init

## the run level is it gui or terminal that boots

> runlevel - run level 5 implies a gui whereas 3 implies non gui, in systemd the run level is called the target.

## to get the default target

> systemctl get-default -

## to see where it is set

> ls -ltr /etc/systemd/system/default.target

## to set it

> systemctl set-default multi-user.target - creates a symbol link. Here we changed from graphical to multii user this changes the run level from 5 to 3

runlevel 0 -> poweroff.target
runlevel 1 -> rescue.target
runlevel 2 -> multi-user.target
runlevel 3 -> multi-user.target
runlevel 4 -> multi-user.target
runlevel 5 -> graphical.target
runlevel 6 -> reboot.target

- to determine what type of file a file is:
  > file bash-script.sh

# File System Explanation

/opt - third party programs
/media - usb drives, all external media,

> df -- shows all mounted file systems
> /dev -- external hard disk mouse (drivers?)
> /bin -- basic system commands mv date...
> /etc -- config files
> /lib lib64 -- shared libraries for programs
> /usr -- user applications, firefox, thunderbird mail, vim
> /var -- logs can be found here, + cached data
