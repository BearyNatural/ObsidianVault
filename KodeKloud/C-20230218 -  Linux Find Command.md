During a routine security audit, the team identified an issue on the Nautilus App Server. Some malicious content was identified within the website code. After digging into the issue they found that there might be more infected files. Before doing a cleanup they would like to find all similar files and copy them to a safe location for further investigation. Accomplish the task as per the following requirements:

a. On `App Server 3` at location `/var/www/html/news` find out all files (not directories) having `.php` extension.
b. Copy all those files along with their `parent directory structure` to location `/news` on same server.
c. Please make sure not to copy the entire `/var/www/html/news` directory content.

stapp03
172.16.238.12
stapp03.stratos.xfusioncorp.com
banner
BigGr33n
Nautilus App 3

%% ssh into stapp03 %% BigGr33n
ssh banner@stapp03
ll /var/www/html/news  
ll / %% confirmed location %%
ll /news %% empty directory %%

%% they specifically say copy not move... so only copy %%
find /var/www/html/news -type f -name '*.php* ' %% lots of .php files %%

sudo find /var/www/html/news -type f -name '*.php*' -exec cp --parents {} /news \;








