The `Nautilus` system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in `Stratos DC` on a set schedule. Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below:

a. Install `cronie` package on all `Nautilus` app servers and start `crond` service.

b. Add a cron `*/5 * * * * echo hello > /tmp/cron_text` for `root` user.

%% stapp01 %% Ir0nM@n
ssh tony@stapp01
sudo -i
yum install cronie -y 
systemctl enable crond
systemctl start crond
systemctl status crond
ll /etc | grep 'cron'
crontab --help
crontab -e [`*/5 * * * * echo hello > /tmp/cron_text`]
crontab -l 
ll /tmp [you may have to wait a few mins to confirm the file is created]

%% stapp02 %% Am3ric@
ssh steve@stapp02
sudo -i
yum install cronie -y 
systemctl enable crond
systemctl start crond
systemctl status crond
crontab -e %% insert this in the file [`*/5 * * * * echo hello > /tmp/cron_text`] %%
crontab -l 
ll /tmp [you may have to wait a few mins to confirm the file is created]

%% stapp03 %% BigGr33n
ssh banner@stapp03
sudo -i
yum install cronie -y 
systemctl enable crond
systemctl start crond
systemctl status crond
crontab -e %% insert this in the file [`*/5 * * * * echo hello > /tmp/cron_text`] %%
crontab -l 
ll /tmp [you may have to wait a few mins to confirm the file is created]
