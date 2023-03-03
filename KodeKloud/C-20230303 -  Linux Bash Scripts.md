The production support team of `xFusionCorp Industries` is working on developing some bash scripts to automate different day to day tasks. One is to create a bash script for taking websites backup. They have a static website running on `App Server 3` in `Stratos Datacenter`, and they need to create a bash script named `official_backup.sh` which should accomplish the following tasks. (Also remember to place the script under `/scripts` directory on `App Server 3`)
- a. Create a zip archive named `xfusioncorp_official.zip` of `/var/www/html/official` directory.
- b. Save the archive in `/backup/` on `App Server 3`. This is a temporary storage, as backups from this location will be clean on weekly basis. Therefore, we also need to save this backup archive on `Nautilus Backup Server`.
- c. Copy the created archive to `Nautilus Backup Server` server in `/backup/` location.
- d. Please make sure script won't ask for password while copying the archive file. Additionally, the respective server user (for example, `tony` in case of `App Server 1`) must be able to run it.

stapp03
172.16.238.12
stapp03.stratos.xfusioncorp.com
banner
BigGr33n
Nautilus App 3

%% shh into stapp03 %% BigGr33n
ssh banner@stapp03

%% create script %%
touch /scripts/official_backup.sh
sudo chmod +x /scripts/official_backup.sh
ll /scripts/official_backup.sh
echo 'zip -r /backup/xfusioncorp_official.zip /var/www/html/official' >/scripts/official_backup.sh
echo 'scp /backup/xfusioncorp_official.zip clint@stbkp01:/backup' >> /scripts/official_backup.sh 
cat /scripts/official_backup.sh  [confirm contents]

%% create permissions for the backup to go to the Nautilus Backup Server %%
ssh-keygen
ssh-copy-id clint@stbkp01
ssh clint@stbkp01 [check the connection]
exit

%% execute the script %%
./scripts/official_backup.sh [check the script]
ll /backup [check the temporary backup]
ssh clint@stbkp01
ll /backup [check the backup made it over to the server]