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
3. SAMPLE EXAM:
	1. 
		1. Answer: 
			1. a
	2. 
		1. Answer: 
			1. 
	3. .
		1. Answer: 
			1. .
	4. 
		1. Answer: 
			1. .
	5. .
		1. Answer: 
			1. .
	6.  .
		1. Answer: 
			1. .
	7.  .
		1. Answer: 
			1. .
	8.  .
		1. Answer: 
			1. .
	9.  .
		1. Answer: 
			1. .
	10.  .
		1. Answer: 
			1. .
	11.  .
		1. Answer: 
			1. .
	12.  .
		1. Answer: 
			1. .
	13. .
		1. Answer: 
			1. .
	14. .
		1. Answer: 
			1. .
	15. .
		1. Answer: 
			1. .
	16. .
		1. Answer: 
			1. .
	17. .
		1. Answer: 
			1. .
	18. .
		1. Answer: 
			1. .
	19. .
		1. Answer: 
			1. .
	20. .
		1. Answer: 
			1. .
	21. .
		1. Answer: 
			1. .
	22. .
		1. Answer: 
			1. .
	23. .
		1. Answer: 
			1. .
	24. .
		1. Answer: 
			1. .
- Linux Foundation Prac Exam: run the setup.sh
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
		2. Create a volume group name ‘vg01’ from the two partitions
		3. Create a logical volume named ‘lv01’ with the following attributes
			1. 2GB of storage from vg01
			2. Format it with the ext3 file system
			3. Give it a label ‘lv01’
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
				10. https://www.linuxbabe.com/desktop-linux/how-to-automount-file-systems-on-linux
	8. Automating routine system tasks using bash scripts can help system administrators complete routine tasks.  Write and run bash script to complete the following system exercises:
		1. Create 2 files in a new directory called ‘manuals’ located in your home directory
			1. Name the first file ‘sed-info’ and redirect the output of the ‘sed’ command man page to the contents of the file
			2. Name the second file ‘grep-info’ and redirect the output of the ‘grep’ command man page to the contents of the file.
		2. Archive and compress the contents of the newly created ‘manuals’ directory using the xz compression tool
		3. decompress the file in the /usr/archive
		4. Move the back up file to /usr/backups
		5. Ensure to clean up any old backup files
	9. System administrotrs need to often setup and maintain network connectivity between machines withing the business.  SSH to exam-1 and complete the following network changes to meet the requirements:  NOTE: if your virtual machine running in the cloud you may not be able to update these values; however you can review the file(s) and proccesses.
		1. Configure your Linux machine with a static networking configuration
		2. After you have set up static networking, add a secondary DNS server at the address of 8.8.8.8
		3. Find a list of current nameservers for the system and redirect the output to a file called ‘dnsservice’ located in /srv/dns
		4. Find the hostname and IP address of your machine and append the output to a file named dns-service located in /srv/dns
	10. System administrators will often have to diagnose and fix disks on Linux machines.  The disk where /mnt/backup is mounted is not working. Repair the disk and verify it will be automatically mounted upon reboots.  NOTE: This question is hard to simulate; however, you can run the corrisponding commands on a working disk and see the outputs.
	11. Setting up redundencies amoung disks is often an important taks that system administrators must complete.  Create a RAID 1 device named md0 using 2 disk devices of 1GB each and complete the following:  NOTE: You will have to add additional disks to do this on your VM. The names may differ than what is shown from my lsblk command
		1. Put a ext4 file system on it with the label of ‘md0’
		2. Add a spare disk of 1GB
		3. Mount to /raid
		4. Save the configuration and write the configuration file to /etc/mdadm/mdadm.conf
		5. make it persistant
	12. Managing groups and group permissions is an important task for system administrators:  Perform the following actions:
		1. Make the following groups:
			1. employees
			2. contractors
		2. Make a new directory called /srv/admin
		3. Give the group administrators full access (read/write/execute) to /srv/admins
		4. Give the group admin the same rights/privileges as root and allow members of the group to run all commands without a password prompt.
		5. Create a directory /data/list and then create a file ‘list-info’. Redirect the output of the ‘ls’ manual page into the contents of the file.
	13. Managing users is an important task of a Linux system administrator.  Perform the following actions (read section as some steps can be combined):
		1. Create the following users:
			1. linuxbro
			2. gharrison
			3. jlennon
			4. pmccartney
			5. rstarr
		2. Make linuxbro’s primary group admin
		3. Make linuxbro’s default shell zsh
		4. Make a comment for the account linuxbro stating the user’s full name of “Linux Broman”
		5. Make the accounts for jlennon and rstarr expire two years from today’s date
		6. Add accounts jlennon and rstarr to the contractors group
		7. Add accounts gharrison and pmccartney to the employees group
		8. Ensure each user has a folder in their home directory called ‘welcome-info’
		9. Set each account’s password to [‘Pa$$w0rd’] and make them change it on next login
	14. The cron.d service is often used to run system scripts on a regular basis.  Create a series of scheduled tasks:
		1. Run the system-info script every day at 6am, 9am, 12pm, 3pm, and 6pm (except Saturday and Sundays).
		2. Run the system-info script on January 9th at 11:01pm
		3. run the system-info script in the first 10 minutes of the hours 14 and 15 on the 4th day of jan feb and april, monday through friday
		4. Run the system-info script every 3 months at 12:01am
	15. Find all of the the files in /home/example:
		1. that are not owned by Sue and write them to a file /home/example/answer1 overriding anything that is currently there
		2. that have the suid enabled and append them to a file /home/example/answer2
		3. that are 126MB in size and append them to a file /home/example/answer3
		4. that are larger than 400kb and write them to a file /home/example/answer4 overriding anything that is currently there
		5. that have a .tar extention and haven't been accessed in more than 30 days
	16. User 'Bob' recieved several error messages while trying to run commands as root this morning.  NOTE: You can nu to Bob and run some root commands to generate this log activity.
		1. Search the log viles in /var/log and write any errors pertaining to this to /usr/log/root.error
	17. Find the apt package which owns the library file /usr/lib/NetworkManager/conf.d/10-slaves-order.conf and append the output to /rpm/rpm-data.  Find the last 5 rpm packages installed and append them to /rpm/rpm-data.
	18. Open the file under /home/student/textreferences/editme.txt and complete the following tasks:  NOTE: I'm sharing the exact keystrokes I use in vim to accomplish this. Keep in mind with copy paste, vim, and your imagination there are many ways to do this.
		1. Move line 7777 to line 1.
		2. Remove line 7000.
		3. Replace every occurrence of the word Earth shown with an uppercase E, with the word Globe.
		4. Add a new line at the very end of the document that contains Auctores Varii
	19. Manipulating services running on a system can be a very important task for system administrators.  There is a service named apache2 running on a system:  NOTE this is difficult to simulate the way the LFCS asks it, but these steps can be performed on sshd to see the commands in action
		1. figure out which port apache2 is listening on
		2. edit the config file for apache2 to listen on another port, 99
		3. start apache2
		4. send a SIGHUP signal to apache2
		5. write the list of all files foo has open to /usr/service/foo.txt
	20. Running scripts and manipulating their outputs is an important skill to understand as a system administrator.
		1. run the sript at /usr/bin/samplescript.sh and append the standard out to the file at /usr/script/sampleone.txt
		2. run the script at /usr/bin/samplescript2.sh and override the contents of the file at /usr/script/sampletwo.txt with the standard error
		3. run the script at /usr/bin/samplescript.sh and use the standard out and standard error as a standard in for script /usr/bin/samplescript2.sh
		4. append the standarrd out of this to /usr/script/samplethree.txt
	21. Performing backup, compression, and clean up are all important tasks for Linux System Administrators.  Perform the following tasks to demonstrate your ability to work with archives and compressed files:
		1. create 3 blank files in your home directory and perform the following
		2. Extract all files from archive file /opt/SAMPLE001.zip into target directory /opt/SAMPLE001
		3. Create a tar archive file /opt/SAMPLE0001.tar containing all files in the directory /opt/SAMPLE001
		4. Compress the tar archive file /opt/SAMPLE0001.tar using the bzip2 compression algorithm
		5. Compress the tar archive file /opt/SAMPLE0001.tar using the xz compression algorithm
			1. Make sure that the uncompressed archive file /opt/SAMPLE0001.tar is not removed after creating the compressed versions of the archive file!
	22. Being able to quickly search files is an important task for system administrators.  Search the file /usr/sample/example.txt for the follwoing and write them to file.txt:
		1. all lines that end with the word linux
		2. all lines that start with the word Linux
		3. all lines with Linux and yay both in them.
		4. lines that contain linux or yay in them.
	23. Create a 1GB SWAP file and add it to the exiting SWAP pool. Ensure it is mounted at boot.  NOTE: understand the difference between Swap file and swap partition and be able to complete the above with both.
	24. Identifying the difference between files and directories is a common system administrator task.  
		1. Find which files in /usr/diff/ is different and write the file name to a file /usr/diff/answer1
		2. Find all of the files that are in /usr/diff/diff1 but not in /usr/diff/diff2 and write them to /usr/diff/answer2
	25. Complete the following:
		1. Add Bob to the ACL for /usr/acl/file.txt so he can read and write to it
		2. Remove Sue from the ACL for the file
		3. Add group admin to the acl for the file with execute permissions
		4. Delete /home/delete.me
	26. 

















