- 47%;  72%; 63%; 72%
- Find and `delete` all the files which have the following octal permissions: 666
	- find /opt/assets/ -type f -perm 666 [did not work also ugo=rw]
	- https://unix.stackexchange.com/questions/31770/find-files-which-have-a-higher-permission-than-xxx
- bash script which:
	- `lists` all the files present inside `/opt/` directory, pipes this output to the `sha256sum` command and then saves the output of the `sha256sum` command in `/home/bob/binhash.txt` file.  Use the regular command to list the directory contents without any options like `long listing format, hidden files` etc. Make sure to give it executable permissions.
		- echo 'ls | sha256sum > /home/bob/binhash.txt' > /home/bob/script.sh
- cut all data before/after
	- diff dir2 dir1 | cut -d ':' -f1 [after]
	- diff dir2 dir1 | cut -d ':' -f2 [before]
- anacron job & at job (instead of crontab) - anacron job still wrong 
	- First, create an `anacron job` with the following parameters:  
		* Job will run once every `three days`.  
		* The job delay is `10 minutes`.  
		* The job identifier (name) is `exam`.  
		* The command it should run is `/opt/anacron.sh`.
		* [sudo vi /etc/anacrontab]
			* 3 10 exam /opt/anacron.sh
	* Next, create an `at` job. Schedule it to run at this exact date: `August 21 2040`. The at job should run the following command: echo 'Wow, this took a long time!' > finally.txt https://docs.oracle.com/cd/E26502_01/html/E29011/gmacc.html#sysrescron-26337
		* systemctl enable+start+status atd
		* https://phoenixnap.com/kb/linux-at-command
		* at 082140
			* echo 'Wow, this took a long time!' > finally.txt
			* press ctrl+d [will end the job and stdout]
* Find out which software package provided this file: `/usr/bin/botti` on the system and then remove [don't care about doing the centos one]
	* dpkg -S /package [not sure what the centos version is though...]
	* rpm -qf /package [also tried --whatprovides doesn't work]
	* yum remove irssi -y
* Edit `/etc/security/limits.conf` file and add `@developers - maxlogins 5` line at the end of file:
	* vi /etc/security/limits.conf
		* @developers - maxlogins 5
* Modify the following kernel runtime parameter:  `vm.swappiness`. Set a value `10` for it. This can be a temporary change, so the parameter should temporarily keep this value in the current session, but the change should be forgotten at next boot.
	* Set a value `10` for `vm.swappiness`
	* sysctl -w vm.swappiness=10
* Inspect the `httpd` service and figure out its unit file. Further, find out the `SELinux` label that it has. Save this label to this file: `/opt/label.txt`.  For example, the SELinux label for `/bin/sudo` shows up like this `system_u:object_r:sudo_exec_t:s0 /usr/bin/sudo` In that case, you would write `system_u:object_r:sudo_exec_t:s0` to that file, skipping the `/usr/bin/sudo` part. https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/selinux_users_and_administrators_guide/sect-security-enhanced_linux-working_with_selinux-selinux_contexts_labeling_files
	* systemctl status httpd
	* You will find the unit file besides `loaded` parameter, execute below given command to find out the `SELinux label`:
	* which httpd.service [will give you the relative path and file to ls -Z]
	* ls -Z /usr/lib/systemd/system/httpd.service
	* Save the required value in `/opt/label.txt` file:
	* system_u:object_r:httpd_unit_file_t:s0
* SSH into `node01` using user `bob` and password `caleston123` , further perform the following actions on it:  
	* List `all` firewall rules and save the output in `/opt/rules.txt` file. Make sure to `append` the file so that you don't overwrite any existing content of the file.  
	* Add a new firewall rule so that traffic to port `80/tcp` is `allowed` on this host. This rule should be applied immediately, for the current session. But also make this rule `permanent` so that it remains active for new sessions as well.  
		* firewall-cmd --list-all >> /opt/rules.txt
		* firewall-cmd --add-port=80/tcp --permanent
		* systemctl restart firewalld [don't forget to do this step!]
* Now, let's set up some `email aliases`: 
	* Add an email alias so that all emails sent to the user called `bob` are redirected to the user called `root`
	* Add another email alias so that all emails sent to the user called `john` are redirected to an external email address: `john@example.com`
		* vi /etc/aliases
			* bob:root
			* john: john@example.com
			* newaliases [don't forget to do this step!]
* SSH into `node01` host using user `bob` and password `caleston123` . You'll need to make some changes to the configuration of the `SSH daemon` (not the client). https://www.thegeekstuff.com/2011/05/openssh-options/
	* First, disable the SSH root user login.
		* vi /etc/ssh/sshd_config
			* PermitRootLogin yes [change yes to no]
	* Next, make sure the `login grace time` is changed from the default `2 minutes` to `1 minute`.
		* in same file as above sshd_config
			* LoginGraceTime 2m [change the 2 to 1, save and exit]
	* Don't forget to `log out` from this system when you finish this exercise.
* Edit the `main config` file of the `httpd` daemon and make sure that `Indexes` are `disabled` for the `/var/www/html/`directory.
	* vi /etc/httpd/conf/httpd.conf
		* comment out <Directory "/var/www/html">
		* systemctl restart httpd [don't forget to do this step!]
* List all `VMs` that exist on this host. Your VM is currently stopped so it won't show up in the regular command that lists virtual machines. Make sure to add the correct option to list `all` VMs, even the ones that are not currently running.
	* Start this `virtual machine`.
		* virsh list [could also try 'vmrun list']
		* virsh start [vmname]
* create partitions
	* Create a partition `/dev/vdb1` of `400MB` in size and format it as `xfs` file system. Edit the correct file in `/etc`/ so that `/dev/vdb1` is automatically mounted into the `/backups` directory every time the system boots up. `Default` mount options should be used.
		* fdisk /dev/vdb - n,p,1, ,+400M, p, w
		* mkfs.xfs /dev/vdb1
		* mount /dev/vdb1 /backups/ 
		* blkid /dev/vdb1
		* vi /etc/fstab [uuid /backups xfs defaults 0 0]
	* Create a partition `/dev/vdb2` of `100MB` in size, format it as `ext4` file system and mount it in `/mnt/` . We want to keep some sensitive data on `ext4` filesystem and we want to make sure that it's not modified. To solve this problem, mount `/dev/vdb2` into the `/mnt` directory using `read-only` mount option. It does not matter what the other mount options are. Just make sure this mount point is `read-only` so that users cannot change contents on this filesystem.
		* fdisk /dev/vdb - n,p,2, ,+100M, p, w
		* mkfs.ext4 /dev/vdb2
		* mount -o ro /dev/vdb2 /mnt
		* is this meant to be persistently mounted? if so see above last 2 steps
	* Create a partition `/dev/vdb3` of `450MB` in size and format it with the `xfs` filesystem. To make this easier to spot in the future, among the other filesystems, set the `filesystem label` to `ExamFS` when you format it. Make sure that the label is exactly `ExamFS` and not `examfs` or anything that has different letters in UPPERCASE or lowercase. We will make use of this `/dev/vdb3` partition in the upcoming questions so create it before moving to the next question. https://linuxconfig.org/how-to-name-label-a-partition-or-volume-on-linux
		* fdisk /dev/vdb3 - n,p,3, ,+450M, p, w
		* mkfs.xfs /dev/vdb3 -L "ExamFS" [e2label /dev/vdb3 "ExamFS"]
		* 
* Create a `mirrored (level 1)` RAID array with these two devices: `/dev/vdc` and `/dev/vdd`. The array should be created at `/dev/md0`
	* mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/vdc /dev/vdd
* Edit the `disk quota` for the user called `bob`. Limit the amount of `storage space` he can use (not inodes). Set a `soft limit` of `100MB` and a `hard limit` of `500MB` on `/mydata` partition. https://www.linuxtechi.com/enable-user-group-disk-quota-on-centos-7-rhel-7/
	* edquota -u [username]
		* edquota -u bob 
			* /mydata 0 100 500 
	* edquota -g [groupname]
	* xfs_quota -x -c limit bsoft=100m bhard=500m bob [they don't want you to use the above command, you have to do it this way.  The above command did work for me, I confirmed the change, however still marked incorrect]