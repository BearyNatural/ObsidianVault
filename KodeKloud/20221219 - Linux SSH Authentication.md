The system admins team of `xFusionCorp Industries` has set up some scripts on `jump host` that run on regular intervals and perform operations on all app servers in `Stratos Datacenter`. To make these scripts work properly we need to make sure the `thor` user on jump host has password-less SSH access to all app servers through their respective sudo users (i.e `tony` for app server 1). Based on the requirements, perform the following:
Set up a password-less authentication from user `thor` on jump host to all app servers through their respective sudo users.

%%this is about making sure you are logged in as thor and that it is password less%%
whoami
-- create keygen:
ssh-keygen -t rsa
%% press 'enter' key 3 times%%
-- now copy the public key to all the application servers
i.e. ssh-copy-id [user]@[appServ] for each

--Webservers #1 stapp01:
ssh-copy-id tony@stapp01
yes
Ir0nM@n  %%type password%% 
ssh tony@stapp01
whoami

--Webservers #2 stapp02:
ssh-copy-id steve@stapp02
yes
Am3ric@  %%type password%% 
ssh steve@stapp02
whoami

--Webservers #3 stapp03:
ssh-copy-id banner@stapp03
yes
BigGr33n  %%type password%% 
ssh banner@stapp03
whoami

%%
-- ssh into Webservers #1 stapp01:
pwd
ll -a
ll .ssh
ssh tony@172.16.238.10 -i .ssh/authorized_keys
%%type password%% Ir0nM@n
pwd
ll -a

exit

-- ssh into Webservers #2 stapp02:
ssh steve@172.16.238.11 -i .ssh/authorized_keys
%%type password%% Am3ric@
pwd
ll -a

exit

-- ssh into Webservers #3 stapp03:
ssh banner@172.16.238.12 -i .ssh/authorized_keys
%%type password%% BigGr33n
pwd
ll -a

exit

%%
