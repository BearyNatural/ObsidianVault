There are new requirements to automate a backup process that was performed manually by the `xFusionCorp Industries` system admins team earlier. To automate this task, the team has developed a new bash script `xfusioncorp.sh`. They have already copied the script on all required servers, however they did not make it executable on one the app server i.e `App Server 2 in `Stratos Datacenter`.
Please give executable permissions to `/tmp/xfusioncorp.sh` script on `App Server 2`. Also make sure every user can execute it.

-- ssh into Webservers #2 stapp02:
pwd
ssh steve@172.16.238.11 -i .ssh/authorized_keys
%%type password%% Am3ric@
pwd
cd /tmp
ll -a
sudo chmod +rx xfusioncorp.sh
ll -a  # -r-xr-xr-x 1 root root   40 Dec 16 01:49 xfusioncorp.sh
sudo ./xfusioncorp.sh
exit

