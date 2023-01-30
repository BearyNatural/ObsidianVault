The system admins team of xFusionCorp Industries has noticed intermittent issues with DNS resolution in several apps . `App Server 2` in `Stratos Datacenter` is having some DNS resolution issues, so we want to add some additional DNS nameservers on this server.

As a temporary fix we have decided to go with Google public DNS (ipv4). Please make appropriate changes on this server.

%% google public DNS for ipv4 is 8.8.8.8 %%

stapp02
172.16.238.11
stapp02.stratos.xfusioncorp.com
steve
Am3ric@
Nautilus App 2

%% ssh into stapp02 %%
ssh steve@stapp02
sudo su
vi /etc/resolv.conf %% add the following line to the doc:
nameserver 8.8.8.8 %%
cat /etc/resolv.conf

exit