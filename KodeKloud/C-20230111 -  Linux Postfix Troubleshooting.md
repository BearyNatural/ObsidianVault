Some users of the monitoring app have reported issues with `xFusionCorp Industries` mail server. They have a mail server in `Stork DC` where they are using `postfix` mail transfer agent. `Postfix` service seems to fail. Try to identify the root cause and fix it.

stmail01
172.16.238.17
stmail01.stratos.xfusioncorp.com
groot
Gr00T123
Nautilus Mail Server

--SSH into the mail server:
ssh groot@172.16.238.17 -i .ssh/authorized_keys
Gr00T123   %%type password%% 
pwd
sudo -i
pwd
systemctl status postfix %%loaded & failed%%
chkconfig --list postfix %%error this is for systemV use the following command instead:%%
systemctl list-dependencies postfix %%or%% systemctl list-unit-files
systemctl start postfix
systemctl status postfix -l [this didn't show anything different to the above status command]
cat /etc/postfix/main.cf | grep inet_interface
vi %%or%% vim /etc/postfix/main.cf [# out the 'inet_interfaces = localhost' line]
cat /etc/postfix/main.cf | grep inet_interface
systemctl start postfix
systemctl status postfix
%%need to validate the task by telnet on port 25%%
telnet stmail01 25

#Finished