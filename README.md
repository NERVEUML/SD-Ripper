
![LOGO](/src/SD-Ripper-LOGO.png "LOGO")


# SD-Ripper

## Filename: rip.sh -> Main Driver
run using:

$  ./rip.sh [option] [absolute file path]

### Usage:

 [option][ [absolute file path] - both options are required
 * -m :calls mount function from mount_copy.sh
 * -c :calls copy function from mount_copy.sh
 * -mc or -cm: calls mount  and copy functions from mount_copy.sh
 * -u: calls unmount function from unmount_clean.sh
 * -x: calls the clean function from unmount_clean.sh
 * -ux or -xu: calls the unmount and clean function from unmount_clean.sh
 * -h : for this list of commands in the terminal

 **Note you don't need a file path only when using the -h flag**

###Functions:

**unmount():**
 Loops through the mounted point and unmounting all things that are mounted
 within the created directories.

**clean():**
 This will loop through the mount point and checks
 if the individual directory is empty. If empty then will remove that directory from
 the mount point.  

**amIRoot():**
This will exit the program if they are not root. This is for the ability to
copy over long periods of time without having to type password again.

**Mount():**
This will loop through all drives located by-path on /dev/disk/by-path/*-usb-*-part1.
So its by path to all recognizable exfat devices and the first partition of those
devices. Then will create a new directory for each drive named exactly how your
computer names it. Then the contents of each drive will be mounted to the exact same
corresponding folder by name. The mount point is a pre-made folder in this repository
called mnt.

**copy():**
Will loop through all the contents of the the directories in the mnt folder as
well as go to there /DCIM/ directory.And only copy that folder to a user defined
destination.  This process happens with rysnc a command that works like rysnc
takes three possible arguments. first will be optional flags depending on what
you  want to sync, the second is source you are copying from and the final is
the destination.

```sh
sudo ./rip.sh -mc /media/asgard-linux/2TB_2 /media/asgard-linux/2TB_1
```
