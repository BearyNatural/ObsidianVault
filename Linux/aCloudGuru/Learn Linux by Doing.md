CH 1,
find / -type fdc -iname '.txt' -user [root]
ls -l /etc/
locate -i [command]

CH 2, LAB 1
`sudo -i`

Add the Users to the Server
To add users to the system we can run
`useradd <username>`

So we would run
`useradd tstark`
`useradd cdanvers`
`useradd dprince`

Create the `superhero` Group
To create a new group we would run
`groupadd <groupname>`

So for this task
`groupadd superhero`

Set `wheel` Group as the the `tstark` Account's Primary Group
For this task we would run `usermod` like this
`usermod -g wheel tstark`

Add `superhero` as a Supplementary Group on All Three Users
There isn't an easy way to do this all at once, so we need to run the following command for each user
`usermod -aG superhero <username>`
So
`usermod -aG superhero tstark`
`usermod -aG superhero dprince`
`usermod -aG superhero cdanvers`

Lock the `dprince` Account
To lock an account all we have to do is run:
`usermod -L dprince`


CH 2, LAB 2

Create two new users.
Create two new users on the system, and assign the `avance` user to the `wheel` supplemental group:
`sudo useradd -m gfreeman sudo useradd -G wheel -m avance`
Set the password for both accounts to `LASudo321`:
`sudo passwd gfreeman sudo passwd avance`
Verify the `/etc/sudoers` file and test access.
Using the `visudo` command, verify that the `/etc/sudoers` file will allow the `wheel` group access to run all commands with `sudo`. There should not be a comment (`#`) on this line of the file:
`%wheel ALL=(ALL) ALL`
From the `cloud_user` login, use the `su` (substitute user) command to switch to the `avance` account, and use the dash (`-`) to utilize a login shell:
`sudo su - avance`
As the `avance` user, attempt to read the `/etc/shadow` file at the console:
`cat /etc/shadow`
As a regular user, `avance` does not have sufficient privileges to do so. Rerun the command with the `sudo` command:
`sudo cat /etc/shadow`
After you have verified that `avance` can read the `/etc/shadow` file, log out of that account:
`exit`
Set up the web administrator.
Now we need to configure `gfreeman`'s account to have the ability to restart or reload the web server when needed. Since he will be the webmaster, he needs `sudo` permissions to restart the service.
First, create a new `sudoers` file in the `/etc/sudoers.d` directory that will contain a standalone entry for webmasters. Use the `-f` option with the `visudo` command to create this new file:
`sudo visudo -f /etc/sudoers.d/web_admin`
Enter in the following at the top of the file. This will create an alias command group that we can apply to any user or group that we add to this file. This group of commands will contain the necessary commands for restarting or reloading the web server:
`Cmnd_Alias WEB = /bin/systemctl restart httpd.service, /bin/systemctl reload httpd.service`
Add another line in the file for `gfreeman` to be able to use the `sudo` command in conjunction with any commands listed in the WEB alias:
`gfreeman ALL=WEB`
Save and close the file.    
Next, log into the `gfreeman` account:    
`sudo su - gfreeman`
Attempt to restart the web service:
`sudo systemctl restart httpd.service`
Now `gfreeman` can restart the web server. As the `gfreeman` user, try to read the new `web_admin sudoers` file with the `sudo` command:
`sudo cat /etc/sudoers.d/web_admin`
Since the `cat` command is not listed in the command alias group for WEB, `gfreeman` cannot use `sudo` to read this file.


CH 2, LAB 3

Enable SSH to Connect Without a Password from the `dev` User on `server1` to the `dev` User on `server2`
We need to use SSH keys to satisfy this requirement, so generate them with this:
`[dev@server1]$ ssh-keygen`
Then run:
`[dev@server1]$ ssh-copy-id <server2 IP>`

Copy All tar Files from `/home/dev/` on `server1` to `/home/dev/` on `server2`, Extract Them, and Redirect Output to `/home/dev/tar-output.log`
We need to use a method of copying files over a network. `scp` is the best tool, like this:
`[dev@server1]$ scp *.gz <server2 IP>:~/`
Then connect to `server2` using `ssh`:
`[dev@server1]$ ssh <server2_IP>`
Then we can extract the files:
`[dev@server2]$ tar -xvf deploy_content.tar.gz >> tar-output.log`
`[dev@server2]$ tar -xvf deploy_script.tar.gz >> tar-output.log`
Make sure to use `>>`, so that the output is appended rather than overwritten.

Set the Umask So That New Files Are Only Readable and Writeable by the Owner
The task is asking to make new files with the following permission: `0600`.
So we can do subtraction to figure out what our umask should be.
`0666` <-- Default
`0600` <-- Desired
`----`
`0066` <-- What we need to set
So we run:
`[dev@server2]$ umask 0066`

Verify the `/home/dev/deploy.sh` Script Is Executable and Run It
First, we check permissions on `deploy.sh`:
`[dev@server2]$ ls -l deploy.sh`
There's no execute bit. Let's add one:
`[dev@server2]$ chmod +x deploy.sh`
And then run it:
`[dev@server2]$ ./deploy.sh`


CH 3, LAB 1

Check the default target
**Note:** If you have an issue connecting to the instance, wait a minute or two to allow the instance to finish provisioning and retry.
The current default target is set to multi-user.target. Use the appropriate command to verify this:
`systemctl get-default`

Change the default target
The administrator will need to change the default target so that the computer boots into a graphical desktop:
`sudo systemctl set-default graphical.target`

Check the Default Target again
## Check the Default Target again
Now verify that the system is set for a graphical boot:
systemctl get-default


CH 3, LAB 2

sudo -i
Create a Service Timer Unit File
Follow the scenario to create the appropriate timer unit file.
- web-backup.service:
[[Unit]
Description=Backup the web site, every day, or the boss will be mad

[Service]
Type=simple
ExecStart=/usr/local/sbin/web-backup.sh

[Install]
WantedBy=multi-user.target]
- anaconda-ks.cfg
- web-backup.sh
[#!/bin/bash

DATE=$9date "+%d")

/bin/tar -czf /root/site-backup-$DATE.tar.gz /var/www/html]
- web-backup.timer:
[`[Unit] 
Description=Fire off the backup 

[Timer] 
OnCalendar=*-*-* 23:00:00 Persistent=true Unit=web-backup.service 

[Install] 
WantedBy=multi-user.target`]

Putting Files Where They Belong
Copy the service and timer files and the shell script into the correct locations.
`cp web-backup.sh /usr/local/sbin/`
`cp web-backup.{service,timer} /etc/systemd/system/`

Run the Custom Service
Once the backup service has been created successfully from the scenario, make sure it is running so the backup will happen as scheduled.
`systemctl enable web-backup.service`
`systemctl enable web-backup.timer`
`chmod +x /usr/local/sbin/web-backup.sh`
`systemctl start web-backup.timer web-backup.service`
`systemctl status web-backup.timer`
`systemctl status web-backup.service`


CH 3, LAB 3

Check the Web Server Configuration File
The Apache website's default configuration file is missing. Once this task is completed, the service will start as expected.

Verify That the Web Server Service Is Running
Once the configuration issue is resolved, make sure the appropriate service is running.

## Connecting to the Lab
1.  Open your terminal application, and run the following command. (Remember to replace `<PUBLIC_IP>` with the public IP you were provided on the lab instructions page.)
`ssh cloud_user@&lt;PUBLIC_IP&gt;`
1.  Enter your password at the prompt.
## Check the Web Server Configuration File
1.  Change to the root account.
`sudo su -`
1.  Check the status of the web service.
`systemctl status httpd.service`
1.  Attempt to start the web service.
`systemctl start httpd.service`
1.  After the service fails to start, check the journal.
`journalctl -u httpd.service`
1.  Check the directory where the httpd configuration file should be.
`ls /etc/httpd/conf`
1.  Restore the original httpd configuration file.
`mv /etc/httpd/conf/httpd.conf.bkup /etc/httpd/conf/httpd.conf`
1.  Restart the service.
`systemctl restart httpd.service`

## Verify That the Web Server Service Is Running
1.  Check the status of the service.
`systemctl status httpd.service`
1.  Navigate to the local web page.
`elinks http://localhost`


CH 4, LAB 1
Create the SSH Keys on Server 1 and Server 2.
1.  Generate a new key on `server 1`.
    `ssh-keygen`
2.  Generate a new key on `server 2`.
    `ssh-keygen`
Exchange the Keys between Server 1 and Server 2.

The student will need to exchange the `cloud_user` service account keys created previously with the matching account to and from `SERVER ONE` and `SERVER TWO`.
1.  Copy the contents of `id_rsa.pub` to the clipboard.
2.  Connect to `server 2`.
3.  Append the public key to the `authorized_keys` file.
4.  Generate a new key on `server 2`.
5.  Copy the contents of the `id_rsa.pub` to the clipboard.
6.  Connect back to `server 1`.
7.  Append the public key to the `authorized_keys` file.

## Create the SSH Keys on Server 1 and Server 2
### Create the Key on Server 1
1.  In your terminal, log in to Server 1.
`ssh cloud_user@&lt;SERVER1_PUBLIC_IP&gt;`
1.  List the contents of the current directory.
`ls -la`
1.  Change to the `.ssh` directory.
`cd .ssh`
1.  List the contents of the `.ssh` directory.
`ls -la`
1.  Generate a key for Server 1.
`ssh-keygen`
1.  Press **Enter** at the next three prompts.
2.  List the contents of the `.ssh` directory again.
`ls -la`
1.  List the contents of the `id_rsa.pub` file.
`cat id_rsa.pub`
1.  Copy the output of this command to your clipboard.
2. `cp id_rsa.pub cloud_user@IP`
3. ```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@host```

### Create the Key on Server 2
1.  Log in to Server 2.
`ssh cloud_user@&lt;SERVER2_PUBLIC_IP&gt;`
1.  Change to the `.ssh` directory.
2.  List the contents of the `.ssh` directory.
`ls -la`
1.  Install the nano text editor.
`sudo yum install nano`
1.  Enter your password at the prompt.
2.  Open the `authorized_keys` file in nano.
`nano authorized_keys`
1.  Add the key we just generated to the file.
2.  Press **Ctrl + X**.
3.  Press **Y** then **Enter** to save the changes.

## Exchange the SSH Keys between Server 1 and Server 2
1.  In your Server 2 terminal window, create a new key.
`ssh-keygen`
1.  Press **Enter** for the next three prompts.
2.  List the contents of the current directory.
`ls -la`
1.  List the contents of the `id_rsa.pub` file.
`cat id_rsa.pub`
1.  Copy the output of this command to your clipboard.
2.  Type `exit` to log out of Server 2.
3.  Install nano.
`sudo yum install nano`
1.  Type `y` to continue.
2.  List the contents of the current directory.
`ls -la`
1.  Open the `authorized_keys` file in nano.
`nano authorized_keys`
1.  Add the key we just generated to the file.
2.  Press **Ctrl + X**.
3.  Press **Y** then **Enter** to save the changes.

## Test the Configuration
1.  Attempt to log in to Server 2 from Server 1 without a password.
`ssh cloud_user@&lt;SERVER2PUBLIC_IP&gt;`
1.  Attempt to log in to Server 1 from Server 2 without a password.
`ssh cloud_user@&lt;SERVER1PUBLIC_IP&gt;`


CH 4, LAB 2



CH 4, LAB 3



CH 5, LAB 1



CH 5, LAB 2



CH 5, LAB 3



CH 6, LAB 1



CH 6, LAB 2



CH 6, LAB 3



CH 6, LAB 4



CH 6, LAB 5



CH 7, LAB 1



CH 7, LAB 2



CH 7, LAB 3



CH 8, LAB 1



CH 8, LAB 2



CH 8, LAB 3



CH 8, LAB 4



CH 9, LAB 1



CH 10, LAB 1



CH 10, LAB 2



CH 10, LAB 3
