As per details shared by the development team, the new application release has some dependencies on the back end. There are some packages/services that need to be installed on all app servers under `Stratos Datacenter`. As per requirements please perform the following steps:

a. Install `squid` package on all the application servers.

b. Once installed, make sure it is enabled to start during boot.

%% ssh stapp01 %% Ir0nM@n
ssh tony@stapp01
squid 
sudo yum install squid -y
systemctl status squid %% status advises squid.service %%
systemctl enable squid.service 
systemctl status squid.service

%% ssh stapp02 %% Am3ric@
ssh steve@stapp02 
sudo yum install squid -y
systemctl status squid.service
sudo systemctl enable squid.service
systemctl status squid.service

%% ssh stapp03 %% BigGr33n
ssh banner@stapp03
sudo yum install squid -y
sudo systemctl enable squid.service
systemctl status squid.service