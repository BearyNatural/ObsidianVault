There was some users data copied on `Nautilus App Server 2` at `/home/usersdata` location by the `Nautilus` production support team in `Stratos DC`. Later they found that they mistakenly mixed up different user data there. Now they want to filter out some user data and copy it to another location. Find the details below:

On `App Server 3` find all files (not directories) owned by user `javed` inside `/home/usersdata` directory and copy them all `while keeping the folder structure` (preserve the directories path) to `/media` directory.

https://serverfault.com/questions/180853/how-to-copy-file-preserving-directory-path-in-linux
https://explainshell.com/explain?cmd=find+.+-name+%27*.jpg%27+-exec+cp+--parents+%7B%7D+%2Ftarget+%3B

stapp03
172.16.238.12
stapp03.stratos.xfusioncorp.com
banner
BigGr33n
Nautilus App 3

%% ssh into stapp03 %% BigGr33n
ssh banner@stapp03
ll /home/usersdata %% 208 files %%
ll /media %% 0 fles%%
%% this didn't work more research required :'( 
cp --help
sudo cp -arp *.php* /home/usersdata /media
ll /media %%

ll /official %% 0 fles%%
sudo find /home/usersdata -type f -user javed | wc -l %% 1383 %% -exec cp -sudo find /home/usersdata -type f -user javed -exec cp --parents {} /media \;
ll /official %% drwxr-xr-x 3 root root 4096 Feb  6 03:50 home %%
ll /media/home/usersdata/

