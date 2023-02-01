A developer mark has been assigned `Nautilus` project temporarily as a backup resource. As a temporary resource for this project, we need a temporary user for mark. It’s a good idea to create a user with a set expiration date so that the user won't be able to access servers beyond that point.

Therefore, create a user named `mark` on the `App Server 1`. Set `expiry date` to `2021-03-28` in `Stratos Datacenter`. Make sure the user is created as per standard and is in lowercase.

stapp01
172.16.238.10
stapp01.stratos.xfusioncorp.com
tony
Ir0nM@n
Nautilus App 1

%% ssh into stapp01 %%
ssh tony@stapp01
sudo -i

%% check that username isn't already taken %%
grep mark /etc/passwd %% no response %%
id mark %% id: mark: no such user %%

%% Add user & confirm add %%
useradd --help
useradd mark
id mark %% uid=1002(mark) gid=1002(mark) groups=1002(mark) %%

%% modify user for expiration & confirm change %%
usermod mark -e 2021-03-28
chage --help
chage -l mark %%
Last password change                                    : Feb 01, 2023
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : Mar 28, 2021
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7 %%

exit