There is a critical issue going on with the `Nautilus` application in `Stratos DC`. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.
Look into the issue and fix the same.

stdb01
172.16.239.10
stdb01.stratos.xfusioncorp.com
peter
Sp!dy
Nautilus DB Server

--ssh into stdb01:
ssh peter@172.16.239.10 -i .ssh/authorized_keys
Sp!dy  %%type password%% 
pwd
ll -a
systemctl get-default %%multi-user.target%%
systemctl status 
%%● stdb01.stratos.xfusioncorp.com
    State: degraded
     Jobs: 0 queued
   Failed: 6 units
    Since: Tue 2022-12-20 23:48:35 UTC; 11min ago
   CGroup: /docker/612b26458dcf2a43373b9c5b54e2ba6210d102766926d8042b2d1e2ea595b033
           ├─1 /usr/sbin/init /usr/sbin/sshd -D
           └─system.slice
             ├─systemd-udevd.service
             │ └─295 /usr/lib/systemd/systemd-udevd
             ├─systemd-journald.service
             │ └─158 /usr/lib/systemd/systemd-journald
             ├─sshd.service
             │ ├─493 /usr/sbin/sshd -D
             │ ├─512 sshd: peter [priv]  
             │ ├─520 sshd: peter@pts/0   
             │ ├─521 -bash
             │ ├─540 systemctl status
             │ └─541 more
             ├─dbus.service
             │ └─435 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
             └─systemd-logind.service
               └─437 /usr/lib/systemd/systemd-logind%%
systemctl status mariadb %%
● mariadb.service - MariaDB database server
   Loaded: loaded (/usr/lib/systemd/system/mariadb.service; disabled; vendor preset: disabled)
   Active: inactive (dead)
Dec 21 00:03:19 stdb01.stratos.xfusioncorp.com systemd[1]: Collecting mariadb.service%%
sudo chkconfig --list mariadb %% this checks dependencies and configuration files etc, wasn't useful%%
systemctl start mariadb %%Job for mariadb.service failed because the control process exited with error code. See "systemctl status mariadb.service" and "journalctl -xe" for details.%%
systemctl status mariadb %%
● mariadb.service - MariaDB database server
   Loaded: loaded (/usr/lib/systemd/system/mariadb.service; disabled; vendor preset: disabled)
   Active: failed (Result: exit-code) since Wed 2022-12-21 00:14:26 UTC; 1min 7s ago
  Process: 590 ExecStartPre=/usr/libexec/mariadb-prepare-db-dir %n (code=exited, status=1/FAILURE)

Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com mariadb-prepare-db-dir[590]: Database MariaDB is not initialized, but the directory /var/lib/mysql is ... done.
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: Child 590 belongs to mariadb.service
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: mariadb.service: control process exited, code=exited status=1
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: mariadb.service got final SIGCHLD for state start-pre
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: mariadb.service changed start-pre -> failed
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: Job mariadb.service/start finished, result=failed
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: Failed to start MariaDB database server.
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: Unit mariadb.service entered failed state.
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: mariadb.service failed.
Dec 21 00:14:26 stdb01.stratos.xfusioncorp.com systemd[1]: mariadb.service: cgroup is empty
Hint: Some lines were ellipsized, use -l to show in full.%%
sudo journalctl --filesystem.journal %%incorrect%%
ll /var/lib/mysql %% no such file or directory exists%%
sudo -i
ll /var/lib/mysql %% no such file or directory exists%%
cd /var
ll -a
cd /lib %%can't see sql in here??%%
cd /mysql %%not here%%
cd ~
ll /var/lib %%now shows mysqld?? super weird, file is empty, permissions are correct
drwxr-xr-x 2 mysql mysql 4096 Oct  1  2020 mysqld%%

--if ownership doesn't match the above:
chown mysql:mysql /var/run/mysqld
chownmysql:mysql /var/run
chown mysql:mysql /var/run/mariadb/
ll -lsd /var/run/mariadb/

--if ownership is fine continue:
mv /var/lib/mysqld/ /var/lib/mysql
ll /var/lib/ %% confirmed change%%
-- now start the service
systemctl start mariadb
systemctl status mariadb %%confirmed is running and active%%
exit %%sudo -u%%
exit
