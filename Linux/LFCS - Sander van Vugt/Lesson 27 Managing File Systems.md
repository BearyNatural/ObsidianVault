![[M11.png]]

1. Create a new partition and format it with the ext3 file system 
2. Set the label to "newfs"
3. Create a systemd mount and automount unit file to automatically mount this filesystem on the directory /data/newfs
4. Answers:
	1. lsblk
	2. fdisk /dev/xvdc
		1. n - p - 1 -  - +500M
		2. p - w
		3. partprobe [a program that informs the os kernel of partition table changes it is a check]
	3. mkfs.ext3 -L newfs /dev/xvdc1
	4. cd /etc/systemd/system [he is copying a file that is not general, he uses it as a template] 
		1. cp - CAN NOT DO THIS STEP
			1. cp books.mount data-newfs.mount
			2. cp books.automount data-newfs.automount
		2. vi - do this step instead
			1. vi data-newfs.mount
				1. ![[Pasted image 20230219155342.png]]
				2. # This is part of systemd # # systemd is part of blah blah blah
				3. What=/dev/xvdc1 Where=/data/newfs Type=ext3 Options=defaults [this is what needs to change from the above under Mount]
			2. vi data-newfs.automount
				1. ![[Pasted image 20230219160145.png]]
				2. Where=/data/newfs [just need to change this line :)]
	5. mkdir -p /data/newfs
	6. systemctl enable --now data-newfs.automount
	7. mount | grep newfs
	8. cd /data/newfs/
	9. mount | grep newfs