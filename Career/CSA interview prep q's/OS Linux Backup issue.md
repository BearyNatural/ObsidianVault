Preparation topics for candidates who are selected for loops: Cloud Support Associate. 


OS: 
· OS boot process (Linux) https://kumo-knowledge-ui-iad-prod.amazon.com/view/article_30921 https://www.geeksforgeeks.org/how-linux-kernel-boots/
	- Bios/UEFI - Brain - low level software that initialises before the boot of os starts. i.e. motherboard [UEFI is used if adanced required for intel or amd]
	- Memory level - MBR/GPT - master boot record/guid partition table; GPT is more versatile as you can have more than 4 partitions on each dish & on disks greater than 2 terabytes;
	- Grub - loads linux kernel and configuration files
	- Kernel - executes /sbin/init Kernel Initialization and Boot Options:
			1.  CPU examination
			2.  Memory examination
			3.  Device bus discovery
			4.  Device discovery
			5.  Auxiliary kernel system setup
			6.  Root filesystem mount
			7.  Userspace begin
	- Init - executes system boot & fstab
	- Runlevel - 7 run levels 0 - 7 
		- 0 – System halt _i.e_ the system can be safely powered off with no activity.
		-   1 – Single user mode.
		-   2 – Multiple user mode with no NFS(network file system).
		-   3 – Multiple user mode under the command line interface and not under the graphical user interface.
		-   4 – User-definable.
		-   5 – Multiple user mode under GUI (graphical user interface) and this is the standard runlevel for most of the LINUX based systems.
		-   6 – Reboot which is used to restart the system.
	- Bootprocess failures
		- no bootloader screen
			- cause 
				- check for GRUB misconfiguration or 
				- a corrupt boot sector.  
			- fix
				- Bootloader re-install needed?
		- Kernel fails to load
			- cause 
				- most likely misconfigured or 
				- corrupt kernel or 
				- incorrect kernel boot parameters in the GRUB conf file.
			- if it has previously booted successfully in the past either 
				- it has corrupted or 
				- bad parameters have been applied;
			- fixes
				- re-install the kernel;
				- enter into interactive GRUB menu at boot;
				- try re-booting into a rescue image;
		- Kernel loads but fails to mount the root filesystem
			- cause
				- misconfigured GRUB config file
				- misconfigured /etc/fstab
				- no support for the root fs type build into the kernel or in the initramfs image
		- Failure during the init process
			- cause
				- many things could go wrong here
					- corrupted fs
					- startup script errrors, etc
				- see messages that are displayed before things stop
			- fix
				- try booting at a lower runlevel such as 3 (no graphics) or 1 (single user)
· Memory management; Memory pages; Buffer and Caches, Basic commands 
	- free, swap, top, vmstat, pmap
	- /proc/sys/vm & /proc/meminfo
	- sudo dmesg for seeing the audit trail - kernel related messages good if there is a crash see what caused it;
· System date/time management, network time protocol 
	- timedatectl 
· Managing Users and groups 
	- useradd, userdel, id, groupmod; groupadd; etc;
	- chgrp, chmod, chown;
· File permissions RWX
	- chown, chmod, umask, 
	- chmod - change permissions for files and folders that already exist!  
		- parameters - owner, group & others  
		- Set the default permission of file to 622 (666-622=044) and directory to 733 (777-733=044)  
	- umask - changes the default permissions and thus the permissions for all newly created files and folders  
		- octal version inverted chmod
	- If a directory is readable, writable, and executable by the owner, a selected group of users, and everyone on the system, its octal permission is 777. **If a file is readable and writable by the owner, a selected group of users, and everyone on the system, its octal permission is 666**.
· Managing software’s - installation, uninstallation, upgrade etc. 
	- sudo apt update
	- sudo apt upgrade -y
	- sudo apt autoremove -y
	- sudo apt autoremove [packagename]
· Managing system services and background processes 
· Remote management of a system - SSH, RDP etc. 
	- secure shell protocol login
		- ssh-keygen - generates private and public encryption keys; private key don't share; public key cp to machine you want to permit password-less access; ssh [username]@localhost
		- cat authorized_keys - holds all the public keys
		- cat known_hosts - contains only info about computer nodes it detects changes in the users who are tying to log in;
		- pssh - parallel ssh used to execute a command on multiple systems at one time;
· Network protocols - FTP, HTTP (web servers), SMTP (mail server) 
· System automation - cron, batch jobs, windows startup tasks 
· **Linux commands** - 20 common commands **cat**, **chgrp**, **chmod**, **chown**, **cp**, **date**, **dd**, **df**, **dmesg**, **echo**, **false**, **hostname**, **kill**, **ln**, **login**, **ls**, **mkdir**, **mknod**, **more**, **mount**, **mv**, **ps**, **pwd**, **rm**, **rmdir**, **sed**, **sh**, **stty**, **su**, **sync**, **true**, **umount** and **uname**
	- ls or ll - list files and directories in a directory (ll is short version if aliased)
	- cd - change directory, used to move around directories
	- uname - system information (-a) for all info 
	- apt (dpkg for lower level) - package management system - Advanced Packaging Tool
			- apt install -y (installs packages and the -y for scripting)
			- apt update - downloads package information do this before upgrade command
			- apt upgrade - upgrades existing packages does not install new packages
			- apt autoremove - gets rid of any old packages not needed anymore
			- apt clean - cleans out cache files and any archived package files that have been installed;
		- apt-cache or apt-file - queries the package cache of the apt
			- apt-cache akgnames | grep (packetname)
		- dpkg -S [package name i.e. logrotate] find out what package the file belongs to
		- dpkg - L [package name] list info about the package
		- dpkg -V [package name] verify the package installation
		- sudo dpkg -r [package name] to remove the package
	- cp - copy the source
	- mv - move the source
	- rm - remove or delete
	- mkdir - make or create directory
	- rmdir - remove or delete directory
	- chown - change ownership
	- chgrp - change group ownership
	- vm control commands/tools
		- cgroups; nice; numactl;
	- chmod - change permissions for files and folders that already exist!
		- parameters - owner, group & others
		- Set the default permission of file to 622 (666-622=044) and directory to 733 (777-733=044)
	- umask - octal form; changes the default permissions and thus the permissions for all newly created files and folders; umask -S - symbolic form;
		- octal version inverted chmod
	- getfacl - filesystem acls (access control lists)
	- setfacl - to change the filesystem acls
	- ulimit - displays or resets process resource limits; -a gives us all current limits;
	- date - displays date & time set on your device
	- tar - compression
	- cat - display/view contents of file 'concatenate'
	- less - displays the contents of a file or a command output, one page at a time
	- ssh - secure shell protocol login
		- ssh-keygen - generates private and public encryption keys; private key don't share; public key cp to machine you want to permit password-less access; ssh [username]@localhost
		- cat authorized_keys - holds all the public keys
		- cat known_hosts - contains only info about computer nodes it detects changes in the users who are tying to log in;
		- pssh - parallel ssh used to execute a command on multiple systems at one time;
	- editor commands i.e. vi, vim, nano etc
	- Manipulating text 
		- scp - secure copy
		- grep - search - grep [username] /etc/passwd /etc/group
		- diff - compares 2 files or directories - -y for side by side viewing
	- File utilities
		- locate/find - find files, directories, etc
		- du - disk usage, reports files' and directories' disk usage
		- df - disk filesystem, displays the amount of disk space available on the filesystem with each file name's argument
		- partitions 
			- fdisk; blkid; lsblk;
	- Users & passwords:
		- useradd - useradd -m(creates home dir) -c "Full Name" -s /bin/bash [username]
		- userdel - userdel -r(removes home dir) [username]
		- passwd - passwd [username]
		- chage - to view & change the user password expiry info
		- groupadd; groupmod; groupdel; usermod -a
	- SuperUser:
		- sudo -i; su;
	- clear - clears the screen (shortcut is crtl+l)
	- Virtualisation
		- podman - not working best on vmbox
			- systemctl start/stop/status podman.socket
			- podman --help
		- docker using this one
			- systemctl start/stop/status docker
			- 
· Linux package management 3 different types:
	- Debian/Ubuntu
	- Red Hat/Fedora/Centos
	- OpenSuse/suse
	- ![[Pasted image 20230123131532.png]]
· Linux Standard Directory Tree - Main Directories
	- /root; 
	- /bin executable programs that must be available in single user mode; 
	- /boot boot system incl kernel, init; 
	- /dev Device nodes that interact with hardware and software devices;
	- /etc system wide configuration files;
	- /home user home directories incl personal files and folders;
	- /lib libraries required by executable binaries in /bin & /sbin
	- /lib64 SAA but for 64-bit libraries
	- /media mounting points for removable media such as cd, dvd, usb;
	- /mnt temporarily mounted filesystems;
	- /usr files not needed for system booting i.e software, games, etc;
	- /proc variable or volatile data files that frequently change during system operation i.e. logs, admin files, cache contents;
	- /msc miscellaneous data
	- /run transient files i.e. runtime info, system startup, etc;
	- 
	- ![[Pasted image 20230124104604.png]]
- LDAP - lightweight directory access protocol i.e. provides directory services i.e. phonebook via the ip protocol
	- single sign on & identity management solutions
	- ldap provides authentication and authorisation data
to find out your ip address in the cli:
	sudo lynx -dump http://whatismyip.akamai.com | awk '{print $1}'


Troubleshooting: 
· System performance - CPU, DISK, memory and network 
· System Login issues 
· System booting issues 
· System logs 
· Network connectivity issues



