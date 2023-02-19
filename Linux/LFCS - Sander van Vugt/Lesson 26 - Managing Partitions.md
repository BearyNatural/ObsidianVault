![[M10.png]]

1. Use a new (virtual) hard disk to create the following:
	1. 1 swap partition with a 1 GB size
	2. 1 Luks encrypted partition with a 1 GB size and an Ext4 file system
2. Enable the service that allows for trimming of your SSD devices
3. Answers:
	1. lsblk [I choose xvdb 8g drive, 1x1G partition, 7g free ]
	2. fdisk /dev/xvdb
		1. n - p - 2 -  - +1G [1st partition set]
			1. t - 82 [to change the partition type to 82]
		2. n - p - 3 -  - +1G [2nd partition set; leave partition type]
		3. p - w [p = to see the changes; w = to write the changes]
	3. lsblk
	4. free -m [to see free space]
	5. mkswap /dev/xvdb2
	6. swapon /dev/xvdb2 [easiest way,to make it persistentsee below:]
		1. vi /etc/fstab
			1. /dev/xvdb2 swap swap defaults 0 0
		2. swapon -a [or you could reboot]
	7. cryptsetup luksFormat /dev/xvdb3
		1. YES
		2. [enter password & confirm password]
	8. cryptsetup luksOpen /dev/xvdb3 secret [this names it, enter password]
	9. ll /dev/mapper [it should be viewable in dev/mapper]
		1. also listed under lsblk
	10. mkfs.ext4 /dev/mapper/secret [filesystem formating]
	11. mkdir /secret
	12. vi /etc/crypttab [automate the mount]
		1. secret /dev/xvdb3 
	13. vi /etc/fstab
		1. /dev/mapper/secret /secret ext4 defaults 0 0
	15. systemctl enable --now fstrim.timer