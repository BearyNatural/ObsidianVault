The system admins team of `xFusionCorp Industries` has set up a new tool on all app servers, as they have a requirement to create a service user account that will be used by that tool. They are finished with all apps except for `App Server 2` in `Stratos Datacenter`.

Create a user named `yousuf` in `App Server 2` without a home directory.

https://www.tecmint.com/add-users-in-linux/

stapp02
172.16.238.11
stapp02.stratos.xfusioncorp.com
steve
Am3ric@
Nautilus App 2

%%Login to Server - stapp02:%%
ssh steve@172.16.238.11 -i .ssh/authorized_keys
%%type password%% Am3ric@
pwd
sudo -i
%%Check if user exists: /etc/passwd%%
id username   %% this command is the only one that stipulates 'no such user' %%


%%Create user with non-interactive shell%%
adduser -M username


%%Check if user exists:%%
id username   %%# uid=1002(john) gid=1002(john) groups=1002(john) %%
ls -l /home/yousuf %%check to ensure no home directory has been created%%
cat /etc/passwd | grep username  %%# john:x:1002:1002::/home/john:/sbin/nologin %%
exit