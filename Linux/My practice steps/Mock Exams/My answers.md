1. Bottlenose labs:
	1. 
2. OReilly's
	3.  ![[L2.png]]
		1. Answer: 
			1. 
	4. ![[L3.png]]
		1. Answer: 
			1. 
	5. ![[L4.png]]
		1. Answer: 
			1. 
	6. ![[L5.png]]
		1. Answer: 
			1. 
	7. ![[L6.png]]
		1. Answer: 
			1. 
	8. ![[L7.png]]
		1. Answer: 
			1. 
	9. ![[L8.png]]
		1. Answer: 
			1. 
	10. ![[L9.png]]
		1. Answer: 
			1. 
	11. ![[L10.png]]
		1. Answer: 
			1. 
	12. ![[L11.png]]
		1. Answer: 
			1. 
	13. ![[L12.png]]
		1. Answer: 
			1. 
	14. ![[L13.png]]
		1. Answer: 
			1. 
	15. ![[L14.png]]
		1. Answer: 
			1. 
	16. ![[L15.png]]
		1. Answer: 
			1. 
	17. ![[L16.png]]
		1. Answer: 
			1. 
	18. ![[Pasted image 20230213164108.png]]
		1. Answer: 
			1. 
	19. ![[Pasted image 20230213164232.png]]
		1. Answer: 
			1. 
	20. ![[Pasted image 20230213164334.png]]
		1. Answer: 
			1. 
	21. ![[Pasted image 20230213164409.png]]
		1. Answer: 
			1. 
	22. ![[Pasted image 20230213164446.png]]
		1. Answer: 
			1. 
	23. ![[Pasted image 20230213164551.png]]
		1. Answer: 
			1. 
	24. ![[Pasted image 20230213164634.png]]
		1. Answer: 
			1. 
	25. ![[Pasted image 20230213164736.png]]
		1. Answer: 
			1. 
	26. ![[Pasted image 20230213164844.png]]
		1. Answer: 
			1. 
	27. ![[Pasted image 20230213165012.png]]
		1. Answer: 
			1. 
	28. ![[Pasted image 20230213165043.png]]
		1. Answer: 
			1. 
	29. ![[Pasted image 20230213165207.png]]
		1. Answer: 
			1. 
	30. ![[Pasted image 20230213165136.png]]
		1. Answer: 
			1. 
	31. ![[Pasted image 20230213165730.png]]
		1. Answer: 
			1. 
	32. ![[Pasted image 20230213165808.png]]
		1. Answer: 
			1. 
	33. ![[Pasted image 20230213165838.png]]
		1. Answer: 
			1. 
	34. ![[Pasted image 20230213165905.png]]
		1. Answer: 
			1. 
	35. ![[Pasted image 20230213165943.png]]
		1. Answer: 
			1. 
	36. ![[Pasted image 20230213170008.png]]
		1. Answer: 
			1. 
	37. ![[Pasted image 20230213170053.png]]
		1. Answer: 
			1. 
	38. ![[Pasted image 20230213170146.png]]
		1. Answer: 
			1. 
	39. ![[Pasted image 20230213170244.png]]
		1. Answer: 
			1. 
	40. ![[Pasted image 20230213170319.png]]
		1. Answer: 
			1. 
	41. ![[Pasted image 20230213170451.png]]
		1. Answer: 
			1. 
3. https://ozguryarikkas.medium.com/lfcs-linux-foundation-system-administrator-exam-study-guide-with-exercises-part-1-d9ddc9efc39f similar as LFCS prac test run the setup.sh  1x10g + 2x5g
	1. D1:q18. Open the file under  /home/student/textreferences/editme.txt and  complete the following tasks:  
		1. Move line 7777 to line 1.    
		2. Replace every occurrence of the word Earth shown with  an uppercase E, with the word Globe.  
		3. Remove line 7001 (this line will be removed)
		4. Add a new line at the very end of the document that  contains Auctores Varii.
		5. Answer: 
			1. cd /home/student/textreferences/
			2. ll 
			3. vi editme.txt
			4. esc 7777 shift+g
			5. :move -7777
			6. :%s/Earth/Globe/g
			7. dd
			8. :wq
			9. echo 'Auctores Varii' >> editme.txt
	2. D1:q21. Perform the following tasks to demonstrate your ability to work with archives and compressed files:
		1. 1. Extract all files from archive file /opt/SAMPLE001.zip  into target directory /opt/SAMPLE001  
		2. Create a tar archive file /opt/SAMPLE0001.tar  containing all files in the directory /opt/SAMPLE001  
		3. Compress the tar archive file /opt/SAMPLE0001.tar  using the bzip2 compression algorithm  
		4. Compress the tar archive file /opt/SAMPLE0001.tar  using the xz compression algorithm  
			Make sure that the uncompressed archive file  /opt/SAMPLE0001.tar is not removed after creating the  compressed versions of the archive file!
		1. Answer: 
			1. cd /opt/
			2. rm -r file*.txt
			3. tar -xf SAMPLE001.zip 
			4. mv file*.txt /opt/SAMPLE001
			5. tar -cvf SAMPLE0001.tar /opt/SAMPLE001/
			6. bzip2 -zk SAMPLE0001.tar
			7. xz -zk SAMPLE0001.tar
	3. D1:A data directory is not used anymore and is about to be archived.  You have been asked to identify and remove some files, before archiving takes place.  Perform the following tasks to demonstrate your ability to search  for files given various criteria:
		1. Find all executable files in the directory /srv/SAMPLE002 and remove them
		2. Find all files in the directory /srv/SAMPLE002, which have not been accessed during the last month and remove them
		3. Find all empty directories in the directory /srv/SAMPLE002 and remove them
		4. Find all files in the directory /srv/SAMPLE002 with a file extension of .tar. Write a list of matching filenames, one per line, to the file /opt/SAMPLE002/toBeCompressed.txt, which has already been created. Ensure that you specify a relative path to each file, using /srv/SAMPLE001 as the base directory for the relative path
		5. Answer:
			1. cd /srv/SAMPLE002
			2. ll 
			3. find . -type f -executable -delete
			4. find . -type f -mtime 30 -delete
			5. find . -type f -empty -delete
			6. find /srv/SAMPLE002/ -type f -name '^.tar' >/opt/SAMPLE002/toBeCompressed.txt [must show relative path - READ THE INSTRUCTIONS CAREFULLY]
			7. cat /opt/SAMPLE002/toBeCompressed.txt
	4. D1:Hard and soft links offer a wide variety of options for System administrators. Perform the following tasks with system links:
		1. Create a hard link to /usr/local/links/hardlinkme.txt named 'hardlink1'
		2. Create a soft link to /usr/local/links/softlinkme.txt named 'softlink1'
		3. Write the path that 'softlink1' in /usr/local/links resolves to softlink2
		4. Answer:
			1. ch /home/ssm-user
			2. ln /usr/local/lins/hardlinkme.txt hardlink1
			3. ln -s /usr/local/links/softlinkme.txt softlink1
			4. ls -lrt | grep softlink1 | awk '{print $9,$10,$11}' >softlink2
	5. D2:Create a bash shell script named certscript.sh under /home/student/apps/
		1. 1. Make sure the script can be invoked as ./certscript.sh
		2. The first line of output from the script should consist of the name of the user who invoked it
		3. The second line of output should contain the IP address of the default gateway.
		4. Answer: 
			1. cd /home/student/apps
			2. vim certscript.sh
				1. whoami
				2. netstat -rn | grep 'UG[ /t]' | awk '{print $2}'
			3. chmod +x certscript.sh
			4. ./certscript.sh
	6. D2:Install the tmux package on your system.
		1. Answer:
			1. apt install tmux -y
	7. D2:Create a cron job that kills all processes named scan_filesystem which is owned by root, every minute.
		3. Answer: 
			1. vi script1.sh
				1. killall -1 -u root scan_filesystem
			2. chmod u+x script1.sh
			3. crontab -e
			4. */1 * * * * ./script1.sh     *
	8. D3:Linux administrators are responsible for the creation, deletion, and the modification of groups, as well as the group membership.  Complete the following tasks to demonstrate your ability to create and manage groups and group membership:
		1. Create a group called students.  
		2. Create the computestream group.
		3. Create a computestream folder in /exam/.
		4. Make the computestream group the owner of the /exam/computestream folder.
		5. Answer:
			1. groupadd students
			2. groupadd computestream
			3. mkdir -p /exam/computestream
			4. ll /exam/
			5. chgrp computesream -R /exam/computestream/
			6. chmod -R g+w /exam/computestream
			7. ll /exam/
	9. D3:Create a candidate user account with the password cert456.  Modify the sudo configuration to let the candidate account  access root privileges with no password prompt.
		1. Answer: 
			1. useradd candidate -p cert456
			2. vi /etc/sudoers
			3. candidate ALL=(ALL) NOPASSWD:ALL
			4. to test
				1. su - candidate
				2. sudo useradd test
				3. id test
				4. sudo userdel test
	10.  D3:Configure the system so that an empty NEWS file is automatically created in the home directory of any new user.
		1. Answer: 
			1. touch /etc/skel/news [do this 1st as this will automatically add to each new users home directory]
	11. D3:Create a new user account with the following attributes:
		3. Username is harry.
		4. Password is magic.
		5. This user???s home directory is defined as /home/school/harry/. [remember this does spit out errors - check before you change something doesn't mean it wasn't done as requested it might just be having a whinge!]
		6. This new user is a member of the existing students group.
		7. The /home/school/harry/binaries/ directory is part of the PATH variable. 
		8. Answer: 
			1. useradd -p magic -m -d /home/school/harry harry [error message may pop up double check it is done]
			3. ll /home/school/harry
			4. usermod -aG students harry
			5. id harry 
			7. usermod -m -d /home/school/harry/binaries harry
	12. D3:Create a user account with username sysadmin with the following attributes:
		1. Use a password of science.
		2. This user???s home directory is defined as /sysadmin/.
		3. sysadmin has sudo privileges and will not be prompted for a password when using the sudo command.
		4. The default shell for this user is zsh.
		5. Answer:
			1. useradd sysadmin -p science -m -d /sysadmin
			2. vi /etc/sudoers
				1. sysadmin ALL=(ALL) NOPASSWD:ALL
			3. chsh -s zsh sysadmin [may need to install it] apt install zsh -y [still errors zsh does not exist]
			4. chsh -s $(which zsh) sysadmin
	13. D3:Ensure that all users can invoke the last command and access a list of users who previously logged in.
		1. Answer:
			1. vi /etc/sudoers
			2. $user ALL=(ALL) NOPASSWD:/bin/last
			3. to test
				1. useradd test
				2. su - test
				3. useradd moretest [this should be permission denied]
				4. last [should show up list]
	14. D3:Correct the projectadmin user account so that logins are possible using the password _onetime43_. Set the home directory to /home/projectadmin.
		1. Answer:
			1. usermod -p onetime43 -m -d /home/projectadmin projectadmin 
	15. D3:Alter the devel user account so that it can log into the system with a working bash shell environment.
		1. Answer:
			1. chsh -s $(which bash) devel
	16.  D4:Find ports under /etc/services:
		1. Find the name of the service which uses TCP port 2605, as documented in /etc/services, and write the service name to the file /home/student/port-2605.txt.
		2. Find all the ports used for TCP services IMAP3 and IMAPS, again as documented in /etc/services, and write those port numbers to the file /home/student/imap-ports.txt
		3. Answer: 
			1. cat /etc/services | grep 2605 | awk '{print $1}' > /home/student/port-2605.txt
			2. cat /home/student/port-2605.txt
			3. cat /etc/services | grep tcp | grep -i imap | awk '{print $2}' | sed 's/\/.*//g' > /home/student/imap-ports.txt  v
	17. D5:As a Linux System administrater you will often be tasked with recording and making changes to networking configuration of VMs.  
		1. Write the contents of the routing table to a file in /usr/local/networking/routing.txt 
		2. Answer: 
			1. .route -n | tail -n 5 > /usr/local/networking/routing.txt
			2. cat /usr/local/networking/routing.txt
	18.  D5:As a Linux System administrator you will often be tasked with maintaining webservers.  Sometimes you will want to change the default behavior of the apache2 service to accommodate your needs.
		1. Update the port that the apache2 service listens on from 80 to 1990.
		2. Ensure these changes are persistent
		1. Answer: 
			1. netstat -lnp | grep apache2
			2. find /etc/ -name *.conf | grep apache2
			3. cat /etc/apache2/ports.conf
			4. vi /etc/apache2/ports.conf 
			5. vi /etc/apache2/sites-available/000-default.conf
			6. systemctl restart apache2
			7. systemctl status apache2
			8. netstat -lnp | grep apache2
	19.  D5:As a Linux System administrator you will often make changes to Virtual Machines running in your environment.  NOTE you will need to install libvirt libvirt-bin qemu qemu-kvm virt-install virt-manager wget and create the webservers first with but the exam seems to test your ability to modify runnig webservers.  see unable to replicate this yet so write the commands as if they were set up if you are getting 'error: failed to get domain 'webserver'' then you have the correct command.
		1. Start webserver
		2. Stop webserver2
		3. Ensure that webserver automatically starts when the server restarts
		1. Answer: 
			1. apt install 
				1. qemu-kvm -y
				2. libvirt-daemon-system -y
				3. virt-manager -y
				4. wget -y
			2. virsh list
			3. virsh start webserver
			4. virsh shutdown webserver2
			5. virsh autostart webserver 
			6. other virsh commands:
				1. reboot
				2. shutdown
				3. save 
				4. restore
	20. D5:Containerized services offer Linux administrators flexible options and often increased performance. Perform the following tasks with docker containers.
		1. Stop the docker container 'docker1'
		2. Delete the docker container 'docker2'
		3. Create a docker container 'docker3' ensuring it automatically restarts when the system reboots
		4. map port 80 on the container to 8080 on the local machine and use the latest version of nginx
		1. Answer: 
			1. Answers: 
				1. docker container list 
				2. docker container stop docker01
				3. docker container stop docker02
				4. docker container rm docker02 
				5. docker container create --name docker03 -p 80:8080 --restart unless-stopped nginx
				6. other commands for playing:
					1. docker container start docker03
					2. docker ps; or
					3. docker container list
	21. D5:Logical volumes can enhance the file system capabilities of a Linux VM. Understanding and being able to manipulate them is critical to being a successful Linux administrator.  After attaching a 10gb disk for additional storage, perform the following tasks:  
		1. Create two partitions, each with 2GB of storage
		2. Create a volume group name ???vg01??? from the two partitions
		3. Create a logical volume named ???lv01??? with the following attributes
			1. 2GB of storage from vg01
			2. Format it with the ext3 file system
			3. Give it a label ???lv01???
			4. Mount it persistently to /mnt
		1. Answer: 
			1. Create the partitions
					1. fdisk --help
						1. fdisk -l
						2. fdisk /dev/xvdb
							1. m
							2. n - p - 1 -  - 2G  x 2
							3. p - w
					2. lsblk don't do this section
						1. df -kh [to check if drive is mounted] 
						2. mkfs --type ext3 /dev/nvme1n1
						3. or mkfs.ext3 /dev/nvme1n1
						4. mount /dev/nvme1n1 /mnt [don't mount the disk]
						5. df -kh [confirm disk mount]
						6. blkid [grab the uuid no ""]
						7. vi /etc/fstab [UUID=ef25b663-d33e-479e-b90e-759287fb7dbc /mnt  ext3  defaults,noatime,nofail  1  0]
					4. fdisk -l [disk /dev/nvme1n1  has the biggest space; plus up to 5 loops]
					5. fdisk /dev/nvme1n1
						1. m - do the following twice 
						2. n [for add a new partition]
						3. p [for primary]
						4. 1 [for partition #]
						5. [leave 1st blank as this is the start or the partition]
						6. +2G [extend the partition 2Gbs]
						7. p [print to confirm partitions]
						8. w [this will write/save your partitions]
				3. fdisk -l /dev/nvme1n1
				4. lsblk [shows the mounted drive plus the partitions]
					1. nvme1n1p1
					2. nvme1n1p2
				5. create physical volumes
					1. pvcreate /dev/nvme1n1p1 /dev/nvme1n1p2
					2. pvscan
					3. pvdisplay
				6. create volume group
					1. vgcreate vg01 /dev/nvme1n1p1 /dev/nvme1n1p2
					2. vgdisplay
				7. create logical volume
					1. lvcreate --help
					2. lvcreate --size 2g --name lv01 vg01
					3. lvdisplay
					4. mkfs.ext3 /dev/vg01/lv01
				8. mount /dev/vg01/lv01 /mnt
					1. blkid
					2. vi /etc/fstab
					3. UUID=5abcf53d-1de6-4ce5-9095-79574eaed6f2 /mnt  ext3  defaults 0 2
				9. https://www.thegeekstuff.com/2010/08/how-to-create-lvm/
	22. D6:Complete the following tasks:
		1. Temporarily mount the filesystem available on /dev/(additionaldrive) under /mnt/backup/. NOTE: setup the filesystem with ext4, after mounting cp /opt/SAMPLE0001.tar.bz2 /mnt/backup/backup-primary.tar.bz2
		2. Decompress and unarchive the /mnt/backup/backup-primary.tar.bz2 archive into /opt/. This should result in a new directory (created from the archive itself) named /SAMPLE002/
		3. Answer: 
			1. lsblk 
			2. mkdir /mnt/backup
			3. xz -d /opt/SAMPLE001.tar.bz2 or use bzip2
			4. tar -xf /opt/SAMPLE0001.tar 
	23. D6:Configure the swap partition on new drive so that it does not* become attached automatically at boot time.
		1. Answer: 
			1. fdisk /dev/disk [if using additional drive]
				1. n - p - # -  - +1G [set partition]
				2. t - 82 [to change the type to swap]
				3. p - w [to see the changes and to write the changes]
				4. other ways:
					1. fallocate -l 1G /swapfile [if using system ebs]
			3. mkswap /swapfile
			4. swapon /swapfile
			5. swapon --show
	24. D6:Configure the system so that the existing filesystem that corresponds to /staging gets persistently mounted in read-only mode.
		1. Answer:
			1. mount -r /dev/xvdd /staging
			2. vi /etc/fstab
				1. UUID= /staging ext4 defaults 0 2
- Linux Foundation Prac Exam: run the setup.sh + 1x10gebs + 3 x 4gebs
	1. As the Linux system administration of AVC company you have been getting complaints about the performance of some of the Linux servers used by your development team.  After investigating the source of these performance issues you realise the number of running processes started by users is too high.
		1. Set a limit on the number of processes users of the 'developer' group can start to 20.
		2. Ensure that user 'Bob' who is a member of the 'developer' group is not impacted by these limits.
		3. Answers:
			1. sudo -i
			2. find /etc | grep limit
			3. cat /etc/security/limits.conf
			4. vi /etc/security/limits.conf
				1. @developer hard nproc 20
				2. Bob hard nproc 4194304 [/proc/sys/kernel/pid_max]
			5. su - Bob
				1. ulimit -a
				2. exit 
	2. As a Linux System administrater you will often be tasked with recording and making changes to networking configuration of VMs.  For the below question you will need to ssh to exam-1 to complete the following: NOTE: for the purpose of the practice exam perform this locally, but ensure you are familiar with how to ssh to a remove server.
		1. Write the contents of the routing table to a file in /usr/local/networking/routing.txt 
		2. Answers: 
			1. don't need to ssh as it says above - chill
			2. ip route [current recommended way of printing the routing table in Linux]
			3. ip route > /usr/local/networking/routing.txt
			4. cat /usr/local/networking/routing.txt
			5. other ways of seeing the routing table:
				1. netstat -r
				2. route -n (wasn't installed)
	3. As a Linux System administrator you will often be tasked with maintaining webservers.  Sometimes you will want to change the default behavior of the apache2 service to accommodate your needs.
		1. Update the port that the apache2 service listens on from 80 to 1990.
		2. Ensure these changes are persistent
		3. Answers:
			1. systemctl status apache2
			2. netstat -lnp
			3. find /etc | grep apache2
			4. cat /etc/apache/ports.conf
			5. vi /etc/apache/ports.conf
				1. change line 'Listen 80' to 'Listen 1990'
			6. cat /etc/apache/ports.conf
			7. systemctl restart apache2
			8. systemctl status apache2
			9. netstat -lnp
	4. As a Linux System administrator you will often make changes to Virtual Machines running in your environment.  NOTE you will need to install libvirt libvirt-bin qemu qemu-kvm virt-install virt-manager wget and create the webservers first with but the exam seems to test your ability to modify runnig webservers.  see q4 for further instructions.
		1. Start webserver
		2. Stop webserver2
		3. Ensure that webserver automatically starts when the server restarts
		4. Answers: - doesn't seem realistic to have to memorise a url :O 
			1. apt install libvirt-clients -y
			2. apt install qemu -y
			3. apt install qemu-kvm libvirt-daemon-system -y
			4. virsh list
			5. virsh start webserver
			6. virsh stop webserver2
			7. virsh autostart webserver
	5. Containerized services offer Linux administrators flexible options and often increased performance. Perform the following tasks with docker containers.
		1. Stop the docker container 'docker1'
		2. Delete the docker container 'docker2'
		3. Create a docker container 'docker3' ensuring it automatically restarts when the system reboots
		4. map port 80 on the container to 8080 on the local machine and use the latest version of nginx
		5. Answers: these aren't setup and therefore you'll need to play with them at a later time;  just use the following commands:
			1. docker container stop docker01
			2. docker container stop docker02
			3. docker container rm docker02
			4. docker container create --name docker03 -p 80:8080 --restart unless-stopped nginx
			5. other commands for playing:
				1. docker container start docker03
				2. docker ps; or
				3. docker container list
	6. Hard and soft links offer a wide variety of options for System administrators. Perform the following tasks with system links:
		1. Create a hard link to /usr/local/links/hardlinkme.txt named 'hardlink1'
		2. Create a soft link to /usr/local/links/softlinkme.txt named 'softlink1'
		3. Write the path that 'softlink2' in /usr/local/links resolves to
		4. Verify which file in /usr/local/links/hardlinks/ had the most hardlinks to it and write the number of hard links to a file called 'linknum' in /usr/local/links/hardlinks/
		5. Answers:
			1. ln /usr/local/links/hardlinkme.txt hardlink1
			2. ln -s /usr/local/links/softlinkme.txt softlink1
			3. ll [should show both hard & soft link files]
	7. Logical volumes can enhance the file system capabilities of a Linux VM. Understanding and being able to manipulate them is critical to being a successful Linux administrator.  After attaching a 10gb disk for additional storage, perform the folling tasks:  NOTE: You will need to add an additional disk to your VM; however, the exam will specify which disk to use.
		1. Create two partitions, each with 2GB of storage
		2. Create a volume group name ???vg01??? from the two partitions
		3. Create a logical volume named ???lv01??? with the following attributes
			1. 2GB of storage from vg01
			2. Format it with the ext3 file system
			3. Give it a label ???lv01???
			4. Mount it persistently to /mnt
			5. Answers:
				1. Create the partitions
					1. fdisk --help
					2. lsblk					3. .
					3. df -kh [to check if drive is mounted]
						2. mkfs --type ext3 /dev/nvme1n1
						3. or mkfs.ext3 /dev/nvme1n1
						4. mount /dev/nvme1n1 /mnt [don't mount the disk]
						5. df -kh [confirm disk mount]
						6. blkid [grab the uuid no ""]
						7. vi /etc/fstab [UUID=ef25b663-d33e-479e-b90e-759287fb7dbc /mnt  ext3  defaults,noatime,nofail  1  0]
					4. fdisk -l [disk /dev/nvme1n1  has the biggest space; plus up to 5 loops]
					5. fdisk /dev/nvme1n1
						1. m - do the following twice 
						2. n [for add a new partition]
						3. p [for primary]
						4. 1 [for partition #]
						5. [leave 1st blank as this is the start or the partition]
						6. +2G [extend the partition 2Gbs]
						7. p [print to confirm partitions]
						8. w [this will write/save your partitions]
				3. fdisk -l /dev/nvme1n1
				4. lsblk [shows the mounted drive plus the partitions]
					1. nvme1n1p1
					2. nvme1n1p2
				5. create physical volumes
					1. pvcreate /dev/nvme1n1p1 /dev/nvme1n1p2
					2. pvscan
					3. pvdisplay
				6. create volume group
					1. vgcreate vg01 /dev/nvme1n1p1 /dev/nvme1n1p2
					2. vgdisplay
				7. create logical volume
					1. lvcreate --help
					2. lvcreate --size 2g --name lv01 vg01
					3. lvdisplay
					4. mkfs.ext3 /dev/vg01/lv01
				8. mount /dev/vg01/lv01 /mnt
					1. blkid
					2. UUID=5abcf53d-1de6-4ce5-9095-79574eaed6f2 /mnt  ext3  defaults 0 2
				9. https://www.thegeekstuff.com/2010/08/how-to-create-lvm/
				10.  https://www.linuxbabe.com/desktop-linux/how-to-automount-file-systems-on-linux
	8. Automating routine system tasks using bash scripts can help system administrators complete routine tasks.  Write and run bash script to complete the following system exercises:
		1. Create 2 files in a new directory called ???manuals??? located in your home directory
			1. Name the first file ???sed-info??? and redirect the output of the ???sed??? command man page to the contents of the file
			2. Name the second file ???grep-info??? and redirect the output of the ???grep??? command man page to the contents of the file.
		2. Archive and compress the contents of the newly created ???manuals??? directory using the xz compression tool
		3. decompress the file in the /usr/archive
		4. Move the back up file to /usr/backups
		5. Ensure to clean up any old backup files
		6. Answers:
			1. Write the bash script2:
				1. #!/bin/bash
				2. # 
				3. #comments
				4. rm -r /home/manuals
				5. mkdir -p /home/manuals
				6. cd /home/manuals
				7. man sed > sed-info
				8. man grep > grep-info
				9. tar -cvf manuals.tar *
				10. xz -z manuals.tar
				11. mv manuals.tar.xz /usr/archive
				12. xz -d manuals.tar.xz
				13. mv manuals.tar /usr/backups
				14. exit 0
			2. chmod +x script2
			3. ./script2
			4. to run it regularly i.e. crontab
				1. crontab -e
				2. select editor of choice
				3. in file enter line for automating the script the file explains it all double check the times use the date command to find out the computer time
				4. check once it is done
	9. System administrators need to often setup and maintain network connectivity between machines withing the business.  SSH to exam-1 and complete the following network changes to meet the requirements:  NOTE: if your virtual machine running in the cloud you may not be able to update these values; however you can review the file(s) and proccesses.
		1. Configure your Linux machine with a static networking configuration
		2. After you have set up static networking, add a secondary DNS server at the address of 8.8.8.8
		3. Find a list of current nameservers for the system and redirect the output to a file called ???dnsservice??? located in /srv/dns
		4. Find the hostname and IP address of your machine and append the output to a file named dns-service located in /srv/dns
		5. Answers: these aren't correct I don't think - doesn't match my system :( )
			1. configure to static:
				1. vi /etc/network/interfaces [change 2nd line to]
				2. iface eth0 inet dhcp [iface eth0 inet static \n address 192.168.0.100 \n netmask 255.255.255.0 \n gateway 192.168.0.1 \n dns-nameservers 8.8.8.8]
			2. cat /etc/resolv.conf | grep nameserver
			3. resolvectl status
			4. systemctl restart network
	10. System administrators will often have to diagnose and fix disks on Linux machines.  The disk where /mnt/backup is mounted is not working. Repair the disk and verify it will be automatically mounted upon reboots.  NOTE: This question is hard to simulate; however, you can run the corresponding commands on a working disk and see the outputs.
		1. Answers:
			1. fsck -a /dev/driveletters
			2. mount /devdriveletters /mnt/backup
			3. blkid
			4. vi /etc/fstab [uuid=blkiduuid /dev/driveletters /mnt/back ext4 defaults 0 0]
	11. Setting up redundencies amoung disks is often an important taks that system administrators must complete.  Create a RAID 1 device named md0 using 2 disk devices of 1GB each and complete the following:  NOTE: You will have to add additional disks to do this on your VM. The names may differ than what is shown from my lsblk command https://bobcares.com/blog/removal-of-mdadm-raid-devices/
		1. Put a ext4 file system on it with the label of ???md0???
		2. Add a spare disk of 1GB
		3. Mount to /raid
		4. Save the raid configuration and write the configuration file to /etc/mdadm/mdadm.conf
		5. make it persistant
		6. Answers:
			1. lsblk
				1. nvme2n1 (sdb)
				2. nvme3n1 (sdc)
			2. fdisk -l
				1. MBR = msdos | GPT = gpt
				2. parted /dev/sdb mklabel msdos
				3. parted /dev/sdc mlabel msdos
			3. fdisk /dev/sdb then do sdc
				1. n
				2. p
				3. 1
				4. blank
				5. +1G
				6. p
				7. t [to change the partition type]
				8. fd  [set partition type to linux raid autodetect]
				9. p
				10. w
			4. lsblk
				1. nvme2n1p1 (sdb1)
				2. nvme3n1p1 (sdc1)
			6. mdadm - is it installed? apt install mdadm -y [installed]
				1. mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1 /dev/sdc1
				2. mdadm --detail /dev/md0
			7. format & mount
				1. mkfs.ext4 /dev/md0
				2. mkdir /mnt/raid1
				3. mount /dev/md0 /mnt/raid1
				4. df -kh /mnt/raid1
				5. https://www.linuxbabe.com/linux-server/linux-software-raid-1-setup
			8. save raid configuration
				1. mdadm --detail --scan --verbose >> /etc/mdadm/mdadm.conf
			9. make it persistent
				1. blkid /dev/md0 [grab uuid]
				2. vi /etc/fstab
					1. UUID=1700a7ef-6dbc-416f-b45d-149897e86f2d /mnt/raid1 ext4 defaults 0 0
	12. Managing groups and group permissions is an important task for system administrators:  Perform the following actions:
		1. Make the following groups:
			1. employees
			2. contractors
		2. Make a new directory called /srv/admins
		3. Give the group administrators full access (read/write/execute) to /srv/admins
		4. Give the group admin the same rights/privileges as root and allow members of the group to run all commands without a password prompt.
		5. Create a directory /data/list and then create a file ???list-info???. Redirect the output of the ???ls??? manual page into the contents of the file.
		6. Answers:
			1. groupadd employees
			2. groupadd contractors
			3. mkdir -p /srv/admins
			4. chmod g+w /srv/admins
			5. cat /etc/passwd [compgen -u or compgen -g works also!!!]
			6. cat /etc/group | grep admin [admin is a group assumed group administrators]
			7. chgrp admin /srv/admins [ll /srv to check]
			8. find /etc | grep sudo
			9. vi /etc/sudoers [%admin ALL=(ALL) NOPASSWD:ALL]
			10. mkdir -p /data/list
			11. man ls > /data/list/list-info
	13. Managing users is an important task of a Linux system administrator.  Perform the following actions (read section as some steps can be combined):
		1. Create the following users:
			1. linuxbro
			2. gharrison
			3. jlennon
			4. pmccartney
			5. rstarr
		2. Make linuxbro???s primary group admin
		3. Make linuxbro???s default shell zsh
		4. Make a comment for the account linuxbro stating the user???s full name of ???Linux Broman???
		5. Make the accounts for jlennon and rstarr expire two years from today???s date
		6. Add accounts jlennon and rstarr to the contractors group
		7. Add accounts gharrison and pmccartney to the employees group
		8. Ensure each user has a folder in their home directory called ???welcome-info???
		9. Set each account???s password to [???Pa$$w0rd???] and make them change it on next login
		10. Answers:
			1. touch /etc/skel/welcome-info [do this 1st as this will automatically add to each new users home directory]
			2. useradd -m gharrison [jlennon, pmccartney, rstarr]
			3. useradd -m -c "Linux Broman" -s /bin/bash linuxbro
			4. usermod --shell zsh linuxbro
			5. usermod -ag admin linuxbro
			6. date [feb 14 2023] -e yyyy-mm-dd
				1. usermod -e 2025-02-14 jlennon rstarr [chage -l username to check]
			7. usermod -aG contractors jlennon rstarr
			8. usermod -aG employees gharrison pmccartney
			9. usermod -p [???Pa$$w0rd???] linuxbro gharrison jlennon pmccartney rstarr
			10. chage -d 2023-02-14 linuxbro gharrison jlennon pmccartney rstarr
	14. The cron.d service is often used to run system scripts on a regular basis.  Create a series of scheduled tasks:
		1. Run the system-info script every day at 6am, 9am, 12pm, 3pm, and 6pm (except Saturday and Sundays).
		2. Run the system-info script on January 9th at 11:01pm
		3. run the system-info script in the first 10 minutes of the hours 14 and 15 on the 4th day of jan feb and april, monday through friday
		4. Run the system-info script every 3 months at 12:01am
		5. Answers:
			1. couldn't find this system-info script so I made copies of previously made script2
				1. cp /root/script2.sh /root/script3.sh
				2. cp /root/script2.sh /root/script4.sh
				3. cp /root/script2.sh /root/script5.sh
			2. crontab -e
				1. 00 06,09,12,15,18 * * 1,2,3,4,5 ./script3.sh
				2. 01 23 09 01 * ./script4.sh
				3. 10 14,15 04 01,02,04 1,2,3,4,5 ./script2.sh
				4. 01 0 1 */3 * ./script5.sh
	15. Find all of the the files in /home/example:
		1. that are not owned by Sue and write them to a file /home/example/answer1 overriding anything that is currently there
		2. that have the suid enabled and append them to a file /home/example/answer2
		3. that are 126MB in size and append them to a file /home/example/answer3
		4. that are larger than 400kb and write them to a file /home/example/answer4 overriding anything that is currently there
		5. that have a .tar extention and haven't been accessed in more than 30 days
		6. Answers: best to move into the actual folder /home/example for this activity
			1. ll /home/example/
				1. -rw-r--r--  1 root root          0 Feb 13 21:38 answer1
				2. -rw-r--r--  1 root root          0 Feb 13 21:38 answer2
				3. -rw-r--r--  1 root root          0 Feb 13 21:38 answer3
				4. -rw-r--r--  1 root root          0 Feb 13 21:38 answer4
				5. -rw-r--r--  1 root root          0 Feb 13 21:38 answer5
				6. -rw-r--r--  1 Bob  admin         0 Feb 13 21:38 file0
				7. -rw-r--r--  1 Sue  admin         0 Feb 13 21:38 file1
				8. -rw-r--r--  1 root root  132120576 Feb 13 21:38 file10
				9. -rw-r--r--  1 root root     524288 Feb 13 21:38 file11
				10. -rw-r--r--  1 Sue  admin         0 Feb 13 21:38 file2
				11. -rw-r--r--  1 Sue  admin         0 Feb 13 21:38 file3
				12. -rw-r--r--  1 Sue  admin         0 Feb 13 21:38 file4
				13. -rw-r--r--  1 Sue  admin         0 Feb 13 21:38 file5
				14. ------S---  1 Sue  admin         0 Feb 13 21:38 file6
				15. -rw-r--r--  1 Sue  admin         0 Feb 13 21:38 file7
				16. ------S---  1 Sue  admin         0 Feb 13 21:38 file8
				17. -rw-r--r--  1 Sue  admin         0 Feb 13 21:38 file9
			2. find /home/example/ -type f ! -user Sue > /home/example/answer1
				1. cat /home/example/answer1
			3. find /home/example/ -type f -perm /4000 > /home/example/answer2
				1. cat /home/example/answer2
			4. find /home/example/ -type f -size 126M > /home/example/answer3
				1. cat /home/example/answer3 [for greater + & lesser -]
			5. find /home/example/ -type f -size +400k > /home/example/answer4
				1. cat /home/example/answer4
			6. find /home/example/ -type f -name *.tar > /home/example/answer5
				1. tar -cvf answer4.tar answer4 to check the command is correct 
				2. cat /home/example/answer5
	16. User 'Bob' recieved several error messages while trying to run commands as root this morning.  NOTE: You can su to Bob and run some root commands to generate this log activity.
		1. Search the log files in /var/log and write any errors pertaining to this to /usr/log/root.error
		2. Answers:
			1. ll /var/log/
			2. cat /var/log/auth.log or syslog or wtmp or faillog
			3. cat /var/log/ | grep -r Bob | grep -ri error [ r looks recursively i.e. in things & i removes case sensitivity]
	17. Find the apt package which owns the library file /usr/lib/NetworkManager/conf.d/10-slaves-order.conf and append the output to /rpm/rpm-data.  Find the last 5 rpm packages installed and append them to /rpm/rpm-data.
		1. Answers:
			1. dpkg --help | grep -i own
			2. dpkg -S /usr/lib/NetworkManager [this is enough to find the owner chrony as conf.d doesn't exist]
	18. **Open the file under /home/student/textreferences/editme.txt and complete the following tasks:**  NOTE: I'm sharing the exact keystrokes I use in vim to accomplish this. Keep in mind with copy paste, vim, and your imagination there are many ways to do this.
		1. Move line 7777 to line 1.
		2. Remove line 7000.
		3. Replace every occurrence of the word Earth shown with an uppercase E, with the word Globe.
		4. Add a new line at the very end of the document that contains Auctores Varii
		5. Answers:
			1. Setup
				1. cd /home/student/textreferences/
				2. ll
				3. exitme.txt is the only file in there
			2. tasks
				1. move line 7777 to line 1
					1. :set nu [reveals the line numbers]
					2. esc 7777 shift+g
					3. :move -7777
				2. Remove line 7000
					1. esc 7000 shift+g
					2. :d or dd
				3. :%s/Earth/Globe/g
				4. add new line at bottom of document
					1. esc+G+A  [create new line,then type the following line] or :$
					3. Auctores Varii
	19. Manipulating services running on a system can be a very important task for system administrators.  There is a service named apache2 running on a system:  NOTE this is difficult to simulate the way the LFCS asks it, but these steps can be performed on sshd to see the commands in action
		1. figure out which port apache2 is listening on
		2. edit the config file for apache2 to listen on another port, 99
		3. start apache2
		4. send a SIGHUP signal to apache2
		5. write the list of all files foo has open to /usr/service/foo.txt
		6. Answers:
			1. netstat -lnp | grep apache2
			2. find /etc -type f -name *.conf | grep apache2   *
				1. cat /etc/apache2/ports.conf
				2. vi /etc/apache2/ports.conf [change port to Listen 99]
				3. cat to confirm change
				4. netstat -lnp | grep apache
			3. systemctl start apache2
				1. systemctl status apache2
			4. SIGHUP signal is part of the SIGTERM kill commands
				1. pidof apache2
				2. kill -l 
				3. kill -s 1 [pid]
				4. pidof apache2
			5. this foo person doesn't exist so therefore the command doesn't work...
				1. mkdir /usr/service | lsof -i -u foo > /usr/service/foo.txt
	20. Running scripts and manipulating their outputs is an important skill to understand as a system administrator.
		1. run the script at /usr/bin/samplescript.sh and append the standard out to the file at /usr/script/sampleone.txt
		2. run the script at /usr/bin/samplescript2.sh and override the contents of the file at /usr/script/sampletwo.txt with the standard error
		3. run the script at /usr/bin/samplescript.sh and use the standard out and standard error as a standard in for script /usr/bin/samplescript2.sh
		4. append the standarrd out of this to /usr/script/samplethree.txt
		5. Answers:
			1. cd /usr/bin
				1. ./samplescript.sh >> /usr/script/sampleone.txt [cat will be blank]
				2. ./samplescript2.sh 2> /usr/script/sampletwo.txt [cat shows the error message]
				3. ./samplescript.sh &> /usr/bin/samplescript2.sh [cat shows the bash error]
				4. ./samplescript2.sh < intermediate.txt >> /usr/script/samplethree.txt
	21. **Performing backup, compression, and clean up are all important tasks for Linux System Administrators.  Perform the following tasks to demonstrate your ability to work with archives and compressed files:**
		1. *create 3 blank files in your home directory and perform the following* *not req*
		2. Extract all files from archive file /opt/SAMPLE001.zip into target directory /opt/SAMPLE001
		3. Create a tar archive file /opt/SAMPLE0001.tar containing all files in the directory /opt/SAMPLE001
		4. Compress the tar archive file /opt/SAMPLE0001.tar using the bzip2 compression algorithm
		5. Compress the tar archive file /opt/SAMPLE0001.tar using the xz compression algorithm
			1. Make sure that the uncompressed archive file /opt/SAMPLE0001.tar is not removed after creating the compressed versions of the archive file!
		6. Answers:
			1. touch blank1.txt; touch blank2.txt; touch blank3.txt;
			2. tar -xf sample001.zip -C /opt/sample001
			3. tar -cf sample0001.tar blank1.txt blank2.txt blank3.txt
			4. xz -z archive.tar
			5. xz -kz manuals.tar
	22. Being able to quickly search files is an important task for system administrators.  Search the file /usr/sample/example.txt for the follwoing and write them to file.txt:
		1. all lines that end with the word linux
		2. all lines that start with the word Linux
		3. all lines with Linux and yay both in them.
		4. lines that contain linux or yay in them.
		5. Answers:
			1. cd /usr/sample
			2. ll [confirmed example.txt is here]
			3. grep -i 'linux$' example.txt > file.txt
			4. grep '^Linux' example.txt >> file.txt
			5. cat example.txt | grep Linux | grep yay >> file.txt
			6. grep linux\|yay example.txt >> file.txt
	23. Create a 1GB SWAP file and add it to the exiting SWAP pool. Ensure it is mounted at boot.  NOTE: understand the difference between Swap file and swap partition and be able to complete the above with both.
		1. Answers: https://manpages.ubuntu.com/manpages/bionic/man8/swapon.8.html
			1. fallocate -l 1G /swapfile
			2. mkswap /swapfile
			3. swapon /swapfile
			4. swapon --show
	24. Identifying the difference between files and directories is a common system administrator task.  
		1. Find which files in /usr/diff/ is different and write the file name to a file /usr/diff/answer1
		2. Find all of the files that are in /usr/diff/diff1 but not in /usr/diff/diff2 and write them to /usr/diff/answer2
		3. Answers:
			1. cd /usr/diff
				1. diff file1 file2 
				2. diff file1 file3 
				3. diff file1 file4 >> /usr/diff/answer1
			2. diff /usr/diff/diff1 /usr/diff/diff2 > /usr/diff/answer2
			3.  cat and cat of both to ensure it is correct
	25. Complete the following:
		1. Add Bob to the ACL for /usr/acl/file.txt so he can read and write to it
		2. Remove Sue from the ACL for the file
		3. Add group admin to the acl for the file with execute permissions
		4. Delete /home/delete.me
		5. Answers:
			1. Bob
				1. getfacl -a /usr/acl/file.txt
				2. setfacl -m u:Bob:rw /usr/acl/file.tt
				3. check it
			2. Sue
				1. setfacl -x u:Sue: /usr/acl/file.txt
				2. check it
			3. Group admin
				1. setfacl -m g:admin:x /usr/acl/file.txt
				2. check it
			4. delete
				1. rm -rf /home/delete.me
				2. ll /home
				3. getfacl -a /home/delete.me
				4. lsattr /home/delete.me
				5. chattr -ie /home/delete.me [cause these were the 2 that were listed under lsattr]
				6. lsattr /home/delete.me
				7. rm -rf /home/delete.me

















