The Nautilus team doesn't want its data to be accessed by any of the other groups/teams due to security reasons and want their data to be strictly accessed by the `sysadmin` group of the team.

Setup a collaborative directory `/sysadmin/data` on `Nautilus App 1` server in `Stratos Datacenter`.

The directory should be group owned by the group `sysadmin` and the group should own the files inside the directory. The directory should be `read/write/execute` to the group owners, and `others` should not have any access.

%% ssh into stapp02 %% Ir0nM@n
ssh tony@stapp01
ll / 
mkdir -p /sysadmin/data
ll /sysadmin/data
groupadd sysadmin %% group already exists %%
ll /etc/group*
cat /etc/group | grep sysadmin
chgrp --help
sudo chgrp -R /sysadmin
sudo chmod -R g+w /sysadmin
sudo chmod -R o-rx /sysadmin
ll / | grep sysadmin
ll /sysadmin | grep data %% your user no longer has permission to view :O %%

sudo -i
ll /sysadmin | grep data