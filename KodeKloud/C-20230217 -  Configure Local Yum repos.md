The `Nautilus` production support team and security team had a meeting last month in which they decided to use local yum repositories for maintaing packages needed for their servers. For now they have decided to configure a local yum repo on `Nautilus Backup Server`. This is one of the pending items from last month, so please configure a local yum repository on `Nautilus Backup Server` as per details given below.

a. We have some packages already present at location `/packages/downloaded_rpms/` on `Nautilus Backup Server`.
b. Create a yum repo named `localyum` and make sure to set `Repository ID` to `localyum`. Configure it to use package's location `/packages/downloaded_rpms/`.
c. Install package `wget` from this newly created repo.

stbkp01
172.16.238.16
stbkp01.stratos.xfusioncorp.com
clint
H@wk3y3
Nautilus Backup Server

%% ssh into stbkp01 %% H@wk3y3
ssh clint@stbkp01
sudo -i
yum repolist
mkdir /packages/downloaded_rpms/

vi /etc/yum.repos.d/localyum.repo
[localyum]
name=localyum
baseurl=file:///packages/downloaded_rpms/
enabled = 1
gpgcheck =0
cat /etc/yum.repos.d/localyum.repo

yum repolist
yum install wget -y
yum list wget

exit