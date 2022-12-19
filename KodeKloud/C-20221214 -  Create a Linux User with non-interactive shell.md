The System admin team of `xFusionCorp Industries` has installed a backup agent tool on all app servers. As per the tool's requirements they need to create a user with a non-interactive shell.
Therefore, create a user named `john` with a non-interactive shell on the `App Server 3`

https://tldp.org/LDP/abs/html/intandnonint.html
https://www.nbtechsupport.co.in/2020/12/create-linux-user-with-non-interactive.html

pwd
ll -a
ll -a .ssh
%%Login to Server - stapp03:%%
ssh banner@172.16.238.12 -i .ssh/authorized_keys
%%type password%% BigGr33n


%%Check if user exists:%%
grep username /etc/passwd   %% # or%%
id username   %% # or%% %% this command is the only one that stipulates 'no such user' %%
cat /etc/passwd | grep username


%%Create user with non-interactive shell%%
adduser username -s /sbin/nologin


%%Check if user exists:%%
id username   %%# uid=1002(john) gid=1002(john) groups=1002(john) %%
cat /etc/passwd | grep username  %%# john:x:1002:1002::/home/john:/sbin/nologin %%
exit


