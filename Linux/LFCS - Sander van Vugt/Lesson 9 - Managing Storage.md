![[L9 1.png]]

1. Add a new (virtual) disk to your computer
	1. lsblk [will show all the blocks mounted or otherwise]
2. On this disk, create a 1 GB partition and format it with the ext4 file system
	1. fdisk /dev/xvdb
		1. n - p -  - +1G - p - w
	2. mkfs.ext4 /dev/xvdb1
3. Mount the partition as a temporary mount on the /mnt directory
	1. mount /dev/xvdb1 /mnt
	2. lsblk