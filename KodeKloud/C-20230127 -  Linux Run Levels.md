New tools have been installed on the app server in `Stratos Datacenter`. Some of these tools can only be managed from the graphical user interface. Therefore, there are requirements for these app servers.

On all App servers in `Stratos Datacenter` change the default runlevel so that they can boot in `GUI (graphical user interface)` by default. Please do not try to reboot these servers

https://www.cyberciti.biz/howto/question/linux/changing-run-levels-3-5.php
https://www.tecmint.com/change-runlevels-targets-in-systemd/

%% stapp 01 %%
ssh tony@stapp01
cat /etc/inittab %% has instructions on how to change the runlevel %%
runlevel %% N 3 %%
systemctl get-default %% multi-user.target %%
sudo systemctl set-default graphical.target
systemctl get-default %% graphical.target %%
systemctl status graphical.target %% inactive %%
sudo systemctl start graphical.target 
systemctl status graphical.target %% active %%
runlevel %% 3 5 %%
exit 

%% stapp 02 %%
ssh steve@stapp02
runlevel %% N 3 %%
systemctl get-default %% multi-user.target %%
sudo systemctl set-default graphical.target
systemctl get-default %% graphical.target %%
systemctl status graphical.target %% inactive %%
sudo systemctl start graphical.target 
systemctl status graphical.target %% active %%
runlevel %% 3 5 %%
exit 

%% stapp 03 %%
ssh banner@stapp03
runlevel %% N 3 %%
systemctl get-default %% multi-user.target %%
sudo systemctl set-default graphical.target
systemctl get-default %% graphical.target %%
systemctl status graphical.target %% inactive %%
sudo systemctl start graphical.target 
systemctl status graphical.target %% active %%
runlevel %% 3 5 %%
exit 
