After doing some security audits of servers, `xFusionCorp Industries` security team has implemented some new security policies. One of them is to disable direct root login through SSH.

Disable direct SSH root login on all app servers in `Stratos Datacenter`.

%% ssh into stapp01 %%
ssh tony@stapp01
ll /etc/ssh*
sudo cat /etc/ssh/sshd_config | grep Root
sudo vi /etc/ssh/sshd_config %% PermitRootLogin no %%
sudo cat /etc/ssh/sshd_config | grep Root
sudo systemctl restart sshd
systemctl status sshd

%% ssh into stapp02 %% Am3ric@
ssh steve@stapp02
sudo vi /etc/ssh/sshd_config %% PermitRootLogin no %%
sudo cat /etc/ssh/sshd_config | grep Root
sudo systemctl restart sshd
systemctl status sshd

%% ssh into stapp03 %% BigGr33n
ssh banner@stapp03
sudo vi /etc/ssh/sshd_config %% PermitRootLogin no %%
sudo cat /etc/ssh/sshd_config | grep Root
sudo systemctl restart sshd
systemctl status sshd

exit