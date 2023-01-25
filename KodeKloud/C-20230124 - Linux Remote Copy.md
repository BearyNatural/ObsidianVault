One of the `Nautilus` developers has copied confidential data on the jump host in `Stratos DC`. That data must be copied to one of the app servers. Because developers do not have access to app servers, they asked the system admins team to accomplish the task for them.

Copy `/tmp/nautilus.txt.gpg` file from jump server to `App Server 3` at location `/home/appdata`.

https://www.cybrosys.com/blog/copying-multiple-files-simultaneously-using-scp

stapp03
172.16.238.12
stapp03.stratos.xfusioncorp.com
banner
BigGr33n
Nautilus App 3

%% Confirm location & copy file to server %%
pwd %%/home/thor%%
ll /tmp/nautilus.txt.gpg %%-rw-r--r-- 1 root root 74 Jan 24 02:58 /tmp/nautilus.txt.gpg%%

scp /tmp/nautilus.txt.gpg banner@172.16.238.12:/home/appdata %%nautilus.txt.gpg                                                                                                            100%   74   295.8KB/s   00:00 %%

%% Confirm copied file is on server %%
ssh banner@172.16.238.12
ll /home/appdata %%total 4
-rw-r--r-- 1 banner banner 74 Jan 24 03:11 nautilus.txt.gpg%%

