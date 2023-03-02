We have some users on all app servers in `Stratos Datacenter`. Some of them have been assigned some new roles and responsibilities, therefore their users need to be upgraded with sudo access so that they can perform admin level tasks.
a. Provide sudo access to user `kirsty` on all app servers.
b. Make sure you have set up password-less sudo for the user.

%% stapp01 %% Ir0nM@n
ssh tony@stapp01 
sudo -i
vi /etc/sudoers
kirsty ALL=(ALL) NOPASSWD:ALL
exit
exit

%% stapp02 %% Am3ric@
ssh steve@stapp02
sudo -i
vi /etc/sudoers
kirsty ALL=(ALL) NOPASSWD:ALL
exit
exit

%% stapp03 %% BigGr33n
ssh banner@stapp03
sudo -i
vi /etc/sudoers
kirsty ALL=(ALL) NOPASSWD:ALL
exit
exit