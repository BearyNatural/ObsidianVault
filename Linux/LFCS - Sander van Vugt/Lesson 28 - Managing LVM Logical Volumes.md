![[M12.png]]

1. Create a volume group with the name vgbooks
2. On your second hard disk, add a 1GB LVM volume iwth the name lvbooks, format it with the ext4 file system and mountit persistently on /books
3. Shrink the LVM logical volume you've just created to a size of 800MiB, without losing any data currently on it
4. Create an LVM snapshot of the lvbooks volume and temporarily mount it on /mnt to verify its operation
5. Answers:
	1. lsblk [xvdc]
	2. fdisk /dev/xvdc
		1. n - p - 2 -  - +1G
		2. t - 8E [linux LVM]
		3. p - w
		4. partprobe
	3. vgcreate vgbooks /dev/xvdc2
	4. lvcreate -l 100%FREE -n lvbooks vgbooks
	5. mkfs.ext4 /dev/vgbooks/lvbooks
	6. mkdir /books
	7. mount /dev/vgbooks/lvbooks /books 
	8. [create 100 books = touch books{1..100}]
	9. lvresize -r -L -100M /dev/vgbooks/lvbooks [this is to reduce the LVbooks] UNABLE AS DRIVE IS BUSY EVEN TRIED UMOUNT :(
	10. lvcreate -s -n lvbooks-snap -L 96M /dev/vgbooks/lvbooks 
	11. mount /dev/vgbooks/lcbooks /mnt
	12. lsblk