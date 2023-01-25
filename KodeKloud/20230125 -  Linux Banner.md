During the monthly compliance meeting, it was pointed out that several servers in the `Stratos DC` do not have a valid banner. The security team has provided serveral approved templates which should be applied to the servers to maintain compliance. These will be displayed to the user upon a successful login.

Update the `message of the day` on all application and db servers for `Nautilus`. Make use of the approved template located at `/home/thor/nautilus_banner` on jump host

https://medium.com/@keshavsaxena/update-banner-in-linux-servers-3d6832f95f44
https://www.cybrosys.com/blog/copying-multiple-files-simultaneously-using-scp

%% stapp 01 %%
ll /home/thor/nautilus_banner
cat /home/thor/nautilus_banner
scp /home/thor/nautilus_banner banner@stapp03:/tmp
ssh banner@stapp03
sudo mv /tmp/nautilus_banner /etc/motd
cat /etc/motd
exit
ssh banner@stapp03
%% banner should appear %%
exit
ctrl+l
%% stapp 02 %%
scp /home/thor/nautilus_banner steve@stapp02:/tmp
ssh steve@stapp02
sudo mv /tmp/nautilus_banner /etc/motd
cat /etc/motd
exit
ssh steve@stapp02
%% banner should appear %%
exit
ctrl+l
%% stapp 01 %%
scp /home/thor/nautilus_banner tony@stapp01:/tmp
ssh tony@stapp01
sudo mv /tmp/nautilus_banner /etc/motd
cat /etc/motd
exit
ssh tony@stapp01
%% banner should appear %%
exit
ctrl+l
%% db server %%
scp /home/thor/nautilus_banner peter@stdb01:/tmp %%this way doesn't work for the server%%
%%bash: scp: command not found - means need to install openssh-clients%%
ssh peter@stdb01
sudo yum install -y openssh-clients
exit
scp /home/thor/nautilus_banner peter@stdb01:/tmp
sudo mv /tmp/nautilus_banner /etc/motd
cat /etc/motd
exit
ssh peter@stdb01
%% banner should appear %%
exit