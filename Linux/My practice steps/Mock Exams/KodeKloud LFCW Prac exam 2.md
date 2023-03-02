- Find and `delete` all the files which have the following octal permissions: 666
	- find /opt/assets/ -type f -perm 666 [did not work also ugo=rw]
	- https://unix.stackexchange.com/questions/31770/find-files-which-have-a-higher-permission-than-xxx
- bash script which: incorrect need to verify the script ???
	- `lists` all the files present inside `/opt/` directory, pipes this output to the `sha256sum` command and then saves the output of the `sha256sum` command in `/home/bob/binhash.txt` file.  Use the regular command to list the directory contents without any options like `long listing format, hidden files` etc. Make sure to give it executable permissions.
		- echo 'ls | sha256sum > /home/bob/binhash.txt' > /home/bob/script.sh
- cut all data before/after
	- diff dir2 dir1 | cut -d ':' -f1 [after]
	- diff dir2 dir1 | cut -d ':' -f2 [before]
- anacron job & at job (instead of crontab)
	- First, create an `anacron job` with the following parameters:  
		* Job will run once every `three days`.  
		* The job delay is `10 minutes`.  
		* The job identifier (name) is `exam`.  
		* The command it should run is `/opt/anacron.sh`.
		* vi /var/spool/anacron/cron.daily
			* @daily/3 10 exam /opt/anacron.sh
		* [sudo vi /etc/anacrontab]
			* 3 10 exam /opt/anacron.sh
	* Next, create an `at` job. Schedule it to run at this exact date: `August 21 2040`. The at job should run the following command: echo 'Wow, this took a long time!' > finally.txt
		* systemctl enable+start+status atd
		* https://phoenixnap.com/kb/linux-at-command
		* at 082140
			* echo 'Wow, this took a long time!' > finally.txt
	* Find out which software package provided this file: `/usr/bin/botti` on the system and then remove [don't care about doing the centos one]
		* dpkg -S /package [not sure what the centos version is though...]
		* rpm -qf /package [also tried --whatprovides doesn't work]
			* yum remove irssi -y
	* Edit `/etc/security/limits.conf` file and add `@developers - maxlogins 5` line at the end of file:
		* vi /etc/security/limits.conf
	* Modify the following kernel runtime parameter:  `vm.swappiness`. Set a value `10` for it. This can be a temporary change, so the parameter should temporarily keep this value in the current session, but the change should be forgotten at next boot.
		* Set a value `10` for `vm.swappiness`
		* sysctl -w vm.swappiness=10
	* Inspect the `httpd` service and figure out its unit file. Further, find out the `SELinux` label that it has. Save this label to this file: `/opt/label.txt`.  For example, the SELinux label for `/bin/sudo` shows up like this `system_u:object_r:sudo_exec_t:s0 /usr/bin/sudo` In that case, you would write `system_u:object_r:sudo_exec_t:s0` to that file, skipping the `/usr/bin/sudo` part.
		* systemctl status httpd
		* You will find the unit file besides `loaded` parameter, execute below given command to find out the `SELinux label`:
			* ls -Z /usr/lib/systemd/system/httpd.service
		* Save the required value in `/opt/label.txt` file:
			* system_u:object_r:httpd_unit_file_t:s
	* SSH into `node01` using user `bob` and password `caleston123` , further perform the following actions on it:  
		* List `all` firewall rules and save the output in `/opt/rules.txt` file. Make sure to `append` the file so that you don't overwrite any existing content of the file.  
  

**B.** `Add` a new firewall rule so that traffic to port `80/tcp` is `allowed` on this host. This rule should be applied immediately, for the current session. But also make this rule `permanent` so that it remains active for new sessions as well.  
fiewall-cmd --list-all >> /opt/rules.txt
firewall-cmd --add-port=80/tcp --permanent
systemctl restart firewalld

  

Don't forget to `log out` from this system when you finish this exercise.
	* List `all` firewall rules and save the output in `/opt/rules.txt` file. Make sure to `append` the file so that you don't overwrite any existing content of the file.  `Add` a new firewall rule so that traffic to port `80/tcp` is `allowed` on this host. This rule should be applied immediately, for the current session. But also make this rule `permanent` so that it remains active for new sessions as well. Don't forget to `log out` from this system when you finish this exercise.
	* Now, let's set up some `email aliases`: 
		* Add an email alias so that all emails sent to the user called `bob` are redirected to the user called `root`
		* Add another email alias so that all emails sent to the user called `john` are redirected to an external email address: `john@example.com`
		* vi /etc/aliases
			* john: john@example.com
			* newaliases
	* SSH into `node01` host using user `bob` and password `caleston123` . You'll need to make some changes to the configuration of the `SSH daemon` (not the client).
		* First, disable the SSH root user login.
		* Next, make sure the `login grace time` is changed from the default `2 minutes` to `1 minute`.
		* Don't forget to `log out` from this system when you finish this exercise.
	* Edit the `main config` file of the `httpd` daemon and make sure that `Indexes` are `disabled` for the `/var/www/html/`directory.
		* vi /etc/httpd/conf/httpd.conf
			* comment out <Directory "/var/www/html">
	* List all `VMs` that exist on this host. Your VM is currently stopped so it won't show up in the regular command that lists virtual machines. Make sure to add the correct option to list `all` VMs, even the ones that are not currently running.
		* Start this `virtual machine`.
	* create partitions
		* Create a partition `/dev/vdb1` of `400MB` in size and format it as `xfs` file system. Edit the correct file in `/etc`/ so that `/dev/vdb1` is automatically mounted into the `/backups` directory every time the system boots up. `Default` mount options should be used.
			* fdisk /dev/vdb - n,p,1, ,+400M, p, w
			* mkfs.xfs /dev/vdb1
			* mount /dev/vdb1 /backups/ 
			* blkid /dev/vdb1
			* vi /etc/fstab [uuid /backups xfs defaults 0 0]
		* Create a partition `/dev/vdb2` of `100MB` in size, format it as `ext4` file system and mount it in `/mnt/` . We want to keep some sensitive data on `ext4` filesystem and we want to make sure that it's not modified. To solve this problem, mount `/dev/vdb2` into the `/mnt` directory using `read-only` mount option. It does not matter what the other mount options are. Just make sure this mount point is `read-only` so that users cannot change contents on this filesystem.
		* Create a partition `/dev/vdb3` of `450MB` in size and format it with the `xfs` filesystem. To make this easier to spot in the future, among the other filesystems, set the `filesystem label` to `ExamFS` when you format it. Make sure that the label is exactly `ExamFS` and not `examfs` or anything that has different letters in UPPERCASE or lowercase. We will make use of this `/dev/vdb3` partition in the upcoming questions so create it before moving to the next question.
	* Create a `mirrored (level 1)` RAID array with these two devices: `/dev/vdc` and `/dev/vdd`. The array should be created at `/dev/md0`
	* Edit the `disk quota` for the user called `bob`. Limit the amount of `storage space` he can use (not inodes). Set a `soft limit` of `100MB` and a `hard limit` of `500MB` on `/mydata` partition.